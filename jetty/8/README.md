## Jetty 8

A simple docker build for installing a vanilla Jetty 8 below
*/opt/jetty*. It comes out of the box and is intended for use in 
integration tests

During startup a directory specified by the environment variable `DEPLOY_DIR`
(*/maven* by default) is checked for .war files. If there
are any, they are linked into Jetty's *webapps/* directory for automatic
deployment. This plays nicely with the Docker maven plugin from
https://github.com/rhuss/docker-maven-plugin/ and its 'assembly' mode which
can automatically create Docker data container with Maven artifacts
exposed from a directory */maven*


Features:

* Jetty Version: **8.1.17.v20150415**
* Java Version: **OpenJDK 1.7.0_60 (7u60-2.5.0-2)** (base image: *fabric8/base-sti*)
* Port: **8080**
* Command: `/opt/jetty/bin/deploy-and-run.sh` which links .war files from */maven* to 
  */opt/jetty/webapps* and then calls `/opt/jetty/bin/jetty.sh run`
* Sets `-Djava.security.egd=file:/dev/./urandom` for faster startup times
  (though a bit less secure)
