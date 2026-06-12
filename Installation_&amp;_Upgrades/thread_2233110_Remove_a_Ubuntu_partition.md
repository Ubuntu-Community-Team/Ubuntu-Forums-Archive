---
title: "Remove a Ubuntu partition"
date: 2014-07-06
forum: Installation &amp; Upgrades
---

### Post by jj.wauters on 2014-07-06
I have a working system with a partition for Windows 8.1, Ubuntu 12.04 and Ubuntu 14.04 loaded by Grub 2.02 beta 2-9. 
I want to keep Windows 8.1, Ubuntu 14.04 and delete 12.04 as there are no important data in it.
Does freeing up the 12.04 partition and running the command "update-grub" are the only things to do ?

---

### Post by yancek on 2014-07-06
> Does freeing up the 12.04 partition and running the command "update-grub" are the only things to do ? 		

Probably not.  I don't know what you mean by 'freeing up'.  The first thing you would need to determine is, how are you booting?  Are you using the bootloader (Grub) from the Ubuntu 14.04?  If so then you would need to determine which partition Ubuntu 14.04 is on as well as which partition Ubuntu 12.04 is on.  If these two partitions are contiguous, then you could format 12.04 from 14.04 and then resize the 14.04 partition to include 12.04.  If they  are not contiguous, you could format the 12.04 partition and then use it as a data partition.  This is pretty general but, you haven't posted specific information.  You could post the output of gparted showing which partition contains which operating system and someone should be able to give you more specific suggestions.

---

### Post by ibjsb4 on 2014-07-06
I do not use this method, but ..

[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

---

### Post by mastablasta on 2014-07-07
boot into live session (live cd/USB). that way paretition are not mounted. delete the 12.04 partitions, extend the 14.04 partitions, update grub.

edit - if oyu do not want to extend and just use the 12.04 parittions as they are then just delete the stuff on them and update grub.

---

### Post by Bucky Ball on 2014-07-07
> **mastablasta said:**
> boot into live session (live cd/USB). that way paretition are not mounted. delete the 12.04 partitions, extend the 14.04 partitions, update grub.

edit - if oyu do not want to extend and just use the 12.04 parittions as they are then just delete the stuff on them and update grub.

^^^
This ... may or not work. I'm presuming you installed 12.04 LTS first, in which case that is probably running the grub. Just to make sure, boot into 14.04 LTS and:

```
sudo grub-install /dev/sda
sudo update-grub
```

Reboot and make sure that is all working and 14.04 now owns grub.

You can then safely follow mastablasta's advice. Once 12.04 is gone, boot to 14.04 and run 'sudo update-grub' again. Good luck.

PS: Find more info here:

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

If all else fails when you delete 12.04, then Boot Repair is your friend:

[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

---

### Post by jj.wauters on 2014-07-10
Indeed 12.04LTS was first installed. Later I added 13.1 which was upgraded to 14.04LTS.
But I forgot the way I made my partitions. 
In fact I have 3 partitions for each Ubuntu version : one for the OS, one for data and one for swap.(see gparted picture)
So 12.O4LTS on sda9, sda10 and sda11 may disappear. But how can I safely add the vacant place to sda13?

ps : grub is linked to 14.04LTS

---

### Post by Bucky Ball on 2014-07-10
Short answer is you can't as you have / on sda12 in the way.

Just a tip for future reference: There is no need to create multiple /home and /swap partition for every install. First install is, say, /, /home, /swap. Second install, choose 'Something Else' at the partitioning section and ONLY install the OS (create only the / partition). Mark the existing /home and /swap to 'use' but NOT to format (you should on have a tick in the format column next to the / partition you are installing the OS to). The system will then assume you want to use the existing mountpoints /home and /swap as the /home and /swap for the new install 'automagically'.

Considering this, you can immediately remove sda11, boot into the install that is using it and change the UUID for the /swap entry in their to the UUID of sda14 (the /swap you are using in the screen shot). Reboot and you will find the other install is now also using the /swap on sda14.

One other thing: Why are your /swap partitions so large? They only need to be 2Gb or so unless you have a stack of RAM and hibernate with a ton of stuff open. If you do, then /swap should be as big as installed RAM.

PS: You said you want to give that free space you create by deleting 12.04 to 13.10. Did you mean 14.04? 13.10 will be out of support very soon and not worth continuing with (we don't give support for end-of-life release here anymore). ;)

---

### Post by jj.wauters on 2014-07-10
Thanks for the info about multiple installations and RAM use.
- I have 12 GB Ram, so previously I took about half of the available RAM memory for swap.
- I did not say I wanted to reserve the vacant room for 13.10, but asked how to integrate the vacant room into sda13.
In other words how to proceed for using the freed space (sda9, sda10, sda11) for my Ubuntu 14.04LTS?

---

### Post by Bucky Ball on 2014-07-10
As I say, sda12 is between sda13 and the free space you are going to create so you can't expand sda13 into it. 

Whack 14.04 on the existing sda9 (where 12.04 is now I presume) and use the method I gave earlier; use the existing /home and /swap (currently sda13 and 14) by choosing 'Something Else' and 'Use' but NOT 'format'. Good luck. 

PS: sda12 is in a rotten place. Your only option is to clone it and stick it somewhere else or kill it and reinstall. 

I would personally leave 12.04 LTS where it is as a fallback (it is supported until 2017 while 13.10 is all but dead in the water and support will soon not be available for it here), kill 13.10 and install 14.04 LTS on a partition right next to 12.04. 

Get rid of 13.10 by killing sda11 and 12;
Shrink sda10 to the right by 20-30Gb;
Install 14.04 into the freespace you leave there;
Make sure to link 14.04 with the existing /home that the already installed OS is using and mark the other /home as 'Do Not Use'.
(If you don't do this the installer will get very confused!)

Then you are free to plop all your data into one /home partition (the one both installed OSs are using) and then kill the other. Ideally, you would then end up with, from the current sda9:

sda9: 12.04
sda10: 14.04
sda11: /home
sda12: /swap (2Gb fine and end of the drive 'traditional')

Just a thought. ;)

---

### Post by jj.wauters on 2014-07-11
There is **NO** version **13.10**!!! 
**13.10** was on sda12, sda13 and sda14 but is now **overwritten** by upgrading to 14.04LTS.
So, at this moment :
-sda9, sda10, sda11 are used by 12.04LTS for OS, data, swap
-sda12, sda13, sda14 are used by 14.04LTS for OS, data, swap

Can I proceed as follows :
-clone sda12(14.04LTS OS) and overwrite sda9(12.04LTS OS)
*dd if=/dev/sda12 of=/dev/sda9 conv=noerror,sync bs=1024*
-clone sda13(14.04LTS data) and overwrite sda10(12.04LTS data)
*dd if=/dev/sda13 of=/dev/sda10 conv=noerror,sync bs=1024*
-remove sda11 partition (12.04LTS swap)
-remove sda12 partition (14.04LTS OS)
-remove sda13 partition (14.04LTS data)
-keep sda9 (now 14.04LTS OS)
-expand sda10 partition to double space (now 14.04LTS data)
-keep sda14 swap partition now named sda11
-update grub

---

### Post by Bucky Ball on 2014-07-11
Sounds fine. Can't confirm whether the codes in the commands are right though. Always used Clonezilla myself. Good luck. ;)

---

### Post by yancek on 2014-07-11
The problem I see with your suggested method is going to be booting which may not be that difficult to resolve.  If you followed the instructions above to install the Grub from 14.04 to the master boot record it will be pointing to the boot files/kernel on sda12.  Since you are going to be moving it to sda9??  I'm not really sure this will be a problem as I have never done it, just a little paranoia?  You could chroot from an Ubuntu installation medium and change this.  

The first thing I would do is back up any personal data to some other medium in case things go wrong.  I would clone sda12 to sda9 and reboot first before deleting any of the 14.04 partitions and formatting.

---

### Post by Bucky Ball on 2014-07-11
Just run Boot Repair from a LiveDVD/USB if you have issues booting after you're done with the re-partitioning/installing.

---

### Post by oldfred on 2014-07-11
If you clone a partition and then install back to a different partition you create duplicate UUIDs and that is not allowed. And with gpt partitioning you have duplicate GUIDs which is even more of an issue. 
Cloning is more for restoring an image not necessarily best for moving it.

I prefer clean reinstall over cloning.

But in your case just make one larger data partition where old install was and configure that for some data you may want to store there. I use SSD with just / & only the part of /home that is the hidden configuration files and link all data folders like Documents, Music etc to a data partition on another drive. I do that as I multi-boot and want same data but not same configuration in /home.

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by jj.wauters on 2014-07-18
As suggested, I made a new 14.04LTS install.
I started with backing up and then I deleted the sda9, sda10, sda11(old 12.04LTS) and sda12(old 14.04LTS) partitions and 
created a new sda9(/) and sda10(/home) partition for the new 14.04LTS installation.
Grub is now showing Ubuntu 14.04LTS and Windows but can't boot Windows anymore.
Running Boot-Repair does not solve the Grub problem and comes with next url : [http://paste.ubuntu.com/7814248/](http://paste.ubuntu.com/7814248/)
Any suggestion to solve?

---

### Post by Bucky Ball on 2014-07-18
If you have the Win recovery or install disk, run that and hit 'R' for repair when you get to that screen. Once at a blinking cursor, type:

chkdsk /f

Let it do its thing or schedule a check on reboot, reboot and see if that boots directly to Windows or the scheduled chkdsk. If it does, that is good. Now boot from the Ubuntu LiveDVD/USB and do the Boot Repair thing again. Reboot. Hopefully now you have a grub menu or you are booting to Ubuntu. If you are booting to Ubuntu with no menu at boot, reboot and hit the shift key after the BIOS screen. That should bring one up. Good luck. 

You are getting there. ;)

PS: If the above doesn't fix, I suggest you post a new thread to improve your chances of help as this is essentially a new problem and is getting off the original topic and support request. Feel free to post a link to the new one here.

---

### Post by oldfred on 2014-07-18
You show these two files.

 /EFI/Microsoft/Boot/bkpbootmgfw.efi 
 /EFI/Microsoft/Boot/bootmgfw.efi 

That is Boot-Repairs fix for booting Windows on HP, Sony & other computers that will not boot anything but efi files with Windows in description. UEFI description for booting bootmgfw.efi says Windows. But Boot-Repair renamed shim or grub  to be bootmgfw.efi and then added a boot stanza (Which looks like it is missing?)  to boot the actual Windows file bkpbootmgfw.efi. But UEFI and grub2's os-prober find bootmgfw.efi and all those entries just boot grub again.

Often better not to rename bootmgfw.efi but rename bootx64.efi or add entry to BCD.
I would undo the rename using Boot-Repair.
      
 **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu  with bkpbootmgr.efi entry
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair of bootmfgw.efi will need to be redone after a Windows update as it will restore Windows files.

Many find this works better:
Copy grubx64 or shimx64 into /efi/boot folder.

 Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.


 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)

 HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

