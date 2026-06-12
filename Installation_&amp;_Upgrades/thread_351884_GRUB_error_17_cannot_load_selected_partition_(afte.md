---
title: "GRUB error 17 cannot load selected partition (after windows install)"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by snoxu on 2007-02-02
Ive reinstalled Windows and Im getting error 17 cannot mount selected partition when I try to boot Ubuntu. Im triple booting XP, OSx86 and Ubuntu. (Windows and OSx86 boot fine.) Ive tried following the guides for recovering GRUB and tried the Super GRUB CD. None of them worked. If someone here can point me in the right direction Id appreciate....

Heres how I have my HD partitioned,

> Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1045     8393931    7  HPFS/NTFS
/dev/sda2            1046        2090     8393962+  af  Unknown
/dev/sda3            2091        3165     8634937+  83  Linux
/dev/sda4            3166        7296    33182257+   5  Extended
/dev/sda5            3166        3216      409594+  82  Linux swap / Solaris
/dev/sda6            3217        7296    32772568+   b  W95 FAT32


Tried recovering the GRUB twice via the Live CD, this is what I get when I try the command setup (hd0,2),

> grub> root (hd0,2)

grub> setup (hd0,2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,2) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.



Check the 5th and 6th lines something is failing or whatever. I reboot and still cant into Ubuntu. The guide talks about passwords, but when I follow the procedure it never asks me for passwords, dunno if thats a problem.

I tried again but with the setup (hd0) command and get this,

> grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub>     


...Still cant get into ubuntu

Meh... anyone here can help?

---

### Post by Herman on 2007-02-02
Hello snoxu,
> 17 : Cannot mount selected partition  This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. If you get this error when trying to boot Ubuntu, check your menu.lst file and make sure your operating system entry's 'root (hdx,y)' details are correct.
             If Windows has corrupted your partition table, maybe your Ubuntu partiton has been given a different partition number now than it had before. 
Try again with Super Grub Disk to boot Ubuntu by symlinks to the kernel when you use, from the English (Main) Menu,-->  Gnu/Linux --> Boot Gnu/Linux Directly -->SCSI ...and it should boot.
You will also need to edit /etc/fstab if your partition numbers have changed.

Otherwise, if you can get a Grub Command Line, either from your installed Grub, or from Super Grub Disk, you will be able to do this, (click link: (Grub's)  [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
...and in particular, this:                                                    [How To Boot Linux from GRUB's CLI]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_Boot_Linux_from_GRUBs_CLI") and try the 'Direct (kernel) boot method. In your case if you follow the steps there it looks like you would probably need to be typing '(hd0,2)' instead of '(hd0,1)' for Ubuntu. (hd0,2 = /dev/sda3).

If that doesn't work you'll need to mount it with a Live CD operating system and make sure it's still there.

I hope I'm being helpful,
Regards, Herman :)

---

### Post by snoxu on 2007-02-02
> **Herman said:**
> Hello snoxu,
 If you get this error when trying to boot Ubuntu, check your menu.lst file and make sure your operating system entry's 'root (hdx,y)' details are correct.
             If Windows has corrupted your partition table, maybe your Ubuntu partiton has been given a different partition number now than it had before. 
Try again with Super Grub Disk to boot Ubuntu by symlinks to the kernel when you use, from the English (Main) Menu,-->  Gnu/Linux --> Boot Gnu/Linux Directly -->SCSI ...and it should boot.
This method didn't work...

> **Herman said:**
> You will also need to edit /etc/fstab if your partition numbers have changed.

Otherwise, if you can get a Grub Command Line, either from your installed Grub, or from Super Grub Disk, you will be able to do this, (click link: (Grub's)  [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
...and in particular, this:                                                    [How To Boot Linux from GRUB's CLI]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_Boot_Linux_from_GRUBs_CLI") and try the 'Direct (kernel) boot method. In your case if you follow the steps there it looks like you would probably need to be typing '(hd0,2)' instead of '(hd0,1)' for Ubuntu. (hd0,2 = /dev/sda3).
I went into the command line and did the following:

I used these comands to find the kernel and root partitions
grub>  find /vmlinuz

hd0,2

grub>  find /sbin/init

hd0,2

Then typed

root (hd0,2)
kernel /vmlinuz root=/dev/hda2
initrd /boot/initrd.img-2.6.17-10-generic (I used the TAB key to get the end part of the filename)
boot

A bunch of lines started printing to the screen then it stopped at the following line:

**Begin: Waiting for the root file system**

It stops and does nothing. I'm stumped!

> **Herman said:**
> If that doesn't work you'll need to mount it with a Live CD operating system and make sure it's still there.
So is this the last resort? If so how do I go about doing that?

---

### Post by Herman on 2007-02-02
snoxu, 
Good work! :) You got it almost right, but there could be a small mistake here, just try it once again. like this, ... and see if it'll boot.
```
 root (hd0,2)
kernel /vmlinuz root=/dev/[COLOR=Red]**sda3**[/COLOR]
initrd /boot/initrd.img-2.6.17-10-generic (and use the TAB key to get the end part of the filename)
boot
```Otherwise, you should mount it with a Live CD operating systrem and take a look and see what your files look  like, especailly trhe ones in your /boot directory, here's how to do that, [Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm") ,and in particular, this section,                             [Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")

---

### Post by snoxu on 2007-02-02
OK I can boot into Ubuntu via the command line. (sda3 was the correct root partition I guess).

Now I still can't boot the normal way. Don't know what is broken and needs fixing. :confused:

---

### Post by Herman on 2007-02-02
Okay, lets check your menu.lst file and make sure your operating system entry's 'root (hdx,y)' details are correct. Can you open a terminal, and type in the following code?
```
sudo gedit /boot/grub/menu.lst
```You'll be asked to type in your password, then a page will open that contains a file which is full of commands that control the way your operating system boots up.
Down close to the bottom of that page, you'll find several operating system entries, they look something (but not exactly), like this,
```
## ## End Default Options ##
                                                            
title        Ubuntu, kernel 2.6.15-25-386
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.15-25-386
savedefault
boot
                                                            
title        Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.15-25-386
boot
                                                            
title        Ubuntu, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin 
boot
                                                            
### END DEBIAN AUTOMAGIC KERNELS LIST
                                                            
# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root
                                                            
                                                            
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1
``` You just need to take a look at these operating system entries very closely and you'll see that the one for Ubuntu has some mistakes in it. The correct commands to use will be the exact copy of whatever you found you needed to type at the command line to get Ubuntu to boot up. You just delete the mistakes and type in the right information and save the changes and reboot, and if you have done that all correctly it will be fixed. 

For more info on editing Ubuntu's /boot/grub/menu.lst, click here, [GRUB Boot Loader Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

See how you go,
Regards, Herman:)

---

### Post by snoxu on 2007-02-02
Woot! We're back in business.

I opened the menu.lst and found that for the Ubuntu entries the root and kernel were changed to hd0.3 and sda4 respectively. I changed them back to hd0.2 and sda3 and now Ubuntu boots fine. Problem solved!

Still scratching my head has to how the re-installation of Windows XP led to this and I didn't mention before but the FAT32 partition was mysteriously erased somehow...

I don't think I would have managed by myself, so thanks a million Herman! Seriously thanks!

---

### Post by Herman on 2007-02-03
Yay! :lolflag: Great!

I'm glad you solved your problem and happy if I've been of some help!

I don't know either, how a Windows re-install could change your partition numbering and cause a partition to be deleted, but Windows is noted as a very selfish operating system, nothing would surprise me.
Happy dual booting, snoxu, and all the best! ... And well done!
Regards, Herman

---

