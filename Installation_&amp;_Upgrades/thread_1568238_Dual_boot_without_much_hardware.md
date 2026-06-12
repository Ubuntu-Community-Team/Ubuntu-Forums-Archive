---
title: "Dual boot without much hardware"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by Austin25 on 2010-09-04
I have an old desktop with Xubuntu on it, and I'd like to set up a dual boot of Xubuntu and Ubuntu Server Edition. I don't have any live CDs, nor can I burn any. I don't have any working floppy drives, and the computer is too old to support usb booting or network booting, any ideas?

---

### Post by bobpress on 2010-09-04
Looks like your choices are limited.  You need a CD to run which will take awhile, but you can get it through a request to [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/).  You probably need both the desktop and server CDs since you need to use gparted on a live CD to create some free space on your hard drive for the Server edition (unless you have a second HD to install).

---

### Post by Austin25 on 2010-09-04
> **bobpress said:**
> Looks like your choices are limited.  You need a CD to run which will take awhile, but you can get it through a request to [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/).  You probably need both the desktop and server CDs since you need to use gparted on a live CD to create some free space on your hard drive for the Server edition (unless you have a second HD to install).
Isn't there some way to do it with GRUB or something?

---

### Post by witeshark17 on 2010-09-05
Good luck yo!

---

### Post by bobpress on 2010-09-05
> **Austin25 said:**
> Isn't there some way to do it with GRUB or something?

No, you need to be able to change the partitions on the hard drive to install a second system and you have to not be using any partition that will be changed.  For Windows users in your situation, there is WUBI to install Ubuntu within the Windows partition, but I don't know of an equivalent for a linux distribution except Virtual Box and similar virtual software.  You need enough memory to run two linux systems at the same time, however, probably a Gig or better.  Don't know what hardware you actually have.

---

### Post by Austin25 on 2010-09-05
> **bobpress said:**
> No, you need to be able to change the partitions on the hard drive to install a second system and you have to not be using any partition that will be changed.  For Windows users in your situation, there is WUBI to install Ubuntu within the Windows partition, but I don't know of an equivalent for a linux distribution except Virtual Box and similar virtual software.  You need enough memory to run two linux systems at the same time, however, probably a Gig or better.  Don't know what hardware you actually have.
I have Virtual box on my laptop. (It has much better spces) I have a Virtual computer set up with the same size hard drive and the same partition table I would like. Is there any way to copy it to the hard drive? What about some form of chainloading to a USB drive?

---

### Post by Doulos1 on 2010-09-05
One daughter got an i5 and the other go an AMD quad. Both are awesome, especially compared to my P4 server.

---

### Post by bobpress on 2010-09-05
> **Austin25 said:**
> I have Virtual box on my laptop. (It has much better spces) I have a Virtual computer set up with the same size hard drive and the same partition table I would like. Is there any way to copy it to the hard drive? What about some form of chainloading to a USB drive?

The problem is that however you use a USB, except for booting from one  (which you can't do - I assume due to older PC and bios), your partition  on the hard drive which you need to partition will be mounted and active.

Since you also have a laptop, can you download and burn a CD there?  I  have two older PCs which I changed from XP to Ubuntu by download Ubuntu  iso to my laptop, burning a CD and booting from the CDs on the older  PCs.

---

### Post by Austin25 on 2010-09-05
> **bobpress said:**
> The problem is that however you use a USB, except for booting from one  (which you can't do - I assume due to older PC and bios), your partition  on the hard drive which you need to partition will be mounted and active.

Since you also have a laptop, can you download and burn a CD there?  I  have two older PCs which I changed from XP to Ubuntu by download Ubuntu  iso to my laptop, burning a CD and booting from the CDs on the older  PCs.
No, I can't burn a CD, see [here.]("http://ubuntuforums.org/showthread.php?t=1549953&highlight=CD+burning")

---

### Post by bobpress on 2010-09-05
> **Austin25 said:**
> No, I can't burn a CD, see [here.]("http://ubuntuforums.org/showthread.php?t=1549953&highlight=CD+burning")

Was K3B among the programs you tried?  I've had trouble on a laptop with Brasero and GnomeBaker burning iso images.

Sorry, didn't see your K3B reference.  Do you have any form of Windows accessible to you?  I resorted to burning a CD under MS for use a couple of times.

I've seen several error reports and this page about problems burning CDs. [http://jeff.ecchi.ca/blog/2010/05/31/burnt-by-disc-burning/](http://jeff.ecchi.ca/blog/2010/05/31/burnt-by-disc-burning/)

---

### Post by Austin25 on 2010-09-05
Are there any tools to boot a Hard Drive Image?

---

### Post by Austin25 on 2010-09-06
Ok, I think I can use unetbootin with slax, then boot it in "copy to ram mode" so it doesn't need to mount the hard drive. Will this command work, or do I need a different format of Hard disk image?
```
dd if=hdimage.vdi of=/dev/sda1
```

---

### Post by GoggleEyedSalmon on 2010-09-08
Did you manage to do this? I am trying to do a similar thing and I can't seem to get any help.

---

### Post by Austin25 on 2010-09-20
I ended up using a broken external hard drive and borking it somewhat. I converted a .vdi to .raw and put it on said hard drive, then copied it with ```
dd /media/sdb1/image.raw /dev/sda
```

---

### Post by Austin25 on 2010-11-20
Alright, I ended up using another computer to burn an ubuntu cd, installed ssh on the live environment, then used:
```
ssh ubuntu@ubuntu.local 'dd if=/dev/sda' | dd of=image.raw
```
Then I used virtualization to install everything on the image, then I used:
```
dd if=image.raw | ssh ubuntu@ubuntu.local 'dd of=/dev/sda'
```

---

