---
title: "install on firewire with vista"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by kpurcell on 2006-07-19
I have a Dell 9300 running the beta 2 of windows vista.
I would like to install a dual boot of ubuntu onto an external firewire drive.

I ran the installer from the dapper live cd and all went well.  But when I reboot it loads vista without an option to boot to the firewire drive.

my devices are ...
 /dev/sda1 for the vista drive which I would like to load by default.
/dev/sdb1 for the firewire drive which has ubuntu already installed but I cannot boot to it right now

I am a total noob so if you could either give me simple step by step or point me to a place that has a simple step by step to get grub installed on the /dev/sda1 and have it boot that drive by default and give me an option to boot the /dev/sdb1 drive which has ubuntu 6.06

thanks

---

### Post by x64Jimbo on 2006-07-19
Booting from firewire is a very tricky thing. A lot of BIOSes don't support it. You should make sure your hardware supports booting from firewire before you spend any more effort on trying to get it to work.

---

### Post by kpurcell on 2006-07-20
thanks x64Jimbo.

I realized that my laptop does not support this.

Is it possible to create a small boot partition on the main drive (/dev/sb1) and then have everything else on the firewire drive?  If so, how would I do this?

My problem is I have a 100 GB notebook drive that is actually a 93 GB drive.  I have about 78 GB of info and windows will only give up about 830 mb of drive space.

---

### Post by x64Jimbo on 2006-07-20
Have a look at this article. It may help you:
[http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html](http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html)

---

### Post by kpurcell on 2006-07-20
Well, my drive is actually a Firewire and USB drive.  So I just plugged in via USB and my computer can boot a USB drive.  So now I'm responding in Ubuntu.

---

### Post by x64Jimbo on 2006-07-22
hehe glad to hear that. :)

---

