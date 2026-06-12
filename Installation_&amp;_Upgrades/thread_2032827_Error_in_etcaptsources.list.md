---
title: "Error in /etc/apt/sources.list"
date: 2012-07-24
forum: Installation &amp; Upgrades
---

### Post by A8rKAnG3L on 2012-07-24
Hello,

I'm getting this error message in the red sign reference Update Manager Package :



E: Type ‘[some repository]’ is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.

I'm trying to install Java but no joy :(

---

### Post by GreatDanton on 2012-07-24
First I would recommend you to change the title of your thread, otherwise it will not be attractive for others users of this forum

---

### Post by A8rKAnG3L on 2012-07-24
Hi Man,

Sorry I'm a bit of a novice, how do I change the title of the THREAD?

Kind regards 

Clive

---

### Post by A8rKAnG3L on 2012-07-24
I think maybe I should have posted this question & not as a thread?

---

### Post by oldos2er on 2012-07-24
I've changed the thread title.

A8rKAnG3L, can you open a terminal (Ctrl-Alt-t), run the following command, and copy and paste all its output here? ```
cat /etc/apt/sources.list
```

---

### Post by lisati on 2012-07-24
Your thread title has been edited. Don't worry too much about the difference between a thread and a question: a thread usually starts as a question.

---

### Post by QIII on 2012-07-24
You really have two questions (you may not realize it).

The first is to get your sources list sorted out.

The second is how to install Java.

 I'll help you with Java.

See the Java link in my signature.  Look for the link "Using webupd8.org's strikingly simple method" in the Oracle Java 7 installation section if you are not looking for Oracle Java.

OpenJDK is also discussed in the wiki if you are looking for that.

---

### Post by A8rKAnG3L on 2012-07-26
> **oldos2er said:**
> I've changed the thread title.

A8rKAnG3L, can you open a terminal (Ctrl-Alt-t), run the following command, and copy and paste all its output here? ```
cat /etc/apt/sources.list
```

OK thank you here it is:

cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
[some repository]
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
#deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

---

### Post by A8rKAnG3L on 2012-07-26
> **QIII said:**
> You really have two questions (you may not realize it).

The first is to get your sources list sorted out.

The second is how to install Java.

 I'll help you with Java.

See the Java link in my signature.  Look for the link "Using webupd8.org's strikingly simple method" in the Oracle Java 7 installation section if you are not looking for Oracle Java.

OpenJDK is also discussed in the wiki if you are looking for that.

When I try to install OpenJDK I get this error message:

E: Type ‘[some repository]’ is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.

:(

---

### Post by oldos2er on 2012-07-26
Open your sources.list with ```
gksu gedit /etc/apt/sources.list
``` and remove line 54 which is

[some repository]

Save and exit the file, run ```
sudo apt-get update
```

---

### Post by A8rKAnG3L on 2012-07-29
> **oldos2er said:**
> Open your sources.list with ```
gksu gedit /etc/apt/sources.list
``` and remove line 54 which is

[some repository]

Save and exit the file, run ```
sudo apt-get update
```

Nice one thank you, this has got rid of the error message. 

:)

Do you have any advice on installing Java 7, I've removed the older version (6) but installing the new version seems really long winded....

---

### Post by arpanaut on 2012-07-30
> Do you have any advice on installing Java 7, I've removed the older  version (6) but installing the new version seems really long winded....

This should help:  [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Scrool down to Command line Methods
this one seems to be the easiest:
[Using webupd8.org's strikingly simple method.]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html")

Or at least the author of the wiki touts this method many times on this forum.
Whatever many methods are outlined there.

---

### Post by A8rKAnG3L on 2012-07-30
> **arpanaut said:**
> This should help:  [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Scrool down to Command line Methods
this one seems to be the easiest:
[Using webupd8.org's strikingly simple method.]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html")

Or at least the author of the wiki touts this method many times on this forum.
Whatever many methods are outlined there.


Thank[FONT=monospace] you so much for all of your help, the advice I have received from yourself & others in the Community [/FONT]has been excellent. 

Java is now working with no errors :D

Kind regards

Clive

---

