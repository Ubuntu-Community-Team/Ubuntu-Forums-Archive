---
title: "Installing WITHOUT Grub"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by ramo on 2007-02-04
I really just want to install Ubuntu WITHOUT having to install or use GRUB. I just want to boot Ubuntu directly off of my second hard drive. **Don't ask me why, I have legitimate reasons do this involving an abnormal installation of XP from a factory that creates hidden partitions and conflicts with the GRUB bootloader. So please, GRUB is 100% out of the question and don't tell me to ditch XP **I do not have the "Alternative" CD of Ubuntu, I have "Ubuntu Linux 10.6 Desktop" or something like that. Any ideas? I Google-searched this thing to hell.

edit: I'm sorry, another older thread I made was bumped by a reply relating to this issue, just ignore this.

---

### Post by louieb on 2007-02-04
You can install Linux but you can't use it without some boot loader. GRUB, LILO, GAG whatever. Do you have a floppy drive? If so you can install a boot loader on a floppy disk and use it when you need to boot Ubuntu.

---

### Post by ramo on 2007-02-04
Uhm, a bootable CD would be better, I have two hard drives and two optical drives all on IDE, so I have no IDE connector available to install my old floppy drive - I found some guides in google, but if I can find a read-to-burn ISO file, that'd be even better - plus, how would I tell the Ubuntu installer to NOT install GRUB?

---

### Post by kebes on 2007-02-04
The ubuntu install CD can also be used as a boot CD. The last option on the menu is "boot from hard drive" I believe. (If it's not there, then it's on the Alternate install CD.)

So you could do a normal install, but when you get to the grub stage, you could cancel it. It will give an error, but just continue without that step. To do a custom install like this, I believe it's easier to use the Alternate CD, because you reach a point where you can cancel the default install, and instead select manually whether you want to install grub or lilo ... in your case you could install neither. Just let it copy files to the hard drive, and then don't install grub.

Like I said you will then use the install CD as a bootloader.

---

### Post by louieb on 2007-02-04
[Super Grub]("http://supergrub.forjamari.linex.org/") CD.
> plus, how would I tell the Ubuntu installer to NOT install GRUB?

Just fake it out and install it in the boot sector of your Linux partition. Just before the install look for (hd0) in the text and click on it and change it 2 (hd1,0) . that will put  grub out of the way on the  first partition of your second drive.

---

### Post by ramo on 2007-02-04
Haha! Super Crub CD is AWESOME. I haven't fixed the problem YET - however, this Super Grub CD allows me to restore the original windows boot launcher after installing Grub on HD0 on the mbr. Thanks louie ):P 

So this time around, I did install Grub on the mdr in HD0 and in the Ubuntu setup, I just chose to erase the entire secondary disk to install Ubuntu on but now I'm getting 'error 18' any ideas?

---

### Post by louieb on 2007-02-04
Just wondering and watching the super bowl, how old is the computer? Error 18 is a BIOS error that you get when the boot loader tries to load a program that is stored in outside the first 1024 cylinders of the hard disk. Newer versions of BIOS don't have this limit.
Very weird error for a new install on an empty hard drive.
Did you use the manual partitioning option?  
Is the first partition a large data partition?
Are you installing Edgy? Have heard that that installer is some what flaky. 
Boot to live CD and Open Applications>Accessories>Terminal. Cut and paste the out put of ```
sudo fdisk -l 
``` that a lowercase l as in little. This command list the partition tables.
See if Super grub can fix it or Just reinstall.
also this page [http://wiki.linuxquestions.org/wiki/GRUB](http://wiki.linuxquestions.org/wiki/GRUB) might be of interest to you.

---

