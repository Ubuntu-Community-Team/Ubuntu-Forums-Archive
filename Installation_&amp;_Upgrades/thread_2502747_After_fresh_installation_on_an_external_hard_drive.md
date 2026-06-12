---
title: "After fresh installation on an external hard drive, grub rescue appear while booting"
date: 2024-11-27
forum: Installation &amp; Upgrades
---

### Post by Deepjyoti_Goswami on 2024-11-27
Since my laptop hard disk has got corrupted recently, using USB-live I have installed Ubuntu 24.04 lts in an external hard drive. But after installation, I can not boot from it. The screen stops at error:unknown filesystem. Entering rescue mode... grub rescue. I have looked at many solutions but nothing worked due to my limited understanding. Finally I have created a boot-infor report ([https://paste.ubuntu.com/p/ZdMSHrvscz/](https://paste.ubuntu.com/p/ZdMSHrvscz/)). Please have a look at it. Any help is greatly appreciated.

---

### Post by oldfred on 2024-11-27
Is this also you?
[https://askubuntu.com/questions/1534073/grub-rescue-while-booting-from-an-external-device](https://askubuntu.com/questions/1534073/grub-rescue-while-booting-from-an-external-device)

I prefer to use gpt partitioning, but conversion usually totally erases a drive, changes UUID.
Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives since 2012 as old MBR(msdos) is very obsolete.
But Linux will install in UEFI mode to MBR, but probably should not. But issue is like yours where you have data, and installer must be careful not to convert a drive and delete your data.

This may allow conversion, but good backups still required.
Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
I started converting all new, or totally reformatted drives to gpt back in 2010. So now have no MBR drives.

For issues like yours forum is easier as AskUbuntu is supposed to be one simple question with one simple answer.
Note forum converting to Discourse, soon.

---

### Post by grahammechanical on 2024-11-27
There is something that I do not understand. This corrupted hard drive (sda) does it have Windows on it? Does it also have Ubuntu on it? I do not understand why when you installed Ubuntu on to the external drive (sdb) you allowed the install to put the Ubuntu (Grub) boot files into sda. The first partition (sda1). The drive is corrupted. 

Boot Repair wants to reinstall Grub to sda1. I do not think that will change any thing. My advice is to reinstall Ubuntu to the external drive and this time use the Erase disk and install Ubuntu option. That will put the Grub boot files on to sdb. Make sure that you are selecting the external drive. Then use the UEFI settings utility to boot from the external drive.

What you do about the corrupted drive is another matter.

Regards

---

### Post by yancek on 2024-11-27
Your boot repair output shows you have Grub boot code installed to the MBR of sdb, the drive on which you have Ubuntu installed (sdb4).  

> core.img is at this location and looksfor (,msdos2)/boot/grub.

The quote above is from the top of boot repair.  That's a problem as msdos2 is a vfat partition which apparently was intended as an EFI partition.  It should be pointing to sdb4 not sdb2.  You have the wrong files on that partition for an EFI boot.  The recommended repair should work to get the correct files on the EFI partition and you should probably follow their suggestion to disable Legacy boot.  You might try changing the drive to gpt from msdos but installing UEFI on msdos is possible.

---

### Post by Deepjyoti_Goswami on 2024-11-28
Yes. I was not sure where to post. Thanks again.

---

### Post by Deepjyoti_Goswami on 2024-11-28
Sorry, I don't know how to reply individually. I forgot to mention that initially it worked for a few days (about a month back). But after an update, suddenly grub rescue appeared. (I am not sure that's the reason.) Anyway, I have learnt two things. If I change boot mode from legacy to uefi, even the usb live does not work. Changing back to legacy, I have used gdisk to change MBR to gpt in the external drive (sdb). Then tried to reinstall Ubuntu in sdb. But the device for bootloader installation option is greyed, and I am stuck.

---

### Post by yancek on 2024-11-28
If you want to do an MBR/Legacy install on a GPT drive, you need to create an unformatted 1MB partition at the beginning of the disk for the Grub core.img file.  If the disk is now not partitioned, boot the Ubuntu install USB and open a terminal and type in:  sudo gparted and use that software to create the unformatted partition.  Go to the site at the link below and scroll down to the section " BIOS/GPT notes".
[h=3]https://help.ubuntu.com/community/Grub2/Installing[/h]Click on unallocated space and go to the Partition tab at the top of the gparted window and click on New.  Set the New size to 1MB and on the right you will see Filesystem.  Click the drop down arrow and select unformatted and click Add in the lower right.  Once that is done, you should be able to proceed with the install.

If you have UEFI options in the BIOS, I'm not sure why you would not be able to install in UEFI mode.

---

### Post by oldfred on 2024-11-28
With gpt you need either the bios_grub partition for BIOS boot, unformatted 1MB or an ESP - efi system partition for UEFI boot, FAT32 with boot,esp flags. Otherwise grub will not install or install correctly.

When first converting some drives from BIOS to UEFI, I would add both ESP and bios_grub. But only needed one or the other. And  you then can convert an install as only real difference is version of grub. You have grub-pc for BIOS and grub-efi-amd64 for UEFI boot.

---

### Post by Deepjyoti_Goswami on 2024-12-01
Thank you, guys. But I have learnt something else and hence couldn't implement the solution you are suggesting. I will come to that in a moment. 
Initially I was using both Ubuntu and window 10, and boot mode was legacy. Suddenly, one fine day, I was greeted with 'boot device not found. Please install an OS on your hard disk. Hard disk -(3F0). I was looking for solutions from then on.
Few days back, as suggested, I changed boot mode from legacy to uefi. There are two options. I went with uefi hybrid (with csm). But then I could not even boot from the live usb, forget about doing what you guys suggested.
With the flash drive inserted, I again tried 'boot options' and I noticed 'boot from efi file'. I saw two options (long ones). I clicked on one, it took me inside the boot folder, after a couple of clicks, and perhaps it didn't work and my laptop restarted. This time, I clicked the second one, and to my utter surprise, it booted to windows, and all this time, I thought it was corrupted. I was busy making it workable for my day-to-day life.

---

