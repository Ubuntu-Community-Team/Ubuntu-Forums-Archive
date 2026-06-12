---
title: "No grub on restart, goes straight into WindowsVista"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by taseedorf on 2008-01-13
I had completely un installed Vista, thinking I was going completely with Ubuntu.  Unfortunately, I realized later I had to reinstall because there were some things I needed.  Anyways, I reinstalled Vista on my  third partition of my only hard drive, and "uncommented" the part in the grub menu.lst so it would boot windows and made a minor change.  However, when I re boot, it goes straight into windows XP.  I fixed this by making the Windows partition NON active.  But than when it isn't active it won't boot, however, i have "make active" in my menu.lst file.  My question is I guess is how should my grub look? It currently looks like this.  I deleted the chainloader to see if it would work, but haven't rebooted yet.


## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b638028f-a0cf-4d00-a102-e8b3244c79a6 ro splash
initrd		/boot/initrd.img-2.6.22-14-generic
## quiet


title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b638028f-a0cf-4d00-a102-e8b3244c79a6 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows Vista
root	(hd0,4)
makeactive

---

### Post by Craigus on 2008-01-13
If you installed windows after installing linux, windows will have overwritten the MBR and grub won't run. You will have to reinstall grub.

Have a look at the supergrub disk:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by logos34 on 2008-01-13
> **taseedorf said:**
>  I reinstalled Vista on my  third partition of my only hard drive...I deleted the chainloader to see if it would work....

Put the 'chainloader +1' back--you need that.

If you reinstalled on third partition, then 'root (hd0,**2**)'  [grub starts counting from 0]

---

### Post by AnonCat on 2008-01-13
Configure Vista's bootloader to load linux for you.  Get a free program to configure it at:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Scroll down to the bottom of the webpage and press that big blue button to download it.

---

### Post by taseedorf on 2008-01-13
I have found out the problem comes because when I start Windows Vista, it changes to active and then upon reboot, it's still active and it boots straight into Vista.  Anyway, where I can make it only temporarily active? And automatically go back to non active status on reboot?   
I have to keep setting my ubuntu partition to active with a live cd, so i can boot grub.

---

### Post by Partyboi2 on 2008-01-14
what happened when you used super grub?
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by taseedorf on 2008-01-14
I never used to grub super disk..... Isn't it just a recovery disk?  What I did was boot my live cd, and go into a terminal and do grub, sudo root (hd0,0) than setup (hd0,0)...... isn't that basically the same as the super grub disk?  If not, whats the difference?

---

### Post by zvacet on 2008-01-14
> If you reinstalled on third partition, then 'root (hd0,2)' [grub starts counting from 0]

Did you try that way?

---

### Post by logos34 on 2008-01-14
Super Grub Disk is a recovery tool that can fix lots of things and allow you to boot windows or linux.  You need to try it.

But you might want to post your fdisk and your **entire** menu.lst 

**sudo fdisk -l**

I don't get the 'active' business with windows...The windows partition should have the boot flag, and it should not be affecting your ability to boot linux (the latter doesn't care about the flag).  In fact, changing the boot flag/active designation doesn't always affect windows' ability to boot: I just unflagged my XP partition and it doesn't seem to do anything, it still boots fine.  Go figure.

---

### Post by adrian15 on 2008-01-16
> **taseedorf said:**
> I never used to grub super disk..... Isn't it just a recovery disk?  What I did was boot my live cd, and go into a terminal and do grub, sudo root (hd0,0) than setup (hd0,0)...... isn't that basically the same as the super grub disk?  If not, whats the difference?

The difference is that SGD would have run: root (hd0,0) setup (hd0). If you only setup (hd0,0) the MBR code is not overwritten. As you say Vista activates its partition boot flag so your windows MBR boot code is nothing but a problem.

However if you use Vista I recommend to use EasyBCD to chainload the Linux partition. Sometimes the setup (hd0) is not effective on Vista, sometimes it is.

adrian15

---

### Post by taseedorf on 2008-01-17
Alright guys, for some reason it's fixed.

I boot in my open suse partition, and than the loader there boots vista fine?  I'm not sure why,  I will have to examine what is written in that code.

---

