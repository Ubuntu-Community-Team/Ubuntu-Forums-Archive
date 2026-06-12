---
title: "New Ubuntu Server 20.04 LTS install will not boot"
date: 2020-05-19
forum: Installation &amp; Upgrades
---

### Post by oshman on 2020-05-19
First I want to preface that this is an old box.  The primary drive finally failed and while my plans are to build something new, I need a short term cheap solution until I can put everything together.  Meanwhile, this BIOS/MB doesn't support UFI so it's got to be a legacy install.  I don't know if this is the issue that I'm running into or not.  The replacement drive is just a new version of what failed (WD Caviar 80GB)...

All of the drives are disconnected except for the new boot drive...

I have the Ubuntu server install image on USB, booting into that and installing to the single system drive I will configure it as the boot drive, then (usually) configure an 8GB swap, a 500MB ext4 /boot partition, and then everything else as ext4 / (root).  I have also tried letting it just configure itself and use the entire drive.  Also opting to just assign it as a boot device and create only the swap and / (root) partitions.  In every case it reboots to the message: "No bootable device -- Insert boot disk and press any key"

All of my searches seem like it's trying to boot UEFI but this box doesn't support that option.  Yet when the installer is starting up, I see the little icons at the bottom that look like some box/drive partitions "=" the little man in the circle and there are mentions that those mean it's booting into legacy mode.

I next tried using the Boot-Repair tool to reset the easy way (returns an error) then reset and reinstall grub using the advanced options and point it at the actual 20.04 install.  While it doesn't give me any errors with the advanced repair, it still doesn't resolve the no bootable device error.

So as of right now, the most recent drive config is to have just the bootable, swap, and / (root) partitions, then I dumped the config report from Boot-Repair and that's at [http://paste.ubuntu.com/p/ZMVKb5hGB9/](http://paste.ubuntu.com/p/ZMVKb5hGB9/)

Is anyone able to take a look and see if they can identify what's gone sideways I would be most appreciative?

Thanks in advance
Osh

---

### Post by oshman on 2020-05-20
I installed the Ubuntu 20.04 Desktop and it booted up just fine.  So I ran Boot-Repair and generated a report from that install as well (shared here at [http://paste.ubuntu.com/p/vbwYgTSv7D/](http://paste.ubuntu.com/p/vbwYgTSv7D/))

When I look at it, the Desktop install creates an sda1 that is fat32 and has boot flag set.  The server install shows sda1 as a BIOS boot partition containing Grub's core.img.  The partition table looks different between the two, but that could be because the Desktop installed an extended partition and it looks like the server install did not.  What do these differences mean and how can I go about getting Server installed (or repaired) so it can boot?

---

### Post by oshman on 2020-05-21
I never got the direct issue figured out, but I was able to finally get 20.04 Server running.  Ubuntu 16.04 LTS installed fine on this box initially so I started with that again.  Then upgraded to 18.04 then 20.04.  For whatever reason, the boot configuration that 16.04 installs works fine and is maintained through the upgrades while 18.04 and 20.04 can't install a good boot partition on this box...

<edit> Not sure if it matters, but I generated a report from Boot-Repair for the current install: [http://paste.ubuntu.com/p/RMY6hW45PG/](http://paste.ubuntu.com/p/RMY6hW45PG/)

For future reference, if this ends up helping anyone else, here are the summaries from the original 20.04 install and 20.04 as upgraded from 16.04

_**<--snip 20.04 install -->**_
============================= Boot Info Summary: ===============================


 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt3)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdf.


sda1: __________________________________________________________________________


    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 


sda2: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sda3: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________
Disk /dev/sda: 74.5 GiB, 80000000000 bytes, 156250000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1   156,249,999   156,249,999  ee GPT




GUID Partition Table detected.


Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1                 2,048         4,095         2,048 BIOS Boot partition
/dev/sda2                 4,096    16,781,311    16,777,216 Swap partition (Linux)
/dev/sda3            16,781,312   156,246,015   139,464,704 Data partition (Linux)


Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set




_**<--snip 20.04 install -->**_


_**<--snip 20.04 upgraded from 16.04 to 18.04 to 20.04 install -->**_
============================= Boot Info Summary: ===============================


 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdf.


sda1: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.cfg /grub/i386-pc/core.img


sda2: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sda3: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04 LTS
    Boot files:        /etc/fstab

============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________
Disk /dev/sda: 74.5 GiB, 80000000000 bytes, 156250000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *          2,048       976,895       974,848  83 Linux
/dev/sda2             976,896    16,601,087    15,624,192  82 Linux swap / Solaris
/dev/sda3          16,601,088   156,248,063   139,646,976  83 Linux



[U][B]<--snip 20.04 upgraded from 16.04 to 18.04 to 20.04 install -->
[/B][/U]

---

