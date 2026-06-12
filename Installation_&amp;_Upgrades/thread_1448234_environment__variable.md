---
title: "environment  variable"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by saramery on 2010-04-06
Hello 

jdk was installed as described with the following steps: 

```
chmod ax jdk-1_5_0_04-linux-i586.bin (you make your file executable) 
./jdk-1_5_0_04-linux-i586.bin (you running the install) 
You answer the questions then heads (normally you can leave tt default). 
It's gonna create a directory jdk1.5.0_04, you can move in / opt / eg. 

    sudo mv jdk1.5.0_04 / / opt / 

Then you add this file in your ~ /. Bashrc (at home I do like that - you can edit the file / etc / environment if you prefer): 

    PATH = / opt/jdk1.5.0_04/bin: $ PATH 
    JAVA_HOME = / opt/jdk1.5.0_04 / 
    JDK_HOME = / opt/jdk1.5.0_04 / 

    export PATH 
    export JAVA_HOME 
    Export JDK_HOME 

Attention has to adapt according to where you install java (for me it is / opt/jdk1.5.0_04) 

Then, when you open a new terminal, you will have java (you can type "java-version" to see if it is ok). And if you really bothered to restart a terminal, do "source ~ /. Bashrc") 

    $ Java-version 
    java version "1.5.0_04" 
    Java (TM) 2 Runtime Environment, Standard Edition (build 1.5.0_04-B05) 
    Java HotSpot (TM) Client VM (build 1.5.0_04-B05, mixed mode, sharing) 

```after it was installed Tomcat as follows: 

```
# Sudo mkdir / opt / tomcat 
# Cd / opt / tomcat 
# Tar-zxf jakarta-tomcat-4.1.30.tar.gz 
# Sudo adduser - system - home / home / intranet / programs / tomcat - shell / bin / true - disabled-password tomcat 
# Sudo chown tomcat: root / opt / tomcat / * 
# Sudo chown-R root: root / opt / tomcat / * 
and to launch Tomcat j'utlise the following command: 
sudo sh / opt/tomcat/apache-tomcat-6.0.26-src/bin/startup.sh 

```This gives the following error: 
[COLOR=Red]Neither the JAVA_HOME nor the [/COLOR][COLOR=Red]JRE_HOME [/COLOR][COLOR=Red]environment variable is defined   [/COLOR]
Please help me solve this problem, it's been a week since I'm on this same problem

---

