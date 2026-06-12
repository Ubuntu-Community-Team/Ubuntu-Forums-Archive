---
title: "Dual boot hell"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by edbyford on 2007-09-15
Hello all

I am trying to dual boot my Ubuntu installation with XP. I used the System Rescue CD ([http://www.sysresccd.org](http://www.sysresccd.org)) to create an 8GB fat32 partition on my 500GB hard drive, right between the swap partition and the main Ubuntu one. Then I booted to make sure it was alright, then I used my XP cd to boot into the XP install.

 I selected the correct partition, which then prompted XP to tell me that another partition was marked as active on my hard drive, and it had to change it before install. I wanted to cancel, but had no option apart from to press ok (but I thought this would just mean that it would ask me again later, before install!) but then after that cancelled setup, deciding to investigate more fully before I actually installed. But now I can't boot Ubuntu!

It just said "Invalid boot disk - insert boot disk and try again" and so I used the System Rescue CD (and specifically GParted) to check the flags on the partition. XP had made itself the 'boot' partition. So I changed it over to the ubuntu one, and still no joy, except now it says "no operating system found"!

I know I didn't format anything, but I decided to stop playing then in case I did any undoable damage! Please help, my life is on that machine!

---

### Post by Pumalite on 2007-09-15
Re-install Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by mikewhatever on 2007-09-15
Not sure why you went creating that FAT32 partition but if it was a logical one then probably (happened to me once) the root partition number has changed and now as you try to boot Grub tells you it can not find it because it is looking in the wrong place but you can probably fix it by running the live CD then mounting the root partition and then editing grub menu.lst and do not hesitate to ask if you need any particulars and lastly sorry for the long sentence I've never tried it before but it is kind of fun.

---

### Post by iheartubuntu on 2007-09-15
> **edbyford said:**
> So I changed it over to the ubuntu one, and still no joy, except now it says "no operating system found"!

Im still a newbie, but check your BIOS settings to make sure your HD is bootable and not selected as CDROM and CDROM like mine somehow magically changed to. I had to change mine to AUTO and CDROM so it would find the HD to boot into.

---

