---
title: "Want to install to external hard drive without losing data, possible?"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by fenderguy on 2007-04-19
Ok first off my computer does allow me set USB hard drive first in my boot order.

I have a 250gb external hard drive which has 180gb worth of information i REALLY don't want to lose.  I plan on backing up the most important parts to another external which is smaller.  I want to be able to boot linux from this external hard drive but keep windows as well.  Can i nudge the content of this drive over with partition magic to leave unallocated space in the beginning of the drive for linux, without losing my data on the drive?  Then when i go to install ubuntu (the new feisty version) with the cd which i've already burnt (and am currently testing in live mode) can i simply have it create the partition in this new space i've opened up and install there, and then make sure grub is also put on the external.  I'm definetely a newb with linux and everything like that so I don't understand the languages and whatnot if i run across errors i'll have no idea what to do so im wondering if this is highly likely to be possible and if the partition editor and ubuntu installation will take care of the difficult parts for me for the most part in this setup.

Thanks for the help

---

### Post by proalan on 2007-04-20
yea it works, i've put ubuntu on a spare usb harddrive no problems, can't do it for xp though

---

### Post by upchucky on 2007-04-20
HMMM... I'm in the same boat ....maybe......
I have a USB bootable laptop
I have xp on a hard drive
I have edgy on a second hard drive

Either drive will boot just fine if installed in my laptop
I wanted to have xp as the bootable USB drive.....apparently the microsoft self-imposed gods of computer hardware wont allow that.

So now i want to use the edgy drive as the bootable USB drive....
the problem is..... I need to edit grub on the edgy drive so it knows that it is supposed to boot as a USB drive.

I downloaded supergrub as a cd ISO, but it wont let me edit the grub on the edgy drive

I am assuming i must edit the edgy grub to see the drive as usb bootable
When I have the xp drive as the usb drive it mounts it as media/usb and the files are readable and writeable in edgy.

I am hoping someone who has done this before can post their grub file for the usb and tell me if i can indeed edit the existing grub file without having to reinstall edgy..... I have edgy already tweaked for my computer and am not looking forward to having to start all over.

---

### Post by proalan on 2007-04-21
I'll tell you how I got my usb installation working

1. changed bios settings to allow 'allow usb legacy' most bios will have an option similar to this. If not a bios update may solve this issue. This will allow the bios to recognise your usb harddrive as a bootable device along side floppy, cd-rom, and your other harddrives.

2. plug in your usb harddrive and boot up the live cd as you would for normal installation.

3. On the desktop go to System->Preferences->Removable drives and media, and uncheck all the boxes in the storage tab. 

4. hit the install icon on the desktop, when you get to the bit asking about your partitioning ensure that ubuntu is installed on your usb harddrive and make a note of what your usb harddrive is mounted as. In my case it was mounted as '/dev/sda1'.

5. when it asks where you wish to install the grub loader change the path to where your usb device was mounted to (again in my case (/dev/sda1) instead of the default hd(0,0) supplied. 

6. after install your usb installation of ubuntu, your installation should be bootable. 

7. you may have to manually select your usb as the boot device by pressing either F2 or F8 before grub loads.

---

### Post by upchucky on 2007-04-21
Quote "6. after install your usb installation of ubuntu, your installation should be bootable". 

Could you please clairify this? Will this overwrite my existing ubuntu install? if so .....I am actually looking to edit the grub file to boot this as a usb drive. I do not want to disturb the existing Ubuntu install as it is already tweaked for my laptop and i am trying to avoid spending days to re-tweak if it breaks my existing install.

Or perhaps I should have installed Ubuntu on the drive when it was connected as the usb drive in the first place? instead of installing ubuntu when the drive was in the laptop.

---

### Post by proalan on 2007-04-21
> Will this overwrite my existing ubuntu install?

yes unfortunately, 

but from what i understand now you already got ubuntu on your usb harddrive then.

further questions.

1. Is the grub loader also on your usb harddrive? 

2. Can you boot into your ubuntu installation using the super grub cd? and if so what is your usb harddrive mounted as?

---

### Post by upchucky on 2007-04-21
Thank you much, i figured it out, only had to edit the grub/menu.lst on the usb drive to sdb1 Ubuntu boost from usb now and all data is intact, but my nvidia settings took a hit, may need to reinstall nvidia.

---

