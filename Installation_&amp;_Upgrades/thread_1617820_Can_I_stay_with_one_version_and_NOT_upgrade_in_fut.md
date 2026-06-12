---
title: "Can I stay with one version and NOT upgrade in future?"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by zhaotianwu on 2010-11-09
I know this question might sounds a bit unusual, but it is because I've read some articles saying that Ubuntu is like a gambling and you never know if the next version is win or lose. 

For me, if 10.10 works fine, then I will just burn a CD and try not upgrade, is it possible? I'm not a computer-person, so I am wondering if such upgrading is mandatory? Or de-facto mandatory? like you will lose all the support if you are not upgrading? Thanks.

---

### Post by qamelian on 2010-11-09
It isn't mandatory to upgrade, but you do need to realize that each version is only supported for a certain period of time. While some upgrades can cause problems, more often than not, they provide bug fixes, security fixes, and/or additional functionality. Whether or not you upgrade is purely your choice and only you can decide, based on your own needs, if an upgrade is desirable.

Personally, I always upgrade. Some others only upgrade from one Long Term Support release to the next.

---

### Post by zhaotianwu on 2010-11-09
> **qamelian said:**
> It isn't mandatory to upgrade, but you do need to realize that each version is only supported for a certain period of time. While some upgrades can cause problems, more often than not, they provide bug fixes, security fixes, and/or additional functionality. Whether or not you upgrade is purely your choice and only you can decide, based on your own needs, if an upgrade is desirable.

Personally, I always upgrade. Some others only upgrade from one Long Term Support release to the next.


Ok, what is Long Term Support then?

---

### Post by witeshark17 on 2010-11-09
The latest long term support (LTS) is 10.04,  8.04 was the previous.

---

### Post by tommcd on 2010-11-10
> **zhaotianwu said:**
> Ok, what is Long Term Support then?
The LTS versions are supported for at least 3 years for the desktop versions. All other versions are supported for 18 months. You can see when each Ubuntu version will reach end of life here:
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
As for upgrading to the next version, I always do clean installs instead of dist-upgrades. This is the best way to avoid problems imo. Of course, whether you upgrade with a clean install or a dist-upgrade is your choice also. Many people do dist-upgrades to get to the next version.

---

### Post by efflandt on 2010-11-10
You can run a Linux version for as long as you want to.  It is just that eventually there will no longer be any updates.  I am running apache on an old version of SuSE on one computer that has not even rebooted since July 2006.  I don't know if that was the last time there were updates or if I shut it down during long power failure.

```
efflandt@XPS-8100:~$ ssh mainpc
Last login: Sat Oct 23 16:57:26 2010 from 172.16.0.68
Have a lot of fun...

efflandt@realhost:~> cat /etc/*release
SuSE Linux 8.2 (i586)
VERSION = 8.2

efflandt@realhost:~> ls -l /var/log/boot*
-rw-r-----    1 root     root            0 2003-05-17 18:03 /var/log/boot.log
-rw-r--r--    1 root     root        20461 2006-07-20 16:00 /var/log/boot.msg
-rw-r--r--    1 root     root        24670 2006-07-20 04:45 /var/log/boot.omsg

efflandt@realhost:~> free
             total       used       free     shared    buffers     cached
Mem:        158808     155616       3192          0      53224      11952
-/+ buffers/cache:      90440      68368
Swap:       370400       7388     363012

efflandt@realhost:~> uname -a
Linux realhost 2.4.20-4GB #1 Tue Mar 29 13:05:16 UTC 2005 i686 unknown unknown GNU/Linux

model name   : Celeron (Mendocino)
stepping     : 0
cpu MHz      : 333.062
cache size   : 128 KB
bogomips     : 665.19
```

---

### Post by qamelian on 2010-11-10
> **tommcd said:**
> As for upgrading to the next version, I always do clean installs instead of dist-upgrades. This is the best way to avoid problems imo. 
This is not always the case. There have been two different releases of Ubuntu (Intrepid and Karmic) that I could not install via fresh install on my hardware. My only option was to install the previous release and upgrade in place. Despite what some people say about clean installs versus upgrades, I have only ever had problems with clean installs and upgrades have always worked flawlessly.

---

### Post by kucerarichard on 2010-11-10
hm,  maybe I will click that upgrade button and be done with it... 9.10 -> 10.04.1

..aw man I've still got 7 hours and 41 minutes left on backing up my home directory... this is a drag..  it's free and not winblows though so can't complain.

I was clearly more productive on this distro than suse.  so I just said just click the upgrade and cross your fingers.   don't really care if gnome and X are out the window in the future.   except for maybe well,   tightvnc support.

ok if it crashes and I have to wipe and reinstall,  what will it be?   opensuse?  mandriva?  mint?   what?

if I'm stuck on 9.10 and it won't upgrade,  then I ought not to go further down this deadend anyways.

i hope I can be done with this :-)    there is no compelling reason to go to any other distro.   esp.  if I'm productive on ubuntu already.

---

### Post by I'mGeorge on 2010-11-10
This it's more like a rhetorical question. Sure you can but the beauty of linux it's that you can always update/upgrade your system and it won't cost you a dime, so I guess you'll be missing all the fun

---

### Post by kucerarichard on 2010-11-11
2 days later and I'm still backing up sh#t so I can press the 10.04.1 upgrade button...

---

### Post by snowpine on 2010-11-11
When you go to the store and buy a carton of milk, it has a "Best by ___" date. Ubuntu is no different. You are free to keep using Ubuntu after its "end of life" date, but it might taste a little sour. :)

---

### Post by mcduck on 2010-11-11
> **zhaotianwu said:**
> I know this question might sounds a bit unusual, but it is because I've read some articles saying that Ubuntu is like a gambling and you never know if the next version is win or lose. 

For me, if 10.10 works fine, then I will just burn a CD and try not upgrade, is it possible? I'm not a computer-person, so I am wondering if such upgrading is mandatory? Or de-facto mandatory? like you will lose all the support if you are not upgrading? Thanks.

if you don't want to install any more programs, get new versions of any program, or have the computer connected to Internet (since you won't get security updates either) then yes, you can run any version as long as you want to. :)

You shouldn't make such decisions based on some articles. People who have problems tend to make lots of noise, while the majority who have no problems are happy and quiet. The only way to know if *you* have problems with an update is doing the update. For most users the updates cause no problems. If they did, there would be significantly less Ubuntu users by now. :D

---

### Post by kucerarichard on 2010-11-15
ok.  backups done..  here goes nothin.    (I must be crazy...)

will do a complete 9.10 up-to-date,   reboot,  then go for it...

---

### Post by dino99 on 2010-11-15
its like saying: "can i stay young all my life long" :)

---

### Post by kucerarichard on 2010-11-15
> **dino99 said:**
> its like saying: "can i stay young all my life long" :)


:-) hee hee

ok,  rebooted,    time to click it

feel lucky punk,  

goodbye diarrhea 

and all that..

cheers

---

### Post by kucerarichard on 2010-11-15
I MADE IT!!!!!!

Everything is there...  jedit runs,  emacs runs,  chrome runs,  xampp runs...

cool desktop,   hello LTS,  no fuss,  no need to switch distros.


:guitar:

[http://www.youtube.com/watch?v=k1Ww-EwBb9I](http://www.youtube.com/watch?v=k1Ww-EwBb9I)

---

### Post by tommcd on 2010-11-15
> **kucerarichard said:**
> ok.  backups done..  here goes nothin.    (I must be crazy...)
will do a complete 9.10 up-to-date,   reboot,  then go for it...
If you create a separate /home partition, then all of your data will be safe on it's own partition and you will not need to back it up in order to reinstall Ubuntu.
See this for creating a separate home partition in Ubuntu using the manual partitioning option in an Ubuntu install:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
> **kucerarichard said:**
> 
I MADE IT!!!!!!
Everything is there... jedit runs, emacs runs, chrome runs, xampp runs...
Glad you got it all worked out! Happy *buntuing!!!
It is important to note here that reinstalling Ubuntu becomes much easier after you have done it a few times. I can reinstall Ubuntu in about 15-20 minutes. Then there is perhaps another hour or so (at the most!) to get all the updates and install all the software I use. So in 90 minutes or less (usually less) I am up and running again with a new pristine Ubuntu install. And most of that time is spent waiting for stuff to finish.

---

