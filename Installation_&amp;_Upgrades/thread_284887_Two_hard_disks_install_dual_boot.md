---
title: "Two hard disks install dual boot"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by Ziggurat on 2006-10-26
Hi, i am going to install ubuntu 6.10 in a few hours. I have now another hard disk that i polan to add to my pc. Is grub capable of boot from a disk in wich is not installed?

I have a 60G and a 40G disk, and want to install ubuntu on the 60G and Windows on the 40G. Where should i install grub for this to work?

Is this possible?

---

### Post by taurus on 2006-10-26
Yes, GRUB can boot from any harddrive you want.  Just install it on MBR and you are all set.

---

### Post by Ziggurat on 2006-10-26
Thanks. Any of the MBR's?

---

### Post by taurus on 2006-10-26
MBR stands for Master Boot Record...

---

### Post by Ziggurat on 2006-10-26
Yes. But the MBR is in the first sector of the HD so if i have two discs i have two MBR's. ;)

---

### Post by gn2 on 2006-10-26
I recommend you read this before installing: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by taurus on 2006-10-26
> **Ziggurat said:**
> Yes. But the MBR is in the first sector of the HD so if i have two discs i have two MBR's. ;)
You would install GRUB on the first sector of your master drive, /dev/hda!!!

---

### Post by Pri0n on 2006-10-26
> **taurus said:**
> You would install GRUB on the first sector of your master drive, /dev/hda!!!

Note that doing so can "hijack" your bootup routine.  For example, I had Fedora Core on /dev/hda, and I installed a second hard drive (/dev/hdb) for Ubuntu.

After installing Ubuntu on the 2nd hard drive (/dev/hdb), it installed GRUB on the MBR on my first hard drive (/dev/hda) without prompting me.  After bootup, the only choices that I had in GRUB were for Ubuntu.  The choices for Fedora Core were gone.  

In reality, the grub.conf file for Fedora Core was still there.  It was just being bypassed by GRUB.  GRUB on the MBR on /dev/hda was looking at /boot/grub/menu.lst on /dev/hdb to know which OS it could boot up, instead of looking at /boot/grub/grub.conf on /dev/hda (the one already in place for Fedora Core).  So what I did was modify the menu.lst file on /dev/hdb to add the required entries for Fedora Core.

I'd strongly suggest making a hardcopy of your grub.conf file on /dev/hda in order to be able to enter the required settings for your original OS if it gets overwritten.

(actually, I've just re-read your question and noticed that you have Windows on your hard drive, not another Linux distro that uses GRUB.  So GRUB on your first hard drive won't be getting overwritten since its not there.  I'm not sure how Windows will handle this)

For the Linux users out there who may be in the same situation, I wanted to add that Ubuntu automatically overwriting my MBR with GRUB was a bit surprising.  Before installing Ubuntu, I had installed CentOS on the 2nd hard drive.  During the install, it asked me whether it should install GRUB on the MBR.  I said No.  After finishing the install (reboot), my only choices in GRUB for bootup was Fedora Core (which makes sense because I told CentOS not to overwrite the MBR).  After booting up in Fedora Core, I edited the grub.conf file to add the entries required so that I could have CentOS as a bootup option.  I found out what entries I would need by mounting the 2nd hard drive and checking out the /boot partition for the kernel file for CentOS (you know the vmlinuz-x kernel file and the initrd-x-.img image)

---

