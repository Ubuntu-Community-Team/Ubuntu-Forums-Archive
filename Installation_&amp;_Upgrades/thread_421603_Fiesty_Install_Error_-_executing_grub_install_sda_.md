---
title: "Fiesty Install Error - executing grub install sda failed"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by sylance on 2007-04-24
Hey gang... new to this and hoping to slowly migrate away from MS.  I have one SATA hard drive and 4 partitions: one for XP and the rest were for other applications.  My XP is a fresh install.  I went through the Ubuntu installation and formated one 30GB partition to ext3(?) and another to 2 GB swap.

At 94% install I get the error message "executing grub install sda failed."  It's a fatal error and aborts the installation.  When I reboot my system it doesn't have a boot loader and thus boots directly into Windows.  I've tried reinstalling afterwards and during the partition part it sees my partitions that I did on my previous install.

Windows is installed on NTFS if that matters.

Thanks for any help.  I greatly appreciate it and I look forward to moving off of MS.

---

### Post by pepsi_max2k on 2007-04-24
install grub on a floppy drive instead? change hd0 to fd0 then boot from floppy. at least you'll be able to boot ubuntu and figure out what might be wrong.

---

### Post by themaven on 2007-04-24
I had faced similar problem earlier today and in fact I could not even boot to Windows after that!

Not sure if it this is of much help, but:

I had a Ubuntu 5.10 alternate CD and I tried installing that and it worked! I am now downloading Fiesty Alternate CD to see if that works. Will let you know how it goes. If you figure out the problem with the Live CD, let me know :-)

---

### Post by sylance on 2007-04-24
I don't have a floppy drive in this computer so I'll have to find another solution.  I might go with the 5.10 version solution to see if that helps.  When I get home I'll post my partition information to see if there's anything I did there.  Thanks...

---

### Post by triwave on 2007-04-25
Not sure if it's a LiveCD problem. I tried installing Fiesty from the alternate CD because my laptop is an older model with 128MB RAM and I've generally had better luck that way. I got an error that was unable to write Grub and now the grub that was there is gone so nothing boots.  This machine used to run Dapper without a hitch :confused:

---

### Post by sylance on 2007-04-27
Okay, I don't know if this will help but here it goes.  I'm reinstalling Feisty again and I'm doing a manual partition during the install.  This is what it shows:

/dev/sda
  /dev/sda1   NTFS   /media/sda1
  /dev/sda5   ext3   /media/sda5
  /dev/sda8   swap  
  /dev/sda6   fat32   /media/sda6
  /dev/sda7   fat32   /media/sda7


It also says "You need to specify a partition for the root file system (mount point "/") with a minimum size of 2 GB, and a swap partition of at least 256 MB."

Is the root file system where the Linux OS goes or where the MBR goes?  Sorry for being noobish...

---

### Post by sylance on 2007-04-27
Okay... I may have found the problem.  I had my swap file formated to 3 GB, and after reading most of the installation instructions, it says it can't be over 2GB.  I changed it to 1 GB and it seems to install now.  Thanks for trying guys.... hope this might help someone else.

---

### Post by Davinci79 on 2007-04-27
Sylance,are you fix the problem?
I've the same problem.

---

### Post by Davinci79 on 2007-04-27
After i typed "sudo fdisk -l" i notice that the boot pointer(*) is near the windows partion.
Maybe grub failed because of that?Someone...

---

### Post by n00blar on 2007-04-27
Has anyone found a fix for this?

The Kubuntu CD seems to give me the same problems, and now I can't even boot to XP. And the problem is that the repair from XP is prompting me for an administrator password, which I have no idea what it is :(

I also ran "sudo fdisk -l" and in the Boot column - no device is set as a bootable device. Any way to fix this also?

Thanks.

---

### Post by Davinci79 on 2007-04-28
Does it matter at what partion i install grub if i have only one hard drive?

---

### Post by bulldog on 2007-04-28
> **Davinci79 said:**
> Does it matter at what partion i install grub if i have only one hard drive?

Install Grub to the MBR of the device (hd0) and it should be alright.
It will detect your windows and ask you if you want to add it to the menu.lst,answer yes, and you can boot windows and ubuntu from the Grub menu.lst

---

### Post by themaven on 2007-04-28
not sure if ur problem is solved, but i solved mine by using the alternate CD!

i tried a fresh install using the 7.04 alternate cd and everything worked fine!

give it a try if u r still having problems. also, a good idea to have one partition as root ("/") with the file system as ext3

---

### Post by Davinci79 on 2007-04-28
I have already burn 2 cd.The cd test is pessed.I still trying to fix it.

---

### Post by Davinci79 on 2007-04-29
If some one still have this problem...
I fixed it at the next way:
While u arrive to partion definition options do next definition:
5Gb for "/"
5Gb for "/var"
1Gb for swap
xxGb for "/home"
next thing fixed the problem => 100Mb for "/boot"
Conitue with install.

Atlist I have done those steps and i have Ubuntu on my laptop.
Good Lack!

---

