---
title: "Not Booting At All"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by idmontie on 2011-01-12
I recently installed Ubuntu to dual-boot with WinXP.  When I restarted the computer, I was immediately prompted with:

error: no such device: [long string of characters]
grub rescue>

I then decided to put the boot disk in and turned off and then turned on the computer.  The screen produced the purple ubuntu background, but then went black and did nothing.

Any help?  This is really disappointing since I've had Ubuntu work alongside Win7 on my laptop.

---

### Post by sikander3786 on 2011-01-12
Welcome to the forums :-)

Please boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us more about your setup and thus help diagnose/solve the problem.

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by idmontie on 2011-01-12
> **sikander3786 said:**
> Welcome to the forums :-)

Please boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us more about your setup and thus help diagnose/solve the problem.

While posting, click the # icon in post menu and paste your text in between the generated code tags.

The problem is that it doesn't even get that far. When I boot using the ubuntu live cd, I get a blank screen after about 10 seconds, and then nothing happens.

I press the delete key when the purple ubuntu screen appears.   I can then select the language, and then I am asked to either try ubuntu, install it, check the disk, etc.  Which ever one I choose, I get a blank screen which does not change.

---

### Post by Rubi1200 on 2011-01-12
What graphics card do you have installed?

---

### Post by idmontie on 2011-01-12
An old GeForce graphics card, I believe it's a NVIDIA GeForce 2 or 3. It should say on the card, right?  I'll edit this post with the exact model in a bit.

---

### Post by Rubi1200 on 2011-01-12
The exact make is not necessary since the following instructions will apply no matter which version.

As the CD boots and you see the options to select language, try etc. immediately after press F6 for the boot options. You need to check the option for nomodeset. Then Enter to continue the process. If this does not work we can try other things.

---

### Post by idmontie on 2011-01-12
> **Rubi1200 said:**
> The exact make is not necessary since the following instructions will apply no matter which version.

As the CD boots and you see the options to select language, try etc. immediately after press F6 for the boot options. You need to check the option for nomodeset. Then Enter to continue the process. If this does not work we can try other things.

I selected the option and picked the "Try Ubuntu" option, which option was I supposed to choose?

EDIT: Just to clarify, it did load when I selected the "Try Ubuntu" option.

---

### Post by Rubi1200 on 2011-01-12
Are you at the desktop on the LiveCD?

If yes, then follow the previous instructions to run the boot info script and post the results back here please.

---

### Post by idmontie on 2011-01-12
Here's the output of the RESULT.txt file:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders, total 241254720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    10,506,509    10,506,447  12 Compaq diagnostics
/dev/sda2    *     10,506,510    39,809,069    29,302,560   7 HPFS/NTFS
/dev/sda3          39,809,070   241,248,104   201,439,035   f W95 Ext d (LBA)
/dev/sda5          39,809,133   241,248,104   201,438,972   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       fcf672d9-0ac5-4323-97c4-9255f1151eea   ext4                                     
/dev/ramzswap0                                          swap                                     
/dev/sda1        8AFCF940FCF9275B                       ntfs                                     
/dev/sda2        8A00464800463C07                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        F070AEA170AE6E52                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
C:\wubildr.mbr = "Ubuntu"

```

---

### Post by sikander3786 on 2011-01-12
So it is a Wubi install. Please follow Problem # 1 here.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

It got borked due to some Grub updates. Once it is fixed, don't forget to apply the Permanent Fix from the page linked above in order to prevent future problems.

Good Luck!

---

### Post by Rubi1200 on 2011-01-12
Just to add to what sikander3786 said; you need to restore the Windows bootloader. Wubi installs cannot boot from the MBR (a normal Ubuntu install would of course).

See problem #1, solution #1 or #2

If you need more help, just ask.

---

### Post by idmontie on 2011-01-12
Thanks everyone for the help, I am now able to boot Windows XP and Ubuntu!

Problem solved.

---

### Post by Rubi1200 on 2011-01-12
Excellent! Glad you got it sorted out :)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

