---
title: "Can't install OpenJDK"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by DavidSurfer on 2011-10-21
I just did a clean install of 32 bit Ubuntu 11.10 from CD.  The machine is an old Celeron processor.  I wiped out all previous Windows partitions and started fresh.  It's working as far as I can tell - wireless, browser, and I managed to install flash.  However, I would like to get Java installed as well.  I went to the Software Center and tried to install the latest OpenJDK package.  Here's what I got: 

UBUNTU 11.10 installing OpenJDK Java 7 Runtime

Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

The following packages have unmet dependencies:

openjdk-7-jre: Depends: openjdk-7-jre-headless (>= 7~b147-2.0~pre6-1ubuntu1) but 7~b147-2.0~pre6-1ubuntu1 is to be installed
              Depends: libpulse0 (>= 1:0.99.1) but 1:1.0-0ubuntu3 is to be installed
              Depends: libaccess-bridge-java-jni (>= 1.26.2-6) but it is not going to be installed

Any ideas of what to do next?  

Thanks!

---

### Post by crazy bird on 2011-10-21
I had those message also but then for other programs. I solved it by installing the packages which are needed by getting them from here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/).
 
Make sure you get the version which is needed to install OpenJDK.

---

### Post by DavidSurfer on 2011-10-21
Seems reasonable - my instinct was that I was missing SOMETHING.  My confusion was that the install for OpenJDK doesn't include links to dependencies!!  If I stare at the error message I'd guess I need to install some things called: 

7~b147-2.0~pre6-1ubuntu1
1:1.0-0ubuntu3

I found some instances of these referenced, for example here: 
[https://launchpad.net/ubuntu/+source/openjdk-7/7~b147-2.0~pre6-1ubuntu1/+build/2814829](https://launchpad.net/ubuntu/+source/openjdk-7/7~b147-2.0~pre6-1ubuntu1/+build/2814829) but with maybe a dozen possible downloads.  For the second, I find lots of hits but so many options with no clear flow which leads to OpenJDK that I am stymied.  

I also don't understand what to make of:

Depends: libaccess-bridge-java-jni (>= 1.26.2-6) but it is not going to be installed

Do I need to search for libaccess-bridge-java-ini and what does 1.26.2-6 mean??

Is it possible to do a fresh install of 11.10 and then with a single install get Java working?  Did I do something wrong to land in this quagmire?  Sorry for the newbie questions.  I imagine this is clearer for a more seasoned user!

---

### Post by raja.genupula on 2011-10-21
libaccess-bridge-java-jni

download the req package's from this link 
[http://packages.ubuntu.com/oneiric/libaccess-bridge-java-jni](http://packages.ubuntu.com/oneiric/libaccess-bridge-java-jni)

and then install it by using
```
sudo dpkg -i <pkg>
``` & try again.
all the best.

you can get java from here also

[http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u1-download-513651.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u1-download-513651.html)

---

### Post by DavidSurfer on 2011-10-21
That has the ring of truth!  Thanks- I will attempt to install and repost with results.  Excellent!

---

### Post by DavidSurfer on 2011-10-24
Unfortunately, no dice.  I've tried everything a newb can think of.  None of the manual installs of pretty much ANYTHING work.  I've tried installing the dependencies (and all crap out with messages about various dependencies but" not installable', and it's circular!  (If I manually try to install the dependent package such as mentioned above these refer back to the openjdk-7-jre package.  I've tried all the variants I can think of.  

As a side note, I"ve now tried to install a lot of code (including package managers and various java things) and the only one that I've had success with so far is Adobe Flash.  I"m thinking I must have done something wrong to have such dismal results.  Maybe I should have not used 11.10 but maybe a more stable and older version?  Any other ideas?  I'm a Ubuntu/Linux newb but a pretty experienced computer user/programmer.  I would have thought I could get somewhere with a bit less effort than this ... 

Thanks!

---

### Post by raja.genupula on 2011-10-25
> **DavidSurfer said:**
> I just did a clean install of 32 bit Ubuntu 11.10 from CD.  The machine is an old Celeron processor.  I wiped out all previous Windows partitions and started fresh.  It's working as far as I can tell - wireless, browser, and I managed to install flash.  However, I would like to get Java installed as well.  I went to the Software Center and tried to install the latest OpenJDK package.  Here's what I got: 

UBUNTU 11.10 installing OpenJDK Java 7 Runtime

Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

The following packages have unmet dependencies:

openjdk-7-jre: Depends: openjdk-7-jre-headless (>= 7~b147-2.0~pre6-1ubuntu1) but 7~b147-2.0~pre6-1ubuntu1 is to be installed
              Depends: libpulse0 (>= 1:0.99.1) but 1:1.0-0ubuntu3 is to be installed
              Depends: libaccess-bridge-java-jni (>= 1.26.2-6) but it is not going to be installed

Any ideas of what to do next?  

Thanks!
I think after this the terminal may be suggested you to do the 
```
sudo apt-get install -f
```

so do again the same process again and it will show like that at that time do this & try to install again. because previously i have got same as this while installing chrome and that helped me . 

All the best.

all the best.

---

### Post by DavidSurfer on 2011-11-09
To close out on this issue:  I haven't been able to install Java using the suggestions put forth so far.  I much appreciate the help I've gotten (very impressive to have a reservoir of experts out there!).  However, for whatever reason (hardware? Ubuntu version?) the methods I've tried haven't worked.  It's back to option B for me I guess.  

At this point I'm going to try to install a back-version of Ubuntu and try again.  If that fails, I probably will give up for now.  It's not worth it to me to mess with hardware for this spare computer.  It's curious that this was a perfectly fine install of Windows XP, just that it was slower than molasses for most things.  I'll try again when another computer needs to be retired!  I'm still interested if somebody has insight into why all of these installs end up in circular requirements for multiple packages.  I never got any of the subsidiary packages to install as I chased down the rabbit hole.

---

### Post by darkod on 2011-11-09
Just a note, OpenJDK is not the only choice. Unless you exactly need openjdk, you can always use Oracle (former Sun) JDK.
Just visit the oracle website and download the compressed file for jdk for linux (the latest jdk7 for example if you want to).
There is no installation involved, just extract it where ever you want.

Because there is no installation I'm not sure if you will have to somehow "tell" ubuntu where jdk is. But there is a way to do that surely.

For example, for Netbeans I use the latest jdk7 from Oracle. When installing netbeans there is a parameter to tell it where jdk is, and it works. Other software might do thing differently but there is always a solution.

And this way you can always install the latest jdk without waiting someone to develop it for the repositories.

---

### Post by DavidSurfer on 2011-11-14
Thanks for the idea.  More background:

I want to have my young son be able to play Minecraft in FireFox.  This game requires Java, so I guess FireFox would have to know about this version of Java as you say.  Not sure how to do that.  

More importantly, I haven't have ANY success installing packages under Ubuntu.  I might be just very confused but so far manual installs and the automatic method (I forget what the built-in tool in Ubuntu is called right now) have both failed for me.  Going forward, this makes me less excited about using Ubuntu (sadly since I really want to like this distrib).

---

### Post by darkod on 2011-11-14
In the latest version I think they call it Software Centre. But if that doesn't work too it might be something with internet/network connectivity. Are you sure it's working fine?

Try opening terminal and pinging some website, for example:

ping [www.google.com](www.google.com)

I fit reports it can't find/reach it, internet is not working. In that case both software centre and manual installs won't.

---

### Post by darkod on 2011-11-14
I think java in Firefox in Ubuntu works by default. You don't need to do anything. I just looked in my Add-Ons and there is no java add-on.
Have you tried running this application? Does it give you java missing message?

JDK is a different thing, you need JDK for developing java apps, not simply for running java.

I don't recall having to install java so that firefox can run it.

---

### Post by MoreOrLess on 2011-11-14
> **darkod said:**
> JDK is a different thing, you need JDK for developing java apps, not simply for running java.

Yes, but the collective java suite is called "OpenJDK" (confusing, I know). Anyway, I think what the OP is wanting is the icedtea plugin.

OpenJDK should work for most sites nowadays, but if you still need the official oracle java: [http://sites.google.com/site/easylinuxtipsproject/java#TOC-Oracle-Sun-Java:-removed-from-all-r](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Oracle-Sun-Java:-removed-from-all-r)

---

### Post by sarthak5 on 2011-11-22
I was trying to install openjdk-6-jdk in 10.04 desktop
Basically it was complaining about a higher version of tzdata, which you have to downgrade.
$ sudo apt-get install tzdata-java
...
The following packages have unmet dependencies:
  tzdata-java: Depends: tzdata (= 2010i-1) but 2011g-0ubuntu0.10.04 is to be installed
$ sudo apt-get install tzdata=2010i-1
...
Do you want to continue [Y/n]? Y
...
$ sudo apt-get install tzdata-java
...
$ sudo apt-get install openjdk-6-jdk icedtea6-plugin
...
And it works all the way through...

---

