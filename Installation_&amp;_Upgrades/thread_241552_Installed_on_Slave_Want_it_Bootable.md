---
title: "Installed on Slave Want it Bootable"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by v1nce on 2006-08-22
I just finished installing Ubuntu on a slave hard drive, my master is a Windows install. Instead of seeing GRUB, the boot manager every time I boot my computer I'd rather move it if possible to the second hard drive this way if I want to run Ubuntu all I have to do is hit the F9 key when my computer boots up to select another drive to boot to then I'd choose the Ubuntu drive. Is this possible since right now Grub is on my master drive?

---

### Post by v1nce on 2006-08-24
Do I take it that this is impossible or no one's ever done this before? :-(

---

### Post by confused57 on 2006-08-24
You could repair the Windows mbr by booting up with the Windows installation cd(not a recovery cd), press "r" for recovery mode, then enter **fixmbr**, as explained in this tutorial:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If you can't boot Ubuntu using F9, you may need to reinstall grub to hdb1:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

I don't know if this is what you're looking for, should work...but no guarantees.

---

### Post by mpgarate on 2006-08-24
I have a similar situation. I installed ubuntu on my slave HD on my windows pc, hoping to move the HD over to the computer I want to use it on later, without changing the windows computer at all. I chose this because the ubuntu install hung for hours when I tried to boot off the CD on the non-windows computer. I succesfully Installed it on the windows computer on the second HD, but now I have 2 problems. I tried switching the HD over to the non windows computer, but It would not boot. Just a black screen with a blinking cursour. I figure I need to install GRUB on that computer, and I could not figure out how to do that. After I get that to work, I would like to uninstall GRUB and re-install the normal booter for windows, on my windows computer.

---

### Post by v1nce on 2006-08-25
Thanks confused! First I used the MbrFix utility to restore my Windows MBR then I installed Grub to hd (1,0) my slave drive which I have Ubuntu on. It all worked like a charm (well that is after I did it wrong by doing setup (hd0) instead of (hd1) - now I have Windows perfectly booting up by default and if I want Ubuntu to boot I just select the slave drive to boot after my BIOS screen :)

MUCH better for me, thanks again for the help guys!

---

