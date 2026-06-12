---
title: "Is there a trusted way to install Gradle 2.0 in Ubuntu 14.04 lts ?"
date: 2014-08-28
forum: Installation &amp; Upgrades
---

### Post by ricardo072 on 2014-08-28
Hi All,

I have tried to install Gradle from the Ubuntu Software Center, but there is a bug when Gradle is installed from there, basically Gradle finds wrong JAVA_HOME, the particular Gradle binary I downloaded from the Ubuntu 14.04 repository itself tries to export JAVA_HOME, the /usr/bin/gradle says:

export JAVA_HOME=/usr/lib/jvm/default-java

richard@richard-EP35-DS3L:~$ java -version
java version "1.8.0_20"
Java(TM) SE Runtime Environment (build 1.8.0_20-b26)
Java HotSpot(TM) 64-Bit Server VM (build 25.20-b23, mixed mode)

I was trying several things and there is nothing useful on the web so I have uninstalled it from the Ubuntu Software Center, as far as I can see it shouldn't be installed from the package manager, [one post from the web]("http://stackoverflow.com/questions/22307516/gradle-finds-wrong-java-home-even-though-its-correctly-set") says that if you just download the binary from their website it does not have this problem, but says nothing about how to do it.. 

could you please tell me how can Gradle 2.0 can be installed in ubuntu 14.04 LTS using the binary from [http://www.gradle.org/downloads](http://www.gradle.org/downloads) ?

Thank you and looking forward to hearing from you.
Best regards.

---

### Post by claracc on 2014-08-29
Here, [http://tutorialforlinux.com/2014/05/11/how-to-install-and-getting-started-with-gradle-automation-tool-on-ubuntu-14-04-trusty-lts-easy-guide/](http://tutorialforlinux.com/2014/05/11/how-to-install-and-getting-started-with-gradle-automation-tool-on-ubuntu-14-04-trusty-lts-easy-guide/) you have a step by step guide to install gradle.

As you have the required java installed, I understand you can skip steps 3 and 4.

---

### Post by ricardo072 on 2014-08-29
Hey claracc,

This is great... I will do it as soon as I can.. right now I'm in the office and that is for my PC in home...

Thanks
Best regards.

---

### Post by claracc on 2014-08-30
You are very welcome.

---

### Post by ricardo072 on 2014-08-31
Hi Claracc,

I have some bad news... I followed exactly the steps described on your link:
[http://tutorialforlinux.com/2014/05/11/how-to-install-and-getting-started-with-gradle-automation-tool-on-ubuntu-14-04-trusty-lts-easy-guide/](http://tutorialforlinux.com/2014/05/11/how-to-install-and-getting-started-with-gradle-automation-tool-on-ubuntu-14-04-trusty-lts-easy-guide/)

... everything went fine, no errors, but at the end in point # 8, when I was trying the gradle version, this is the output:

richard@richard-EP35-DS3L:~$ gradle -v
The program 'gradle' is currently not installed. You can install it by typing:
sudo apt-get install gradle

Could you please give me your advice at this point?

Thanks,
Best regards.

---

### Post by claracc on 2014-08-31
You can  try in a xterm (ctrl+alt+t) to run the installation command:

```
sudo apt-get install gradle
```

and then test the version installed with 

```
gradle -v
```

I have read other links, referring to how to install gradle through ppa: [https://launchpad.net/~cwchien/+archive/ubuntu/gradle?field.series_filter=trusty](https://launchpad.net/~cwchien/+archive/ubuntu/gradle?field.series_filter=trusty), you have to add the ppa to your repositories and the install the package: [http://askubuntu.com/questions/328178/gradle-in-ubuntu](http://askubuntu.com/questions/328178/gradle-in-ubuntu)

---

### Post by ricardo072 on 2014-08-31
Hi Claracc,

Everything is a mess... I have tryied with sudo apt-get install gradle

richard@richard-EP35-DS3L:~$ gradle -v

ERROR: JAVA_HOME is set to an invalid directory: /usr/lib/jvm/default-java

Please set the JAVA_HOME variable in your environment to match the
location of your Java installation.

This particular Gradle binary I downloaded from the Ubuntu 14.04 repository itself tries to export JAVA_HOME, the /usr/bin/gradle says:

export JAVA_HOME=/usr/lib/jvm/default-java

Do you know how to fix it and point it to /usr/lib/jvm/java-8-oracle ? I mean, the list of commands I need to execute in the console...


I appreciate your help,
Thanks,
Best regards.

---

### Post by ricardo072 on 2014-08-31
Hi All,

I have just found this article:
[http://forums.gradle.org/gradle/topics/export_java_home_usr_lib_jvm_default_java_in_gradle_shell_script](http://forums.gradle.org/gradle/topics/export_java_home_usr_lib_jvm_default_java_in_gradle_shell_script)

But as far as I can see is just a workaround, not a fix.. I can use it ?


Thanks,
Best regards

---

### Post by ricardo072 on 2014-09-01
Hi Claracc,

I was able to edit the gradle script using:   sudo gedit /usr/bin/gradle
and I fixed this line as follows:  export JAVA_HOME=/usr/lib/jvm/java-8-oracle

The topic now is that I have an old version:

richard@richard-EP35-DS3L:~$ gradle -v

------------------------------------------------------------
Gradle 1.4
------------------------------------------------------------

Gradle build time: Monday, September 9, 2013 8:44:25 PM UTC
Groovy: 1.8.6
Ant: Apache Ant(TM) version 1.9.3 compiled on April 8 2014
Ivy: non official version
JVM: 1.8.0_20 (Oracle Corporation 25.20-b23)
OS: Linux 3.13.0-35-generic amd64

Do you know how can I update it to vers. Gradle 2.0 ?

Thanks,
Best regards.

---

### Post by ricardo072 on 2014-09-01
Hi Claracc & All,

Here is the best way to install or update the last gradle version:
[http://wtanaka.com/node/8079](http://wtanaka.com/node/8079)

I appreciate Claracc for your help and advice,.. after all I have found the answer...

Thanks,
Best regards.

---

### Post by claracc on 2014-09-02
So, you could install gradle 2.0 through ppa:cwchien/?, I was reading a lot of threads and it seemed there were certain bugs in old gradle versions as 1.4. Installation of gradle software through ppa seems to be the easiest and secure way as you have proved.

Very glad you got fixed your problem.

Regards.

---

