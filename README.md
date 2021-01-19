## Docker Image for Android CI
You can use this image for building your Android app within your CI.

<a href="https://hub.docker.com/repository/docker/seanghay/android-ci-node">
        <img src="https://img.shields.io/docker/pulls/seanghay/android-ci-node.svg"
            alt="Pulls"></a> 

```sh
docker pull seanghay/android-ci-node:latest
```

-----

## Usage in GitLab CI

```yaml
image: seanghay/android-ci-node

before_script:
    - chmod +x ./gradlew
    
stages:
    - build

cache:
  paths:
    - .gradle/wrapper
    - .gradle/caches

assembleDebug:
    stage: build
    script:
        - ./gradlew assembleDebug
        - cp app/build/outputs/apk/debug/app-debug.apk app-debug.apk
    artifacts:
        paths:
            - app-debug.apk
           
```
