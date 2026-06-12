---
title: "grub installation failed 9.10"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by Sanhime on 2010-03-19
Hello. I am fairly new to linux. I have ubuntu/Win7 dual boot installed via wubi, I enjoyed playing around with ubuntu. So I decided to do a real dual boot install. Installation seem to go fine untill it hit 94% and I get a message saying GRUB installation failed. I googled everywhere and I cannot find a suitable solution. Can anyone provide assistance? TY.  My system current has Win7 64bit and WinXP dual boot.  I am trying to get triple boot with Win7, XP, and Ubuntu.

---

### Post by presence1960 on 2010-03-19
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by Sanhime on 2010-03-19
```
             Boot Info Script 0.55    dated February 15th, 2010                    
 
============================= Boot Info Summary: ==============================
 
 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/mapper/isw_jbgiijhih_Bonta
 
sda1: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
 
sdb1: _________________________________________________________________________
 
    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
 
sdd1: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
 
isw_jbgiijhih_Bonta1: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM
 
=========================== Drive/Partition Info: =============================
 
Drive: sda ___________________ _____________________________________________________
 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x495d01ab
 
Partition  Boot         Start           End          Size  Id System
 
/dev/sda1    *          2,048   312,578,047   312,576,000   7 HPFS/NTFS
 
 
Drive: sdb ___________________ _____________________________________________________
 
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf38f7635
 
Partition  Boot         Start           End          Size  Id System
 
/dev/sdb1    *             63   584,189,675   584,189,613   7 HPFS/NTFS
 
/dev/sdb1 ends after the last sector of /dev/sdb
 
Drive: sdd ___________________ _____________________________________________________
 
Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646
 
Partition  Boot         Start           End          Size  Id System
 
/dev/sdd1    *             63   625,137,344   625,137,282   7 HPFS/NTFS
 
 
Drive: isw_jbgiijhih_Bonta ___________________ _____________________________________________________
 
Disk /dev/mapper/isw_jbgiijhih_Bonta: 320.1 GB, 320079134720 bytes
255 heads, 63 sectors/track, 38914 cylinders, total 625154560 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf38f7635
 
Partition  Boot         Start           End          Size  Id System
 
/dev/mapper/isw_jbgiijhih_Bonta1   *             63   584,189,675   584,189,613   7 HPFS/NTFS
 
 
blkid -c /dev/null: ____________________________________________________________
 
Device           UUID                                   TYPE       LABEL                         
 
/dev/loop0                                              squashfs                                 
/dev/mapper/isw_jbgiijhih_Bonta1 542CA9D42CA9B182                       ntfs                                     
/dev/sda1        DEFA8591FA85671D                       ntfs                                     
/dev/sdb                                                isw_raid_member                               
/dev/sdc                                                isw_raid_member                               
/dev/sdd1        ACC031A5C03176A4                       ntfs                                     
 
=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_jbgiijhih_Bonta
isw_jbgiijhih_Bonta1
 
============================ "mount | grep ^/dev  output: ===========================
 
Device           Mount_Point              Type       Options
 
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdd1        /media/ACC031A5C03176A4  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
 
 
======================== isw_jbgiijhih_Bonta1/boot.ini: ========================
 
; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 
=========================== Unknown MBRs/Boot Sectors/etc =======================
 
Unknown BootLoader  on sdb1
 
 
 
=======Devices which don't seem to have a corresponding hard drive==============

```
 
 
Weird, I thouht i got rid of XP parition and got rid of it from boot menu with easybcd.  How do I get rid of all traces of XP?

---

### Post by presence1960 on 2010-03-19
Ubuntu is not even partially installed on your machine. You have RAID set up so you should use the alternate text based installer not the Live CD. Get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by Sanhime on 2010-03-19
Thanks for the tip!  I will give it a try.
In demo mode, I thought ubuntu is not suppose to be installed in anyway,l no?

---

### Post by Sanhime on 2010-03-20
I can't seem to install grub with the alternate CD . Should I try LILO?  :(

---

