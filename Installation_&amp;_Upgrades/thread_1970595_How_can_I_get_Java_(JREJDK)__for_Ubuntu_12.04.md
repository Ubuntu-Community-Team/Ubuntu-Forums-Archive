---
title: "How can I get Java (JRE/JDK)  for Ubuntu 12.04?"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by ricardo072 on 2012-05-01
Hi All,

Right now, I have a clean installation of Ubuntu 12.04 x64 (Desktop Ed.) on my machine,.. I'm not an ubuntu guru, so please help me, I would like to to know:

1) how can I install Java Version 6 Update 31 (or the most current 6.XX vers) ?? 
2) I need the JRE and the JDK for development. (I'm assuming/guessing that I already have installed the JRE, but not sure how to check if I already have the JRE)
3) do you know how and where can I declare and set the java environment variables (JAVA_HOME and the classpath) ?? (what I mean is, something similar to windows environment variables).

Thanks in advance,
Best regards.

---

### Post by oldos2er on 2012-05-01
[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by lykeion on 2012-05-01
OP needs JDK and JRE, easylinux-link in above post is only a guide to install JRE and plugin.

Installing Oracle (Sun) Java 6 JDK/JRE see here: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Setting JAVA_HOME path by adding these lines to ~/.bashrc
```
JAVA_HOME=<your_path>
export PATH=$PATH:$JAVA_HOME
```

---

### Post by ricardo072 on 2012-05-01
> **lykeion said:**
> Setting JAVA_HOME path by adding these lines to ~/.bashrc
```
JAVA_HOME=<your_path>
export PATH=$PATH:$JAVA_HOME
```

I really appreciate your help,.. anyway, could you please give me an example?

- where is the  ~/.bashrc ?
- Should I add those lines at the EOF ?
- what does <your_path> means exactly ? my home directory ? Is this path absolute, right?

---

### Post by SingingBush on 2012-05-01
when saying <your_path> lykeion is meaning that you have to put the path to wherever you put the JDK on your system there.

The ~ symbol is a shortcut to your user directory. so ~/.bashrc is the same as writing /home/USERNAME/.bashrc

bashrc is a hidden file (the . means hidden). You should probably first find out about using basic terminal commands and a command line text editor such as nano, vim, or emacs before doing this. (vim is good).

---

### Post by lykeion on 2012-05-02
Sorry if was a bit unclear, it would be a bit easier to help you if you said exactly what are you trying to do. Are you setting up a jdk environment to develop java applications or something else?

If you are using the script from [https://github.com/flexiondotorg/oab-java6](https://github.com/flexiondotorg/oab-java6) (as mentioned in the above ubuntu community help link) to install jdk you'll also set system-wide path to java and the java compiler (javac) so you wouldn't have to specify any JAVA_HOME variable.

---

### Post by ricardo072 on 2012-05-02
> **lykeion said:**
> Sorry if was a bit unclear, it would be a bit easier to help you if you said exactly what are you trying to do. Are you setting up a jdk environment to develop java applications or something else?

Yes, I did not do anything so far, but I would like to set up a java development envirionment. 

I'm a little worry about it.. according to [https://help.ubuntu.com/community/Java;](https://help.ubuntu.com/community/Java;) 

1.- Oracle (Sun) Java 6 is no longer available to be distributed by Ubuntu, because of license issues....... "It is recommended that users either migrate to OpenJDK, or download and install the newest version of Oracle (Sun) Java 6 manually, or switch to Oracle Java 7.

2.- Oracle Java 7 is probably at this time not as fit for general use, as OpenJDK and Oracle (Sun) Java 6.

3.- So,... the best option under this scenario right now would be install:

- the openjdk-6-jre package, 
- the icedtea6-plugin package and,
- the openjdk-6-jdk package using any installation method.


is this right ??

---

### Post by sammiev on 2012-05-02
I always used post # 2. Works great. :)

---

### Post by ricardo072 on 2012-05-02
[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java) ??

will be working fine for ubuntu 12.04 64-bits?

:confused:

---

### Post by sammiev on 2012-05-02
Been using it on 12.04 since it was pre alpha. Instructions are on the left for 32 bit and right hand side for 64 bit.

---

### Post by The Cog on 2012-05-02
I would just do:
```
sudo apt-get install openjdk-6-jdk openjdk-6-doc
```
The jdk has a jre built into it so you don't need a separate one.

I always found that I didn't need to set JAVA_HOME at all, and I think the java docs suggest that you shouldn't normally set it. If you really want to, ~/.bashrc means the file .bashrc in your home folder. The command ```
gedit ~/.bashrc
``` will get you there.

---

### Post by ricardo072 on 2012-05-03
Ok thanks, going to check and I will let you know...

==================
Adding information:

I'm assuming that I will be able to execute something like: 
> java -version

and I must see something similar to:
> java version "1.6.0_23"
> Java(TM) SE Runtime Environment (build 1.6.0_23-b05)
> Java HotSpot(TM) Client VM (build 19.0-b09, mixed mode, sharing)

is this right?

---

### Post by sammiev on 2012-05-03
The latest JRE Java Version is 6 Update 32.

---

### Post by pals0007 on 2012-05-03
There is a script on rootzwiki which is an android forum that installs the jdk, eclipse and something else for developement. dont know if i can post a link but a search will bring it up

---

### Post by lykeion on 2012-05-03
> **ricardo072 said:**
> Yes, I did not do anything so far, but I would like to set up a java development envirionment.
If you want to develop java applications you'll need a JDK (=Java Development Kit)
> **ricardo072 said:**
> 3.- So,... the best option under this scenario right now would be install:

- the openjdk-6-jre package, 
- the icedtea6-plugin package and,
- the openjdk-6-jdk package using any installation method.

is this right ??Like mentioned above the runtime environment JRE is included in the JDK so no need to install that. The icedtea java browser plugin has nothing to do with developing Java applications.

What JDK version to choose depends on what you are developing. Android development requires Oracle (Sun) JDK, but if you're just programming for yourself in Ubuntu I'd use OpenJDK JDK.

Install openjdk-6-jdk or openjdk-7-jdk both available from the repos in Ubuntu 12.04.

---

### Post by ricardo072 on 2012-05-04
> **The Cog said:**
> I would just do:
```
sudo apt-get install openjdk-6-jdk openjdk-6-doc
```
The jdk has a jre built into it so you don't need a separate one.

Ok, ok,.. right now I'm on the office, but I will do it ASAP and I will let you know my results later today.  :o)

Thank you for your help.
Best regards.

---

### Post by ricardo072 on 2012-05-09
Thank you ALL for your help..


richard@richard-WorkStation:~$ java -version
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.1) (6b24-1.11.1-4ubuntu2)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)

---

### Post by ricardo072 on 2012-05-12
> **lykeion said:**
> If you want to develop java applications you'll need a JDK (=Java Development Kit)
Like mentioned above the runtime environment JRE is included in the JDK so no need to install that. 


[INDENT]I'm about to install Apache Tomcat (apache-tomcat-7.0.27.tar.gz), So, now I have MANY questions... I must configure some environment variables... According to the documentation, I need to edit the "catalina.sh" file ($ sudo gedit /<my_path>/tomcat7/bin/catalina.sh) in order to add the following lines at the end of that file:

JAVA_HOME="/<??????????>/jdk"
JRE_HOME="/<???????????>/jre"[/INDENT]

**Questions:**
- Based on the fact that I have the OpenJDK,.. Where is the JDK and the JRE?
- I'm not seeing a 64-version of Tomcat on the official web,.. just one 32-bit version... and the OpenSDK is 64-bit... Will Tomcat be working fine ??


Thanks,
Best regards.

---

