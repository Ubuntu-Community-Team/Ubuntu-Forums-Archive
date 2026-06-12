---
title: "Upgrade from Lubuntu 14.04LTS to 16.04 went badly wrong."
date: 2017-09-08
forum: Installation &amp; Upgrades
---

### Post by The Frenchman on 2017-09-08
Did the upgrade in terminal,everything seemed to be going well until about 83% then a pop up told me the upgrade had stopped,did I want to report etc.Terminal carried on loading and after I tried apt-get update and dist-upgrade it booted into LXDE Lubuntu 16.04 (after about three attempts).But I have no wifi (tick boxes greyed out) and every time I try to log out it puts me back into password screen.Is there a way I can find and repair missing/ broken packages without internet access and is there a way I can make it shut down correctly? You can I'm sure tell by this post I'm something of a novice.

---

### Post by BenginM on 2017-09-08
try to run dpkg to fix things from from recovery (safe) mode 

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

[http://imgur.com/9KUUOHI](http://imgur.com/9KUUOHI)

what terminal command did you use to upgrade, were there third party PPAs enabled while preforming the upgrade? usually, before preforming a release upgrade in terminal one needs to run apt update && apt dist-upgrade.

---

### Post by The Frenchman on 2017-09-08
I ran sudo do-release-upgrade.I had updated and upgraded about an hour before in the same session.I'd only been made aware that Lubuntu 14.04LTS was no longer supported as I was still receiving security updates....how time flies! The laptop I'm on has Ubuntu 14.04LTS which version would be the safest one step upgrade that will keep me supported or was the upgrade I did on the netbook just bad luck?

---

### Post by The Frenchman on 2017-09-08
Sad to say tried it but still the same.Tried to log in to Openbox and got. wifi networks device not ready. Failed to apply network settings org,freedesktop.DBus.Error.Spawn.FailedToSetup.and keep getting system program problem detected pop ups

---

### Post by ian-weisser on 2017-09-08
You have two choices:

1) You can troubleshoot and fix your system. You will learn a lot about apt in the process. Takes a few days due to the learning curve.

2) If you simply want a working system and don't want to learn about apt, then back up your data and do a fresh install.

---

### Post by The Frenchman on 2017-09-09
I'd like to go the apt route,can you point me in the direction of a tutorial? BTW How secure is this system I'm using Ubuntu 14.04 LTS.Still getting security updates?

---

### Post by Autodave on 2017-09-09
LTS releases are supported for 5 years. So, your 14.04 is still good until April 2019. The newest LTS is 16.04.  In about 8 months, 18.04 will become available.

In case you are wondering, the first 2 digits (14, 16, etc) are the year of the release. The second 2 digits are the month. Any releases between the LTS releases are short term only and are released every 6 months. These short term releases are only supported until the next short term release is issued.

   I stick with only the LTSs and even then I usually wait a month after their release before installing them. Further, I do not upgrade to them but completely install the new release after copying all files that I need to save to an external HD.

I have never had any luck upgrading from one release to the next. Some people here will tell you that they have never had a problem. Personally, on 13 machines, the last time I tried upgrading to the newer release, only one machine worked without any problems. a few had minor problems. The majority had major issues and I just reinstalled on those machines.

---

### Post by The Frenchman on 2017-09-09
I thought that was the case when I downloaded 14.04LTS,Wish I hadn&#8217;t done the 14.04-1604 LTS Like you I've had various problems with upgrades,but never as serious as this.

---

### Post by ian-weisser on 2017-09-09
My experience is nearly the opposite of Autodave.
I've been upgrading every six months for a decade, and it's been a great experience every time...except once, and that was my fault.

I don't know of any good 'apt tutorial'. There are four basic concepts to learn:
1) dpkg's super-simple package logic and search tools.
2) apt's super-simple repository logic, repository lists, and package cache.
3) How developers extended the simple, unsubtle logic with metapackages, apt-marking, kernel-removal scripts, and automated-upgrade scripts to meet sophisticated user expectations.
4) How to read apt and dpkg error messages

Once you understand those, you will understand how to troubleshoot 95% of Debian/Ubuntu package problems.

---

### Post by The Frenchman on 2017-09-09
> **ian-weisser said:**
> My experience is nearly the opposite of Autodave.
I've been upgrading every six months for a decade, and it's been a great experience every time...except once, and that was my fault.

I don't know of any good 'apt tutorial'. There are four basic concepts to learn:
1) dpkg's super-simple package logic and search tools.
2) apt's super-simple repository logic, repository lists, and package cache.
3) How developers extended the simple, unsubtle logic with metapackages, apt-marking, kernel-removal scripts, and automated-upgrade scripts to meet sophisticated user expectations.
4) How to read apt and dpkg error messages

Once you understand those, you will understand how to troubleshoot 95% of Debian/Ubuntu package problems.
As stated earlier I'm somewhat of a novice,and can I use the commands you mention without internet access? If I can fix that I might have a fighting chance.:)

---

### Post by westie457 on 2017-09-09
Hi, assuming all packages for the upgrade have been downloaded open a terminal and try 'sudo dpkg --configure -a'
Any error messages post them back here please.

---

### Post by mörgæs on 2017-09-10
> **The Frenchman said:**
> How secure is this system I'm using Ubuntu 14.04 LTS. Still getting security updates?

Are you using Ubuntu or Lubuntu? The former is still supported, the latter is not.

---

### Post by kc1di on 2017-09-19
Lubuntu is only supported for 3 years instead of 5 years - > LTS implies that, for 3 years (in our case) - From 
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu/LTS]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu/LTS")

---

### Post by The Frenchman on 2017-09-19
Decided discretion was the better point of valor and did a clean install of Peppermint lost a few files,but that's life.On this laptop I'm using Ubuntu 14.04 LTS so safe for now.Thanks for all the help and suggestions gents,

---

