---
title: "Feisty Update Manage breaks DVD playback"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by raymer on 2007-06-16
First let me say that I really like Ubuntu. I have been away from the Linux world (used to use RedHat) for a couple of years (using Windows and FreeBSD for various projects and my personal PCs) and getting back to Linux via Ubuntu has really been fun. Because of the Vista / Office2007 problems I have seen I will be going Linux for everything I can from here on out. 
 
However, I am very newbish about certain things still and hope to get some help here. 
**Recently the update manager on Feisty updated my libdvdcss2 to version 1.2.9-2 and this instantly broke my DVD playback.** Totem and VLC both say they cannot access the DVD anymore (worked fine before that update). 
 
**Running the script at /usr/share/doc/libdvdread3/install-css.sh downgrades libdvdcss2 to version 1.2.5-1 and DVD playback works fine after that.** I know this must be something that either affects a lot of people or something stupid and simple on my part because it is so easy to reproduce and is caused by an "official" upgrade and fixed by an "official" install script.
 
**How can I upgrade to the latest and greatest without breaking CSS block-read support?**
 
I'm trying to use the official packages and managers as much as possible so please don7t recommend using automatix or the like. 
 
Thanks and best regards,
Ray Mercer

---

### Post by Pumalite on 2007-06-16
> **raymer said:**
> First let me say that I really like Ubuntu. I have been away from the Linux world (used to use RedHat) for a couple of years (using Windows and FreeBSD for various projects and my personal PCs) and getting back to Linux via Ubuntu has really been fun. Because of the Vista / Office2007 problems I have seen I will be going Linux for everything I can from here on out. 
 
However, I am very newbish about certain things still and hope to get some help here. 
**Recently the update manager on Feisty updated my libdvdcss2 to version 1.2.9-2 and this instantly broke my DVD playback.** Totem and VLC both say they cannot access the DVD anymore (worked fine before that update). 
 
**Running the script at /usr/share/doc/libdvdread3/install-css.sh downgrades libdvdcss2 to version 1.2.5-1 and DVD playback works fine after that.** I know this must be something that either affects a lot of people or something stupid and simple on my part because it is so easy to reproduce and is caused by an "official" upgrade and fixed by an "official" install script.
 
**How can I upgrade to the latest and greatest without breaking CSS block-read support?**
 
I'm trying to use the official packages and managers as much as possible so please don7t recommend using automatix or the like. 
 
Thanks and best regards,
Ray Mercer

My advice to you is: if your system is working, don't update. Wait until the next release.

---

### Post by wpshooter on 2007-06-16
Have you reported this as a bug ?

---

### Post by raymer on 2007-06-16
> **Pumalite said:**
> My advice to you is: if your system is working, don't update. Wait until the next release.
 
OK, good advice ;-) Is there any way to get rid of the update notification that pops up on every login to the Gnome destop? Can this be silenced temporarily until the next release?
 
By the way, I apologize if this is not the most appropriate forum for update manager questions. 
 
Thanks,
Ray

---

### Post by raymer on 2007-06-16
> **wpshooter said:**
> Have you reported this as a bug ?
 
Done.
<[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/120704](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/120704)>
 
Although the developers of ubuntu probably don't want to touch libdvdcss with a ten-foot pole! :-) What a mixed up world we live in when I'm scared to watch my own DVDs because of crazy copyright laws...

---

### Post by raymer on 2007-06-16
[quote=raymer;2855070]Done.
<[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/120704](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/120704)>
[quote]
 
Well... the bug report was rejected already because libdvdcss2 is not really an official ubuntu package - although I installed it with the official script located in my ubuntu fiesty disty. and the package-manager is official. Does anybody have a suggestion on how to proceed? 
 
-Ray

---

### Post by Pumalite on 2007-06-16
> **raymer said:**
> [quote=raymer;2855070]Done.
<[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/120704](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/120704)>
[quote]
 
Well... the bug report was rejected already because libdvdcss2 is not really an official ubuntu package - although I installed it with the official script located in my ubuntu fiesty disty. and the package-manager is official. Does anybody have a suggestion on how to proceed? 
 
-Ray

Check this:

[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

---

### Post by psiu on 2007-06-16
Got my dvd playback working again, thanks for the info on this one!

---

### Post by raymer on 2007-06-18
Pumalite said:
> 
Check this:
[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)
 
Thanks for the reply but I'm not sure what you are saying here - did you read the thread? I had DVD playback working and the update manager installed a new version of libdvdcss2 which broke DVD playback. How does this link relate?
 
Maybe you are saying I should post in Medibuntu-specific forum?

---

### Post by raymer on 2007-06-18
> **psiu said:**
> Got my dvd playback working again, thanks for the info on this one!
 
Glad it helped - that install script is not obvious. But it works well. I'm glad they included it in the distribution.

---

### Post by noynac on 2007-06-18
> **raymer said:**
> OK, good advice ;-) Is there any way to get rid of the update notification that pops up on every login to the Gnome destop? Can this be silenced temporarily until the next release?...

You can lock the version of a program using synaptic (look under the Package menu). If the older version of libdvdcss2 works and the newer one doesn't, I'd lock in the older version. I assume that you still want to get security and other updates. 

BTW, the newer version is the one that comes from medibuntu and seems to work well with most computers (it does with mine). Perhaps there is a problem with one of the other programs needed for encrypted DVD playback. See "Starting Fresh with xine Based Players" at:

[http://tinyurl.com/sujvo](http://tinyurl.com/sujvo)

---

### Post by raymer on 2007-06-18
Noynac,
> **noynac said:**
> You can lock the version of a program using synaptic (look under the Package menu). If the older version of libdvdcss2 works and the newer one doesn't, I'd lock in the older version. I assume that you still want to get security and other updates. 
Great info. Thanks! I just did this.

> BTW, the newer version is the one that comes from medibuntu and seems to work well with most computers (it does with mine). Perhaps there is a problem with one of the other programs needed for encrypted DVD playback. See "Starting Fresh with xine Based Players" at:
[http://tinyurl.com/sujvo](http://tinyurl.com/sujvo)I think I used this page to get started myself. In any case 'apt-cache policy' shows that I have the following versions for necessary bits listed on that page:

libdvdread3:
  Installed: 0.9.7-2ubuntu1
  Candidate: 0.9.7-2ubuntu1
  Version table:
 *** 0.9.7-2ubuntu1 0
        500 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/universe Packages
        100 /var/lib/dpkg/status
ray@raymer:~$ apt-cache policy libxine1-ffmpeg
libxine1-ffmpeg:
  Installed: 1.1.4-2ubuntu3
  Candidate: 1.1.4-2ubuntu3
  Version table:
 *** 1.1.4-2ubuntu3 0
        500 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/universe Packages
        100 /var/lib/dpkg/status

Do you have different versions of these? Are there any other parts I should upgrade? I am up to date on everything from the universe and multiverse repositories as far as I know...

-Ray

---

### Post by noynac on 2007-06-18
Those are the same versions as I have. Do you have totem-xine installed and not totem-gstreamer? 

Sound like locking in the old version is probably the best option in your case.

---

