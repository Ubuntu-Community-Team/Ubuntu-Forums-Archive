---
title: "How do i install conky offline"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by ANiK3T on 2013-02-04
Hi all
im an offline user 
how can i install any version of conky being Offline
i dont have an internet connection i go to cyber cafe
pls help

---

### Post by schragge on 2013-02-04
[LIST]
[*]Download the deb for your Ubuntu release from
[http://archive.ubuntu.com/ubuntu/pool/universe/c/conky/](http://archive.ubuntu.com/ubuntu/pool/universe/c/conky/) or from [another mirror]("https://launchpad.net/ubuntu/+archivemirrors") and any additional companions you need from [Conky Companions PPA]("https://launchpad.net/%7Econky-companions/+archive/ppa/+packages").
[*]Save the files to a USB stick.
[*]At home, insert the USB stick, and type in a terminal window (assuming your USB stick is mounted as /media/usb):```
sudo dpkg -i /media/usb/*.deb
```
[/LIST]

---

