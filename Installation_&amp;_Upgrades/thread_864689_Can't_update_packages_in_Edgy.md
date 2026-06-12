---
title: "Can't update packages in Edgy"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by brknee on 2008-07-19
Hi guys, looked everywhere for this problem and haven't found it...

I'm running Ubuntu Edgy Eft (6.10) and have been since May. Initially when I installed it everything worked PERFECTLY. Then I moved and switched ISPs (to AT&T, formerly Bellsouth). I can definitely connect to the internet with all my programs (Firefox, Gaim, LimeWire, etc. etc.) but I can't update ANY packages or repositories and I can't upgrade to Feisty. In Synaptic and Add/Remove Programs I always get this message:

[B]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.[/B]

I honestly don't even know what's wrong, much less how to fix it. I've noticed people having problems LIKE this before but it was apparently an overloaded server issue and they didn't have to do anything except wait, whereas it looks like this problem is on MY end. I've configured my networking and connected directly to the modem instead of the router (Belkin 54G) and done everything else I can think of; I even wiped my hard drive today and did a clean install of Edgy. What can be the issue here?

Thanks in advance!!

SOLVED. I'm outdated. :(

---

### Post by Pumalite on 2008-07-19
6.10 might not be supported anymore. I'm not sure.

---

### Post by brknee on 2008-07-19
> **Pumalite said:**
> 6.10 might not be supported anymore. I'm not sure.

I also considered that, which is why I tried to upgrade to Feisty, but I'm not sure either. Where would this information even be, I wonder?

---

### Post by Pumalite on 2008-07-19
[http://www.ubuntu.com/news/ubuntu610end-of-life](http://www.ubuntu.com/news/ubuntu610end-of-life)

---

### Post by brknee on 2008-07-19
> **Pumalite said:**
> [http://www.ubuntu.com/news/ubuntu610end-of-life](http://www.ubuntu.com/news/ubuntu610end-of-life)

Ok; thanks so much! Since I can't upgrade to Feisty directly without updating Edgy which is no longer possible, I'll get a disc burnt somehow for 7.04. Thanks again! :)

---

### Post by Pumalite on 2008-07-19
You are welcome. Good luck!

---

### Post by Liakath on 2008-07-19
Dear brknee,

> **brknee said:**
> Hi guys, looked everywhere for this problem and haven't found it...

I'm running Ubuntu Edgy Eft (6.10) and have been since May. Initially when I installed it everything worked PERFECTLY. Then I moved and switched ISPs (to AT&T, formerly Bellsouth). I can definitely connect to the internet with all my programs (Firefox, Gaim, LimeWire, etc. etc.) but I can't update ANY packages or repositories and I can't upgrade to Feisty. In Synaptic and Add/Remove Programs I always get this message:

[B]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.[/B]

I honestly don't even know what's wrong, much less how to fix it. I've noticed people having problems LIKE this before but it was apparently an overloaded server issue and they didn't have to do anything except wait, whereas it looks like this problem is on MY end. I've configured my networking and connected directly to the modem instead of the router (Belkin 54G) and done everything else I can think of; I even wiped my hard drive today and did a clean install of Edgy. What can be the issue here?

Thanks in advance!!

EdgyEft is not supported any more. See the link [HTML]http://www.ubuntu.com/news/ubuntu610end-of-life[/HTML]

You may have to upgrade through upgrade manager to latest hardy heron 8.04.1 by using this option ```
update-manager -d
``` or do a clean install after downloading hardy heron 8.04.1 from [HTML]www.ubuntu.com[/HTML]

Edit: Additional information is available here [HTML]http://www.ubuntu.com/getubuntu/upgrading[/HTML]

Liakath

---

### Post by Pumalite on 2008-07-19
> **brknee said:**
> Ok; thanks so much! Since I can't upgrade to Feisty directly without updating Edgy which is no longer possible, I'll get a disc burnt somehow for 7.04. Thanks again! :)

You might want to try this:

udo sed -i 's/edgy/feisty/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by GeekBug on 2008-07-28
or try this ...

[http://ubuntuforums.org/showthread.php?t=868926&highlight=edgy](http://ubuntuforums.org/showthread.php?t=868926&highlight=edgy)

---

### Post by stchman on 2008-07-28
Yes, the Edgy repository has been removed.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

In the news section:

2008-06-10

    Removed edgy

---

### Post by Rocket2DMn on 2008-07-28
Rather than trying to upgrade to Feisty which will be unsupported within a few short months, I suggest doing a completely fresh install for 8.04 Hardy Heron.  This is a LTS release and is supported for 3 years on the desktop, so you won't have to do updates for a few more years.

---

