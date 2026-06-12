---
title: "Reinstalling grub using grub-install (without LiveCD)"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by sl789 on 2010-09-26
Recently, I needed to reinstall GRUB2 from LiveCD.

I had 2 instances of ubuntu (in addition to WinXP in **/dev/sda2** ) - 10.04 in** /dev/sda6**   and then development 10.10 in **/dev/sda7 ** which I installed few days ago after WinXP and 10.04, just to check it out. I wanted to delete 10.10 and since GRUB2 was part of it, I needed to reinstall it after deletion. 

Following recommendations (many thanks to **Rubi1200** for explanations and link to BootInfoScript) I've deleted partition with 10.10, then booted with LiveCD and installed GRUB2 so it becomes again part of 10.04 (as it was before  installing 10.10). I had no problems at all doing it.

The question I would like to ask : would it be possible to achieve the same without booting from LiveCD by doing the follows ?

1. Boot to 10.04 Ubuntu **/dev/sda6**
2. Delete partition  /**dev/sda7** with 10.10 (and GRUB2 which was part of it)
3. Issue **sudo grub-install /dev/sda** 

This would save booting from LiveCD 

Any disadvantages/pitfalls vs LiveCD approach ?

---

### Post by ronparent on 2010-09-26
If I understand what you said the answer would be yes! I think what you meant was that you would use the grub installed to 10.10 to boot to 10.04 in its own partition. From the 10.04 session you would be able to delete the 10.10 partition including its grub and use the grub-install command to reinstall grub so that it would boot to the 10.04 install.

I have actually been able to do a similar thing.

---

### Post by sl789 on 2010-09-26
Hi Ronparent !

 >I think what you meant was that you would use the grub installed to 10.10 to boot to >10.04 in its own partition.

That's correct (after installation of 10.10 I had a triple boot system - WinXP, 10.04 and 10.10). The only reason I didn't like LiveCD is that it took a long time to boot from it.

So I thought, for the future, if I decide to install some Ubuntu development version along side the main one, I would be able to uninstall it easily. (My problm also was that when installing 10.10, I choose to check option "nstall bootloader", otherwise it would be enough just to boot to 10.04, delete partition with 10.10 and then run update-grub)

---

### Post by ka3sem on 2010-10-12
Hi s1786,

how do you did the installation without CD. I have a same problem to resolve. 

have only ubuntu 8.10 in my computer, and trying to desinstall some tools and make more free space to do the update to ubuntu 9, I have deleted some system-files (python), and my OS become defected  , no internet connexion, no graphic interface, ...

my ubuntu CD is defected too and shows ubiquited error. I can only boot from it, but can not install the install packet which is in the desktop.

I have downloaded the .iso version 10.04 but the grub failed :confused:

I have followed this link
[https://help.ubuntu.com/community/In...tion/FromLinux](https://help.ubuntu.com/community/In...tion/FromLinux)

but in step3, I founed /etc/grub.d/20_memtest86+ instead of /etc/grub.conf or /boot/grub/menu.lst or /etc/grub.d/40_custom and I have added the following files in my 20_memtest86+

menuentry "installer" {
insmod ext2
set root=(hd0,1)
linux /casper/vmlinuz boot=casper root=/dev/ram1 ramdisk_size=1048576 rw
initrd /casper/initrd.lz
}


Thanks for help

---

### Post by drs305 on 2010-10-12
> **ka3sem said:**
> the grub failed :confused:

I have followed this link
[https://help.ubuntu.com/community/In...tion/FromLinux](https://help.ubuntu.com/community/In...tion/FromLinux)
Thanks for help

The link is incomplete - it doesn't contain a valid address:
[https://help.ubuntu.com/community/In...tion/FromLinux](https://help.ubuntu.com/community/In...tion/FromLinux)

Without seeing the link's contents, I can say that 20_memtest86+ is not the file you want to try to add any menuentry. It is most likely meant to go into the /etc/grub.d/40_custom file (if you are using Grub2).

As a minimum, post the correct link and tell us what version of Grub you are using:
```
grub-install -v
```

---

### Post by ka3sem on 2010-10-12
sorry, it is the following

[https://help.ubuntu.com/community/Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux")

---

### Post by ka3sem on 2010-10-12
I don t know which grub-version I am using, but as I can t find the grub.cfg file, I estimate I use grup 2. How can I verify it:confused:

---

### Post by drs305 on 2010-10-12
We still don't know which version of Grub you are using, but if you are using Lucid or Maverick it is Grub 2. Karmic could be either Grub legacy (0.97) or Grub 2 (1.96 or later).

You can open a root text editor. If you are using Grub2, this command should open the first tab to /etc/grub.d/40_custom. It will have about 6 lines of text, with nothing else. You would add the contents from your previous post at the end of what currently exists:
```
gksu gedit /etc/grub.d/40_custom /boot/grub/menu.lst
```

Contents of 40_custom:
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

```

If the file opens and is completely blank, you don't have a 40_custom file and might be using Grub legacy. If that is the case, edit the menu.lst file which will open in the second tab in Gedit.

---

### Post by ka3sem on 2010-10-12
whith grub-install -v, I obtain

grub-install (GNU GRUB 0.97)

is that means my version is 0.97 :confused:

---

### Post by drs305 on 2010-10-12
> **ka3sem said:**
> whith grub-install -v, I obtain

grub-install (GNU GRUB 0.97)

is that means my version is 0.97 :confused:

Yes, so you would edit the second tab - the menu.lst file.

---

### Post by ka3sem on 2010-10-12
thanks drs305,

the 2 opened files are empty !!!

as I said above, now I am booting from my defected cd and connected to the internet through it, so I think that I am trying to access to temporary displayed data and not to the data resided in my defected computer.

Without the cd I can not go beyond the BIOS

---

### Post by drs305 on 2010-10-12
> **ka3sem said:**
> the 2 opened files are empty !!!


I missed that you were booting from the LiveCD. The reason the files are empty is it is trying to find them on the CD and not your partition.

You will need to mount the partition your 8.10 installation is on, and then open those files:

```

sudo mount /dev/sdXY /mnt  # XY are your drive and partition, example: sda5
gksudo gedit /mnt/boot/grub/menu.lst

```

---

### Post by ka3sem on 2010-10-12
thanks drs305,

the 2 opened files are empty !!!

as I said above, now I am booting from my defected cd and connected to the internet through it, so I think that I am trying to access to temporary displayed data and not to the data resided in my defected computer.

Without the cd I can not go beyond the BIOS

---

### Post by ka3sem on 2010-10-12
I have sda, sda1, sda2, sda3, which one should I use

---

### Post by ka3sem on 2010-10-12
the one which I have created with gparted is /dev/sda2, but the opened menu.ls is empty. Should I edit it

---

### Post by ka3sem on 2010-10-12
after gksudo gedit /mnt/boot/grub/menu.lst, I can not save the file, the recieved message is:

Could not find the file /mnt/boot/grub/menu.lst

---

### Post by drs305 on 2010-10-12
> **ka3sem said:**
> the one which I have created with gparted is /dev/sda2, but the opened menu.ls is empty. Should I edit it

I reread all your posts. You said that you deleted or corrupted some of you system files. The procedure you are trying to follow says that it will work from a working system. I assume you don't have a working system - but you CAN at least get to the Grub menu?

Please download and run the boot info script from this site. It will tell us your partitions, boot files, etc:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

It will generate a file called RESULTS.txt. Open that file, then copy the contents here.

---

### Post by ka3sem on 2010-10-12
I m pleased to receive quickly answers and guide :-)

here is the result:
```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7e227e22

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       979,964       979,902  82 Linux swap / Solaris
/dev/sda2             979,965   124,166,384   123,186,420  83 Linux
/dev/sda3         124,166,385   312,576,704   188,410,320  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9824c022-89b4-4caf-940a-5a5f3d2e29d0   swap                                     
/dev/sda2        6ea89aac-06b8-4586-8c91-44245035ff9f   ext3       /                             
/dev/sda3        e00cb457-274f-4d92-aa80-8bf475ea0d0b   ext3       /home                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sda3        /media/_home             ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sda2        /mnt                     ext3       (rw)
/dev/sda3        /mnt                     ext3       (rw)
/dev/sda2        /mnt                     ext3       (rw)


```

---

### Post by oldfred on 2010-10-12
ka3sem

AS drs305 suggests start a new thread of your own. I may have a way, but it may be too advanced, so we need others to look at your thread for better solutions.

---

### Post by ka3sem on 2010-10-12
my own started thread is here:

[http://ubuntuforums.org/showthread.php?p=9962259#post9962259](http://ubuntuforums.org/showthread.php?p=9962259#post9962259)

@drs305
can you move please the rest of the rest of the responses or should I resume it?

---

### Post by drs305 on 2010-10-12
> **ka3sem said:**
> my own started thread is here:

[http://ubuntuforums.org/showthread.php?p=9962259#post9962259](http://ubuntuforums.org/showthread.php?p=9962259#post9962259)

@drs305
can you move please the rest of the rest of the responses or should I resume it?

I'll move the ones that are important to the thread.

---

