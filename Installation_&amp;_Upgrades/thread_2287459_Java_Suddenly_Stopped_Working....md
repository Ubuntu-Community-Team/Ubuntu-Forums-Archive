---
title: "Java Suddenly Stopped Working..."
date: 2015-07-19
forum: Installation &amp; Upgrades
---

### Post by chome4 on 2015-07-19
Using Ubuntu 14.04.2 LTS with 

Java(TM) SE Runtime Environment (build 1.8.0_45-b14)
Java HotSpot(TM) Server VM (build 25.45-b02, mixed mode)

When using a program that requires Java, I now get the message: Unable to launch the application. When I 

Under 'Details', I get two tabs.

The first tab, Launch File, I get:

<jnlp spec="1.0+" codebase="https://www.prorealtime.com//">
  <information>
    <title>ProRealTime Complete</title>
    <vendor>ProRealTime</vendor>
    <homepage href="https://www.prorealtime.com"/>
    <description>ProRealTime - Complete workstation</description>
    <description kind="short">ProRealTime - Complete workstation</description>
    <icon href="https://www.prorealtime.com/en/images/logo.gif?c1400826628c" kind="splash"/>
    <icon href="https://www.prorealtime.com/images/icon.png?c1422978832c"/>
  </information>
  <security>
    <all-permissions/>
  </security>
  <resources>
    <property name="jnlp.packEnabled" value="true"/>
    <j2se version="1.6.0+" href="http://java.sun.com/products/autodl/j2se" max-heap-size="1024M" java-vm-args="-noverify"/>
    <jar href="https://www.prorealtime.com/java/ProRealTime-10.2-20150627010001-main.jar" main="true" download="eager"/>
    <jar href="https://www.prorealtime.com/java/ProRealTime-10.2-20150627010001.jar" download="eager"/>
    <jar href="https://www.prorealtime.com/java/ProRealTime-10.2-20150627010001-en.jar" download="eager"/>
  </resources>
  <application-desc>
    <argument>http://c.rt1.e.prorealtime.com/ProRealTimeNew/</argument>
    <argument>8938d57e1683e1cad4484b8859b62e02e05cd3895c209d9322417a40dfe62c01</argument>
    <argument>lang=en_GB_ProRealTime|url_server=https://www.prorealtime.com/|mainframetitle=ProRealTime Complete|url_custom_memory=../en/manage_memory|ws_path=services/serverlist|pkey=305cb1f77fc9b36d1415462f7fe2d7daafe5e994194787f2aaeb1b05dbe7b39f|prt_key=086713d4d1bbbf02a7eb8200939e333fb81b84322a13f95a64de3056d08362f1|prttrading=t|licence=Complete|server_encoding=UTF-8|sign=8be0f9e6a5f948f09c8db3ba2b9bf682c5cb32490bb847d31ee2f0fdb0269af4</argument>
  </application-desc>
</jnlp>
======================================================================================================

The second tab, 'Exception', I get:

java.io.IOException: JNLP Jar download failure.
    at com.sun.javaws.LaunchDownload.validateResults(Unknown Source)
    at com.sun.javaws.LaunchDownload.downloadJarFiles(Unknown Source)
    at com.sun.javaws.LaunchDownload.downloadEagerorAll(Unknown Source)
    at com.sun.javaws.Launcher.downloadResources(Unknown Source)
    at com.sun.javaws.Launcher.prepareResources(Unknown Source)
    at com.sun.javaws.Launcher.prepareAllResources(Unknown Source)
    at com.sun.javaws.Launcher.prepareToLaunch(Unknown Source)
    at com.sun.javaws.Launcher.prepareToLaunch(Unknown Source)
    at com.sun.javaws.Launcher.launch(Unknown Source)
    at com.sun.javaws.Main.launchApp(Unknown Source)
    at com.sun.javaws.Main.continueInSecureThread(Unknown Source)
    at com.sun.javaws.Main.access$000(Unknown Source)
    at com.sun.javaws.Main$1.run(Unknown Source)
    at java.lang.Thread.run(Thread.java:745)

======================================================================================================
I follow the instructions below to install Java:

sudo add-apt-repository ppa:webupd8team/java

sudo apt-get update

sudo apt-get install oracle-java8-installer

But 'java -version' gives 

java version "1.8.0_45"
Java(TM) SE Runtime Environment (build 1.8.0_45-b14)
Java HotSpot(TM) Server VM (build 25.45-b02, mixed mode)

The current update for version 8 is 51 and I have 45.

I installed this months ago via terminal with instructions I found online but I can't seem to find references to installing new updates.

How do I, via terminal, install update 51?

Thanks in advance.

---

