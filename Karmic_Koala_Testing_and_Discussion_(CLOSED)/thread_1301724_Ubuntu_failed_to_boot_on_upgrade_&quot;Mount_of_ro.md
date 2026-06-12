---
title: "Ubuntu failed to boot on upgrade: &quot;Mount of root filesystem failed&quot; error"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bcasanov on 2009-10-26
Hi,

Last night I upgraded to Ubuntu Karmic on my Dell Inspiron 1420 laptop.  The upgrade process went fine and when it asked me to reboot, I did.  After the BIOS screen and Grub came up, the splash with the Ubuntu logo loaded, and then, after a short while, an error message came up: 

"Mount of root filesystem failed.  A maintenance shell will now be started.  Control-D will terminate this shell and reboot the system.  Give root password for maintenance (or type Control-D to continue):"

What do I do to restore my system and be able to boot back up?  I pressed Control-D and rebooted.  I'm currently on a Live USB with Ubuntu Karmic RC and the system seems to be working fine from the live environment (sound, networking, etc., works). 

 Any help you can give me would be greatly appreciated.

---

### Post by ajgreeny on 2009-10-26
Have a look at [http://ubuntuforums.org/showthread.php?p=8156875](http://ubuntuforums.org/showthread.php?p=8156875) where it appears the mount options in fstab need editing.

---

### Post by philinux on 2009-10-26
> **bcasanov said:**
> Hi,

Last night I upgraded to Ubuntu Karmic on my Dell Inspiron 1420 laptop.  The upgrade process went fine and when it asked me to reboot, I did.  After the BIOS screen and Grub came up, the splash with the Ubuntu logo loaded, and then, after a short while, an error message came up: 

"Mount of root filesystem failed.  A maintenance shell will now be started.  Control-D will terminate this shell and reboot the system.  Give root password for maintenance (or type Control-D to continue):"

What do I do to restore my system and be able to boot back up?  I pressed Control-D and rebooted.  I'm currently on a Live USB with Ubuntu Karmic RC and the system seems to be working fine from the live environment (sound, networking, etc., works). 

 Any help you can give me would be greatly appreciated.

I would reboot into karmic, and at the shell just use this.

```
fsck /dev/sdax -v
```
If it offers to fix things hit the Y key.

It might be sda or sda1 or 2 , or sdb etc depending on your setup.

---

### Post by bcasanov on 2009-10-26
ajgreeny, thanks for the link.  Unlike the person who posted the solution, I could not boot up from the  2.6.28 kernel.  The Ubuntu logo splash screen came up, and displayed the error message:

 "One or more of the mounts listed in /etc/fstab cannot yet be mounted: 
/boot: waiting for UUID={UUID here} 
Press ESC to enter a recovery shell"

When I press ESC, I get the same error I got before, telling me to press Control-D to continue.  After pressing Control-D, I am taken back to the Ubuntu logo splash screen and the error specified above is displayed.  I again press ESC, and now I am presented with:

"General error mounting filesystems
A maintenance shell will now be started. Control-D will terminate this shell and reboot the system. Give root password for maintenance (or type Control-D to continue)
mountall start/starting
swapon: /dev/disk by-uuid...{UUID here}:
swapon failed: Device or resource busy
mountall: swapon /dev/disk/by-uuid...{UUID here} [865] terminated with status 255
mountall: Problem activating swap
mountall: Cancelled"

From there I had to do a cold shutdown and try booting again.  After several tries, I booted to the Live USB.  I haven't tried the solution offered by the poster in the link ("My fstab didn't work in 2.6.31. It didn't work with options
  defaults,data=writeback,noatime,barrier=0,extents,  journal_checksum
and worked fine when I changed them to
  errors=remount-ro,noatime,relatime,nodiratime") since I cannot duplicate booting from the 2.6.28 kernel.

---

### Post by bcasanov on 2009-10-26
philinux, thanks for your reply.  I'll try that out right now and post what happens soon.

---

### Post by magneze on 2009-10-26
Do you have /home in a separate partition?

---

### Post by bcasanov on 2009-10-26
No, I do not.

---

### Post by bcasanov on 2009-10-26
I booted into Karmic on my hard drive and entered the command that philinux gave above, with the exception that I replaced sdax with sda4 (which is my extended partition which includes the swap partition and ext3 partition, according to GParted).  The result of this command is: "Attempt to read block from filesystem resulted in short read while trying to open /dev/sda4.  Could this be a zero-length partition?"  I tried to replace sda4 with sda6 (the ext3 partition) in the command and got the following result: "os_part: clean, 226773/9500672 files, 20482709/76003480 blocks"  I did not get offer to fix anything from the commandline output.

---

### Post by philinux on 2009-10-26
What does ```
sudo fdisk -l
``` show

---

### Post by bcasanov on 2009-10-26
The commandline output of the above command is:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda4               1        9729    78148161    f  W95 Ext'd (LBA)
/dev/sda5               1         267     2144614+  82  Linux swap / Solaris
/dev/sda6             268        9729    76003483+  83  Linux

Disk /dev/sdb: 2003 MB, 2003828736 bytes
62 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Disk identifier: 0x00022fa1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1018     1956565    c  W95 FAT32 (LBA)

---

### Post by philinux on 2009-10-26
Indeed then it would be fsck /dev/sda6 -v

Erm when it fails to the shell does can you post back the exact errors. does it identify sda6?

You could try fsck from the live cd.

---

### Post by bcasanov on 2009-10-26
Indeed, it does identify sda6.  Actually, just now, I tried fsck from the terminal on a Live USB session instead of booting to the hard disk, except I added sudo to the command: sudo fsck /dev/sda6 -v.  What I got was the following, which was different from the last output I posted: 

fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
Superblock last mount time is in the future.
    (by less than a day, probably due to bad system clock last boot)  Fix<y>? yes

Superblock last write time is in the future.
    (by less than a day, probably due to bad system clock last boot).  Fix<y>? 

I stopped the command by pressing Ctrl+Z, and tried the command again.  This time, my output was:

fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext3: Device or resource busy while trying to open /dev/sda6
Filesystem mounted or opened exclusively by another program?


So it seems that the system does indeed identify /dev/sda6.

---

### Post by philinux on 2009-10-26
Let it do the fix then. Hit the Y button. You need to unmount /dev/sda6  first.

---

### Post by bcasanov on 2009-10-26
I re-entered the command, but I got this result instead:

fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
os_part: clean, 226773/9500672 files, 20482709/76003480 blocks

It does not give me the option anymore to fix anything.

---

### Post by magneze on 2009-10-26
> **bcasanov said:**
> No, I do not.Just wondering cos I had some weird stuff happen because the boot volume changed from sda7 to sda6 which messed stuff up. I think this was more to do with adding a new partition for Windows 7. The error message was exactly the same so check your /etc/fstab - make sure the disks are called the right things.

---

### Post by bcasanov on 2009-10-26
This is what is in my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=927f2970-14be-4b98-b65f-286b6c23af23 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=2794a001-b25c-4bfb-8dd5-0c880d2716ec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
UUID=95b5b7f2-95ec-4aaf-ae9f-d9ea528b30ec  /boot ext3 defaults,relatime 0 0
none /proc/bus/usb usbfs devgid=116,devmode=664 0 0
devpts /dev/pts devpts (rw,noexec,nosuid,gid=5,mode=620)

---

### Post by magneze on 2009-10-26
Try doing:

sudo blkid

and checking those UUID values against what you have in fstab .. maybe there's a discrepancy. :confused:

---

### Post by bcasanov on 2009-10-26
The output of that command is:

/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="c1e6af3d-8c62-4d64-a979-92b2f055c0fc" TYPE="ext3" 
/dev/sda5: UUID="2794a001-b25c-4bfb-8dd5-0c880d2716ec" TYPE="swap" 
/dev/sda6: LABEL="os_part" UUID="927f2970-14be-4b98-b65f-286b6c23af23" TYPE="ext3" 
/dev/sdb1: LABEL="" UUID="D174-900E" TYPE="vfat"

I don't know if I am seeing this wrong, but it seems that /dev/sda1 in fstab and /dev/sda6 from the blkid output have the same UUID value.

---

### Post by oooooops on 2009-10-26
> **magneze said:**
> Try doing:

sudo blkid

and checking those UUID values against what you have in fstab .. maybe there's a discrepancy. :confused:

I think what's being discussed is the same issue I am facing.  

I checked the output of blkid against my FSTAB and don't see any differences.

---

### Post by bcasanov on 2009-10-26
I don't know if this is relevant or not, but I have an encrypted home folder that I had migrated all my home data to in Jaunty before upgrading to Karmic.  I don't think that having an encrypted home folder in Jaunty when upgrading to Karmic should be an issue, since I had the same setup on my Acer Aspire One netbook and I had no problem booting up when I upgraded it to Karmic.

---

### Post by bcasanov on 2009-10-27
Well, I've decided to do a fresh install of Karmic instead of an upgrade, since I have all of my files backed up.  The fresh install succeeded without any problems.  Thanks for all the help you've all given with this issue.

---

### Post by raygj on 2009-10-27
hi i had the same problem (dropping to busybox("Mount of root filesystem failed" error).
I rebooted into my previous running kernel.started up "Synaptic Package Manager" selected "linux-source-2.6.31" for "install" 
& also selected "linux-headers-2.6.31-14" for "reinstall" and "linux-image-2.6.31-generic" for "reinstallation".selected "apply" . After "Synaptic" was finished reinstalling,I rebooted/logged into my desktop using the latest kernel(2.6.31-14) with no errors.

---

### Post by grandtoubab on 2009-10-27
It sounds like a problem happened in september
  	 	 	 	 	 	  [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/278429](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/278429)
[URL="https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/278429"]
[/URL]
    	 	 	 	 	 	  :/etc/default# cat rcS
   	 	 	 	 	 	  #  
 # /etc/default/rcS  
 #  
 # Default settings for the scripts in /etc/rcS.d/  
 #  
 # For information about these variables see the rcS(5) manual page.  
 #  
 # This file belongs to the "initscripts" package.  
 

 TMPTIME=0  
 SULOGIN=no  
 DELAYLOGIN=no  
 [COLOR=Red]#changer utc de no a yes pour eviter l'obligation fsck au boot  [/COLOR]
 [COLOR=Red]UTC=yes[/COLOR]  
 VERBOSE=no  
 FSCKFIX=no  
 RAMRUN=yes  
 RAMLOCK=yes

---

