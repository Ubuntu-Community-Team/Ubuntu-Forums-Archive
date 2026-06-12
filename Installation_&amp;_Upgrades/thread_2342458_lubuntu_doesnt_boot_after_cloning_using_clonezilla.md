---
title: "lubuntu doesnt boot after cloning using clonezilla and &quot;dd&quot; command"
date: 2016-11-06
forum: Installation &amp; Upgrades
---

### Post by rahulk7858 on 2016-11-06
[COLOR=#333333][FONT=sans-serif]MicroSD card(lubuntu installed) 32GB-----> .ios saved on pendrive 16GB(also tried with 1TB hardsdisk)------> new microSD card 32BGB[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]sd will be used on raspberry kind((ARM processor)) of board and all clonezilla stuff done on intel desktop. As total OS size is around 8gb so it fits well on 16gb pendrive(clonezilla also showed image clone successful)[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]on booting i am gettting following error:[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]Gave up wating for root device. Common problems:[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]-Boot args (cat /proc/cmdline)[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]-Check rootdelay= (did the system wait long enough?)[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]-Check root= (did the system wait for right device?)[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]-Missing modules (cat /proc/modules; ls /dev)[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]ALERT! /dev/disk/by-uuid/X-X-X-X does not exist. Dropping to a shell![/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]BusyBox v1.21.1 (Ubuntu 1:1.21.0-xubuntu1) built-in shel (ash) Enter help for a list of built-in commands.
(initramfs)_[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]i check all other similar issue solution like changing /etc/fstab, checking /boot folder or executing "blkid" and editing fstab. 
partition structure is same in both cards.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]/* properly booting card lsblk output */
rahulk@hadoopsn:~$ lsblk -fs
NAME  FSTYPE LABEL  UUID                                 MOUNTPOINT
sda1  ext4          4e5d1f53-38b9-427a-b510-f285d536185d /
&#9492;&#9472;sda                                                    
sda2                                                     
&#9492;&#9472;sda                                                    
sda5  swap          38083e31-ac29-40fa-ba52-4a5e4fb990c1 [SWAP]
&#9492;&#9472;sda                                                    
sdb1  vfat   BOOT   6E35-5356                            /media/rahulk/BOOT
&#9492;&#9472;sdb                                                    
sdb2  ext4   trusty e139ce78-9841-40fe-8823-96a304a09859 /media/rahulk/trusty
&#9492;&#9472;sdb                                                    
sr0                                                 [/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]/*not booting card output */    
rahulk@hadoopsn:~$ lsblk -fs
NAME  FSTYPE LABEL  UUID                                 MOUNTPOINT
sda1  ext4          4e5d1f53-38b9-427a-b510-f285d536185d /
&#9492;&#9472;sda                                                    
sda2                                                     
&#9492;&#9472;sda                                                    
sda5  swap          38083e31-ac29-40fa-ba52-4a5e4fb990c1 [SWAP]
&#9492;&#9472;sda                                                    
sdb1  vfat   BOOT   6E35-5356                            /media/rahulk/BOOT
&#9492;&#9472;sdb                                                    
sdb2  ext4   trusty e139ce78-9841-40fe-8823-96a304a09859 /media/rahulk/trusty
&#9492;&#9472;sdb                                                    
sr0[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]sdb2 is not getting mounted somehow. on checking "blkid" in initrmfs i am only getting sdb1.[/FONT][/COLOR]

[COLOR=#333333][FONT=sans-serif]content in boot.txt under sdb2 /boot/boot.txt
  setenv initrd_high "0xffffffff" 
  setenv fdt_high "0xffffffff"
  setenv bootcmd "fatload mmc 0:1 0x40008000 zImage; fatload mmc 0:1 0x42000000 uInitrd; bootm 0x40008000 0x42000000"
  setenv bootargs "console=tty1 console=ttySAC1,115200n8 root=/dev/mmcblk0p2 rootwait ro mem=2047M"
  boot[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]content under sdb1 /boot.ini[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]ODROIDXU-UBOOT-CONFIG[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]# U-Boot Parameters
setenv initrd_high "0xffffffff"
setenv fdt_high "0xffffffff"[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]# Mac address configuration
setenv macaddr "00:1e:06:61:7a:39"[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]#------------------------------------------------------------------------------------------------------
# Basic Ubuntu Setup. Don't touch unless you know what you are doing.
# --------------------------------
# setenv bootrootfs "console=tty1 console=ttySAC2,115200n8 root=UUID=e139ce78-9841-40fe-8823-96a304a09859 rootwait ro"
setenv bootrootfs "console=tty1 root=UUID=e139ce78-9841-40fe-8823-96a304a09859 rootwait ro" #edit - added uart SAC2 support for wifi[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]# boot commands
setenv bootcmd "fatload mmc 0:1 0x40008000 zImage; fatload mmc 0:1 0x42000000 uInitrd; fatload mmc 0:1 0x44000000 exynos5422-odroidxu3.dtb; bootz 0x40008000 0x42000000 0x44000000"[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]# --- Screen Configuration for HDMI --- # 
# ---------------------------------------
# Uncomment only ONE line! Leave all commented for automatic selection.
# Uncomment only the setenv line!
# ---------------------------------------
# ODROID-VU forced resolution
# setenv videoconfig "video=HDMI-A-1:1280x800@60"
# -----------------------------------------------
# 1920x1080 (1080P) with monitor provided EDID information. (1080p-edid)
# setenv videoconfig "video=HDMI-A-1:1920x1080@60"
# -----------------------------------------------
# 1920x1080 (1080P) without monitor data using generic information (1080p-noedid)
# setenv videoconfig "drm_kms_helper.edid_firmware=edid/1920x1080.bin"
# -----------------------------------------------
# 1280x720 (720P) with monitor provided EDID information. (720p-edid)
# setenv videoconfig "video=HDMI-A-1:1280x720@60"
# -----------------------------------------------
# 1280x720 (720P) without monitor data using generic information (720p-noedid)
# setenv videoconfig "drm_kms_helper.edid_firmware=edid/1280x720.bin"
# -----------------------------------------------
# 1024x768 without monitor data using generic information
# setenv videoconfig "drm_kms_helper.edid_firmware=edid/1024x768.bin"[/FONT][/COLOR]

[COLOR=#333333][FONT=sans-serif]# final boot args
setenv bootargs "${bootrootfs} ${videoconfig} smsc95xx.macaddr=${macaddr}"
# drm.debug=0xff
# Boot the board
boot[/FONT][/COLOR]



[COLOR=#333333][FONT=sans-serif]i used latest clonezilla and beginner/expert mode to make clone.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]is there is something wrong ? if both card looks same by every mean(except hardware) then its not booting up clone case. how we can debug this issue ?
any pointer will be help full.[/FONT][/COLOR]

---

### Post by sudodus on 2016-11-07
Welcome to the Ubuntu Forums :-)

Did you clone a Lubuntu system made for [Intel/AMD] PC computers? Such a system will not work in a Raspberry Pi because of the different architecture of the processors (arm).

There are special builds of Ubuntu as well as Debian for Raspberry Pi, and I suggest that you start from such an image, which can be cloned to a [micro] SD card.

See these links:

[https://wiki.ubuntu.com/ARM/RaspberryPi](https://wiki.ubuntu.com/ARM/RaspberryPi)

[https://www.raspberrypi.org/downloads/](https://www.raspberrypi.org/downloads/)

---

### Post by rahulk7858 on 2016-11-07
Thanks sudodus,
I am cloning bootable image from one SD card to another SD card(parent SD card no issue). I am taking backup, just in case something get screwed up or need to put same OS on other similar board.

---

### Post by sudodus on 2016-11-07
Well, it *should* work to clone from a working card, both with dd and Clonezilla. You could try mkusb too.

Things to check:

1. You must clone the *whole* drive, not partitions, so /dev/mmcblk0 (not /dev/mmcblk0p1 ...) or if connected via USB: /dev/sdx (not /dev/sdx1 ...)

2a. When you clone, you must clone between drives of exactly the same size or from a smaller to a bigger drive. Two drives (cards) with the same size nominally might have different sizes. You have to check it on the byte level.

2b. If the partition table is GPT, you must fix the backup table at the end of the drive.

Otherwise the cloned card will fail.

---

### Post by rahulk7858 on 2016-11-09
@sudodus
i have taken care of these points before also and rechecked after you pointed out. i think problem is not how i am cloning. problem is my drive(second partition) is not getting mounted. As my memory cards are of same company(and same size) but different model. What i did, i brought same model memory card and cloned. BOOM it start working. but i dont think this is the solution, i need to find which file i need to change so that cloning with different model should also work.

in /boot/boot.txt we have this argument "[COLOR=#333333][FONT=sans-serif]root=/dev/mmcblk0p2[/FONT][/COLOR]". On my other model card i dont see that partition name as mmcblk0 or p1 or p2(while choosing target device in clonezilla, with same model new SD card it shows it shows as mmcblk0 other then clonezilla cloning time ,i never seen showing  this name), it will be like sdb/ sdbp1/sdbp2 or sdc/sdcp1/sdcp2.. strange thing is i dont see this name (mmcblk) while i mount this parent card to any live ubuntu. when i mount these 2(parent and non working card) to ubuntu one will become sdb other becomes sdc, it depend on which mounted first. so its clear sdc/sdb are not permanent name for partition. i tried changing boot.txt parameter to /dev/sdc or /dev/sdb but on boot kernel get in panic state and get stuck.

any clue how we can find correct partition name and is there any other place we need to change ?

---

### Post by sudodus on 2016-11-09
If the card is seen as sdb, I think it is connected via USB (which will be the case with a card reader connected via USB). If Clonezilla tries to create partitions sdbp1 sdbp2, it might be a bug (in Clonezilla). I think the p should be there only if the device is seen as mmcblk0 (or mmcblk1 ...).

But I think cloning with dd or mkusb can manage that problem. I have cloned cards, I have made images of cards and I have flashed images to cards (and the cloned copies (cards) work).

-o-

There might also be a problem with the size. Card with the same nominal size can have slightly different sizes, when checked on the byte level. You can expect problems, if you clone from a bigger drive to a smaller drive, even when they are nominally of the same size. You can check the sizes with the following command

```
sudo lsblk -bd
```

---

### Post by rahulk7858 on 2016-11-09
its looks same for both card(different model)
output for lsblk -bd
```

original
NAME MAJ:MIN RM        SIZE RO TYPE MOUNTPOINT
sda    8:0    0 53687091200  0 disk 
sdb    8:16   1 31914983424  0 disk 
sr0   11:0    1  1073741312  0 rom  

clone
rahulk@hadoopsn:~$ sudo lsblk -bd
NAME MAJ:MIN RM        SIZE RO TYPE MOUNTPOINT
sda    8:0    0 53687091200  0 disk 
sdb    8:16   1 31914983424  0 disk 
sr0   11:0    1  1073741312  0 rom  



```


Here is output with lsblk -O

```

sdb    sdb     8:16                                                                                                                                         128  0  1 Storage Device   121220130416       29.7G runni root  disk  brw-rw----         0    512      0     512     512    1 deadline     128 disk        0        0B       0B         0    0B        1        34:0:0:0   usb    1.00 Mass    
&#9500;&#9472;sdb1 sdb1    8:17  vfat   /media/rahulk/BOOT  BOOT   6E35-5356                            0x6                000c4046-01                                    128  0  1                                    128.5M       root  disk  brw-rw----         0    512      0     512     512    1 deadline     128 part        0        0B       0B         0    0B        1 sdb                           
&#9492;&#9472;sdb2 sdb2    8:18  ext4   /media/rahulk/trust trusty e139ce78-9841-40fe-8823-96a304a09859 0x83               000c4046-02                                    128  0  1                                     29.6G       root  disk  brw-rw----         0    512      0     512     512    1 deadline     128 part        0        0B       0B         0    0B        1 sdb                           
sr0    sr0    11:0                                                                                                                                          128  0  1 VMware SATA CD01 01000000000000000  1024M runni root  cdrom brw-rw----         0    512      0     512     512    1 deadline     128 rom         0        0B       0B         0    0B        1        4:0:0:0    sata   1.00 NECVMWar
rahulk@hadoopsn:~$ sudo lsblk -O
NAME   KNAME MAJ:MIN FSTYPE MOUNTPOINT        LABEL  UUID                                 PARTTYPE PARTLABEL PARTUUID                             PARTFLAGS  RA RO RM MODEL            SERIAL              SIZE STATE OWNER GROUP MODE       ALIGNMENT MIN-IO OPT-IO PHY-SEC LOG-SEC ROTA SCHED    RQ-SIZE TYPE DISC-ALN DISC-GRAN DISC-MAX DISC-ZERO WSAME WWN RAND PKNAME HCTL       TRAN    REV VENDOR
sda    sda     8:0                                                                                                                                          128  0  0 VMware Virtual S                      50G runni root  disk  brw-rw----         0    512      0     512     512    1 deadline     128 disk        0        0B       0B         0    0B        1        2:0:0:0    spi    1.0  VMware, 
&#9500;&#9472;sda1 sda1    8:1   ext4   /                        4e5d1f53-38b9-427a-b510-f285d536185d 0x83               b421aa85-01                          0x80      128  0  0                                       19G       root  disk  brw-rw----         0    512      0     512     512    1 deadline     128 part        0        0B       0B         0    0B        1 sda                           
&#9500;&#9472;sda2 sda2    8:2                                                                        0x5                b421aa85-02                                    128  0  0                                        1K       root  disk  brw-rw----         0    512      0     512     512    1 deadline     128 part        0        0B       0B         0    0B        1 sda                           
&#9492;&#9472;sda5 sda5    8:5   swap   [SWAP]                   38083e31-ac29-40fa-ba52-4a5e4fb990c1 0x82               b421aa85-05                                    128  0  0                                     1022M       root  disk  brw-rw----         0    512      0     512     512    1 deadline     128 part        0        0B       0B         0    0B        1 sda                           
sdb    sdb     8:16                                                                                                                                         128  0  1 Storage Device   121220130416       29.7G runni root  disk  brw-rw----         0    512      0     512     512    1 deadline     128 disk        0        0B       0B         0    0B        1        35:0:0:0   usb    1.00 Mass    
&#9500;&#9472;sdb1 sdb1    8:17  vfat   /media/rahulk/BOOT  BOOT   6E35-5356                            0x6                000c4046-01                                    128  0  1                                    128.5M       root  disk  brw-rw----         0    512      0     512     512    1 deadline     128 part        0        0B       0B         0    0B        1 sdb                           
&#9492;&#9472;sdb2 sdb2    8:18  ext4   /media/rahulk/trust trusty e139ce78-9841-40fe-8823-96a304a09859 0x83               000c4046-02                                    128  0  1                                     29.6G       root  disk  brw-rw----         0    512      0     512     512    1 deadline     128 part        0        0B       0B         0    0B        1 sdb                           




```

what could be missing now?

---

### Post by sudodus on 2016-11-09
*I must admit that I don't know.* Obviously the size of the two cards are exactly the same.

-o-

Sometimes a particular USB pendrive or memory card (model or individual) does not boot while other cards work, even when they look the same from the tools that we have.

If you boot with both the cloned copy and the original drive connected at the same time, one of them might be borked, because some things are written assuming a critical file is located in the other drive.

---

