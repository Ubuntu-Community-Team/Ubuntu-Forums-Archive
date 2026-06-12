---
title: "Please Help - Ubuntu Alternate Install Failed"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by DyWaN on 2006-06-30
Hi people, I'm new to linux and have decided to use Ubuntu. However, I found difficulties in installing this to my laptop. It's an old Toshiba P3-1 Ghz, 512 MB RAM, 40 GB HD, a broken floppy, a broken CDROM , a working USB & a working LAN port.

It's going to be long as I try to explain my difficulties as detail as possible to get help from seniors here. and thank you very much if someone could help me out also sorry for my bad english as it's not my daily language.

Let's start

Based on the situation above, I decided to download a .iso of Ubuntu 6.0.6 alternate because I want to install Ubuntu from a local partition of FAT32 as the HD is structured as : 

1. Primary 20 GB - FAT32 - Windows XP & Windows 98 system file, so I got two options in my windows boot loader, one to directly go to Windows XP, and 2 for going to C:\ prompt

2. another 20 GB I left this unpartitioned (supposed to be used by ubuntu)

And below are the steps:

1. place the ubuntu-6.06-alternatei386.iso at c:\ubuntu

2. place vmlinuz & initrd.gz which i downloaded from ubuntu's site under hd-media at c:\boot

3. I download latest Grub, extract 2 files only (grldr & menu.lst) and place both of them at root of drive c:\

4. I edit the menu.lst like this :

[B]title Ubuntu 6.0.6 Harddisk Install
kernel   (hd0,0)/boot/vmlinuz root=/dev/ram0 devfs=mount,dall ramdisk_size=17000
initrd    (hd0,0)/boot/initrd.gz[/B]

5. I add this to the last line of c:\boot.ini:
**c:\grldr="Ubuntu 6.06 Harddisk Install"**

please note that the steps I got at point no.4 doesn't mean i know anythng about them, i got the reference from instlux at sourceforge. :)

6. Reboot, it goes to Window's boot selection and I choose Ubuntu...

7. The kernel loaded & the setup starts, enter my language, location & keyboard layout

8. It searches for ISO installer image or something like that founds it, retrieving modules, i configure my network, and the Partition disks page loaded.

9. I choose "Manually edit partition table", and it shows :

[B]IDE1 master (hda) - 40.0 GB FUJITSU MHT2040AH
   #1 primary     20.0 GB B K fat32          /media/hda1
       pri/log       20.0 GB      FREE SPACE[/B]

10. I choose the second one, & choose the "Automatically partition the free space" and finally came up with this :

[B]IDE1 master (hda) - 40.0 GB FUJITSU MHT2040AH
   #1 primary     20.0 GB      B K  fat32          /media/hda1
   #2 primary     19.2 GB      B f   ext3           /
   #5 logical       847.2 MB      f   swap          swap[/B]

11. I choose **"Finish partitioning and write changes to disk"**. it asked me to write changes to the disk and I choose ***"Yes"***.

12. Asked me to select my time zone : I choose ***"Jakarta"***

13. Asked me to input Full name, username account & password

14. It then showed **"Installing base system"**

15. After that showed **"Configuring apt"**

16. Continued to **"Select and install software"**

17. Everything works fine and finally showed "Cleaning up..."

Problems started here....

16. It then shows a dialog with **"Install the Grub boot loader on a hard disk"** with the message :
[B][I]The grub package failed to install into /target/. Installing GRUB as a boot loader is q reauired step...and so on.
[/I][/B]
Grub installation failed. continue anyway?

I choose **yes**

18. It then showed another dialog teling me that it detected a Microsoft Windows XP Professional and asked me whether to install GRUB loader to the MBR.

I choosed **No**

19. it showed me another options where to install the GRUB, so I choose to install it to (hd0,1) or /dev/hda2

20. It showed a dialog with the message:

[B][COLOR="Red"]Unable to install GRUB i /dev/hda2
Executing 'grub-install /dev/hda2 failed.

This is a fatal error.[/COLOR][/B]

21. I then choose **<Continue>**

22. It showed a dialog with the message :

[B]Installation step failed
And installation step failed. You can try to run the failing item again from menu or skip it and choose something else. The failing step is : Install the GRUB loader on a hardisk[/B]

23. I choose **<Continue>** and it brings me back to a menu with lot's of options.

Here's where I got stucked. I even don't got the balls to restart my laptop. and wait for a response from experts from this forum.

anwyay, I tried to install  GRUB to different partition also like /dev/hda1 and t floppy /dev/fd0 it just failed with the same message.

also tried to execute **"Install LILO boot loader on a hardisk"** still got the same error.

sorry for the long posts, and thank you very much for your efforts spending your time reading this. I hope someone could help me. 

thank you very much..

---

### Post by Adrian_b on 2006-06-30
[QUOTE=DyWaN]Hi people, I'm new to linux and have decided to use Ubuntu. However, I found difficulties in installing this to my laptop. It's an old Toshiba P3-1 Ghz, 512 MB RAM, 40 GB HD, a broken floppy, a broken CDROM , a working USB & a working LAN port.

It's going to be long as I try to explain my difficulties as detail as possible to get help from seniors here. and thank you very much if someone could help me out also sorry for my bad english as it's not my daily language.

Let's start

Based on the situation above, I decided to download a .iso of Ubuntu 6.0.6 alternate because I want to install Ubuntu from a local partition of FAT32 as the HD is structured as : 

1. Primary 20 GB - FAT32 - Windows XP & Windows 98 system file, so I got two options in my windows boot loader, one to directly go to Windows XP, and 2 for going to C:\ prompt

2. another 20 GB I left this unpartitioned (supposed to be used by ubuntu)

And below are the steps:

1. place the ubuntu-6.06-alternatei386.iso at c:\ubuntu

2. place vmlinuz & initrd.gz which i downloaded from ubuntu's site under hd-media at c:\boot

3. I download latest Grub, extract 2 files only (grldr & menu.lst) and place both of them at root of drive c:\

4. I edit the menu.lst like this :

[B]title Ubuntu 6.0.6 Harddisk Install
kernel   (hd0,0)/boot/vmlinuz root=/dev/ram0 devfs=mount,dall ramdisk_size=17000
initrd    (hd0,0)/boot/initrd.gz[/B]

5. I add this to the last line of c:\boot.ini:
**c:\grldr="Ubuntu 6.06 Harddisk Install"**

please note that the steps I got at point no.4 doesn't mean i know anythng about them, i got the reference from instlux at sourceforge. :)

6. Reboot, it goes to Window's boot selection and I choose Ubuntu...

7. The kernel loaded & the setup starts, enter my language, location & keyboard layout

8. It searches for ISO installer image or something like that founds it, retrieving modules, i configure my network, and the Partition disks page loaded.

9. I choose "Manually edit partition table", and it shows :

[B]IDE1 master (hda) - 40.0 GB FUJITSU MHT2040AH
   #1 primary     20.0 GB B K fat32          /media/hda1
       pri/log       20.0 GB      FREE SPACE[/B]

10. I choose the second one, & choose the "Automatically partition the free space" and finally came up with this :

[B]IDE1 master (hda) - 40.0 GB FUJITSU MHT2040AH
   #1 primary     20.0 GB      B K  fat32          /media/hda1
   #2 primary     19.2 GB      B f   ext3           /
   #5 logical       847.2 MB      f   swap          swap[/B]

11. I choose **"Finish partitioning and write changes to disk"**. it asked me to write changes to the disk and I choose ***"Yes"***.

12. Asked me to select my time zone : I choose ***"Jakarta"***

13. Asked me to input Full name, username account & password

14. It then showed **"Installing base system"**

15. After that showed **"Configuring apt"**

16. Continued to **"Select and install software"**

17. Everything works fine and finally showed "Cleaning up..."

Problems started here....

16. It then shows a dialog with **"Install the Grub boot loader on a hard disk"** with the message :
[B][I]The grub package failed to install into /target/. Installing GRUB as a boot loader is q reauired step...and so on.
[/I][/B]
Grub installation failed. continue anyway?

I choose **yes**

18. It then showed another dialog teling me that it detected a Microsoft Windows XP Professional and asked me whether to install GRUB loader to the MBR.

I choosed **No**

19. it showed me another options where to install the GRUB, so I choose to install it to (hd0,1) or /dev/hda2

20. It showed a dialog with the message:

[B][COLOR="Red"]Unable to install GRUB i /dev/hda2
Executing 'grub-install /dev/hda2 failed.

This is a fatal error.[/COLOR][/B]

21. I then choose **<Continue>**

22. It showed a dialog with the message :

[B]Installation step failed
And installation step failed. You can try to run the failing item again from menu or skip it and choose something else. The failing step is : Install the GRUB loader on a hardisk[/B]

23. I choose **<Continue>** and it brings me back to a menu with lot's of options.

Here's where I got stucked. I even don't got the balls to restart my laptop. and wait for a response from experts from this forum.

anwyay, I tried to install  GRUB to different partition also like /dev/hda1 and t floppy /dev/fd0 it just failed with the same message.

also tried to execute **"Install LILO boot loader on a hardisk"** still got the same error.

sorry for the long posts, and thank you very much for your efforts spending your time reading this. I hope someone could help me. 

thank you very much..[/QUOTE]

Why don't you install it to the MBR?(I believe you would be installing GRUB to hd0,0 then)
I always do it..

---

### Post by DyWaN on 2006-06-30
thanks for your reply Adrian,

wherever I install it, it just came up with the same error, it's just gettin me crazy....

---

