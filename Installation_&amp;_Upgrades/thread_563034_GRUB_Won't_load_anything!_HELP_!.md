---
title: "GRUB Won't load anything! HELP !"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by Guardian-Mage on 2007-09-29
I have WIndows XP Home on my internal hard disk and I just installed Ubuntu 7.10 Beta on my External Hard Disk. When I boot up I get the GRUB loading message than an error 18. I googled it and I have no idea what it meant when I read it. I am using my live CD right now. How do I fix this? I can't even get into windows, I need a step by step guide. Please hurry.

My Computer is very new if that helps

---

### Post by Pumalite on 2007-09-29
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by Guardian-Mage on 2007-09-29
My Computer is Brand New. I installed Ubuntu on a portable USB hard drive with a partition size of 200+mb(accidental) and when using my live cd I am unable to resize it. I have no idea what anything on that page means. What's the best way to fix this?

---

### Post by Pumalite on 2007-09-29
That's the best link I know to give you. You are going to have to read it, understand it, and follow the suggestions. Unfortunately Linux has a learning curve.

---

### Post by kellemes on 2007-09-29
Agree with Pumalite I'm afraid..
For a quick fix of booting your system you may visit the same site, different page.
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

It's not complicated, just download/burn/boot the disk.

---

### Post by Guardian-Mage on 2007-09-29
OK, i fixed the error by resizing my partition and moving it. Next Problem, now when I boot it takes me to the Grub Command line, what is the command for booting to Ubuntu and the one for WIndows?

---

### Post by Pumalite on 2007-09-29
Do you see a Grub menu first?

---

### Post by Guardian-Mage on 2007-09-29
no

---

### Post by Pumalite on 2007-09-29
I don't like it, but you can try this:
sudo dpkg-reconfigure xserver-org, accept most defaults, choose 'vesa' as the driver, then: startx
And cross your fingers

---

### Post by Guardian-Mage on 2007-09-29
I didn't do what you said. I did this:
root (hd0,0)
rootnoverify (hd0,0)
chainloader +1
boot

and I booted to Windows XP. Can I change the settings to make the GRUB menu appear and How can I boot to ubuntu? It is on an external hard drive

---

### Post by Pumalite on 2007-09-29
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Guardian-Mage on 2007-09-29
It didn't do anything. Could it have something to do with my hard drive turning off when I reboot and not turning back on until I boot in an OS? I can I fix this?

---

