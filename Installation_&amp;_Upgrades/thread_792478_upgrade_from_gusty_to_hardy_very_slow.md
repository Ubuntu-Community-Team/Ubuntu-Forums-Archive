---
title: "upgrade from gusty to hardy very slow"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by srimalik on 2008-05-13
Hello, 

I have just installed ubuntu gusty on my laptop.

I am trying to upgrade from gusty to hardy, when I install/upgrade/patch any packages in gusty the download speed I get is ~200 kbps but when do a distro upgrade the download speed is 2-10 kbps only.

I tried finding out and setting  the fastest mirror but that didn't help the upgrade is still slow.

Also, tried to add the nearest mirror to sources.list.distupgrade

deb [http://ftp.iitm.ac.in/ubuntu/](http://ftp.iitm.ac.in/ubuntu/) hardy main universe restricted multiuniverse but that also didn't help.

One this I noticed is: the updater is downloading software from canonical site only and seems to be ignoring all other mirrors.
output of netstat shows me this:

tcp        0      0 l3-lr893.local:52613    lithium.canonical.c:www ESTABLISHED
 
I have arch on all my other machines and the procedure there is quite simple.

I am unaware of what should I change in ubuntu to pickup the nearest mirror???

-Sri

---

### Post by lemming465 on 2008-05-19
> ... what should I change in ubuntu to pickup the nearest mirror
The timezone, at least during the initial install.

Anothe option is to download the alternate CD's, and use those to do a local offline upgrade.

---

### Post by aha5262 on 2008-11-08
> **lemming465 said:**
> The timezone, at least during the initial install.

Anothe option is to download the alternate CD's, and use those to do a local offline upgrade.

There seem to be some problem with that upgrade. Because what I hoped would be a quick update is quite opposite. At this moment I am trying to upgrade to ubuntyu 8.10 from 8.04. I canceled the first attempt from the alternate cd, because it seemed it will take many days  to upgrade. The second attempt I answered No to fetch internet updates, but the upgrade dialog still show 'fetching xxxx of 1911 at xx kB/s'. xx days and xx hours remaining'. So what is the use of xx hours of downloading the alternate cd when the upgrade happen via internet and slow servers anyhow? I thought the upgrade from cd would be fast.

---

