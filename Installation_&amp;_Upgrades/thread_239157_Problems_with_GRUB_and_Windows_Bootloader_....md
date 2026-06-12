---
title: "Problems with GRUB and Windows Bootloader ..."
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by Rez. on 2006-08-18
Hi ..
 My first post and what a whopping long one it's going to be :D As you may have guessed I'm having problems with my Ubuntu installation. The problem lies in the fact that I do not want to use Grub as my bootloader and instead would like to use the Windows (XP in this case) bootloader instead.

 **My Master HDD is partitioned as follows:**
[I]Partition 1:  Windows XP         (Primary)  NTFS
Partition 2:  Spare Partition    (Primary)  NTFS
Partition 3:  Ubuntu 6.06        (Primary)   Ext3 
Partition 4:  Spare Partition    (Logical)  NTFS
Partition 5:  OSShare Partition  (Logical)  Fat32[/I]

The Ubuntu installation went fine and at the end it asked me where I wanted to install 'Grub'. I directed it to install Grub in the linux root (hda,2) and rebooted. I was expecting to see the 'No OS Detected' message but instead I got the grub bootloader menu. I booted into XP and changed the XP Partition to 'Active' and rebooted. The Grub menu was gone and my machine loaded straight into Windows. 
 I then booted into my Sysreccd and used the following command to get a copy of the linux boot file :
```
dd if=/dev/hda3 of=/mnt/dump/ubuntu.bin bs=512 count=1
```

 I rebooted back into XP and edited the boot.ini file with this addition ```
C:\ubuntu.bin="Ubuntu 6.06"
```

 I rebooted and got a boot menu (The XP boot menu) with two options : Windows XP and Ubuntu. I selected Ubuntu and got a black screen with the word 'GRUB' at the top of the screen. And that is as far as it went - No Ubuntu. 

 i have searched around and according to a website I have one of two problems :
 - I used the dd command incorrectly
 Or
 - I have an old bios that can't read beyond 1024 Cylinders.

 Now I have done the dd command three times, I'm no Einstien but I know i typed the command correctly.  I have a pretty new system ( barely three months old) So the bios does support LBA as does my HDD (Western Digital). I was rummaging around the bios and I have one of two options for LBA, either disabled or AUTO. I have it set to AUTO. I did something in the bios and now when i boot i get a diagnostic screem before boot with all sorts of information. One of the things i've noticed is that my Master HDD's LBA mode is set to OFF while my slave is set to ON. I've googled on how to turn LBA on but haven't really found anything helpful. 

Does anyone know what could be going wrong? Any advice?

Thanks for reading such a long post ..

---

### Post by zxee on 2006-08-18
I've seen this method of using windows bootloader to boot linux (NTLDR)
Good going for getting as far as you did, and you may be a help for others who want to try this.
Now on to the issue: If you're getting the grub prompt, looks like this:> grub>
You should be actually able to type commands there.
Try > find /boot/grub/stage1
and > root
from the previous command if it returns something like (hd0,2)
then type > setup (hd0,2) the #'s might not be the same use whatever grub returns. and then reboot. Hope that helps.

---

