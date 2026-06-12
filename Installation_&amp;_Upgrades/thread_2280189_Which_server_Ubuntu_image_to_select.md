---
title: "Which server Ubuntu image to select"
date: 2015-05-28
forum: Installation &amp; Upgrades
---

### Post by manish-sehgal on 2015-05-28
Hi There,

I am new to ubuntu. I need to configure a new server. Could you please help me understand which image I should use among the different ones listed:

[ubuntu-14.04.1-server-i386.iso]("http://old-releases.ubuntu.com/releases/14.04.0/ubuntu-14.04.1-server-i386.iso")

[ubuntu-14.04.1-server-i386.iso.torrent]("http://old-releases.ubuntu.com/releases/14.04.0/ubuntu-14.04.1-server-i386.iso.torrent")

[ubuntu-14.04.1-server-i386.iso.zsync]("http://old-releases.ubuntu.com/releases/14.04.0/ubuntu-14.04.1-server-i386.iso.zsync") 

[ubuntu-14.04.1-server-i386.jigdo]("http://old-releases.ubuntu.com/releases/14.04.0/ubuntu-14.04.1-server-i386.jigdo") 

[ubuntu-14.04.1-server-i386.list]("http://old-releases.ubuntu.com/releases/14.04.0/ubuntu-14.04.1-server-i386.list") 

Is there any specific reason to use one above other?

Thanks,

---

### Post by mastablasta on 2015-05-29
all are 32bit images that use various download techniques. one of safest way to do is via torrent file as images hash is checked during download. but other methods are fine as well. 

note that unless you plan to install on some old server with low ram it would make more sense to download a 64bit (the AMD64 image).

---

### Post by Bucky Ball on 2015-05-29
Welcome. Download [this]("http://www.ubuntu.com/download/server") if you are using 64bit. If not, select 32bit. 

For torrents, go [here]("http://www.ubuntu.com/download/alternative-downloads"), scroll down the page a bit to the heading 'Bittorrent'. Done.

Don't use any of the links you provided. They are all 14.04.1, the first point release. 14.04 is now at 14.04.2. I've no idea where you found those links, but you should stick to the official Canonical sources for downloading your .iso. Good luck.

---

