# TP 2

## 2-1
Les testcontainers sont dans la bibliotheque java

## 2-2 Document your Github Actions configurations.

```yaml
name: CI devops 2023
on:
  #to begin you want to launch this job in main and develop
  push:
    branches:
      - main
      - develop
  pull_request:

jobs:
  test-backend:
    runs-on: ubuntu-22.04
    steps:
      #checkout your github code using actions/checkout@v2.5.0
      - uses: actions/checkout@v2.5.0

      #do the same with another action (actions/setup-java@v3) that enable to setup jdk 17
      - name: Set up JDK 17
        uses: actions/setup-java@v3
        with:
          java-version: '17'
          distribution: 'adopt'

      #finally build your app with the latest command
      - name: Build and test with Maven
        run: mvn clean verify -f BackendApi/simple-api-student-main/ #-f to the folder where the pom file is
```

