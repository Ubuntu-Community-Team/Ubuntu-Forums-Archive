---
title: "Ended up in &quot;grub rescue&quot; - what now?"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by blazius1 on 2010-02-06
OK, this is embarrasing.

I have a new Asus netbook which came with Windows 7 on it.  I decided to install Ubuntu as well.  As the computer has no optical drive, I chose to use the Unetbootin method, which seemed to work well.  I set aside 50 GB for Unubtu, with 5 GB for swap and the rest for /.

After finishing the install I rebooted, and got up GRUB with six options - the two usual Ubuntu options, thwo Memtest options, the Win7 and a Vista option.  I first tried the Win7 to confirm everything was still working, it was.  Unetbootin uninstalled itself, and I rebooted again.

This time, I made an unwise choice.  Curious about the Vista boot option, I tried it.  Well, it was Asus' restore utility, designed to reset the HDD to the original configuration.  It did warn me that it would erase all data on the disk, so I chose to abort it and reboot.

Well, it obviously has done something to my boot setup...  Now I'm only getting this:

GRUB loading.
error: no such partition
grub rescue >

The only command that does something useful is ls, which gives this output:

(hd0) (hd0,5) (hd0,4) (hd0,3) (hd0,1) (hd1) (hd1,1)

My hard disk should have these partitions:
- Win 7
- Win 7 data partition
- Ubuntu swap
- Ubuntu /
- Windows/ASUS rescue partition (1 or 2 partitions, not sure)

I have googled for "grub rescue", but have found nothing helpful so far.  Any suggestions on what I should do?  My ASUS is able to boot from an external optical drive (but I don't have one) or a USB stick.  The largest I have here is about 1 GB.

My final resort would be to buy the external DVD drive, pop in the ASUS system restore disk and start all over again.  There's not much data on the computer, but it would be some hours setting it up like it was...

---

### Post by drs305 on 2010-02-06
blazius1,

First, welcome to Ubuntu and the Ubuntu forums.  :-)

We can get this straightened out but to remove doubts about the current configuration please run the boot info script from the following link. Make sure to post the results inside "code" brackets by clicking the # icon in the post's menu.

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

If you feel the need to experiment, you can try manually booting from the command line or editing the menu entry in the Grub 2 menu by referring to this:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

---

### Post by blazius1 on 2010-02-06
Hi, I dont' have an external CD/DVD dribe for this computer.  I have tried to make a bootable USB stick with Ubuntu Live on it, but it was not recognized by by computer.  This is a quite old USB drive, maybe it does not support boot-from-USB?

I'll try getting a new one and I'll try again.  Thanks for your help so far.

BTW, I've tried to "ls" all the partitions listed by a "bare" ls, all gives "error: unknown filesystem".

Hmmm.

---

### Post by amsterdamharu on 2010-02-06
Boot using commands in grub:
[http://ubuntuforums.org/showthread.php?t=1390088#2](http://ubuntuforums.org/showthread.php?t=1390088#2)

You probably have grub2 so you can't use:
kernel        /boot/vmlinuz-2.6.24-26-generic root=/dev/sda3 ro single
instead use
linux        /boot/vmlinuz-2.6.24-26-generic root=/dev/sda3 ro single

But that is explained in there as well.

---

### Post by Leppie on 2010-02-06
what does the command "set" (without the quotes) do?

also
```
The only command that does something useful is ls, which gives this  output:
[COLOR=Red](hd0)[/COLOR] (hd0,5) (hd0,4) (hd0,3) (hd0,1) [COLOR=Red](hd1)[/COLOR] (hd1,1)
```this indicates there's 2 drives present (or should be present).

---

### Post by blazius1 on 2010-02-06
> **amsterdamharu said:**
> Boot using commands in grub:
[http://ubuntuforums.org/showthread.php?t=1390088#2](http://ubuntuforums.org/showthread.php?t=1390088#2)

You probably have grub2 so you can't use:
kernel        /boot/vmlinuz-2.6.24-26-generic root=/dev/sda3 ro single
instead use
linux        /boot/vmlinuz-2.6.24-26-generic root=/dev/sda3 ro single

But that is explained in there as well.

Both "kernel" and "linux" returns "Unknown command" at the "grub rescue>" prompt.

---

### Post by blazius1 on 2010-02-06
> **Leppie said:**
> what does the command "set" (without the quotes) do?

prefix=(hd0,7)/boot/grub
root=hd0,7

[quoye]also
```
The only command that does something useful is ls, which gives this  output:
[COLOR=Red](hd0)[/COLOR] (hd0,5) (hd0,4) (hd0,3) (hd0,1) [COLOR=Red](hd1)[/COLOR] (hd1,1)
```this indicates there's 2 drives present (or should be present).[/QUOTE]

Seems like the hd1 part is my USB drive-

---

### Post by blazius1 on 2010-02-06
Well, I made a Ubuntu Live 9.10 USB drive with UNetbootin.  The drive is seen by my BIOS and is loaded, but I end up in a menu like this:

"UNetbootin
Default
Help
oem=OEM install (for manufacturers)

Press [Tab] to edit options
Automatic boot in 10 seconds..." (counting down)

No matter what option I choose, I get back to the menu.  By pressing [Tab] I am able to edit the options, but I don't want to fiddle with those...

---

### Post by darkod on 2010-02-06
> **blazius1 said:**
> Well, I made a Ubuntu Live 9.10 USB drive with UNetbootin.  The drive is seen by my BIOS and is loaded, but I end up in a menu like this:

"UNetbootin
Default
Help
oem=OEM install (for manufacturers)

Press [Tab] to edit options
Automatic boot in 10 seconds..." (counting down)

No matter what option I choose, I get back to the menu.  By pressing [Tab] I am able to edit the options, but I don't want to fiddle with those...

If you can boot windows open the usb stick and do the following to get rid of that unetbootin menu:
1. In the root folder rename syslinux.cfg to syslinux.old
2. In the folder isolinux find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

That will enable the standard ubuntu menu as you see from a cd.

---

### Post by blazius1 on 2010-02-06
> **darkod said:**
> If you can boot windows open the usb stick and do the following to get rid of that unetbootin menu:
1. In the root folder rename syslinux.cfg to syslinux.old
2. In the folder isolinux find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

That will enable the standard ubuntu menu as you see from a cd.

Got the menu, but selecting any option gets me straight back to the menu, except for "Help".  I then get a selection of help topics and a "boot:" prompt.  Pressing enter on this prompt gives "Could not find kernel image: /casper/vmlinuz"

---

### Post by darkod on 2010-02-06
> **blazius1 said:**
> Got the menu, but selecting any option gets me straight back to the menu, except for "Help".  I then get a selection of help topics and a "boot:" prompt.  Pressing enter on this prompt gives "Could not find kernel image: /casper/vmlinuz"

Hmmm, sounds like some sort of a loop. Maybe it wasn't created correctly. Try again.
Boot windows, plug in the usb stick, format it as FAT32 to wipe everything. Use unetbootin to create it with Diskimage option and ignore the question to reboot at the end, just close unetbootin. Then do the rename procedure as above.

That should be OK.

---

### Post by raymondh on 2010-02-06
just a side note,

Similar thing happened to me with an acer aspire one.  I was using Jaunty (9.04).  My fix was to re-install Juanty and then rename the VISTA header in the menu.lst to 'windows recovery' (my words) so my sister wouldn't get confused.

Raymond

---

### Post by blazius1 on 2010-02-06
I am remaking the USB drive now.  I just had some second thoughts: This computer is delivered with a "mini-OS" with an image viewer, net browser etc.  Could what I am seing be the bootloader for this browser, and not Ubuntu's GRUB?

---

### Post by darkod on 2010-02-06
> **blazius1 said:**
> I am remaking the USB drive now.  I just had some second thoughts: This computer is delivered with a "mini-OS" with an image viewer, net browser etc.  Could what I am seing be the bootloader for this browser, and not Ubuntu's GRUB?

It could. Make sure you are booting from USB, or how it's usually called USB HDD (yes, even for usb stick it goes under the category USB HDD).

---

### Post by blazius1 on 2010-02-06
I also found out how to restore the computer to its original state with an USB drive.  As I had done very little on this computer yet (started using it less than 24 h ago) I am considering that route if there's no EUreka moment soon...  Thanks for all your help so far, anyway.  I'll keep you posted.

---

### Post by Miki800 on 2010-02-06
looks like I had the same problem as you (maybe?) maybe you could use the same solution as me:
[http://ubuntuforums.org/showthread.php?p=8781873](http://ubuntuforums.org/showthread.php?p=8781873)

---

### Post by blazius1 on 2010-02-06
> **darkod said:**
> Hmmm, sounds like some sort of a loop. Maybe it wasn't created correctly. Try again.
Boot windows, plug in the usb stick, format it as FAT32 to wipe everything. Use unetbootin to create it with Diskimage option and ignore the question to reboot at the end, just close unetbootin. Then do the rename procedure as above.

That should be OK.

Yay! It worked now.  Heres the log file requested earlier

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xabf319e9

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   209,717,247   209,715,200   7 HPFS/NTFS
/dev/sda2         209,728,636   467,386,367   257,657,732   f W95 Ext d (LBA)
/dev/sda5         312,121,344   467,386,367   155,265,024   7 HPFS/NTFS
/dev/sda3    *    467,386,368   488,357,887    20,971,520   b W95 FAT32
/dev/sda4         488,357,888   488,392,064        34,177  1b Hidden W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
43 heads, 43 sectors/track, 4233 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04030201

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          1,080     7,827,455     7,826,376   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AEDED57FDED5406F                       ntfs                                     
/dev/sda3        86F4-D40A                              vfat                                     
/dev/sda5        EC9CEFFD9CEFBFE6                       ntfs       Felles data                   
/dev/sdb1        0C2A-BF5C                              vfat       UBUNTU USB                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  55 aa 03 e9 7a 00 93 00  00 00 00 00 00 00 00 00  |U...z...........|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  ff ff 00 00 00 9b cf 00  |................|
00000030  ff ff 00 00 00 93 cf 00  ff ff 00 00 00 9a 0f 00  |................|
00000040  ff ff 00 00 00 92 0f 00  27 00 20 00 00 00 00 00  |........'. .....|
00000050  ff ff 00 00 00 00 00 00  10 00 44 65 76 69 63 65  |..........Device|
00000060  56 4d 20 52 6f 6d 20 4c  6f 61 64 65 72 00 00 00  |VM Rom Loader...|
00000070  01 31 31 2f 32 32 2f 32  30 30 37 00 00 00 00 00  |.11/22/2007.....|
00000080  0e 58 2e a3 42 02 68 00  00 1f 68 00 00 07 57 2e  |.X..B.h...h...W.|
00000090  8d 3e 00 06 2e 80 7d 20  03 75 17 9c 60 b8 03 00  |.>....} .u..`...|
000000a0  cd 10 61 9d 2e 8d 3e 8c  03 e8 fd 02 b4 00 50 cd  |..a...>.......P.|
000000b0  16 58 5f b8 03 00 c1 e0  09 89 c3 0e 07 26 66 8b  |.X_..........&f.|
000000c0  47 0c 66 85 c0 74 05 2e  66 a3 56 00 fa 66 31 c0  |G.f..t..f.V..f1.|
000000d0  8c c8 66 c1 e0 04 2e 66  01 06 4a 00 fb 2e 66 a3  |..f....f..J...f.|
000000e0  3a 00 b0 9a 2e a2 3d 00  66 50 e8 25 03 66 58 66  |:.....=.fP.%.fXf|
000000f0  50 66 51 1e c8 0c 00 00  0e 1f 66 31 c0 3e a1 06  |PfQ.......f1.>..|
00000100  00 66 c1 e0 09 66 2d 03  00 00 00 66 50 2e 66 a1  |.f...f-....fP.f.|
00000110  56 00 66 50 66 31 c0 66  31 c9 b9 00 06 8c c8 66  |V.fPf1.f1......f|
00000120  c1 e0 04 66 01 c8 66 50  e8 cb 01 c9 1f 66 59 66  |...f..fP.....fYf|
00000130  58 fa 2e 0f 01 16 48 00  0f 20 c0 0c 01 0f 22 c0  |X.....H.. ....".|
00000140  2e 66 8b 36 56 00 66 67  66 67 8b 06 66 3d eb 3e  |.f.6V.fgfg..f=.>|
00000150  45 54 74 14 0f 20 c0 24  fe 0f 22 c0 57 2e 8d 3e  |ETt.. .$..".W..>|
00000160  5a 03 e8 44 02 5f cd 18  0f 20 c0 24 fe 0f 22 c0  |Z..D._... .$..".|
00000170  06 53 8c cb 8e c3 bb 00  06 e8 e0 00 5b 07 c8 0c  |.S..........[...|
00000180  00 00 66 b8 00 02 00 00  66 50 2e 66 a1 56 00 66  |..f.....fP.f.V.f|
00000190  50 66 31 c0 66 31 c9 b9  00 06 8c c8 66 c1 e0 04  |Pf1.f1......f...|
000001a0  66 01 c8 66 50 e8 4e 01  c9 2e 66 8b 36 56 00 66  |f..fP.N...f.6V.f|
000001b0  89 e0 66 50 16 66 29 db  bb 48 00 66 29 c9 8c c9  |..fP.f)..H.f)...|
000001c0  66 c1 e1 04 66 01 d9 66  51 66 29 c0 66 29 c9 b8  |f...f..fQf).f)..|
000001d0  08 00 66 50 b8 14 02 8c  c9 66 c1 e1 04 66 01 c1  |..fP.....f...f..|
000001e0  66 51 66 29 c0 89 e0 66  29 c9 8c d1 66 c1 e1 04  |fQf)...f)...f...|
000001f0  66 01 c1 fa 2e 0f 01 16  48 00 0f 20 c0 0c 01 0f  |f.......H.. ....|
00000200


```

If this works, theres a us$50 reward payable to the open source association of your preference (split along the preferences of those of you who are helping me out on this one):KS

---

### Post by darkod on 2010-02-06
/dev/sda1               2,048   209,717,247   209,715,200   7 HPFS/NTFS
/dev/sda2         209,728,636   467,386,367   257,657,732   f W95 Ext d (LBA)
/dev/sda5         312,121,344   467,386,367   155,265,024   7 HPFS/NTFS
/dev/sda3    *    467,386,368   488,357,887    20,971,520   b W95 FAT32
/dev/sda4         488,357,888   488,392,064        34,177  1b Hidden W95 FAT32

And where exactly do you have ubuntu installed? There are no linux partitions on the hdd at all.

On another note, if you boot again with Try Ubuntu, open terminal and do:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings. That will write generic windows MBR to /dev/sda so you can boot windows.

Also from the live desktop you will need to open Gparted (System-Administration) and remove the boot flag from /dev/sda3, and put it on your win7 system partition, /dev/sda1.

With the above commands executed that should make you boot into win7 directly. After that, consider where you want to install ubuntu and prepare unallocated unpartitioned space and take it from there.

---

### Post by blazius1 on 2010-02-06
> **darkod said:**
> /dev/sda1               2,048   209,717,247   209,715,200   7 HPFS/NTFS
/dev/sda2         209,728,636   467,386,367   257,657,732   f W95 Ext d (LBA)
/dev/sda5         312,121,344   467,386,367   155,265,024   7 HPFS/NTFS
/dev/sda3    *    467,386,368   488,357,887    20,971,520   b W95 FAT32
/dev/sda4         488,357,888   488,392,064        34,177  1b Hidden W95 FAT32

And where exactly do you have ubuntu installed? There are no linux partitions on the hdd at all.

I never came as far as running Ubuntu from my HDD, I completed the install from Ubuntu Live and rebooted, then messed around in the Asus restore partition.

---

### Post by darkod on 2010-02-06
> **blazius1 said:**
> I never came as far as running Ubuntu from my HDD, I completed the install from Ubuntu Live and rebooted, then messed around in the Asus restore partition.

Why do you still keep that restore partition? They're useless.
What I would do. Make win7 boot as I explained in the previous post. If it works, boot it few times.
Using win7 Backup&Restore tool create a system rescue disc (it fits on cd). That would allow you to repair the win7 boot process or boot with the cd and restore an image you've made of your win7. That would replace your useless restore partition which destroys usually all data on the hdd.
But read more about the Backup&Restore tool, I haven't used it (yet) and know just the basics.

After you've sorted that out, you can consider deleting the restore partition and what kind of layout you want to plan for your hdd.

Of course, you don't have to do the above and you can start planning the layout as it is, keeping the restore partition.

---

### Post by blazius1 on 2010-02-06
Well, I was able to get into Win7 again, everything there seems to be intact.  But after I reboot again I get an error message telling me no bootable partitions are found.  Went into Ubuntu Live again and what had happened?  The boot flag had been moved to /dev/sda4 again, probably the restore partition.  Grrr.  Moved the boot flag back to sda1.  Booted again, worked again.  Seems like removing the restore partition is a wise choice!

BTW, you have earned the $50.  Should I donate it to some open source association, or should I buy you a Tshirt from the Ubuntu store?

---

### Post by darkod on 2010-02-06
> **blazius1 said:**
> Well, I was able to get into Win7 again, everything there seems to be intact.  But after I reboot again I get an error message telling me no bootable partitions are found.  Went into Ubuntu Live again and what had happened?  The boot flag had been moved to /dev/sda4 again, probably the restore partition.  Grrr.  Moved the boot flag back to sda1.  Booted again, worked again.  Seems like removing the restore partition is a wise choice!

BTW, you have earned the $50.  Should I donate it to some open source association, or should I buy you a Tshirt from the Ubuntu store?

T-shirt sounds nice. :)
But we still have things to do. As I said, I haven't used win7 B&R but the general logic would be:
1. Creating system repair cd which allows you to boot with it and restore an image.
2. Instead of making image of your current C: on DVDs (it can take lots of them), create the image as single file on ext hdd for example.

So, in case of restore you would plug in the ext hdd, boot from the restore cd, and use the image to restore your win7 as it is right now (or the last time you made an image). A restore partition would return it to factory state. This is why I think using B&R and creating your own backup image is better. And once you have that, no need for the partition at all.

Otherwise, looking at the start/end sectors in the results file, it looks the ubuntu partition was deleted by the Asus restore partition, there is a gap inside /dev/sda2 which is extended partition, you can see the logic partition /dev/sda5 is not taking whole of /dev/sda2.

---

### Post by Leppie on 2010-02-06
> **darkod said:**
> 1. Creating system repair cd which allows you to boot with it and restore an image.
you can freely download a win 7 recovery disk here: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

not sure what the partition sda4 contains, but it's very small (like 17mb). some oem utility partition?

---

### Post by darkod on 2010-02-06
> **Leppie said:**
> you can freely download a win 7 recovery disk here: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

not sure what the partition sda4 contains, but it's very small (like 17mb). some oem utility partition?

I know about that, but the main point in creating your own disc is that the main purpose would be restore from image, not repairing a bootloader. I don't know whether the generic discs have the same ability.

---

### Post by Leppie on 2010-02-06
> **darkod said:**
> I know about that, but the main point in creating your own disc is that the main purpose would be restore from image, not repairing a bootloader. I don't know whether the generic discs have the same ability.
true, it's better to create a recovery set. i have never tried those disks. i just know they're around...

---

### Post by blazius1 on 2010-02-06
> **darkod said:**
> T-shirt sounds nice. :)Please PM me with info on what size and style you prefer.  I'll also need your postal address.

> 
So, in case of restore you would plug in the ext hdd, boot from the restore cd, and use the image to restore your win7 as it is right now (or the last time you made an image). A restore partition would return it to factory state. This is why I think using B&R and creating your own backup image is better. And once you have that, no need for the partition at all.


I guess that would be useful.  Thanks for all your help!

---

