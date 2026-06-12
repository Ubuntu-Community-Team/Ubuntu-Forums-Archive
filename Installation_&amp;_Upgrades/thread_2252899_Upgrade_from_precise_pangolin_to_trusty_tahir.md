---
title: "Upgrade from precise pangolin to trusty tahir"
date: 2014-11-15
forum: Installation &amp; Upgrades
---

### Post by RotherhamN on 2014-11-15
After being pestered about the upgrade for a few months, I finally relented and went ahead. I wish I hadn't. The upgrade appeared to go smoothly enough, but when I went back in after the reboot, I noticed that not only did it take much longer, but there were a number of system errors (which I duly reported). Now that the kernel has been upgraded, I can no longer compile the realtek wireless card driver and thus could not connect to the internet without plugging directly into my hub. After finding a post on this site I downloaded a .gz file and followed the instructions. The first time I executed the required make and make install commands, the driver was built - but upon entering the modprobe command, no connection was established. I re-booted and after experiencing and reporting more system errors, it seemed slower still. This time I re-built the driver, but the make install command hung and the whole thing ground to a halt. I am writing this from windows on the same machine as Ubuntu is now of no use. This is a real shame.
Has anyone else had a similar experience? Is there a "cure"? If not, it would appear that the latest version of Ubuntu is of little use on any hardware having a realtech network card. Even with a direct connection performance is decidedly slow and there seem to be lots of errors.

---

### Post by mörgæs on 2014-11-16
> **RotherhamN said:**
> 
If not, it would appear that the latest version of Ubuntu is of little use on any hardware having a realtech network card.

We don't know that yet. How does 14.04 run in a live boot?

---

### Post by RotherhamN on 2014-11-17
I'm not sure I know what you mean by "live boot". Is this a startup option via grub?

---

### Post by Impavidus on 2014-11-17
That's booting from a live dvd or a live usb, the one you can also use to install Ubuntu. Live disks are a great tool to rescue broken Ubuntu systems.

---

### Post by RotherhamN on 2014-11-17
Well I just managed to remake the driver and the modprobe has worked. I'm not altogether sure where I went wrong when following the instructions I found here (from Chilli)
[http://ubuntuforums.org/showthread.php?t=2239745](http://ubuntuforums.org/showthread.php?t=2239745)
The only thing I can remember is executing modprobe before re-booting. This time I did as I was told by the instructions output produced by "sudo make install" and re-booted before executing modprobe and I'm now connected to the internet wirelessly - which means my main worry is sorted! Nevertheless, I have to admit to being somewhat uneasy. I don't know what is causing the system errors (a window appears saying Ubuntu has encountered a problem). Also, the cooling fan now seems to be on permanently which is annoying. Perhaps it'll go away next time I re-boot. Things do seem slower, too...

---

### Post by mörgæs on 2014-11-18
We are still awaiting your report regarding a live boot...

---

