---
title: "No way to get exact ISO file sizes"
date: 2015-06-19
forum: Installation &amp; Upgrades
---

### Post by tiaan3 on 2015-06-19
I am trying to download ubuntu-14.04.2-desktop-i386.iso. Afterwards the MD5 sum does not match that which is publicized on the Ubuntu web page. I'm trying to figure out whether it was short downloaded or what but I can't get the file size in any way. The closest I get is 1Gb which is not exactly helpful. The ftp server shows it to be a symbolic link to an inaccessible directory and the web page just shows 1Gb. Please help.

---

### Post by slickymaster on 2015-06-19
Have you tried this link:
Download: [http://cdimage.ubuntu.com/trusty/daily-live/current/trusty-desktop-i386.iso]("http://cdimage.ubuntu.com/trusty/daily-live/20150218.1/trusty-desktop-i386.iso")
MD5 checksum: [http://cdimage.ubuntu.com/trusty/daily-live/current/MD5SUMS]("http://cdimage.ubuntu.com/trusty/daily-live/20150218.1/MD5SUMS")

---

### Post by tiaan3 on 2015-06-19
The requested URL /trusty/daily-live/20150218.1/trusty-desktop-i386.iso was not found on this server.

---

### Post by slickymaster on 2015-06-19
> **tiaan3 said:**
> The requested URL /trusty/daily-live/20150218.1/trusty-desktop-i386.iso was not found on this server.
I initially posted the wrong url, sorry for that. I've already edit my post correcting it. Can you please try again.

---

### Post by tiaan3 on 2015-06-19
Thanks, MD5 sums matched. As a closing remark I'd say it would have been helpful for Ubuntu to somehow list the file size along with the MD5 sum else its a semi-blind process when the MD5 sum doesn't match.

---

### Post by sudodus on 2015-06-19
Many people prefer to get the Ubuntu iso files via ***torrent***. An iso file will be divided into a large number of small chunks, and each chunk will be transferred and checked (with a checksum method). Afterwards the chunks will be assembled to the whole file (automatically). This method can manage bad internet connections (simply re-send a chunk that is not correct). ***Transmission*** is a program the comes with Ubuntu for managing torrents, but several other programs are available in linux.

---

