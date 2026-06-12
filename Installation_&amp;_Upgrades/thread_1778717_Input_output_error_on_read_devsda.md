---
title: "Input output error on read /dev/sda"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by Manuj19 on 2011-06-09
[SIZE=2]This all started when i install kubuntu 10.10 on my Western Digital Hard drive. It installed perfectly but one day i was not able to boot to kubuntu. so i tried to install it again but got the error[/SIZE]
 
[SIZE=2]"**[SIZE=2]INPUT OUTPUT ERROR ON READ /DEV/SDA"[/SIZE]**[/SIZE]
**[SIZE=2]and installer is not detecting windows partitions[/SIZE]**
 
[SIZE=2]I have 120G western digital wdc wd1200bevs-22rst0 hard drive.[/SIZE]
 
[SIZE=2]I have tried following commands[/SIZE]
[SIZE=2]1) fdisk -l[/SIZE]
[SIZE=2]this doesn't detect my hard drive[/SIZE]
[SIZE=2]2) sfdisk -l[/SIZE]
[SIZE=2]read error. cannot read sector 0[/SIZE]
[SIZE=2]3) Gparted live cd[/SIZE]
[SIZE=2]input output error[/SIZE]
[SIZE=2]4) test disk (gparted live cd)[/SIZE]
[SIZE=2]read error[/SIZE]
[SIZE=2]5) test disk(windows version)[/SIZE]
[SIZE=2]no error detected[/SIZE]
[SIZE=2]6) smartmontools[/SIZE]
[SIZE=2]completly passed.no error detected[/SIZE]
[SIZE=2]7) windows is saying that hard drive is healthy[/SIZE]
[SIZE=2]8) even the manufacture's life diagnostic tool says that hard drive is healthy[/SIZE]
[SIZE=2]9) tried to burn the cds at slowest speed and even with usb stick . no luck[/SIZE]
[SIZE=2]10) completely wiped the hard drive[/SIZE]
[SIZE=2]11) tried the alternate cd but still no luck[/SIZE]
[SIZE=2]12) used 'fsck' but still failed[/SIZE]
 
I have tried ubuntu, xubuntu and kubuntu 10.10 and 11.04 but no luck
 
[SIZE=2]I have tried the above things and still no succes ](*,) . if anyone can help?[/SIZE]
 
[SIZE=2]thanks in advance[/SIZE]

---

### Post by jerrrys on 2011-06-09
maybe

[http://ubuntuforums.org/showthread.php?t=1710706](http://ubuntuforums.org/showthread.php?t=1710706)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=INPUT+OUTPUT+ERROR+ON+READ+%2FDEV%2FSDA+western+digital&sa=Search&cof=FORID:9#1076](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=INPUT+OUTPUT+ERROR+ON+READ+%2FDEV%2FSDA+western+digital&sa=Search&cof=FORID:9#1076)

---

### Post by Manuj19 on 2011-06-09
[QUOTE=jerrrys;10920829]maybe
 
[http://ubuntuforums.org/showthread.php?t=1710706](http://ubuntuforums.org/showthread.php?t=1710706)
 
Thank you mate :D
 
I have seen this thread. My problem is exactly same. But according to it i have to turn on AHCI mode in my BIOS 
but my hard drive do not support AHCI mode :( . So i cannot turn it on. Thanks for help and would like to hear more suggestions from you.
 
hdd: SATA wdc wd1200bevs-22rsto

---

### Post by jerrrys on 2011-06-09
so you ran the boot info script and no joy?

---

### Post by psusi on 2011-06-09
AHCI is not a property of the drive; it is the native mode of the SATA controller.

Did you actually run the SMART long selftest?  How about posting the actual SMART attributes?  Also check your dmesg for errors.

---

### Post by Manuj19 on 2011-06-09
> **jerrrys said:**
> so you ran the boot info script and no joy?
Here is the output of boot info script


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No known boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22
    Boot sector info:   Syslinux looks at sector 1426536 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the G:\syslinux 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4007 MB, 4007624704 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7827392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,823,654     7,823,592   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        8CCE-9A73                              vfat       KINGSTON

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sda



=============================== StdErr Messages: ===============================

ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

---

### Post by Manuj19 on 2011-06-09
> **psusi said:**
> AHCI is not a property of the drive; it is the native mode of the SATA controller.

Did you actually run the SMART long selftest?  How about posting the actual SMART attributes?  Also check your dmesg for errors.
The attachment provide the output of demsg command. As for as AHCI is concerned my BIOS donot provide option for selecting the particular mode. Yes i have done that self test and I will post the result of smart test soon

Thank you for help

---

### Post by jerrrys on 2011-06-09
ok, you got me down to guessing and i got just two.  [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and one i have yet to [try]("http://cinderbox.net/2011/06/08/how-to-fix-grub-grub2-windows-mbr-and-lost-systems/") 

don't know if you will get results or not.  good luck

---

### Post by psusi on 2011-06-09
It looks like the controller is boned.  Do you have another computer you can try the drive in?

---

### Post by Manuj19 on 2011-06-09
> **psusi said:**
> It looks like the controller is boned.  Do you have another computer you can try the drive in?

Unfortunately I don't have another computer
but here is attached SMART test results

---

### Post by Manuj19 on 2011-06-09
> **jerrrys said:**
> ok, you got me down to guessing and i got just two.  [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and one i have yet to [try]("http://cinderbox.net/2011/06/08/how-to-fix-grub-grub2-windows-mbr-and-lost-systems/") 

don't know if you will get results or not.  good luck

i have already tried two versions of test disk already mentioned in first post and i also fixed the MBR with different utilities. But still no luck

Any way thanks for your help8)

---

### Post by Manuj19 on 2011-06-10
Hey anyone could help?   ](*,)

---

### Post by psusi on 2011-06-10
The dmesg you posted previously had overflowed from so many errors from all of the attempts to access the drive you had made.  Can you start over and post it without all of those attempts?

---

### Post by Manuj19 on 2011-06-10
> **psusi said:**
> The dmesg you posted previously had overflowed from so many errors from all of the attempts to access the drive you had made.  Can you start over and post it without all of those attempts?

First somehow my hard drive is somehow detected as SDB instead of SDA
when i ran the command
dmesg | grep sdb

the following same error occur many times

  445.723367] sd 3:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  445.723377] sd 3:0:0:0: [sdb]  Sense Key : Aborted Command [current] [descriptor]
[  445.723436] sd 3:0:0:0: [sdb]  Add. Sense: No additional sense information
[  445.723448] sd 3:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  445.723473] end_request: I/O error, dev sdb, sector 0 :confused:

Thanks for reply

---

### Post by psusi on 2011-06-10
Can you verify that this drive works in any other configuration?  Like under Windows, or in another computer?  Either the drive is fubar, or the controller or cable is.

---

### Post by Manuj19 on 2011-06-10
> **psusi said:**
> Can you verify that this drive works in any other configuration? Like under Windows, or in another computer? Either the drive is fubar, or the controller or cable is.
 
If there is problem in drive or controller or cable then why did windows 7 works fine.
Here is an disk management image of drive in windows 7

---

### Post by psusi on 2011-06-10
This is before, or since you started getting these errors in Linux?

---

### Post by Manuj19 on 2011-06-10
> **psusi said:**
> This is before, or since you started getting these errors in Linux?
 
Earlier i have installed kubuntu 10.10 successfully but due to some error i am not able to boot kubuntu. Then i tried to reinstall 10.10 an even tried 11.04 but then this error occur during every installation. Earlier there is not such kind of error

---

### Post by psusi on 2011-06-10
Can you try Windows again and see if it now fails too, or if it is still ok?

If windows can no longer access the drive either, then the drive has gone bad.  If it can, then something about the way Linux is configuring the hardware is making the drive upset.

---

### Post by Manuj19 on 2011-06-10
> **psusi said:**
> Can you try Windows again and see if it now fails too, or if it is still ok?
 
If windows can no longer access the drive either, then the drive has gone bad. If it can, then something about the way Linux is configuring the hardware is making the drive upset.
 
Windows is detecting hard disk . I just tried a bootable DVD of windows 7. 
 
1) So should I try older version ubuntu 8.10 (as other threads show that this problem also exist in version 9.04 and 9.10)?
Or
2) Should i tried another distribution like debian?
I have tried Open Suse 11.4 it doesn't detect my hard drive at all 
 
Thanks for your help

---

### Post by Manuj19 on 2011-06-10
Thank you eveyone for help
 
I think its time to leave Ubuntu and Ubuntu forums ):P
Problem not solved

---

### Post by Manuj19 on 2011-06-16
Hello everyone my problem is solved.

Actually i have locked my hard disk by HD master lock by BIOS. So i removed that lock then the installer detect my hard disk:D

Thank you everyone

---

