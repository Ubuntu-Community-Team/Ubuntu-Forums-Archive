---
title: "Kubuntu fails to logon daily build 030310"
date: 2010-03-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by caryb on 2010-03-02
I have tried to build a Lucid i386 machine for a while now & am conceding defeat. I have googled faults concerning this & it seems as though this is a long standing problem. My daily build from last week would log in from the cd but not allow any user to logon after install from within KDE today's CD wont logon at all, it constantly loops the logon process from the live CD.

I guess this is systematic of picking a very under resourced distro faults do take a extraordinarily long time to fix :-(


Cary

---

### Post by VMC on 2010-03-02
> **caryb said:**
> I have tried to build a Lucid i386 machine for a while now & am conceding defeat. I have googled faults concerning this & it seems as though this is a long standing problem. My daily build from last week would log in from the cd but not allow any user to logon after install from within KDE today's CD wont logon at all, it constantly loops the logon process from the live CD.

I guess this is systematic of picking a very under resourced distro faults do take a extraordinarily long time to fix :-(


Cary
Is it the motherboard that has you defeated or Lucid? 
What's the hardware your trying this on.

---

### Post by caryb on 2010-03-02
Was on a old Athalon white box PC but have replicated my issues on a 3 year old IBM 3.2Ghz Intel 1G Ram Nvidia & a new Lenovo 2.66G/4G ram Intel Intel graphics. 

I'm making the assumption that it's not a hardware issue.

Cary

---

### Post by Kevbert on 2010-03-03
Originally had the problem where I start to enter the password in Kubuntu and then the screen went black and then I had to re-enter my password completely again in order to log in. Just tried the latest alternate build and install fails at 'installing and setting up software' (red screen of death ?) Can't get any further regardless of what I try.  CD burn check OK and md5sum OK.  Will just have to wait for a later build.](*,):sad:

---

### Post by VMC on 2010-03-03
I tried Kubuntu Lucid early on, and had so many problems I decided to wait for the release. I'm now using Kubuntu 9.10 and its almost perfect.

The problem I see regarding Kubuntu ,is were not only testing a new OS, but also KDE4 itself, which I have problems with.

I have few problems with Ubuntu Gnome updates. Once the migration to Gnome3 comes along then hopefully KDE4 will be more mature or at least manageable.

---

### Post by bhuvi07 on 2010-03-03
my wi-fi n connections do not work in KDE...
but they work completly fine for GNOME...
AT the same time..
i insatlled the ATI graphics card driver for ubuntu..
it is available on GNOME n higher bgraphics work fine...
but as soon as i switch to KDE..
it does reads as well as the  driver is not available..
m in lot of fix..
plzzz help me get through my problemss

---

### Post by Kevbert on 2010-03-04
Hi bhuvi07. If you're new to Ubuntu you should not be using Lucid as it's not even in the Beta testing phase and so is expected to be unstable (instead try [[COLOR="Red"]Karmic 9.10[/COLOR]]("http://www.ubuntu.com/GetUbuntu/download") it will be more successful).
If you've decided that you want to risk Lucid, open Terminal (for Ubuntu or Konsole for Kubuntu) and enter
```
lspci
```
and post back the output.

Just tried today's daily build (5/3/10). Can't check integrity of disk (just hangs PC), Can't install from CD menu (just hangs PC again) and if I try to install from 'Try Kubuntu...' [COLOR="Red"][ubiquity crashes]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/532533")[/COLOR].

---

### Post by Kevbert on 2010-03-10
Latest daily build 100310 a bit better I can now get to the partitioning part where ubi-partman fails with exit code 141 when trying to set up manual partitions. Also before that there's a unreadahead error which fails with exit status 4 and a Ubuntu screen with the five red lights. Aren't we at beta freeze ? (seems a bit premature as can't even install Kubuntu).  :sad::sad::sad:

---

