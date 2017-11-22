# Description

This is a test-scenarion to demonstrate that the wait on a docker container log doesn't
work with Docker for Windows Community Edition.

The project contains just one image configuration to start the currently stable
mongo-db image `(mongo:3.0.15)` and waits for the log output containing
the log pattern `'waiting for connections'`.

# How to reproduce

You can reproduce the failing behavior either with:

```shell
mvn clean install
```

or just:

```shell
mvn docker:start
```

The log output shows the following output:

```shell
mvn docker:start
[INFO] Scanning for projects...
[INFO]
[INFO] ------------------------------------------------------------------------
[INFO] Building docker-maven-plugin-waitlog-scenario 0.0.1
[INFO] ------------------------------------------------------------------------
[INFO]
[INFO] --- docker-maven-plugin:0.23.0:start (default-cli) @ docker-maven-plugin-waitlog-scenario ---
[INFO] DOCKER> [mongo:3.0.15] "database": Start container 29d1ec81789c
```

# Observed behaviour

After starting the maven docker:start goal and given the logs above, the maven build
hangs forever.

# Tested versions

Windows 10 Pro Version 1703 Build 15063.726 having all current updates  
Apache Maven 3.3.9 (bb52d8502b132ec0a5a3f4c09453c07478323dc5; 2015-11-10T17:41:47+01:00)  
Docker Maven Plugin io.fabric8:docker-maven-plugin:0.23.0  
Docker for Windows Edge Version 17.11.0-ce-rc4-win39 (14244) and Stable Version 17.09.0-ce-win33 (13620)  