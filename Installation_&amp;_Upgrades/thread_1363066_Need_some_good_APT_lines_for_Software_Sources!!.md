---
title: "Need some good APT lines for Software Sources!!"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by zollen on 2009-12-23
The default APT lines defined in the Administration -> Software Sources don't carry the latest packages. Would you guys know any good APT lines (e.g. 'deb [http://.](http://.)....) which carry the latest stuff? 

I need libxml2, apache2 and apache2-mod-security. I have all of them in my system but the Update Manager could not get the latest packages for me.

Zollen

---

### Post by zollen on 2009-12-24
> **zollen said:**
> The default APT lines defined in the Administration -> Software Sources don't carry the latest packages. Would you guys know any good APT lines (e.g. 'deb [http://.](http://.)....) which carry the latest stuff? 

I need libxml2, apache2 and apache2-mod-security. I have all of them in my system but the Update Manager could not get the latest packages for me.

Zollen


Any idea?

---

### Post by tommcd on 2009-12-24
To be sure you have the latest packages from the Ubuntu repos, run:
```
apt-cache policy package_name
```
It will report the version you have installed, along with the latest version in the repos. If they match, you have the latest version. If you have got all the updates, then you most likely already have the latest version.
There is really no easy way to do what you want without going outside the official Karmic repos. You can try searching the Launchpad ppa repos. Some of them have newer stuff than what is in the official repos:
[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)
To add the ppa repos to your souces.list, see:
[https://help.ubuntu.com/9.10/add-applications/C/adding-repos.html](https://help.ubuntu.com/9.10/add-applications/C/adding-repos.html)
Be sure to read the caveat:
> You download and install PPA packages at your own risk. Ubuntu, Launchpad and Canonical do not endorse these packages. You must be certain that you trust the PPA owner before you install their software.
also see:
[https://help.launchpad.net/Packaging/PPA#keys?action=show&redirect=PPAKeys](https://help.launchpad.net/Packaging/PPA#keys?action=show&redirect=PPAKeys)
Be aware that these are unofficial repos. I have never actually used them. From answering a great many threads around here though, I can tell you that adding a lot of ppa stuff to Ubuntu seems to be a good way to break it. Use them sparingly, and at your own risk.

---

### Post by wkulecz on 2009-12-24
> Be aware that these are unofficial repos. I have never actually used them. From answering a great many threads around here though, I can tell you that adding a lot of ppa stuff to Ubuntu seems to be a good way to break it. Use them sparingly, and at your own risk.

Am I the only one that finds this distressing?  Are we heading to being even more  windows-like where installing a broken application breaks the system?  I hope not, but the situation with things like ffmpeg sure makes it look like moving to Linux is just going to be trading dll-hell for so-hell.

--wally.

---

### Post by tommcd on 2009-12-25
> **wkulecz said:**
> Am I the only one that finds this distressing?  Are we heading to being even more  windows-like where installing a broken application breaks the system?  
The ppa repos are for ordinary users like you and me to upload packages to. Obviously, the quality of these packages, and the skill of the packagers, will vary quite a lot.  You can not expect Canonical to endorse and support the stuff that people upload there.
 I do think the idea of the ppa repos is perhaps a bit misleading to a lot of people though. It seems that people assume that if the stuff is on Launchpad then it must be official, or at least semi-official. Anyone can join Launchpad. You don't need to possess any special skills to put stuff up there.
> **wkulecz said:**
> 
... the situation with things like ffmpeg sure makes it look like moving to Linux is just going to be trading dll-hell for so-hell.

What is the problem with ffmpeg? I don't really use it, expect a little bit on Slackware, so I don't know what you mean here.
To get the latest ffmpeg, and to fix various problems with ffmpeg in Ubuntu, I found this thread:
[http://ubuntuforums.org/showthread.php?t=1117283&highlight=ffmpeg](http://ubuntuforums.org/showthread.php?t=1117283&highlight=ffmpeg)

Your other option for getting the latest version of the packages you want would be to compile them from source code. I would remove the Ubuntu packages before installing them from source to avoid conflicts.

---

### Post by andrew.46 on 2009-12-25
Hi wally,

> **wkulecz said:**
> Am I the only one that finds this distressing?  Are we heading to being even more  windows-like where installing a broken application breaks the system?  I hope not, but the situation with things like ffmpeg sure makes it look like moving to Linux is just going to be trading dll-hell for so-hell.

I will have to admit that when I see the choices available to Ubuntu users in terms of repository packages, PPAs and the possibilities of 'building your own' I feel excited rather than distressed. If the only option was depending on a large centralised respository provided by Ubuntu I believe that Ubuntu would be a less exciting Linux distro.

As regards FFmpeg can I mention that these forums provide an excellent guide to building the best possible version:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

All the best,

Andrew

---

### Post by tommcd on 2010-01-02
For what it's worth, it seems that Canonical is working to have the new Software Center "establish and convey a trust level for software in PPAs ..."  in future releases of Ubuntu:
[https://wiki.ubuntu.com/SoftwareCenter#April 2010](https://wiki.ubuntu.com/SoftwareCenter#April 2010)

---

