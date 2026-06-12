---
title: "[SOLVED] JAVA installation problem"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by CasPol on 2008-06-14
When trying to install JAVA I get this error :

: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

What does this mean, and how do I solve it ?

Thanks.

---

### Post by Pumalite on 2008-06-14
sudo dpkg --configure -a
Post the output.

---

### Post by prshah on 2008-06-14
> **CasPol said:**
> When trying to install JAVA I get this error :

: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

What does this mean, and how do I solve it ?

Thanks.

It means that something (power outage, network outage, Ctrl+C) interrupted a previous update/install process. To solve it, as suggested, open a terminal (Applications-Accessories-Terminal), then give the following commands  ```

sudo dpkg --configure -a

``` and as further suggested, post back error messages if any.

---

### Post by CasPol on 2008-06-15
How do I install JAVA in ubuntu ?

---

### Post by gijsisok on 2008-06-15
Ubuntu 8.04 has a open source version of Java by default in the repo's, this is not as good as the Sun version. To install the Sun version, open a terminal and type:

sudo apt-get install sun-java6-jre sun-java6-plugin

This should work.

---

### Post by CasPol on 2008-06-15
Hi there ;

No output ...

---

### Post by Sef on 2008-06-15
> Ubuntu 8.04 has a open source version of Java by default in the repo's, this is not as good as the Sun version. To install the Sun version, open a terminal and type:

sudo apt-get install sun-java6-jre sun-java6-plugin

This should work.

Much easier to use Add/Remove.  Applications > Add/Remove > Show: 'All Available Applications' > Search: Sun Java 6 > click on the box > apply changes > apply > close

> Ubuntu 8.04 has a open source version of Java by default in the repo's, this is not as good as the Sun version.

Actually OpenJDK is very close to being as good as Java.  There are a few sites that need Java, but not too many.  With time, it will do those sites too.  OpenJDK is Java without the proprietary software.  If you are on 64-bit, then you have to use OpenJDk, unless you install the 32-bit version of Firefox.

---

### Post by PmDematagoda on 2008-06-15
CasPol:- Please don't start duplicate threads on the same issue, just one thread will be more than enough.

---

### Post by CasPol on 2008-06-15
Sorry guys, but  it remains a problem. when try to install it I gat a blue screen popping up, with text and  the installation halts...

what else can I do?

---

### Post by Pumalite on 2008-06-15
Can you use apt-get_? Try installing>
sudo aptitude install ubuntu-restricted-extras

---

### Post by CasPol on 2008-06-15
Seems I have got it installed now. Output of sudo java -version:

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

Unfortunately, it still does not work. When I use Firefox to open a website requiring JAVA, firefox still prompts me to download the plug in, and directs me to the "SUN" website to download the jre .... .bin file.

How can I get Firefox to work with the installed JAVA version. I am using Ubuntu 8.04 and firefox 2.0.0.14 ?

Thanks.

---

### Post by CasPol on 2008-06-26
Everything working now, simply has to restart Firefox.

Thank you everyone for your help and advise.

---

