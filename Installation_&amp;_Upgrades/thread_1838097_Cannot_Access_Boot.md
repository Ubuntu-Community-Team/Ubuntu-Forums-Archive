---
title: "Cannot Access Boot"
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by Maya_Iz on 2011-09-03
I upgraded from 9.04 to 11.04 and have a Windows Vista Boot already installed. When I start my PC, I get a black screen that says:

> GNU GRUB version 1.99~rc1-13ubuntu3

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>

When I type "root (hd0,5)", my Linux partition, I get "error: unknown command 'root'."

I tried to run Boot-Repair on the system to correct the boot, however, I got an error message: "System program problem detected."

HELP!

Overview of current system is the following:
```
                                                                     
                                                                     
                                                                     
                                             
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /menu.lst /boot.ini /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /grldr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *      3,074,048   235,805,749   232,731,702   7 NTFS / exFAT / HPFS
/dev/sda3         235,818,196   488,392,064   252,573,869   5 Extended
/dev/sda5         235,818,198   478,046,204   242,228,007  83 Linux
/dev/sda6         478,046,268   488,392,064    10,345,797  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        14A6273FA627212A                       ntfs       TOSHIBA SYSTEM VOLUME
/dev/sda2        365A58295A57E3E1                       ntfs       SQ004740V04
/dev/sda5        a71fb74d-1fa3-4305-afbc-60b171c0f419   ext3       
/dev/sda6        a3c3c581-d526-47d7-83be-24171e81b02a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda2/menu.lst: ================================

--------------------------------------------------------------------------------
timeout 0
default 0
title grub2
find --set-root /grub/core.img
kernel /grub/core.img
boot--------------------------------------------------------------------------------

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=0
default=c:\grldr.mbr
[operating systems]
C:\grldr.mbr="Grub4Dos"--------------------------------------------------------------------------------

========================== sda2/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
pxe detect
configfile
default 0
timeout 1
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             menu.lst                                       0

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=a71fb74d-1fa3-4305-afbc-60b171c0f419 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a3c3c581-d526-47d7-83be-24171e81b02a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 174.707209587 = 187.590437888  boot/grub/core.img                             1
 136.220450401 = 146.265594880  boot/grub/stage2                               4
 136.312785149 = 146.364738560  boot/initrd.img-2.6.28-19-generic              3
 136.305636406 = 146.357062656  boot/initrd.img-2.6.31-22-generic              4
 136.215010643 = 146.259753984  boot/vmlinuz-2.6.28-19-generic                 2
 136.229495049 = 146.275306496  boot/vmlinuz-2.6.31-22-generic                 4
 139.942202568 = 150.261795840  boot/vmlinuz-2.6.38-8-generic                  4
 139.942202568 = 150.261795840  vmlinuz                                        4

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  6d 69 6c 6c 69 73 65 63  6f 6e 64 73 22 3e 0a 09  |milliseconds">..|
00000010  09 09 09 09 09 09 09 3c  64 65 66 61 75 6c 74 20  |.......<default |
00000020  74 79 70 65 3d 22 69 6e  74 22 20 76 61 6c 75 65  |type="int" value|
00000030  3d 22 30 22 2f 3e 0a 09  09 09 09 09 09 09 09 3c  |="0"/>.........<|
00000040  6c 6f 6e 67 64 65 73 63  3e 49 67 6e 6f 72 65 20  |longdesc>Ignore |
00000050  6d 75 6c 74 69 70 6c 65  20 70 72 65 73 73 65 73  |multiple presses|
00000060  20 6f 66 20 74 68 65 20  5f 73 61 6d 65 5f 20 6b  | of the _same_ k|
00000070  65 79 20 77 69 74 68 69  6e 20 40 64 65 6c 61 79  |ey within @delay|
00000080  20 6d 69 6c 6c 69 73 65  63 6f 6e 64 73 2e 3c 2f  | milliseconds.</|
00000090  6c 6f 6e 67 64 65 73 63  3e 0a 09 09 09 09 09 09  |longdesc>.......|
000000a0  09 3c 2f 6c 6f 63 61 6c  5f 73 63 68 65 6d 61 3e  |.</local_schema>|
000000b0  0a 09 09 09 09 09 09 3c  2f 65 6e 74 72 79 3e 0a  |.......</entry>.|
000000c0  09 09 09 09 09 09 3c 65  6e 74 72 79 20 6e 61 6d  |......<entry nam|
000000d0  65 3d 22 74 69 6d 65 6f  75 74 22 20 6d 74 69 6d  |e="timeout" mtim|
000000e0  65 3d 22 31 32 34 30 32  33 36 36 31 37 22 20 74  |e="1240236617" t|
000000f0  79 70 65 3d 22 73 63 68  65 6d 61 22 20 73 74 79  |ype="schema" sty|
00000100  70 65 3d 22 69 6e 74 22  20 6f 77 6e 65 72 3d 22  |pe="int" owner="|
00000110  67 6e 6f 6d 65 22 3e 0a  09 09 09 09 09 09 09 3c  |gnome">........<|
00000120  6c 6f 63 61 6c 5f 73 63  68 65 6d 61 20 6c 6f 63  |local_schema loc|
00000130  61 6c 65 3d 22 43 22 20  73 68 6f 72 74 5f 64 65  |ale="C" short_de|
00000140  73 63 3d 22 22 3e 0a 09  09 09 09 09 09 09 09 3c  |sc="">.........<|
00000150  64 65 66 61 75 6c 74 20  74 79 70 65 3d 22 69 6e  |default type="in|
00000160  74 22 20 76 61 6c 75 65  3d 22 32 30 30 22 2f 3e  |t" value="200"/>|
00000170  0a 09 09 09 09 09 09 09  3c 2f 6c 6f 63 61 6c 5f  |........</local_|
00000180  73 63 68 65 6d 61 3e 0a  09 09 09 09 09 09 3c 2f  |schema>.......</|
00000190  65 6e 74 72 79 3e 0a 09  09 09 09 09 09 3c 65 6e  |entry>.......<en|
000001a0  74 72 79 20 6e 61 6d 65  3d 22 74 69 6d 65 6f 75  |try name="timeou|
000001b0  74 5f 65 6e 61 62 6c 65  22 20 6d 74 69 6d 00 fe  |t_enable" mtim..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 27 1b 70 0e 00 fe  |..........'.p...|
000001d0  ff ff 05 fe ff ff 29 1b  70 0e 84 dd 9d 00 00 00  |......).p.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by dino99 on 2011-09-03
watch the grub guide link below

---

### Post by Hakunka-Matata on 2011-09-03
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Reinstall Grub, see Section 12.1.X

You will need a LiveCD for these procedures, I noticed you upgraded so you may not have one.  A LiveCD/USB is required though, so download your .iso and burn it to CD or better yet USB first.

Your Linux installation is on sda5

Reinstall Grub using Section 12.1.2 [ Copy LiveCD Files]("https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files"). 
if that doesn't fix your installation then use Section 12.1.3 [Copy Partition Files]("https://help.ubuntu.com/community/Grub2#Copy_Partition_Files").
if that doesn't fix your installation then use Section 12.1.4 [ChRoot]("https://help.ubuntu.com/community/Grub2#ChRoot")
if that doesn't fix your installation then use Section 12.1.5 [Purge & Reinstall]("https://help.ubuntu.com/community/Grub2#Purge_.26_Reinstall")  

sdX for you is sda
sdXY for you  is sda5

```
sudo grub-install --boot-directory=/mnt/boot /dev/sdX
# you're using 11.04 so use the above command and NOT 

sudo grub-install --root-directory=/mnt /dev/sdX
# which is used for earlier (than 11.04) releases,
# where both commands are given as possibility

```The very first procedure may work, however Purgre and Reinstall would be the best choice for you, since you have some residual files leftover from 9.10's earlier Grub version.  It's more complicated, but just copy and paste the commands, should work fine.  And you can always just 'do it again", it's only messing with the Grub function, not your Linux OS.

---

### Post by Maya_Iz on 2011-09-03
First two options did not work, so I tried the "Purge and Reinstall" option. Everything went well until I ran an "sudo apt-get update". The overall output:

```
E: Some index files failed to download. They have been ignored, or old ones used instead.
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# apt-get purge grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-common* grub-gfxpayload-lists* grub-pc*
0 upgraded, 0 newly installed, 3 to remove and 239 not upgraded.
After this operation, 7,803 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 134322 files and directories currently installed.)
Removing grub-gfxpayload-lists ...
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
/usr/bin/mandb: can't write to /var/cache/man/5719: No space left on device
Processing triggers for install-info ...
Processing triggers for ureadahead ...
root@ubuntu:/# apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  grub-common grub-gfxpayload-lists
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-gfxpayload-lists grub-pc
0 upgraded, 3 newly installed, 0 to remove and 239 not upgraded.
Need to get 2,985 kB of archives.
After this operation, 7,803 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  grub-common grub-pc grub-gfxpayload-lists
Install these packages without verification [y/N]? y
Err http://us.archive.ubuntu.com/ubuntu/ natty/main grub-common amd64 1.99~rc1-13ubuntu3
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ natty/main grub-pc amd64 1.99~rc1-13ubuntu3
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com/ubuntu/ natty/main grub-gfxpayload-lists amd64 0.2
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.99~rc1-13ubuntu3_amd64.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.99~rc1-13ubuntu3_amd64.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub-gfxpayload-lists/grub-gfxpayload-lists_0.2_amd64.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by Hakunka-Matata on 2011-09-03
and what state has this left your machine in?  You're writing here, from what liveCD?  What's next?

---

### Post by Maya_Iz on 2011-09-03
I'm in the live CD but afraid to reboot. What should I do?

---

### Post by Hakunka-Matata on 2011-09-03
> **Maya_Iz said:**
> I'm in the live CD but afraid to reboot. What should I do?
I say relax, that's always a good start.  
Just reboot the machine, if grub doesn't work right, it can be fixed.

And if you want to, try reinstalling Grub again, it can't hurt anything, 
the failures you posted may have botched the install, or maybe just installed with not quit all the latest updates.

---

### Post by Maya_Iz on 2011-09-03
I rebooted.

Black screen:
```
error: file not found.

grub rescue>
```

---

### Post by Maya_Iz on 2011-09-03
And how do I solve the "Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)" problem?

---

### Post by Hakunka-Matata on 2011-09-03
well i'm not sure, it looks like the repository wanted isn't online or having some other problem.
Change the main repository in updates, settings.  Looks like it couldn't find the repository it wanted, point to a different repository.

---

### Post by Maya_Iz on 2011-09-03
OK. I went to Update Manager->Settings, Ubuntu Software tab, Download from: Other-> Select Best Server. It tested a series of download servers and suggested a different server. I selected that server, reran an apt-get update. Same output.

---

### Post by Hakunka-Matata on 2011-09-03
[http://ubuntuforums.org/archive/index.php/t-1476136.html](http://ubuntuforums.org/archive/index.php/t-1476136.html)
That's a link to somebody else having the same or similar problem.  Time for me to go to sleep.  Good luck,

---

### Post by YannBuntu on 2011-09-05
Hello

Below I guess you were just changing the server of your live-CD:

> **Maya_Iz said:**
> OK. I went to Update Manager->Settings, Ubuntu Software tab, Download from: Other-> Select Best Server. It tested a series of download servers and suggested a different server. I selected that server, reran an apt-get update. Same output.

But the server problem you had was in the chroot, so you need to change the server of your installed Ubuntu.

To change the server of your installed Ubuntu, please :
- first burn a [Super-Grub-Disk]("http://www.supergrubdisk.org/2010/08/20/sg2d-downloads-20100820/"), boot on it. It should allow you to boot on the Ubuntu that is on your disk.
- then change the server (take "Best server")
- Then you can reinstall GRUB by the following command:
sudo grub-install grub-pc
- a blue window will appear, use Tab, Space and Enter keys to put a star behind "sda" and validate.
- run the following command just to check your systems are recognized by GRUB:
sudo update-grub

This should finish the purge&reinstall procedure advised by Hakunka-Matata.

---

### Post by Maya_Iz on 2011-09-06
Another grand failure. I boot from the disk, choose to detect and OS, then choose to load my Linux boot. It starts to boot then hangs after five lines of ```
request-module:runaway loop modprobe binfmt-464c
```

This is becoming beyond frustrating to the point that I am ready to toss this entire machine out of the window. I'd literally reimage if only I didn't have much needed files on the system.

Please help!

---

### Post by YannBuntu on 2011-09-06
after googling a little, it seems like a 32/64 bits issue...

If I were you, I would just :
- backup my data on an external drive
- reinstall Ubuntu above the old one (without formatting , so that you keep the /home)

---

