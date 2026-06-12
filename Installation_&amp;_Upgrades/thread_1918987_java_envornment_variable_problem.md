---
title: "java envornment variable problem"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by blaablaa on 2012-02-02
```
paritosh@paritosh-laptop:~$ sudo su 
[sudo] password for paritosh: 
bash: export: `=': not a valid identifier
bash: export: `/usr/lib/jvm/ava-6-openjdk': not a valid identifier
root@paritosh-laptop:/home/paritosh# ant -version
Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-6-openjdk/lib/tools.jar
Apache Ant(TM) version 1.8.2 compiled on December 20 2010
root@paritosh-laptop:/home/paritosh# sudo update-alternatives --config java
There is only one alternative in link group java: /usr/lib/jvm/java-6-openjdk/jre/bin/java
Nothing to configure.
root@paritosh-laptop:/home/paritosh# 

```i want to sent java_home environment  variable , so i did some config somewhere in file , dont know where . After configuring , this ```

bash: export: `=': not a valid identifier
bash: export: `/usr/lib/jvm/ava-6-openjdk': not a valid identifier

```problem arises .  Please help me to fix .
I did setting of java environment variable and it works fine . ( followed this post : [http://ubuntuforums.org/showthread.php?t=1491846](http://ubuntuforums.org/showthread.php?t=1491846) ) 
Now the second problem , when i execute ant -version , it shows me 
```
Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-6-openjdk/lib/tools.jar
```, so i followed this post ( [http://www.imlucas.com/post/263896412/ubuntu-fix-for-unable-to-locate-tools-jar-expected-to](http://www.imlucas.com/post/263896412/ubuntu-fix-for-unable-to-locate-tools-jar-expected-to) )  and hang on this situation . Please help me .

---

