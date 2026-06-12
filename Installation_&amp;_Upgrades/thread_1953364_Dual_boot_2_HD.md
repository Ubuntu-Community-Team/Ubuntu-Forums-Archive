---
title: "Dual boot 2 HD"
date: 2012-04-06
forum: Installation &amp; Upgrades
---

### Post by kompressorgpl on 2012-04-06
Hello! I have 2 HD on my pc. Can I install Win 7 on one and Ubuntu 10.04LTS on the other? And, when it cames to the boot, will be same as if they where on the same HD? Thank´s!!!

---

### Post by 2F4U on 2012-04-06
Yes, you can go that route. Here is some information on how to do it:
[http://ubuntuforums.org/showthread.php?t=1950071](http://ubuntuforums.org/showthread.php?t=1950071)

This tutorial uses the Windows boot loader instead of grub:
[http://www.linuxbsdos.com/2011/10/27/dual-boot-ubuntu-11-10-windows-7-on-a-pc-with-2-hard-drives/](http://www.linuxbsdos.com/2011/10/27/dual-boot-ubuntu-11-10-windows-7-on-a-pc-with-2-hard-drives/)

---

### Post by Mark Phelps on 2012-04-06
> **kompressorgpl said:**
> Hello! I have 2 HD on my pc. Can I install Win 7 on one and Ubuntu 10.04LTS on the other? 
Actually, that's what I do because I prefer to have the situation where each physical hard drive can boot by itself.

[QOUTE}And, when it cames to the boot, will be same as if they where on the same HD? Thank´s!!![/QUOTE]
Don't understand the question.  

Dual-boot requires you boot into one of the two OSs at PC boot time, not from inside the other OS.

So, in that case, it doesn't matter if the OSs are on different drives, or if they share the same drive.

---

### Post by Roger49 on 2012-04-10
Hi,
I've got 10.04 and Windows XP on separate drives of my desktop machine.
I boot into GRUB and can choose which OS to use.
If I were to do it again, I would disconnect the cable to the Windows drive, and update GRUB after installation, so that it recognises the other OS.
The 10.04 installer _really_ wanted to overwrite my Windows installation - the destination for installation kept on changing - I had to watch it like a hawk!
Good luck,
Roger.

---

### Post by oldfred on 2012-04-10
If you do not disconnect Windows drive, then you have to use manual install or Something else to have the choice on which MBR to install the grub2 boot loader to.

Some links with screenshots showing install to second drive and combo box for choosing drive to install boot loader.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by roelforg on 2012-04-10
I though the way to do that was:
Install win on hd2 (eg. slave drive)
Install ubuntu on hd1 (master) and just be carefull to select ONLY hd1 as install hd.
Grub will detect windows and add an entry.

---

