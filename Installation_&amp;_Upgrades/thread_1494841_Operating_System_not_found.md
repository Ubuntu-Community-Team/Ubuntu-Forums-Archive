---
title: "Operating System not found"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by micahalcorn on 2010-05-27
Acer Travelmate 4070 running Windows XP - I partitioned and installed Ubuntu 10, which ran fine for a few weeks. So I boot up one day, and get "Operating System not found". I cannot boot my Windows or Ubuntu systems. Neither were backed up, which isn't terribly critical, but I would like to be able to recover one or the other if I can. I went ahead and formatted another USB installation of Ubuntu using my desktop, and when I try to do a fresh install on the laptop, I get to the partitioning step and it can't find my hard drive at all. I have a fairly new replacement drive, and i have no evidence of mechanical failure. Any ideas?

Thanks!

---

### Post by kansasnoob on 2010-05-27
If you're able to boot either a Live CD or Live USB please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by WinRiddance on 2010-05-27
> **micahalcorn said:**
> I went ahead and formatted another USB installation of Ubuntu using my desktop, and when I try to do a fresh install on the laptop, I get to the partitioning step and it can't find my hard drive at all. I have a fairly new replacement drive, and i have no evidence of mechanical failure. Any ideas?

Thanks!

Defective replacement drive or a loose connection maybe ???
Have you tried the "try Ubuntu without changing anything" option from the LiveCD in order to get a look at your hard disk that way? It sounds almost as if there's no disk or the disk hadn't been formatted yet (like some new replacement disks sometimes aren't). With the LiveCd you'd be able to verify this very quickly by opening up the computer/file manager under places ...

---

### Post by micahalcorn on 2010-05-27
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


sda: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda         40EA-60DF                              vfat       PENDRIVE                      
error: block: No such file or directory
error: devices: No such file or directory
error: /dev/mapper/no: No such file or directory
error: found: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

no block devices found

---

### Post by neo-75 on 2010-05-27
Can you see the hard drive in BIOS? What type of hard drive are using? SATA or IDE?? If its IDE check the Jumper Settings, make sure it set on Master. If you are using SATA, don't worry about it. SATA hard drives don't use jumpers.

---

### Post by micahalcorn on 2010-05-27
> **neo-75 said:**
> Can you see the hard drive in BIOS? What type of hard drive are using? SATA or IDE?? If its IDE check the Jumper Settings, make sure it set on Master. If you are using SATA, don't worry about it. SATA hard drives don't use jumpers.

You're going to kill me. Apparently when I installed the HD to test it (a year or two ago), I didn't put it in the bracket. Needless to say the pins just fell out. So I'm back up and running for now. Hopefully I'll make some progress on linux and give back to the forum some day.

Thanks so much!

---

### Post by darkod on 2010-05-27
> **micahalcorn said:**
> You're going to kill me. Apparently when I installed the HD to test it (a year or two ago), I didn't put it in the bracket. Needless to say the pins just fell out. So I'm back up and running for now. Hopefully I'll make some progress on linux and give back to the forum some day.

Thanks so much!

You are lucky it didn't die on you (knock on wood). :) HDDs are not produced to be hot-plug (unless specified usually for servers) and if the power plug falls out, it can kill the disk.

---

