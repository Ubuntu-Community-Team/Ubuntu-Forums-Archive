---
title: "Windows unbootable after failed attempt at Ubuntu install"
date: 2014-08-10
forum: Installation &amp; Upgrades
---

### Post by oisin_nz on 2014-08-10
Hi, 

I was trying to create a bootable full Ubuntu installation on a 16Gb USB stick. So first I created an Ubuntu live installation on a 4Gb USB stick which boots fine. When it boots it presents two options:
(i) Try Ubuntu
(ii) Install Ubuntu
So I chose option (ii), a full install, but I chose the 16Gb USB stick (sdc) as the install target rather than the laptop hard-disk (sda), I was expecting this to make changes only to the USB stick and leave the laptop unchanged. The installation appeared to go fine and required a reboot to complete. Upon re-booting I was left with just a blank screen with a cursor. 
So, I can now try booting in 3 different configurations:

(i) With the Live USB stick (4Gb) inserted and choosing boot from USB at boot time:
- This boots fine 

(ii) With no USB sticks inserted (expecting to boot the original Windows installation):
- This fails to boot but just presents the following message at the top of a black screen:
[I]error: no such device: a77XXXXXX-ab23-43fc-b5xxxxxxx
grub rescue> _[/I]

(iii) With the 16Gb USB stick inserted (expecting to boot my newly created full Ubuntu install):
- This fails to boot and just presents the following at the top of a black screen: 
_

So, my main question is: is it possible to recover my Windows installation ? It is Windows XP on an old Dell Inspiron. Current attempts bring me to the 
*grub rescue> _* prompt as described in (ii) above. Does anyone know what options are available from the grub rescue prompt? 

Additionally, did I do something wrong in trying to create the full Ubuntu install on a bootable USB stick ? Should this have worked ? Was I wrong to expect the attempted installation to change only the USB stick. From the current behaviour I imagine the attempted full install actually made changes to the boot sector on the laptop hard-disk, should this have happened ? 

Thanks, 

Oisin

---

### Post by grahammechanical on 2014-08-10
The installer defaults to installing the boot manager (Grub) into the first hard disk (sda). When you put the 16GB USB stick in and boot, do you get a boot menu? Does it give you an option to boot both Windows and Ubuntu?

With both USB sticks unplugged you need to restore the XP boot loader to the hard disk. I cannot tell you how to do that. Then try installing Ubuntu again to the 16GB stick and this time make sure that Grub is not going to be installed into sda.  I guess that the 4GB stick will be sdb with the 16GB stick being sdc.

Regards.

---

### Post by oisin_nz on 2014-08-10
> **grahammechanical said:**
> The installer defaults to installing the boot manager (Grub) into the first hard disk (sda). When you put the 16GB USB stick in and boot, do you get a boot menu? Does it give you an option to boot both Windows and Ubuntu?

With both USB sticks unplugged you need to restore the XP boot loader to the hard disk. I cannot tell you how to do that. Then try installing Ubuntu again to the 16GB stick and this time make sure that Grub is not going to be installed into sda.  I guess that the 4GB stick will be sdb with the 16GB stick being sdc.

Regards.

When I boot with the 16Gb stick inserted and choose 'boot from USB' I get nothing just a blank screen with a blinking cursor a the top. No boot menu.
I can understand why windows wont boot if the attempt to create the Ubuntu install messed up the MBR on sda but I dont understand why the 16Gb wont boot to Ubuntu. When I boot successfully to the 4Gb Ubuntu Live USB I can inspect the 16Gb stick and it appears to have all the standard dirs for a linux installation so I dont know why it wont boot.

---

### Post by ubfan1 on 2014-08-10
On the 16G stick, you might be experiencing bug #384633.  Check the grub.cfg file on the stick.  The problem is when the installer created the grub.cfg, the config of the system was probably hard disk as hd0/sda, usb installer as hd1/sdb, and usb target as hd2/sdc.  After the usb installer is removed, the target moves up to hd1/sdb, and grub cannot find its menues.  Just edit the grub.cfg file and change any hd2 to hd1, and any sdc? to sdb? and try to boot.  The UUIDs in use should be correct and do not need any changes.  Upon the first successful boot, run sudo update-grub to fix the grub.cfg file.
  Cannot help much on the Windows MBR repair of the hard disk, but one fix barely ever mentioned to to install grub to a FAT (tools or recovery) partition.  Make a boot directory there and use the --boot-directory=/mnt/sda?/boot  (whatever your partition instead of ?). in install-grub.

---

### Post by oisin_nz on 2014-08-11
> **ubfan1 said:**
> On the 16G stick, you might be experiencing bug #384633.  Check the grub.cfg file on the stick.  The problem is when the installer created the grub.cfg, the config of the system was probably hard disk as hd0/sda, usb installer as hd1/sdb, and usb target as hd2/sdc.  After the usb installer is removed, the target moves up to hd1/sdb, and grub cannot find its menues.  Just edit the grub.cfg file and change any hd2 to hd1, and any sdc? to sdb? and try to boot.  The UUIDs in use should be correct and do not need any changes.  Upon the first successful boot, run sudo update-grub to fix the grub.cfg file.
  Cannot help much on the Windows MBR repair of the hard disk, but one fix barely ever mentioned to to install grub to a FAT (tools or recovery) partition.  Make a boot directory there and use the --boot-directory=/mnt/sda?/boot  (whatever your partition instead of ?). in install-grub.

Hi ubfan1, 

Thanks for the reply, I've had a look at grub.cfg on the 16Gb stick and it does indeed contain many instances of hd2. I'm a bit confused though, you say 'update the grub.cfg and then boot and then issue the update-grub command to fix the grub.cfg file'. 
Has my manual editing not already 'fixed' the grub.cfg file ? Or does the update-grub command do something more sophisticated to remove the effective hard-coding of where grub expects to find its menus ? Ideally I want this 16Gb stick to be bootable on any random machine (which could have any number of USB sticks or external hard-drives already connected) so it wont be much use if it needs the stick to be assigned a hard-coded hd<X> value to work.

Thanks, 

Oisin

---

### Post by oldfred on 2014-08-11
I have had same issue with installing from one flash drive to another. Not sure why as the search line by UUID is supposed to override an incorrect set root = that is not the correct drive/partition.

Boot-drive is always hd0 as set by BIOS, so if directly booting from flash drive it will be hd0. But when booting from MBR on hard drive that is hd0 and flash drive is hd1 if only the one flash is plugged in.

You should be able to manually boot.
       See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1), (hd1,1) ? If so, run the next command. If you see (hd1,5), use that instead of (hd0,1) in the next command and sdb5.
configfile (hd1,1)/boot/grub/grub.cfg

If that does not work as it just tries to read grub.cfg then directly boot, this assumes second drive hd1 and first partition sdb1:

   set prefix=(hd1,1)/boot/grub
set root=(hd1,1)
linux (hd1,1)/vmlinuz root=/dev/sdb1 ro
initrd (hd1,1)/initrd.img
boot

You can use Boot-Repair, just your live installer, or your Windows CD to  restore a Windows boot loader to sda. And you want to install grub to  the flash drive's MBR.       

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by Jonathan Precise on 2014-08-11
What happens if you boot from the HDD but with the 16 GB USB inserted? It should solve it.

Since GRUB is installed to the HDD, but it looks for ubuntu in the 16GB USB stick, the solution should be to boot from HDD with 16 GB USB inserted.

---

### Post by ubfan1 on 2014-08-11
Running the sudo update-grub rewrites the grub.cfg using more UUIDs than the original installer used when it created the file.  If you just edited the grub.cfg, (with an editor, not just using the grub edit commands, which are not permanent), your changes to the devices would still leave devices where UUIDs would be better.  Unfortunately, there are still places where the hd? devices are used, and that can lead to portability issues.  It might be possible to edit every instance of hd? to use a UUID, but you will lose those changes every time grub.cfg gets rewritten for a new kernel.
  If you're moving the USB stick to different machines, I'd suggest you learn the grub command line and tab completion.  This way you can track down the assignment of whatever hd the stick gets.   Up until 2 years ago, I'd have said hd0 on my compaq presario is the hard disk, regardless of boot device (and I was booting off USB a lot).  These days, hd0 is not assigned as consistently and even on the same machine (Asus) different times can result in the same stick being hd1 or hd0.  To make matters even worse, the device assignment of sda, sdb, etc. need not even match the hd0, hd1 enumeration.  If that happens, even the update-grub will be writing the wrong hd devices.

---

### Post by oisin_nz on 2014-08-12
> **oisin_nz said:**
> Hi ubfan1, 

Thanks for the reply, I've had a look at grub.cfg on the 16Gb stick and it does indeed contain many instances of hd2. I'm a bit confused though, you say 'update the grub.cfg and then boot and then issue the update-grub command to fix the grub.cfg file'. 
Has my manual editing not already 'fixed' the grub.cfg file ? Or does the update-grub command do something more sophisticated to remove the effective hard-coding of where grub expects to find its menus ? Ideally I want this 16Gb stick to be bootable on any random machine (which could have any number of USB sticks or external hard-drives already connected) so it wont be much use if it needs the stick to be assigned a hard-coded hd<X> value to work.

Thanks, 

Oisin

I tried replacing all instances of hd2 with hd1 in the grub.cfg but the 16Gb stick would still not boot. So I started from scratch to create a full install on the 16Gb stick via the procedure described here:
[COLOR=#000000][FONT=Arial]http://ubuntuforums.org/showthread.php?t=2060493

[/FONT][/COLOR]

---

### Post by oisin_nz on 2014-08-12
> **oldfred said:**
> I have had same issue with installing from one flash drive to another. Not sure why as the search line by UUID is supposed to override an incorrect set root = that is not the correct drive/partition.

Boot-drive is always hd0 as set by BIOS, so if directly booting from flash drive it will be hd0. But when booting from MBR on hard drive that is hd0 and flash drive is hd1 if only the one flash is plugged in.

You should be able to manually boot.
       See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1), (hd1,1) ? If so, run the next command. If you see (hd1,5), use that instead of (hd0,1) in the next command and sdb5.
configfile (hd1,1)/boot/grub/grub.cfg

If that does not work as it just tries to read grub.cfg then directly boot, this assumes second drive hd1 and first partition sdb1:

   set prefix=(hd1,1)/boot/grub
set root=(hd1,1)
linux (hd1,1)/vmlinuz root=/dev/sdb1 ro
initrd (hd1,1)/initrd.img
boot

You can use Boot-Repair, just your live installer, or your Windows CD to  restore a Windows boot loader to sda. And you want to install grub to  the flash drive's MBR.       

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

I was able to restore access to the original XP install by using the Windows recovery disk as per
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

