---
title: "Trouble installing Java"
date: 2010-02-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bobmatino17 on 2010-02-27
I have a machine running kubuntu 10.04 Alpha, however, i am having trouble installing the java plugin. it used to be a package called "sun-java6-plugin" but now, i cant find it. any help would be greatly appreciated.

---

### Post by gradinaruvasile on 2010-02-27
I dont know about Lucid, didnt use it, but you dont need to install the plugin package, the neccesary file is installed with sun-java6-jre but you have to link it:

sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so /usr/lib/mozilla/plugins/

---

### Post by Uncle Spellbinder on 2010-02-27
I followed this howto: [http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10)

All went flawlessly.

---

### Post by kahumba on 2010-02-27
I'm myself a Java developer but I can't figure out why people need the Java plugin - I haven't seen a site with an applet in ages..

---

### Post by Uncle Spellbinder on 2010-02-27
> **kahumba said:**
> I'm myself a Java developer but I can't figure out why people need the Java plugin - I haven't seen a site with an applet in ages..

There are uses for it. Several chat areas I visit require it. [http://x007.grizzdesign.nl/chat/](http://x007.grizzdesign.nl/chat/). Some image/file uploading services use it as well.

---

### Post by LKjell on 2010-02-27
Use the icedtea plugin.

---

### Post by kahumba on 2010-02-27
> **Uncle Spellbinder said:**
> There are uses for it. Several chat areas I visit require it. [http://x007.grizzdesign.nl/chat/](http://x007.grizzdesign.nl/chat/). Some image/file uploading services use it as well.
Thanks. Never happened to come across such an uploading service I guess.. But as both a JavaScript and Java developer I acknowledge that writing it as a Java applet gives much more control and flexibility on the client side.

---

### Post by mick222 on 2010-02-27
> **Uncle Spellbinder said:**
> I followed this howto: [http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU-9.10)

All went flawlessly.
 That is a really good guide. Lexulous the scrrable type game also uses the plugin.In Lucid the plugin didn't seem to be in the repositories,maybe just not added yet.

---

### Post by CoreyB. on 2010-02-27
I think sun java is not and won't be included in lucid, use icedtea6-plugin and the openjdk-6-jre.

---

### Post by mick222 on 2010-02-27
Are you sure I'm on windows at the moment my daughters laptop, but i'm sure sun-java was in the repositories but the firefox plugin was missing.It is usually included in restricted-extras.

---

### Post by bobmatino17 on 2010-02-27
I installed icedtea and everything worked fine. Thank you for all of your help.

---

### Post by CoreyB. on 2010-02-27
> **mick222 said:**
> Are you sure I'm on windows at the moment my daughters laptop, but i'm sure sun-java was in the repositories but the firefox plugin was missing.It is usually included in restricted-extras.

Yup, i'm sure [it's not in there]("http://packages.ubuntu.com/search?keywords=sun-java6&searchon=names&suite=all&section=all").  [icedtea6-plugin]("http://packages.ubuntu.com/lucid/icedtea6-plugin") is now included in [ubuntu-restricted-extras]("http://packages.ubuntu.com/lucid/ubuntu-restricted-extras").

---

### Post by Uncle Spellbinder on 2010-02-27
But [http://x007.grizzdesign.nl/chat/](http://x007.grizzdesign.nl/chat/) will get you the current, up-to-date JAVA

---

### Post by Lunx on 2010-02-27
> **kahumba said:**
> I'm myself a Java developer but I can't figure out why people need the Java plugin - I haven't seen a site with an applet in ages..

G'day Kahumba

As someone else has also stated, some chat facilities require it. I'm an on-line university student studying with Open Universities Australia, a consortium of 6-8 different institutions who make use of an online teaching tool called BlackBoard, and it requires JRE and browser plug-in to be able to use an inbuilt chat facility. I was a bit worried when I signed on to uni whether I could use all the features via Linux and open source, pleased to say I had no troubles when running Karmic. Now I've got the IcedTea plugin, it will be interesting to see if that will work for me as as well. I'm currently taking a break from study, Lucid will have gone prime-time before my next study period begins, so time will tell I guess.

---

### Post by crjackson on 2010-02-28
So far I've only tested the LiveCD and no JAVA has been tested yet.  I guess I'll install Lucid on one of my non-critical machines tomorrow or the next day and see what happens.  JAVA COULD be a deal breaker for me.  I use some work applications that REQUIRE the plugin and ICETEA has never worked with it.

Aside from JAVA, I'm liking everything else so far.

---

### Post by dxxvi on 2010-02-28
I installed openjdk-6-jre and openjdk-6-jdk in Lucid. Until now, what I can see is a better font usage in openjdk6 (in both applets and swing applications like Intellij Idea). Haven't seen any trouble until now (I used Idea to write a web app using Spring 3, tomcat 6, jquery and google maps api). However, haven' tried javaee 6 and glassfish yet.

---

### Post by JohnJackson on 2010-02-28
Strange, I did see it was added to lucid here [https://lists.ubuntu.com/archives/lucid-changes/2010-February/006794.html](https://lists.ubuntu.com/archives/lucid-changes/2010-February/006794.html)

---

### Post by meborc on 2010-03-01
> **gradinaruvasile said:**
> I dont know about Lucid, didnt use it, but you dont need to install the plugin package, the neccesary file is installed with sun-java6-jre but you have to link it:

sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so /usr/lib/mozilla/plugins/

thanks, this worked for me :)

---

