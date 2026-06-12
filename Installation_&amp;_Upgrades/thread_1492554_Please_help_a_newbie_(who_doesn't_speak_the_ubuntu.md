---
title: "Please help a newbie (who doesn't speak the ubuntu language)"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by minniecoop on 2010-05-24
I have Windows XP on a 2 year old PC.  Never used Linux, wanted to try it out, so I downloaded the software and burned in onto CD, just like it said to do (I was going by a video from PC world explaining how to do this).  The video suggested I get an updated graphics driver, so I did....but I don't remember what one or if it was even the right one.  I chose to put Ubuntu 10.04 on its own partition (sda7).

When I boot up the PC, I cannot choose between the 2 OS's, which I NEED to be able to do.  I also end up at a frozen Ubuntu desktop screen which leaves me no choice but to hard reboot the system.  The only way I can do anything at all on my computer is if I run the bootable Linux CD I burned.  I even decided to try and reinstall it, hoping it would just overwrite itself, but it didn't help.

Can I just uninstall Ubuntu and then try to start all over the right way?  I don't have the time to fix this PC the long and hard way.  I need to get back to my work on the computer--right now I am screwed because I can't get to my files.

Please help!  Thanks!

---

### Post by presence1960 on 2010-05-24
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by minniecoop on 2010-05-24
OMG, that was a quick response, thank you!!  It is late, so I will have to get to that tomorrow.  Thanks, again, and I will talk to you as soon as I can.

---

### Post by presence1960 on 2010-05-24
> **minniecoop said:**
> OMG, that was a quick response, thank you!!  It is late, so I will have to get to that tomorrow.  Thanks, again, and I will talk to you as soon as I can.

Sounds like a plan to me.

---

### Post by minniecoop on 2010-05-25
presence1960;

I did just what you said to do...here are the results:


               ```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    92,164,904    92,164,842   7 HPFS/NTFS
/dev/sda2          92,164,966   281,794,394   189,629,429   f W95 Ext d (LBA)
/dev/sda5          92,164,968   143,380,124    51,215,157   b W95 FAT32
/dev/sda6         143,380,188   256,245,421   112,865,234   7 HPFS/NTFS
/dev/sda7         256,245,760   281,794,394    25,548,635  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9C90322A90320AF2                       ntfs       PROGRAMS                      
/dev/sda2: PTTYPE="dos" 
/dev/sda5        4890-E667                              vfat                                     
/dev/sda6        8CBCA1B4BCA198EA                       ntfs       DATA BACKUP                   
/dev/sda7        c6a4e86d-0a4f-46a1-b4d6-00ff7c98503a   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /usepmtimer /NoExecute=OptOut 
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by dino99 on 2010-05-25
follow the link below to build good partitions:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by minniecoop on 2010-05-25
why do I have to format the first one?  If I do that, I'll lose all my programs.  I backed up my files, but not my software.  Also, you'll have to forgive me for not understanding half of what you said...I am not *that* techy.

---

### Post by presence1960 on 2010-05-25
You do not have a partition that contains the ubuntu OS on it. Something must have gone wrong during the install. You have GRUB 2 installed and it looks to sda7, but that is the swap partition. You do not have a partition which has the ubuntu OS which is called root (/). Here is my boot info script output which contains the partitions of my hard disks so you can compare:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Lilo is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

[COLOR="Red"]sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img[/COLOR]

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

[COLOR="Red"]sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img[/COLOR]

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7408b4a2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   209,712,509   209,712,447   7 HPFS/NTFS
/dev/sda2         209,712,510   343,919,519   134,207,010   5 Extended
[COLOR="Red"]/dev/sda5         209,712,762   272,623,049    62,910,288  83 Linux[/COLOR]
/dev/sda6         272,623,113   281,008,979     8,385,867  82 Linux swap / Solaris
[COLOR="Red"]/dev/sda7         281,009,043   343,919,519    62,910,477  83 Linux[/COLOR]


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05f07bc0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   754,974,674   754,974,612  83 Linux
/dev/sdb2         754,974,675   976,768,064   221,793,390   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00009028

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   838,866,104   838,866,042  83 Linux
/dev/sdc2         838,866,105 1,090,524,329   251,658,225   7 HPFS/NTFS
/dev/sdc3       1,090,524,330 1,953,520,064   862,995,735   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        BA8404418404029D                       ntfs       xp                            
[COLOR="Red"]/dev/sda5        68133ee7-9788-4905-b012-452696873308   ext4    [/COLOR]                                 
/dev/sda6        935cca57-2e64-487d-94d0-44252620d478   swap                                     
[COLOR="Red"]/dev/sda7        cf2886e6-da33-4cb6-9d0b-14336e4385aa   ext4       9.10 studio [/COLOR]                  
/dev/sdb1        2c0ea91f-1ea5-4394-b694-0a60f5b08b78   ext4       data-linux                    
/dev/sdb2        3075F35B7A562F9F                       ntfs       data-windows                  
/dev/sdc1        945dc762-b626-42a0-9d92-b6c8cf0c090b   ext4       backup-linux                  
/dev/sdc2        3B7E0A127A363CE4                       ntfs       backup-windows                
/dev/sdc3        7953AC5779F24D5B                       ntfs       movies                        

```

sda5 is ubuntu 9.10  and sda7 is ubuntu studio 9.10. sda1 is XP, sda6 is swap. Note my GRUB 2 looks to sda5 (karmic 9.10)

You need to repartition your partitions making room for a partition for the ubuntu OS. You can leave your windows partition untouched so you don't have to reinstall windows.

---

### Post by minniecoop on 2010-05-26
presence, I am having problems with the download/extracting.  It seems to have downloaded fine, but I think something went wrong, because it seems there is nothing to extract.  It won't extract anything, however I do not receive any error messages.  I tried to download it 3 times, different ways.

Can I please just uninstall Ubuntu? I really just want to take the easy way out because I don't have time for this. PLEASE??  When I understand the way this works better, I will try again.  Can you please tell me how to uninstall?

Thank you.

---

### Post by daimaru on 2010-05-26
if you have a windows cd boot from it and enter recovery console. type in 
```
fixmbr
```to rewrite your master boot record. you should now be able to boot in to windows .  grub should be gone. If you don't have an original windows cd to boot from you need to get an alternative. There are some recovery disks out there. but i am not sure what they are called.

EDIT:
heres some links
[http://www.allbootdisks.com/](http://www.allbootdisks.com/)
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
or just google fixmbr without windows cd

---

### Post by WinRiddance on 2010-05-26
> **minniecoop said:**
> 
Can I please just uninstall Ubuntu? I really just want to take the easy way out because I don't have time for this. PLEASE??  When I understand the way this works better, I will try again.  Can you please tell me how to uninstall?

Thank you.

If you can't copy/paste and follow extremely basic directions then there's really only one "simple" way out for you. Unless you're using illegal software you should have a copy of all of your installed programs either on CD, your existing Windows partition, whatever. You already mentioned that you backed up your personal files which means that your personal important work is safe.

So either go ahead and Re-install your legal WindowsXP OS on top of the existing one (this works, I've done it dozen of times in the past 5 years) followed by Re-installing all of your other legal software programs again ... or make a new Windows installation in the partition which is currently being read or occupied by Ubuntu related files. This too should work since the XP installation will ask you which partition to use if you want a new installation?

Other than that, you can only be patient and hope that we can all work through this. If your existing workload was so heavy and so important you should probably at the very least waited with your Ubuntu installation until a free Weekend came around, don't you think? We can try to help you but there's no "quick & dirty" solution no matter which way you want to go about it ...

---

### Post by WinRiddance on 2010-05-26
> **daimaru said:**
> if you have a windows cd boot from it and enter recovery console. type in 
```
fixmbr
```to rewrite your master boot record. you should now be able to boot in to windows .  grub should be gone. If you don't have an original windows cd to boot from you need to get an alternative. There are some recovery disks out there. but i am not sure what they are called.

I stand corrected, you're completely right of course. **That** is the easy and quick fix. Amazing how fast we begin to forget ....

---

### Post by daimaru on 2010-05-26
> **WinRiddance said:**
> I stand corrected, you're completely right of course. **That** is the easy and quick fix. Amazing how fast we begin to forget ....
no worries mate :) just not sure if he has an original cd - I'm going to sign off for the night. Hope you can help him out if he has further questions. Night

---

### Post by minniecoop on 2010-05-26
Thank you.  I do have a bootable Windows CD.  I'll try that.  Thanx!

---

