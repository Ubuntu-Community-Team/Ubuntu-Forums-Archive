---
title: "lost access to windows after reinstalling grub2"
date: 2014-06-22
forum: Installation &amp; Upgrades
---

### Post by Sander_Houttekier on 2014-06-22
Hi,

recently i installed windows 8.1 next to my linux installation (the harddisk was ready for it, i had the partition ready beforehand)
then as usual windows took over the entire system, so I had to reinstall grub2 to regain access to my linux device (i had done this before, but it was already a year ago :))
so I looked up my linux partition sudo fdisk -l  (mine was on /dev/sda5)
i issued the sudo grub-install --boot-directory=/mnt/boot /dev/sda

and after rebooting the system automatically boots into my linux install. so it seems grub2 took over the entire system now, but without giving me the option to boot into windows8

any ideas?

---

### Post by oldfred on 2014-06-22
Windows 8 default is hibernated or fast boot. When Windows is hibernated or needs chkdsk the Linux NTFS driver will not mount it and if not mounted the os-prober will not find it.
You have to have fast boot off.

If BIOS, reinstall Windows boot loader and turn off fast boot.

 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked 

If that is not issue, post link to Boot-Info report.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

