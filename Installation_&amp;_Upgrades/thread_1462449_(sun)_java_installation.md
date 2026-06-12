---
title: "(sun) java installation"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by slwx on 2010-04-25
hi,
Recently I've removed all default java and tried to install sun java 6, jdk and jre.

java -version
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)

but I dont seem to be able to run java aplications anymore! The most important beeing netbeans. 

I've tried this:
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.15/
but it doesnt work, and honestly, i dont know what it does..

Anyone have an idea? I'm new to ubuntu, so sory if its a dumb question :)

thx

---

### Post by coolcaseley67 on 2010-04-25
hi 
 
- go to [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) and see the Choosing the default Java to use bit , you need to update your [FONT=Courier New]alternatives .[/FONT]

[FONT=Courier New]- you may need to reinstall the progarms that use java , I know for open office you need to install are package open office-java or on the lines of that [/FONT]
 
 
[FONT=Courier New]hope it helps [/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]ps for more see [http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/)[/FONT]

---

### Post by slwx on 2010-04-26
Hello,
It still doesnt work. i've followed the extra info you added at the end. java is installed well, also alternatives are well set. But i dont have a folder named /etc/jvm...
I dont know how to add it, since i dont have authorisation anyware..
thx

---

### Post by Soul-Sing on 2010-04-26
update -15 is outdated and ful of security issue's
try this link:  [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by conradin on 2010-04-26
You dont have authorization? You're not root? you may have to contact your administrator.

---

### Post by coolcaseley67 on 2010-04-26
hi 
 
 
-update 15 is out of date but its in ubuntu repos, could do with fixing that some time .
 
- what you need java?.  if its just for everyday internet, openofffice use the openjava , as it says at [http://sites.google.com/site/easylinuxtipsproject/java#TOC-OpenJDK-and-the-Icedtea-Plugin-are](http://sites.google.com/site/easylinuxtipsproject/java#TOC-OpenJDK-and-the-Icedtea-Plugin-are)-  the main java is been  [SIZE=1]regularly moved about & removed .:KS 0r just do by the main website ............... [/SIZE]
[SIZE=1][/SIZE] 
[SIZE=1][/SIZE] 
[SIZE=1][/SIZE] 
_[SIZE=3][COLOR=#0033cc][/COLOR][/SIZE]_

---

### Post by slwx on 2010-04-28
> **conradin said:**
> You dont have authorization? You're not root? you may have to contact your administrator.

hi,
the extra info provided by coolcaseley67 (on the website [http://www.cyberciti.biz/faq/howto-u...igure-jdk-jre/]("http://www.cyberciti.biz/faq/howto-u...igure-jdk-jre/"))
tell me:
"You also need to edit a file called /etc/jvm. This file defines the default system JVM search order. Each JVM should list their JAVA_HOME compatible directory in this file. The default system JVM is the first one available from top to bottom. Open /etc/jvm
$ sudo vi /etc/jvm"

-> but i have no file /etc/jvm
when i go to the folder and try to make one, i get "no authorisation" error..

i dont know how to go in root to make the file, im new!
thx

---

### Post by coolcaseley67 on 2010-04-28
hi 
 
- which java are you installing the openjdk or java sun ?
- are you 32bit or 64 bit ?
 
thanks

---

### Post by slwx on 2010-04-29
> **coolcaseley67 said:**
> hi 
 
- which java are you installing the openjdk or java sun ?
- are you 32bit or 64 bit ?
 
thanks

hi,
i deleted the default java and installed sun java 6, i've installed sun-6-jdk, jre and plugin. i also updated alternatives. 
but java isnt working.. (i cant start netbeans or any internet applications)..
i am using 32 bit system of ubuntu
thx

---

### Post by coolcaseley67 on 2010-04-29
hi 

i will test it out hm ..  how did you download by the website or in ubuntu package mangers ......  ??

back the results

---

### Post by slwx on 2010-04-29
Hello,
to be complete, this is the original problem i had:
[http://forums.netbeans.org/post-72261.html ]("http://forums.netbeans.org/post-72261.html")
 its not really relevant, but maybe you want to know.
I was told to install the sun java instead of the default. 
this is what i did, step by step:

removing via s/w centre: 
OpenJDK java 6 runtime 
OpenJDK java 6 webstart 

removing via apt: 
openjdk-6-jdk 
default-jdk 
openjdk-6-jre-headless 

Then I installed Sun Java: 
via apt: 
sun-java6-jdk 
sun-java6-jre 

via s/w centre: 
sun-java6-plugin 

and finaly
sudo update-alternatives --config java


at this point java sun still didnt work. so i followed the instructions given by you  [here]("http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/")

*at first i didnt have a file at "/etc/jvm" , (this is what i posted on above, i didnt know how to make a file :s)
but now i found my way, i made a file at /etc/jvm/ with this in it:
/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr

like the instructions tell me

finally i made a file
$HOME/.bash_profile

and in it, ther is:

export JAVA_HOME=/usr/lib/jvm/java-6-sun
export PATH=$PATH:$JAVA_HOME/bin



ok, now i have followed evry instruction, still netbeans doenst start, neither do any java applications (e.g. on internet).

thx

---

### Post by coolcaseley67 on 2010-04-29
Hi 
-I've just  tried it  [SIZE=1][COLOR=#000000]MANUALLY and it worked  and  I verified online @ [/COLOR][/SIZE]http://java.com/en/download/installed.jsp . 

- i will check netbeans , i think you may need to go in to synaptic package manager and remove the programs and the con figs. then reinstall ..

hope it helps ](*,)

update 
netbeans use the openjava ...... so you've remove it witch it needs to run  ...

---

### Post by slwx on 2010-04-30
hi,
I have reinstalled java-sun-6 + downloaded netbeans manually from the website, and reinstalled it to. now it is working!
thanks for the help!
slwx

---

### Post by coolcaseley67 on 2010-04-30
hi

no pro's 

mark this as solved in thread tools 

happy ubuntu ing :KS

---

