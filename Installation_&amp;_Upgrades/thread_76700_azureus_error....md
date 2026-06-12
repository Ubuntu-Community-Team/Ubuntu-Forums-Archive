---
title: "azureus error..."
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by krak on 2005-10-15
never had this error
Tracker Status: Connection Error (ZipException:gzip header corrupted)

this error is on all torrents and different trackers with 5.04 i had no such problem. I have installed the latest java form official site.
any one has any idea?

---

### Post by chajuram on 2005-10-19
Hi,

I have a slightly different problem with azureus, though I have a feeling that it is related to breezy. Azureus was telling me that it needed azureusupdater plugin. I though of reinstalling azureus, after removing it I found that it is not there on the breezy repositories. I remember it was on hoary repositories.

I tried to get the tar files from azureus site and install it, but was not very successful. May be I need to spend more time on it. 

I was wondering if there was an easier way. 

Chajuram.

PS. May be you can try this [http://ubuntuforums.org/showthread.php?t=75272](http://ubuntuforums.org/showthread.php?t=75272) it worked for me.

---

### Post by Fanskapet on 2005-10-19
[QUOTE=krak]never had this error
Tracker Status: Connection Error (ZipException:gzip header corrupted)

this error is on all torrents and different trackers with 5.04 i had no such problem. I have installed the latest java form official site.
any one has any idea?[/QUOTE]


I got a a vague answer from one of the guys in the #azureus channel that ubuntu could either have a broken gzip or the java-gzip modules isn't in place.. still i think this is ubuntu specific problem.. hmm well.. hope to find out soon .. i badly need azureus :razz: 

/ Fanskapet

---

### Post by Fanskapet on 2005-10-19
[QUOTE=krak]never had this error
Tracker Status: Connection Error (ZipException:gzip header corrupted)

this error is on all torrents and different trackers with 5.04 i had no such problem. I have installed the latest java form official site.
any one has any idea?[/QUOTE]

I Solved this issue on my computer.. it has nothing todo with the kernel or gzip.. azureus is trying to run with the gcj toolkit and not sun's that's why you get the error. i've solved this by doing the following (this will also remove the openoffice package since gcj is a dependency)

1. sudo apt-get remove gcj
2. sudo apt-get remove gcj-4.0
3. chmod +x jre-1_5_0_05-linux-i586.bin
3. sudo ./jre-1_5_0_05-linux-i586.bin
4. sudo mv -f jre1.5.0_05/ /opt/
5. sudo ln -s /opt/jre1.5.0_05/bin/java /usr/local/bin/java
6. sudo ln -s /opt/jre1.5.0_05/bin/policytool /usr/local/bin/policytool
7. add the following line to your environment: JAVA_HOME=/opt/jre1.5.0_05

and then start azureus and begin leeching :KS 

/ Fanskapet

---

### Post by jsteidl on 2005-11-09
the problem can be solved as written at  [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

run: sudo update-alternatives --config java

and pick your package.. done

EDIT: Azureus is running since 1 Day and its still stable and not to resource-hungry.. it seems to work :)

---

### Post by cydec on 2005-11-16
This solved the problem.

He used "java-gcj" standard, but i changed to "j2re1.5-sun".
Everything seems to work now, thanks dude !

Thought so, because when Azureus booted, he told me there was a new version: "j2re1.5-sun" ... but i installed it already!


I'm i-only a noob, but trying and learing a lot here !

---

