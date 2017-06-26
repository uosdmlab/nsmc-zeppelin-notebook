# Zeppelin 노트북: Naver Sentiment Movie Corpus Word2Vec & Classification
> 2017년 6월 27일 (화) **Spark Day 2017**의 세션 **Spark & Zeppelin을 활용한 한국어 텍스트 분류** 발표에 사용된 노트북입니다.

> 슬라이드: [Spark & Zeppelin을 활용한 한국어 텍스트 분류](https://www.slideshare.net/JunKim22/spark-zeppelin-77273056)

## 노트북 개요
네이버 영화 리뷰 데이터셋에 대해 Word2Vec을 적용해보고 감성 분류를 합니다. (영화 리뷰가 긍정적인지 부정적인지)

## 미리 보기: ZEPL Viewer

[전체 목록](https://www.zepl.com/search?q=nsmc) (총 7개의 노트)

* [0.Settings][2]
* [1.NSMC][3]
* [2.Spark NKP][4]
* [3.TF & TF-IDF][5]
* [4.Word2Vec][6]
* [5.Word2VecViz][7]
* [6.Classification][8]

[1]:https://www.zepl.com/search?q=nsmc
[2]:https://www.zepl.com/viewer/notebooks/bm90ZTovL2p1bi9jMDAwZjAxM2U4ZDc0ZGE1OGNlYTEyYzhhOTk3ZGI3Yi9ub3RlLmpzb24
[3]:https://www.zepl.com/viewer/notebooks/bm90ZTovL2p1bi8yMGMwZjNiMmEzYzY0ZjNmODhiM2NkMjk2M2FmYTg0My9ub3RlLmpzb24
[4]:https://www.zepl.com/viewer/notebooks/bm90ZTovL2p1bi9OU01DLzNjNGFiYTk1Y2IzYjQ1N2Q4NzMwNGI2YTVjMTUwMTJlL25vdGUuanNvbg
[5]:https://www.zepl.com/viewer/notebooks/bm90ZTovL2p1bi84NWJlZmUyY2FiNjc0MjczYmMyM2ZkZWJlNDcxN2ZiZC9ub3RlLmpzb24
[6]:https://www.zepl.com/viewer/notebooks/bm90ZTovL2p1bi9OU01DL2FiMGRjZWVmZTViZTRlYjI4YmFjYWU1ZWNkMmRmMjQxL25vdGUuanNvbg
[7]:https://www.zepl.com/viewer/notebooks/bm90ZTovL2p1bi9OU01DLzY0NTBmZTRlZmM2ODRmZTBhOWNhNGQxYmU2NzA1ZTIxL25vdGUuanNvbg
[8]:https://www.zepl.com/viewer/notebooks/bm90ZTovL2p1bi9OU01DL2Q3ZTA5NGI0NjY4YTRmNzRhNjk0Y2RlYjM0YzY2MjhlL25vdGUuanNvbg

## Naver Sentiment Movie Corpus
네이버 영화 리뷰 데이터셋입니다. 총 20만개의 리뷰로 구성되어 있으며 긍정적인 리뷰는 1, 부정적인 리뷰는 0으로 labeling 되어 있습니다. 자세한 내용은 아래의 출처를 참고해주세요!
> 출처: https://github.com/e9t/nsmc

## 사용법
> Spark와 Zeppelin은 설치하셨다고 가정합니다.

### 1. 노트북 추가하기
저장소를 원하는 곳에 복제합니다.

```bash
git clone git@github.com:uosdmlab/playdata-zeppelin-notebook.git
```

#### 방법1. 노트북 복사
복제한 저장소의 `notebook` 디렉터리 안의 내용물들을 `$ZEPPELIN_HOME/notebook/` 밑으로 복사

#### 방법2. 노트북 폴더 설정
> 기존에 사용하던 노트들과 저장소의 노트들이 섞이는 것이 싫다면 추천하는 방법!

`$ZEPPELIN_HOME/conf/zeppelin-env.sh` 파일을 열어 다음과 같은 라인 추가.

```bash
export ZEPPELIN_NOTEBOOK_DIR="<저장소경로>/notebook"
```

추가 후 Zeppelin을 재시작합니다.

```bash
$ZEPPELIN_HOME/bin/zeppelin-daemon.sh restart
```

다시 원래 노트들을 사용하려면 `$ZEPPELIN_HOME/conf/zeppelin-env.sh`에 추가한 라인을 지우거나 주석처리하고 Zeppelin을 재실행하시면 됩니다.

### 2. Dependency 추가
한국어 형태소 분석기 [spark-nkp](https://github.com/uosdmlab/spark-nkp)을 사용하기 위해 Spark interpreter dependency에 다음과 같이 추가해주세요.

**artifact** `com.github.uosdmlab:spark-nkp_2.11:0.2.1`

### Issue
GitHub issue로 올려주셔도 되고(한국어 가능), 아래 주소로 메일주셔도 됩니다.

김태준(i2r.jun@gmail.com)

[Data Mining Lab, University of Seoul](datamining.uos.ac.kr)
