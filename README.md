# 관리자 웹 디렉토리 구조

관리자 웹은 model과 controller만 존재하는 백엔드와, view를 위한 프론트엔드가 있습니다.

백엔드에는 node.js와 express를 사용하였고, 프론트엔드는 create-react-app를 통해 만든 react 프로젝트를 사용하였습니다.

## 프로젝트 구조
```
frontend/ (create-react-app)
backend/ (node.js + express)
```

## 개발 시 주의할 점
1. 윈도우 배포를 위해서는 파이썬, Visual Studio가 필요합니다.
2. 도커 컨테이너를 사용하지 않을 경우, `backend/model/index.js`에서 `dbPath`를 변경해주세요.
3. backend/ 하단에 uploads 폴더를 만들어주세요!!

## 도커 파일 사용법
1. [Docker Desktop](https://hub.docker.com/search?q=&type=edition&offering=community&sort=updated_at&order=desc)을 다운로드 받습니다.
2. 현재 디렉토리에서 다음 명령어를 실행하여 도커 이미지를 만듭니다.
```
docker build . --tag at-lab
```
3. 다음 명령어를 실행하여 도커 컨테이너를 만듭니다.
```
docker run -it -p 3000:3000 -p 5000:5000 -v {사용자_앱_static_폴더_경로}:/mnt --name admin at-lab
```
4. 다음 명령어를 사용하여 도커 컨테이너를 실행하면, backend와 frontend가 모두 실행됩니다.
```
docker start admin
```
5. 코드 수정을 위해서는 다음 명령어를 사용하여 도커 컨테이너에 진입하여 주십시오.
```
docker exec -it admin sh
```