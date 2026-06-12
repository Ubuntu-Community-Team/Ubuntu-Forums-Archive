---
title: "Can I install a full version of Ubuntu on a flash drive?"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by ben15 on 2013-10-26
I have a live cd version on a flash drive. My question is, can I install a full, living and breathing (and mostly personalizable), version of Ubuntu on a flash drive? I tried yesterday, it went through the process, but at the end it said it had problems installing the bootloader. I don't figure I would need a bootloader on a flashdrive version of it, since it would use the bootloader of the computer it was plugged into. What I want is to be able to customize a flashdrive version, with programs like: arp-scan, nmap, testdisk, etc. If anyone could help me, I would appreciate it.

Ben

---

### Post by oldfred on 2013-10-26
What error did you get?
 
I have full install in 8GB on my 16GB flash drive with the other 8GB as data. I have it more as another "drive" in case I need it with my laptop, but do not use it a lot. Since only 8GB I would have to do regular housecleaning if using it more.

It should just like any install to another drive. Always use Something else or manual install so during the partitioning, you can specify which drive's MBR to install grub2's boot loader into.
Or do you have a very new system with UEFI?

Screen shot was regular install to my Larger sdc drive with many partitions, but at bottom it shows combo box with choice of drive to install grub2 boot loader into. It shows sda in screenshot but you would want sdb or whatever flash drive is.

---

### Post by ben15 on 2013-10-26
I don't actually remember what the full error message said, but it was that is couldn't install the bootloader. I'll try it again and let you know if I get the message again. Your above post is reassuring that it is possible though. Thank you.

---

### Post by Dennis N on 2013-10-26
Yes, easily done. There is an student exercise with steps in doing this I posted here:

[http://ubuntuforums.org/showthread.php?t=2169661](http://ubuntuforums.org/showthread.php?t=2169661)

See post #2 on this thread.

The drawback is that performance on the flash drive can be slow, depending on the drive's read/write performance.

---

### Post by oldfred on 2013-10-26
I did make a few settings to reduce writes. 
Install seemed slow as it is a lot of writes. 

I also have noticed my new USB3 flash drive is about 10% faster even on my old USB2 ports.

Settings I changed:
 With SSD or Flash (trim does not work on flash) drives, Use ext4 without journal where sdXY and X is drive and Y is partition:
sudo tune2fs -O ^has_journal /dev/sdXY
sudo tune2fs -o discard /dev/sdXY
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.

---

### Post by ben15 on 2013-10-26
I just tried it again and got the same message:

"Unable to install GRUB in dev/sdc

Executing 'grub-install/dev/sdc' failed.
This is a fatal error."

It gives me an option, after I click OK, to continue with one of three paths: Choose another device for the bootloader, Continue without installing the bootloader, or cancel the installation.

---

### Post by oldfred on 2013-10-26
post this:

 sudo parted /dev/sdc unit s print

---

### Post by ben15 on 2013-10-26
Now have it plugged into a different computer, getting ready to test it, so it is now sdb.

"sudo parted /dev/sdb unit s print" gives me:

Model:  USB DISK Pro (scsi)
Disk /dev/sdb: 15116736s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start           End            Size           Type      File system      Flags
 1          2048s          11020287s  11018240s  primary  ext4
 2          11020288s  15116287s   4096000s    primary  linux-swap(v1)

---

### Post by oldfred on 2013-10-26
Looks ok.

Since only 8GB, I might not have so much swap. Only 6GB for / (root) now is not very large. You may have to houseclean regularly. On flash drive I do not have any swap, but restrict myself to not loading more than one or maybe two smaller apps at once.

---

### Post by ben15 on 2013-10-26
That's where I'm confused. I can get rid of (or shrink) the swap partition, but would that allow me to install a bootloader? I tried it and it wouldn't boot, it just sat with a blinking cursor. 

I'm not really looking to run too many apps, mostly the file explorer and Gparted in the GUI, and a few in the CLI (basically, making a recovery/salvage drive). 

Also, if I install Ubuntu will it be universal or computer specific (with the hardware driver install, etc.)?

---

### Post by oldfred on 2013-10-26
If you do not install any proprietary drivers it should boot on any computer. But many need boot parameters like nomodeset. 
With my install I added nomodeset as a default and remove it if not needed as I boot. You can edit grub menu entry with e when at menu.

Changing swap should not make any difference to installing grub. And with 6GB it should install and run.

Is port USB3? Some have had issues with that. Try a USB2 port.

Since just a standard install, you should be able to run Boot-Repair. But it just runs commands to reinstall grub2.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

    

On the flash drives that I do not do a full install, I install grub manually and add my own grub.cfg so I can boot ISO directly with loopmount.
This may mess up the grub you ned to boot install though.

These are all the same, but different labels on a  flash drive like grub2, MC4GB, and PreciseInstaller. New versions of Ubuntu now mount with user name in /media.
 sudo grub-install --root-directory=/media/grub2 /dev/sdb

 sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb

 sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde

 This will create a grub.cfg or you can just copy your own grub.cfg into /boot/grub
sudo grub-mkconfig -o /media/fred/PreciseInstaller/boot/grub/grub.cfg

I do not know if I have been lucky but never had issues with either my older Kingston nor recent MicroCenter house brand flash drives.
      
 Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

---

### Post by ubfan1 on 2013-10-26
Is your PC a UEFI machine?  They do have some special problems installing to removable media.

---

### Post by ben15 on 2013-10-27
Alright, I ran the Boot-Repair program. I'm getting ready to test it, but in the meantime, here is my Boot-Info output: [http://paste.ubuntu.com/6313556/](http://paste.ubuntu.com/6313556/)

---

### Post by oldfred on 2013-10-27
It looks normal.


If you have trouble booting change this to hd0. As boot drive is always hd0 from BIOS. When you installed it was not hd0, but search by UUID should override the initial default.

 set root='(hd1,msdos1)'

See line 964:
It also looks like you had incorrect partitioning, and Boot-Repair did not see first partition starting at 2048 and saw ISO file info. It then zeroed out with dd the first 2048 sectors. That space is also used by grub for core.img, so maybe core.img was not being installed correctly?

---

### Post by ben15 on 2013-10-27
The Boot-Repair worked. I am currently on my flash drive OS. There was a message as it was booting up, but it continued on (the message did mention UUID, so that may have been the issue). Booting/GRUB isn't something I've really messed with, so this has been kind of a learning experience. I appreciate your help.

Ben

---

### Post by ben15 on 2013-10-27
Looking through the Pastebin file, the only two files I could see that had 'hd1' were: /etc/grub.d/05_debian_theme and /etc/grub.d/00_header. The rest had 'hd0' marked. Were you talking about one of those two?

---

### Post by oldfred on 2013-10-27
Glad you got it working. Now with grub on a flash drive you can directly boot many ISOs you copy to flash drive using grub2's loopmount. I used to do that will all my flash drives with just grub installed. But now with several hard drives I just use hard drive. Install from ISO on hard drive to SSD is really fast and you do not have to install to flash drive to create an installer. :)

No that was in the grub menu for your external. 
If you boot into flash drive and run this it will update itself. As then you are booted from hd0.

sudo update-grub

Whether a flash drive that is configured like another hard drive or another hard drive.
 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

