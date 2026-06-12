---
title: "Dual-boot with xp. GRUB error 17!"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by Mike7171 on 2008-03-24
I tried to dual boot Ubuntu with Windows XP. Everything seemed to go well until I rebooted. I got GRUB error 17. I have no idea what it is, or how to fix it. Any and all help is greatly appreciated.

---

### Post by zdude on 2008-03-24
You might try Super Grub to help fix the problem. It is downloaded as an ISO. I just used it this morning to fix my Grub error 17 - windows borked the MBR somehow.

---

### Post by Mike7171 on 2008-03-24
Where/how do I download  and install it? And what do I do with it afterwards?

---

### Post by Mike7171 on 2008-03-24
Anyone know how to fix this? I really need to fix this.

---

### Post by Mike7171 on 2008-03-24
One last bump. I really need help with this

---

### Post by logos34 on 2008-03-24
burn it to a cd as an IMAGE, then boot from it:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Mike7171 on 2008-03-24
Alright, I put it onto a disc. So I boot from it, and then what? Are there any specific actions I should take?

Just in case it's important, my computer had Windows first, and I'm attempting to dual boot Ubuntu on to it. If any fdisk specs are needed before I do anything with SuperGrub, let me know. I'll get it. Thank you in advance,

EDIT: is this simple to use? Or do I have to choose specific things? I'm not sure what to do in relation to my problem.

---

### Post by Mike7171 on 2008-03-24
Has anyone used it before?

---

### Post by zdude on 2008-03-25
It is pretty simple, boot the disk and I think there is an auto mode. If your old menu.lst (which is stored on your linux partition at /boot/grub/menu,lst) is still intact it should find it and patch the mbr to point to it. Use google to find more info.

---

