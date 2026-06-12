---
title: "Dual Boot Xubuntu and OpenElec with XBMC - bootloader querie"
date: 2014-06-06
forum: Installation &amp; Upgrades
---

### Post by parker-hugh on 2014-06-06
I have an old laptop hp 530 with intel centrino duo cpu which has windows xp on it

I want to install Xubuntu and also OpenElec with xbmc.

so I have installed Xubuntu 14.04 

this is the partitions I used...

/dev/sda5    / (root)    8001MB        Ext4    minimum 5.7GB
/dev/sda6    / home        2002MB        Ext4    2002
/dev/sda7    swap        1001MB        Swap    1001

I updated Xubuntu which works fine, then I booted to Gparted cd

created two more partitions for xbmc using following instructions....
[http://wiki.openelec.tv/index.php/Manual_Installation_-_multi_boot](http://wiki.openelec.tv/index.php/Manual_Installation_-_multi_boot)

label        
OE_SYSTEM    /dev/sda3    ext4    1024mb    # FLAGGED AS BOOT
OE_DATA        /dev/sda4    ext4    5002mb

The only option I had was to create these as primary partitions, the logical partition choice was greyed out and I could only chose primary. I thought logical would be better so not sure if this is ok or not.  Did I do this correct?

I am now at point of Adding OpenELEC to the GRUB bootloader

These are the instructions from
[http://wiki.openelec.tv/index.php/Manual_Installation_-_multi_boot](http://wiki.openelec.tv/index.php/Manual_Installation_-_multi_boot)

Adding the OpenELEC menu item to GRUB is done by editing the following file:

```
sudo gedit /etc/grub.d/40_custom
```


```
 #!/bin/sh
 exec tail -n +3 $0
 # This file provides an easy way to add custom menu entries.  Simply type the
 # menu entries you want to add after this comment.  Be careful not to change
 # the 'exec tail' line above.
 #
 menuentry "OpenELEC" {
    search --set=root --label OE_SYSTEM --hint hd0,msdos3
    linux /KERNEL boot=LABEL=OE_SYSTEM disk=LABEL=OE_DATA quiet
 }
 menuentry "OpenELEC debugging" {
    search --set=root --label OE_SYSTEM --hint hd0,msdos3
    linux /KERNEL boot=LABEL=OE_SYSTEM disk=LABEL=OE_DATA debugging
 }
```

Please note the /dev/sda3 and /dev/sda4 devices correspond to the two OpenELEC partition device names that you created earlier in this tutorial. In the example, /dev/sda3 corresponds to the partition labelled 'OE_SYSTEM' which KERNEL and SYSTEM have been copied to, and /dev/sda4 corresponds to the partition 'OE_DATA' which was left empty.

Please note that GRUB2 differs from GRUB regarding the partitions schemes, as it starts enumerating partitions from 1 instead of 0. Within GRUB2, the notation 'set root=(hd0,3)' corresponds to the third partition on the first drive, i.e. 'sda3'. The two values shall match. 

My question is, what values do I put into the bootloader as I was confused by the instructions in the two paragraphs above.

any help would be appreciated.

Hugh

---

### Post by parker-hugh on 2014-06-09
I haven't had any respose to my questions and wondered if someone can help me as I am not an experienced linux user yet, I have just move from windows xp.

regards, Hugh

---

### Post by oldfred on 2014-06-09
Those entries look correct. With grub2 sda3 is hd0,3 or hd0,msdos3 in grub menus.

Your partitions look very small?

You only have 4 primary partitions and one is used as the extended partition. But generally it does not matter if partitions are primary or logical for Linux. Windows requires a primary to boot from. And best to have an extended so you can create more than the 4 primary. In an extended you can have an unlimited number of logical partitions.

---

### Post by parker-hugh on 2014-06-09
thanks **oldfred **for your reply, but I managed to successfully install OpenELEC alongside XUBUNTU ....

here are my comments against my original questions....

***1. OE_SYSTEM and OE_DATA was it ok to create these partitions as primary partitions?*** You were correct, this wasn't a problem.

***2. What values do I put into the GRUB? ***Here is what I added to GRUB....

```
menuentry "OpenELEC.tv" {
   set root=(hd0,3)
   linux /KERNEL boot=/dev/sda3 disk=/dev/sda4 quiet
}

menuentry "OpenELEC.tv (Textmode)" {
   set root=(hd0,3)
   linux /KERNEL boot=/dev/sda3 disk=/dev/sda4 textmode quiet
}

menuentry "OpenELEC.tv (Debugmode)" {
   set root=(hd0,3)
   linux /KERNEL boot=/dev/sda3 disk=/dev/sda4 debugging textmode quiet
}
```

***3. When I copy the KERNEL and SYSTEM files to the OE_SYSTEM partition, is it ok to use the following syntax in terminal window... is it ok to have my username in the file path?***

I used following syntax...

```
cp /home/hugh/Downloads/OpenELEC-Generic.i386-4.0.4/target/KERNEL /media/hugh/OE_SYSTEM1
cp /home/hugh/Downloads/OpenELEC-Generic.i386-4.0.4/target/SYSTEM /media/hugh/OE_SYSTEM1
```

 initially the path /media/hugh/OE_SYSTEM didn't work, so I added number 1 to the end as I noticed that this was displayed like that when OE_SYSTEM was opened with file manager, i.e.
/media/hugh/OE_SYSTEM1/  I don't know why a number 1 was needed but it worked.

My partitions are indeed small, but they were only created for test purposes on my laptop, I intend to replace my old hard drive with an SSD and repeat the setup, so this was a test run to see if I coud run with the three operating systems side by side. I'm happy it all worked out in the end, thanks again for your feedback.

Regards,

Hugh

---

