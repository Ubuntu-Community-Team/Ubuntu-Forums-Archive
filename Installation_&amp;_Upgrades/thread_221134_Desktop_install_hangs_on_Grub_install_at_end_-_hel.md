---
title: "Desktop install hangs on Grub install at end - help!"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by ahallubuntu on 2006-07-22
Dell E1505 laptop with 100GB Sata hard drive.  I installed from the regular Dapper Desktop/Live boot CD.  Live boots fine.  Then I did the install from there.  It got all the way to the end to the Grub install then it hung for about 20 minutes until I killed it.   Linux seems to be installed but I know of no way to to boot it.

Configuration:

Drive originally had three visible partitions on it:  a Dell maintenance partition, a restore partition, and a Windows partition.  I deleted all but the maintenance partition and re-partitioned (before install) into this:

Primary 1 : Dell Maintenance Part
Primary 2 : Windows XP/NTFS (re-installed)
Extended
  Logical 1: Windows/FAT32

During install, I made two more Logical Partitions in the free space:  one for swap, one for / .  Installed fine up until Grub.

Any ideas?  The Windows boot sector is still there - I can still boot Windows.  Any way to grab/make a boot sector from my Ubuntu install?  I think I know how to use the Windows boot loader to load Ubuntu from there...

---

### Post by taurus on 2006-07-22
Where did you install GRUB, MBR???

---

### Post by ahallubuntu on 2006-07-22
Grub did not prompt me for anything - maybe it hung up before it got a chance to ask me?

---

### Post by taurus on 2006-07-22
So you didn't see a GRUB screen, asking you where you would like to install it, during the installing process!!!

---

### Post by ahallubuntu on 2006-07-22
That's right - all I saw was the status dialog box for the Ubuntu install, which told what stage the install was in.  It stopped when running grub-install.

I have re-booted the live CD and am now trying re-run grub-install by hand.  This time it actually wrote something to the boot/grub directory so I'll try it now and see if it worked...

---

### Post by ahallubuntu on 2006-07-22
OK, I fixed it.  I re-booted the live CD, mounted the installed / partition, then re-ran grub-install on it:

(my main Linux partition is /dev/sda7)

sudo mount /dev/sda7 /mnt
sudo grub-install --no-floppy --root-directory /mnt /dev/sda

That worked fine, except that it created no menu.lst file under /mnt/boot/grub, so I had to create one.  My Windows XP installation is in /dev/sda2.  Here's the menu.lst file I created (copying  another installation's template) under /mnt/boot/grub (normally this is in /boot/grub).  I found the actual version of my kernel (2.6.16-23-386) in /mnt/boot:

#################################
default         0
timeout         30
title           Ubuntu, kernel 2.6.15-23-386
#my SATA drive is /dev/sda , Windows is /dev/sda2, Ubuntu is /dev/sda7 – Grub starts counting at #ZERO, unlike the operating systems!
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sda7 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sda7 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Windows XP
root            (hd0,1)
makeactive
chainloader +1
savedefault

title           Ubuntu, memtest86+
root            (hd0,6)
kernel          /boot/memtest86+.bin
boot

##################

Now, off to figure out how to set it to native video resolution (mine is 1280x800, not 1024x768; others have figured this out) and how to update the package repository (my laptop wasn't on the internet during install, so now many packages I expected to find are missing.) and installing the SMP kernel to take advantage of my Core Duo CPU.  Should be fun!

---

### Post by taurus on 2006-07-22
For X,

```

sudo dpkg-reconfigure xserver-xorg

```

For updating,

```

sudo apt-get update
sudo apt-get upgrade

```

For SMP kernel,

```

sudo apt-get install linux-686

```

---

### Post by ahallubuntu on 2006-07-22
Screen Resolution:

I found someone who used the "915resolution" hack (which works fairly well and easily) and just went with that - should have tried your suggestion first, sorry!

Thanks for your other suggestions...

---

### Post by taurus on 2006-07-22
> **ahallubuntu said:**
> Screen Resolution:

I found someone who used the "915resolution" hack (which works fairly well and easily) and just went with that - should have tried your suggestion first, sorry!
Hey, as long as it works, who cares how you do it, right!  ;)

---

