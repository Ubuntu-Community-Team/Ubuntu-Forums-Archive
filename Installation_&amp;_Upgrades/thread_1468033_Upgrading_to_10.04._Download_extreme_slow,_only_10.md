---
title: "Upgrading to 10.04. Download extreme slow, only 10.0 B/s."
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by johnnymenmonic on 2010-05-01
Hi,

I try to upgrade to 10.04, but the download rate is extreme slow (10.0 B/s sometimes a bit better and sometimes even worser). I switch to different server but the problem remains.

---

### Post by ssdt on 2010-05-01
I think it's all because of the amount of people downloading that's making it slow. Take a couple of days so that we can evenly download and will get a definite amount of speed.

But you might check this: Fire up your "Software Sources" then go to the Ubuntu Software tab. There you will find Download from. Select Other from the drop down menu. There on the right side, press "Select Best Server". It will find the right server for you.

---

### Post by baekgaard on 2010-05-01
> **johnnymenmonic said:**
> Hi,

I try to upgrade to 10.04, but the download rate is extreme slow (10.0 B/s sometimes a bit better and sometimes even worser). I switch to different server but the problem remains.

The servers indeed are a bit slow at the moment; guess many people try the download all at the same time :P

You may want to download the alternate CD via one of the torrents; that is currently much faster. Either burn to a CD and insert into your PC while it is running the previous version -- it should then ask you if you want to upgrade. Say no to network updates; that you can do later.

Alternatively you can mount it like this

```
mount -o loop Downloads/ubuntu-10.04-alternate-amd64.iso /media/cdrom0
```

(or wherever you stored it/what version you downloaded).

You may need to run sudo /media/cdrom0/cdromupdate manually if it doesn't pop up automatically.


-- Per.

---

### Post by jmberros on 2010-05-01
I was experiencing this issue too and then tried the torrent of the cd image:

[http://btjunkie.org/search?q=ubuntu+alternate](http://btjunkie.org/search?q=ubuntu+alternate)

I just added it 5 mins ago to Transmission and paused all the other downloads. Now it's downloading it at ~300 Kb/s. :)

I'll post when done to confirm it's ok, but the torrent seems legit.

EDIT: corrected the link to the alternate CD now

---

### Post by baekgaard on 2010-05-01
You can find the torrent files directly on the download page at the Ubuntu site.

Note that if you want to to use it for upgrading, you'd need the alternate CD.


-- Per.

---

### Post by duver299 on 2010-05-01
Are you sure it wasn't 10.04 B/s.. lol

---

