---
title: "Boot Problem 10.10"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by lex0429 on 2011-01-28
Couldn't find a definitive fix that worked so maybe someone else has an idea what is going on. I dual boot 10.10 with XP on my laptop. All was good, last night i did some updates, one of which i think was a Kernel update and this morning i was working fine, used my Verizon data card and was doing some work then had some weird errors opening Gedit and after i rebooted i was prompted with the following screen (see attachment)

XP continues to work fine as of now. Any ideas how to repair this?

Thanks in advance.

---

### Post by Rubi1200 on 2011-01-28
Hi,
this is what you need to do please:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by lex0429 on 2011-01-28
Thanks for the quick reply.

Seems to be stuck on "Searching sda6 for information" (sda6 is my ubuntu partition)

I get this error when i try to mount that partition when running the live version


Unable to Mount 25GB Filesystem
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed:
An operation is already pending

---

### Post by Rubi1200 on 2011-01-28
We have seen this before that if there is file-system damage (not saying there is) that it can be a problem trying to run diagnostics.

Here is what I suggest:

download, burn to CD, and run as a LiveCD Slax:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

Unlike many distros, Slax does not try and auto-mount partitions.

Then run the boot info script as described before with one difference; you need to use ```
sudo su
``` and then run the script.

---

### Post by lex0429 on 2011-01-28
Sorry but having trouble running the script in Slax

running **sudo su** produces **bash: sudo: command not found**

running **su boot_info_script055.sh** produces **unknown id: boot_info_script055.sh**

---

### Post by Rubi1200 on 2011-01-28
In the terminal, type```
 sudo su
```This should leave you with a root prompt (it will say root@)

Then copy/paste this into the terminal:

```
su ~/Desktop/boot_info_script*.sh
```Make sure the file is on the desktop before running the command.

(I think this was it, am unable to double-check for you right now; will do soon)

---

### Post by lex0429 on 2011-01-28
i get root@slax when I launch the terminal but regardless here is what happens

---

### Post by lex0429 on 2011-01-28
Just noticed that looking at dmesg | tail there is this line after i tried to mount the drive

EXT3-fs: sda6 couldn't mount because of unsupported optional features (240)

The file system is EXT 4 though, not 3

not sure if that helps at all

---

### Post by Rubi1200 on 2011-01-28
Okay, my mistake (just fired up Slax to test it)

At the root prompt, run this:
```
bash ~/Desktop/boot_info_script*.sh
```

Should work now and give a RESULTS.txt. on the desktop. Then post the contents back here.

---

### Post by petrus250 on 2011-01-28
if anything like this happens, you can always try 
'startx'
it may not work but it is worth a try...

---

### Post by lex0429 on 2011-01-28
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x908a8c03

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    16,779,263    16,777,216   7 HPFS/NTFS
/dev/sda2          16,787,925    88,469,954    71,682,030   7 HPFS/NTFS
/dev/sda3         180,618,795   234,436,544    53,817,750   5 Extended
/dev/sda5         229,440,393   234,436,544     4,996,152  82 Linux swap / Solaris
/dev/sda6         180,618,921   229,440,329    48,821,409  83 Linux
/dev/sda4          88,469,955   180,618,794    92,148,840  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4051 MB, 4051697152 bytes
255 heads, 63 sectors/track, 492 cylinders, total 7913471 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000642b9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        24E0F467E0F4409A                       ntfs       Recovery                      
/dev/sda2        EE3C74F23C74B6E5                       ntfs                                     
/dev/sda4        6f4469fe-c90b-43d9-9ee1-fd32fd413d65   ext3                                     
/dev/sda5        b671ad8b-f1a6-4feb-8421-b493f049d74b   swap                                     
/dev/sda6        2a41a5fc-a997-46c6-8858-97d585f9cc6e   ext4                                     
/dev/sdb1        6E81-6D8E                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw,si=90543e1e,xino=/mnt/live/memory/xino/.aufs.xino,nowarn_perm)
/dev/sr0         /mnt/sr0                 udf        (ro,noatime)
/dev/sda1        /mnt/sda1                fuseblk    (rw,noatime,allow_other,blksize=4096)
/dev/sda2        /mnt/sda2                fuseblk    (rw,noatime,allow_other,blksize=4096)
/dev/sda4        /mnt/sda4                ext3       (rw,noatime)
/dev/sdb1        /mnt/sdb1                vfat       (rw,noatime,quiet,umask=0,check=s,shortname=mixed)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/initrd.gz
    .0GB: boot/vmlinuz
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file


```

---

### Post by Rubi1200 on 2011-01-28
Thanks for the results.

Okay, so let's try and repair the file-system if possible.

Start by running this in the Slax terminal:

```
e2fsck -C0 -p -f -v /dev/hda6
```

If this returns errors (quite likely), then run this:

```
e2fsck -f -y -v /dev/hda6
```

I assume sda6 (hda6 is what Slax calls it) is the Ubuntu partition?

Is sda4 your home partition?

If this works, reboot without the CD and hopefully you will be back in Ubuntu.

---

### Post by lex0429 on 2011-01-28
I believe 4 just has some data saved on it, yes 6 is the ubuntu partition.

see screen shot, both commands produced the same result.

---

### Post by Rubi1200 on 2011-01-28
The only thing I can think of now is to try and run the command suggested.

But first, run this and post the output:

```
fdisk -lu
```

---

### Post by lex0429 on 2011-01-28
I ended up running **sudo fsck.ext4 -v /dev/sda6** from within the Ubuntu live version. That found a ton of errors on the drive and I just let it fix everything it found. After a reboot and a drive check on startup I made it into Ubuntu just fine and it looks like everything is here. I'll just backup some files i need and then if this happens again I wont worry much. Sure the drive will have more problems soon.


Thank you very much for your help, I really appreciate the quick, detailed responses. Have a great weekend.

---

### Post by Rubi1200 on 2011-01-28
Excellent! This is great news.

You are more than welcome for the help and I am glad you got things working again :-)

Please mark this thread Solved using the Thread Tools near the top of the page.

Have a great weekend too.

---

