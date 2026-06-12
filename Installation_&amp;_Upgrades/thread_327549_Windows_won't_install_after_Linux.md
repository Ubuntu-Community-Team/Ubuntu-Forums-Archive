---
title: "Windows won't install after Linux"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by altonbr on 2006-12-29
This is the error I receive when trying to install Windows (the screen, of course, is blue with white text):

> **Windows XP Professional Setup**
======================
Setup did not find any hard disk drives install in your computer.

Make sure any hard disk drives are powered on and properly conncected to your computer, and that any disk-related hardware configuration is correct. This may involve running a manufacturer-supplied diognostic or setup program.

Setup cannot continue. To quit setup, press F3.



-----------------------------------------------------------------------------------
F3=Quit

I receive the same error using the Windows 2000 Professional disk as well.

I have installed Windows XP previously on this machine, but not AFTER multiple distros of Linux have been installed.

I have an empty 40GB partition at the front of the hard drive, formatted as FAT32 as well, so I was hoping Windows could read it, but apparently can not :S.


Any ideas???

---

### Post by meng on 2006-12-29
Perhaps discard the empty partition altogether, leaving unallocated space. I think Windows insists on installing to an NTFS partition, and cannot install on FAT32.

---

### Post by budgie9 on 2006-12-29
It's not the fact you are using a FAT32 it will install to FAT32 as mine is. I suspect it may be the fact you have other distros on there, and it does not like it, But more likely that your first partition is not set ACTIVE.
You will need to use fdisk  and set that partition active as stated, then it should install.
Hope this is helpful.

---

### Post by altonbr on 2007-01-01
How would I set it to "active"? The only flags I see are: boot, hidden, lba, lvm, palo, prep & raid.

I've attached the screenshot of GParted because I forget the command to show your hard drive configuration in the terminal.

The line highlighted in [BLUE]Blue[/BLUE] is the partition I would like Windows XP to install too.

---

### Post by bulldog on 2007-01-01
I think your problem is that windows likes to be installed on the first partition,which can't be because of your ext3 /boot partition.

You should use the Gparted live cd and try to set the FAT32 partition **before** the /boot partition and flag it a s boot able.

You have to modify your menu.lst and fstab as well because of this.

---

### Post by altonbr on 2007-09-16
Yeah, Windows STILL can not install on my computer even after6 months of growing much more intelligent in regards to Linux and computers in general.

My only hope is to backup all of my data, wipe the whole drive and install Windows from scratch.

I've had absolutely no luck with XP. Vista (beta 2) was surprisingly able to read the unallocated space, but not XP.

I even couldn't install XP on a brand new OEM hard drive for a client once. No matter what I did, XP couldn't read it. Glad I'm not dependant on XP anymore, YIKES!

---

### Post by Pumalite on 2007-09-16
But now you are stuck in Vista! YIKES!!

---

### Post by altonbr on 2007-09-16
Oh no no no, I just wiped Vista with my Gparted LiveCD and then reimplemented the GRUB menu via: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351).

I was hoping that if Vista could read and install, then XP would be able to wipe over it since they use the same NTFS partition type... but no, I was wrong.

Thank 'god' for Ubuntu.

---

### Post by Pumalite on 2007-09-16
Good for you! You are smarter than I first thought.

---

