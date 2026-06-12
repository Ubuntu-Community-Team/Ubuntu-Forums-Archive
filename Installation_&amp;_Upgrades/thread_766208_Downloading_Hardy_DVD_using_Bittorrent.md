---
title: "Downloading Hardy DVD using Bittorrent"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Ingo88 on 2008-04-25
Hi!

I thought I'd download a DVD with Ubuntu Hardy, preferably using Bittorrent, but seems like this isn't too easy. Firstly I didn't find the dvd images anywhere, let alone torrent files. After searching the forum I found my way to [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/). However there were five different dvd images there, and none of them matched the md5sum of the image found at [http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/). So there are six different DVDs to choose from? Before noticing this I had started a download of the torrent with md5sum 6c2f277eadcf54521a4f3c119704dbe6f3bc68b2. The download never gets started, though. Probably no seeders.

What to do? Maybe we aren't supposed to download the DVD?

(By the way, how come I got different and fewer results when I searched the forums while logged in than when I wasnt? :?)

Thanks in advance for your help! :)

---

### Post by ch1c0dj on 2008-04-25
Hi, I also downloading the ubuntu-8.04-dvd-i386.iso thru torrent, [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)
What I did is I add the following tracker to the torrent. the first entry is the default tracker, no need to add it, i just include it for no reason. After adding the tracker I notice a significant changes in download speed, and seeders/peers got high in numbers.

I got this to some of the torrent search engine that have ubuntu-8.04-dvd-i386.iso torrent active.

[http://torrent.ubuntu.com:6969/announce](http://torrent.ubuntu.com:6969/announce)
official tracker

[I][http://tpb.tracker.thepiratebay.org:80/announce](http://tpb.tracker.thepiratebay.org:80/announce)
[http://tracker4.finalgear.com:80/announce](http://tracker4.finalgear.com:80/announce)
[http://tracker.prq.to:80/announce](http://tracker.prq.to:80/announce)[/I]
**unofficial tracker, not recommended anymore.**

---

### Post by kraymore on 2008-04-25
is ubuntu-8.04-dvd-i386.iso an official canonical release ?

thanks

---

### Post by lswest on 2008-04-25
seems the DVD is just an Alternate install CD, Wubi installer and LiveCD all in one, may have a few extras to it too, not sure, never used it before, but i'm bored, so i'm downloading it too XD

---

### Post by AndyCee on 2008-04-25
Message removed

---

### Post by Ingo88 on 2008-04-26
> **chicodj said:**
> Hi, I also downloading the ubuntu-8.04-dvd-i386.iso thru torrent, [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)
What I did is I add the following tracker to the torrent. the first entry is the default tracker, no need to add it, i just include it for no reason. After adding the tracker I notice a significant changes in download speed, and seeders/peers got high in numbers.

I got this to some of the torrent search engine that have ubuntu-8.04-dvd-i386.iso torrent active.



[http://torrent.ubuntu.com:6969/announce](http://torrent.ubuntu.com:6969/announce)

[http://tpb.tracker.thepiratebay.org:80/announce](http://tpb.tracker.thepiratebay.org:80/announce)

[http://tracker4.finalgear.com:80/announce](http://tracker4.finalgear.com:80/announce)

[http://tracker.prq.to:80/announce](http://tracker.prq.to:80/announce)

Thanks for your help!

It didn't work for me, though. Maybe I did something wrong? I use [utorrent](http://www.utorrent.com/)

[quote=AndyCee]http://www.torrentportal.com/details/3161229/ubuntu-8.04-dvd-i386.iso.torrent[/quote]

utorrent says "Invalid torrent file" when I try to open that one. Thanks anyway :)

---

### Post by ch1c0dj on 2008-04-26
> **kraymore said:**
> is ubuntu-8.04-dvd-i386.iso an official canonical release ?

thanks

I believe torrent from [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/) is for official release

---

### Post by ch1c0dj on 2008-04-26
> **Ingo88 said:**
> Thanks for your help!

It didn't work for me, though. Maybe I did something wrong? I use [utorrent](http://www.utorrent.com/)

utorrent says "Invalid torrent file" when I try to open that one. Thanks anyway :)


***maybe because the torrent file that you downloaded is not complete or corrupted ** *

[B]here's the step.
[/B]

. open [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/) to your browser

. find ubuntu-8.04-dvd-i386.iso

. download the torrent file ,[[COLOR="DarkRed"][COLOR="Red"]ubuntu-8.04-dvd-i386.iso.torrent[/COLOR][/COLOR]]("http://torrent.ubuntu.com:6969/file?info_hash=l/%27%7E%AD%CFTR%1AO%3C%11%97%04%DB%E6%F3%BCh%B2")

. open ubuntu-8.04-dvd-i386.iso.torrent using **utorrent**

. see the attached screenshot

[INDENT]- right-click the ubuntu-8.04-dvd-i386.iso name for download in utorrent

- select properties

- in Torrent Properties add this lines

[INDENT][http://torrent.ubuntu.com:6969/announce](http://torrent.ubuntu.com:6969/announce)

[http://tpb.tracker.thepiratebay.org:80/announce](http://tpb.tracker.thepiratebay.org:80/announce)

[http://tracker4.finalgear.com:80/announce](http://tracker4.finalgear.com:80/announce)

[http://tracker.prq.to:80/announce](http://tracker.prq.to:80/announce)

[http://linuxtracker.org:2710](http://linuxtracker.org:2710)[/INDENT]

- click OK to apply.

[/INDENT]

---

### Post by Ingo88 on 2008-04-27
> **chicodj said:**
> . open [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/) to your browser

. find ubuntu-8.04-dvd-i386.iso

. download the torrent file ,[[COLOR="DarkRed"][COLOR="Red"]ubuntu-8.04-dvd-i386.iso.torrent[/COLOR][/COLOR]]("http://torrent.ubuntu.com:6969/file?info_hash=l/%27%7E%AD%CFTR%1AO%3C%11%97%04%DB%E6%F3%BCh%B2")

. open ubuntu-8.04-dvd-i386.iso.torrent using **utorrent**

. see the attached screenshot

[INDENT]- right-click the ubuntu-8.04-dvd-i386.iso name for download in utorrent

- select properties

- in Torrent Properties add this lines

[INDENT][http://torrent.ubuntu.com:6969/announce](http://torrent.ubuntu.com:6969/announce)

[http://tpb.tracker.thepiratebay.org:80/announce](http://tpb.tracker.thepiratebay.org:80/announce)

[http://tracker4.finalgear.com:80/announce](http://tracker4.finalgear.com:80/announce)

[http://tracker.prq.to:80/announce](http://tracker.prq.to:80/announce)

[http://linuxtracker.org:2710](http://linuxtracker.org:2710)[/INDENT]

- click OK to apply.

[/INDENT]

Thanks again for your help! :D

This sure did the trick. Now the DVD is coming down at full speed :)

May I still ask you where you found these additional trackers? Could be good to know in the future. Such as when 8.04.1 is released ;)

(I am however still puzzled by the fact that there are at least six different DVD images to choose from. I guess - and hope - that this is the right one, but how can you be sure especially as the image at [http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/) has a completely different md5sum?)

---

### Post by avi.wollman on 2008-04-29
from [http://aamodnerurkar.blogspot.com/](http://aamodnerurkar.blogspot.com/)

MD5SUM - 088b5d9e656dd89483dbb1b845b96fb9 *ubuntu-8.04-dvd-i386.iso
975d92e98ea1fa25a07a763a0a072d41 *ubuntu-8.04-dvd-amd64.iso

I got the same.

Avi

---

### Post by Ingo88 on 2008-04-29
> **Ingo88 said:**
> the image at [http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/) has a completely different md5sum

My download was completed today. I was surprised when I checked the md5sum of the downloaded image. It actually matched the one at [http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/) (088b5d9e656dd89483dbb1b845b96fb9). So the md5sum displayed at [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/) (6c2f277eadcf54521a4f3c119704dbe6f3bc68b2) is wrong. How funny :D

Well, happy end anyway :)

---

### Post by AldenIsZen on 2008-05-09
He's right, it does.. someone got them mixed up when they updated it.

---

### Post by ch1c0dj on 2008-06-09
> **Ingo88 said:**
> 
May I still ask you where you found these additional trackers? Could be good to know in the future. Such as when 8.04.1 is released ;)

I found it in (ubuntu-8.04-dvd-i386.iso) torrent from other torrent search engine.

> **Ingo88 said:**
> 
(I am however still puzzled by the fact that there are at least six different DVD images to choose from. I guess - and hope - that this is the right one, but how can you be sure especially as the image at [http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/) has a completely different md5sum?)

[http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/)   <<   Ubuntu 8.04 LTS (Hardy Heron) Daily Build
AFSK, this is where the daily image of the ubuntu is packed. that is why MD5SUM file from [http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/) is different from [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/) MD5SUM file.
AFSK. Tracker can be reused and no harm effect to the downloaded file.

What you should do is open [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/) to your browser then look for the file ubuntu-8.04-dvd-i386.iso then download its torrent file and open to your favorite torrent clients.

Sorry for late reply.

---

