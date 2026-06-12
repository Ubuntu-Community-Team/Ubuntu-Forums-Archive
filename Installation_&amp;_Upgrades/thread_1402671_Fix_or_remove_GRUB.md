---
title: "Fix or remove GRUB"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by pushkar_k on 2010-02-09
A friend of mine had fedora and XP dual boot on his system. He wanted to try Ubuntu , so he went to disk management in windows and formatted logical drives related to fedora.
         Now after starting computer he gets 
grub >
       prompt even if he inserts bootable kubuntu cd. He also tried after changing preferences giving first preferance to cd. 
        He wants to install kubuntu now . Is there a way to either completely remove or replace grub ?

---

### Post by darkod on 2010-02-09
Make sure the cd was created correctly from an image, not just the image file copied on a cd. If the cd is first device in boot order the computer should boot from it. If you get the cd going and the installation, don't worry about the current grub error, new grub will be installed.
Also, if he reformatted the partitions from windows they would be ntfs now, and kubuntu will not install on ntfs. They need to be deleted, the space left as unallocated, and then the kubuntu installer will do the rest by using the Use Largest Available Free space option.
When you manage to boot with the kubuntu cd select Try Kubuntu first, open the partition manager and delete the fedora partitions which are now ntfs. Then start the install process.

---

### Post by ramaswamyps on 2010-02-09
he can remove the mbr [current grub]
using his windows cd.
at first screen press R
then log on to windows number
then type fixmbr
that will clear the grub.
then he can start installing ubuntu.
the cd may be bad check iso md5sum and burn image again at slowest possible speed.
that may work fine.

---

### Post by pushkar_k on 2010-02-09
> **darkod said:**
> Make sure the cd was created correctly from an image, not just the image file copied on a cd. If the cd is first device in boot order the computer should boot from it. If you get the cd going and the installation, don't worry about the current grub error, new grub will be installed.
Also, if he reformatted the partitions from windows they would be ntfs now, and kubuntu will not install on ntfs. They need to be deleted, the space left as unallocated, and then the kubuntu installer will do the rest by using the Use Largest Available Free space option.
When you manage to boot with the kubuntu cd select Try Kubuntu first, open the partition manager and delete the fedora partitions which are now ntfs. Then start the install process.

CD is working fine because I have installed my own kubuntu from that cd , still I will try some other CD. He has not exactly formatted drives but deleted logical drives , so that space is available as free space. Also , is there a way to check whether bootable cd is fine or not ?
       Thanks for your help.

---

### Post by pushkar_k on 2010-02-09
> **ramaswamyps said:**
> he can remove the mbr [current grub]
using his windows cd.
at first screen press R
then log on to windows number
then type fixmbr
that will clear the grub.
then he can start installing ubuntu.
the cd may be bad check iso md5sum and burn image again at slowest possible speed.
that may work fine.
           
                      Thanks for your help . What is iso md5sum ? is it some linux command ? I think kubuntu bootable cd is fine since I have used it before. Regarding method using Windows CD , he doesn't have Windows cd.

---

### Post by ramaswamyps on 2010-02-09
you must be able to boot qwith kubuntu /ubuntu cd.
check media will check the cd for errors.
but i thought he did partition with windows cd.
he can make bootable floppy from windows
use that to remove the grub
or he can download bartpe iso and make bootable cd. from

[http://www.snapfiles.com/get/bartpe.html](http://www.snapfiles.com/get/bartpe.html)
it can work like windows cd.

---

### Post by darkod on 2010-02-09
If you have used the cd and it doesn't have visible signs of damage on it, then it's up to the computer to boot from it.
Make sure cd is selected as first boot device. If the error on the screen is the same with or without the cd in the drive, it seems like the computer is not trying to boot from it at all.
Sometimes people really think they set the settings correctly, but it will turn out they didn't.

If the partitions were deleted, not formatted, even better. No need to delete them as separate step.

---

