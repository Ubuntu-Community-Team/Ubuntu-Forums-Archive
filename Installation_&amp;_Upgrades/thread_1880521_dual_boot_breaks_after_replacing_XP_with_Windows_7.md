---
title: "dual boot breaks after replacing XP with Windows 7"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by alexmineh on 2011-11-13
I used to have windows xp on my first partition and ubuntu on my second. dual boot used to work fine with that configuration. a boot menu used to appear to select windows xp or ubuntu.

But, today I decided to replace xp with windows 7. So I inserted win7 DVD and reboot the computer with it. Formatted my first partition and installed windows 7.
Now, only the windows 7 boots, and no multiboot menu. the multiboot menu is gone.
I can still see the second partition in Windows 7( but not the files, only the space assigned to it), but I can not boot the unbuntu.
Please help.

---

### Post by mjzanga on 2011-11-13
Windows overwrites the bootloader that was installed when you installed ubuntu (so your ubuntu install is perfectly fine, no worries there).  If you still have the ubuntu live CD you can reinstall grub, though I forget exactly how to do that...

---

### Post by oldfred on 2011-11-13
These have the commands to use.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by alexmineh on 2011-11-13
> **mjzanga said:**
> Windows overwrites the bootloader that was installed when you installed ubuntu (so your ubuntu install is perfectly fine, no worries there).  If you still have the ubuntu live CD you can reinstall grub, though I forget exactly how to do that...

Thank you for your reply.  Is Live CD the same as installation CD that I have to dowenload from here?: 
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by darkod on 2011-11-14
Live CD is the standard Desktop CD. It's called like that because if you select Try Ubuntu in the main menu it will load it from the cd not touching the hdd. Then you can open terminal and run the commands oldfred posted. That will reinstall grub to the MBR.

---

