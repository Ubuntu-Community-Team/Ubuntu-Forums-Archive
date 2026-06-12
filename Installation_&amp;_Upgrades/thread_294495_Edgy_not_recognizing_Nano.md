---
title: "Edgy not recognizing Nano"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by Kismet on 2006-11-06
I just upgraded from Dapper to Edgy, and my ipod is nolonger recognized. On dapper as soon as I plugged it in, it shows up on the desktop, I can right-click, mount, and then connect to it in amarok just fine. 

Now when I plug it in, no icon shows up on the desktop. I can manually mount it using ```
 sudo mount /dev/sda2 /media/ipod 
``` I can then goto the media directory and it appears all the pertinent ipod files are there, but I still cannot see it on the desktop, or connect to it using amarok. 

Thanks

---

### Post by Kismet on 2006-11-07
Not sure why this was happening, but a
[CODE]
sudo apt-get autoremove amarok libgpod0
sudo apt-get install amarok libgpod0
[\CODE]

seems to have solved it, if anyone is interested.

---

