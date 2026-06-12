---
title: "grub2: error: unknown filesystem"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by bogoid on 2009-11-18
I had a Dell 600m w 160GB w XP Pro on it.  I backed it up w Symantec to a big USB drive.  Popped out the 160gb, popped in a new 320gb.
 
I can restore the XP to that drive and boot it and all is groovy.
 
I can install karmic i386 by itself to that drive and all is groovy.
 
But if I restore the XP Pro so it's bootable, then install karmic desktop i386 into the manually partitioned extra space I get 
 
[INDENT]error: unknown filesystem 
grub rescue>
[/INDENT] 
and el deado-meato.
 
Booting with liveCD, fdisk /dev/sda shows
 
[INDENT]/dev/sda1              1   19458    156289024     7  HPFS/NTFS
/dev/sda2  *   19459   37913    148239787+  83  Linux
/dev/sda3       37914   38913       8032500    82  Linux swap / Solaris
[/INDENT] 
as I would expect.
 
If in LiveCD I
[INDENT]sudo -s
mkdir /mnt/root
mount /dev/sda2 /mnt/root
[/INDENT]Then I can look at the installation and it looks groovy-matic.
 
If I try grub-install /dev/sda I get
[INDENT]grub-probe: error: cannot find a device for /boot/grub.
 
No path to device is specified.
 
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
[/INDENT] 
If I try grub-install --modules=ext4 /dev/sda then I get the complaint from grub-probe 4 times, then
[INDENT]You attempted a cross-disk install, but the filesystem containing /boot/grub does not support UUIDs.
[/INDENT] 
If I do blkid, then the UUID I get for /dev/sda2 (where karmic was installed) matches what's in the root=UUID=<gobbledygook> in /mnt/root/boot/grub/grub.cfg.
 
I've spent about a day and a half on this so far.  I've done this install at least three times.
 
Any bright ideas?

---

### Post by mechro on 2009-11-18
This howto mentions "If you encounter any errors, try grub-install --recheck /dev/sda" and also checking and editing the /etc/default/grub file...

[https://wiki.ubuntu.com/Grub2#Recover Grub 2 via LiveCD](https://wiki.ubuntu.com/Grub2#Recover Grub 2 via LiveCD)

---

### Post by bogoid on 2009-11-18
I just followed the steps your link suggested.
 
No change in behavior.

---

### Post by bogoid on 2009-11-18
Thinking I could work my way towards having XP's boot process let me choose to bring up karmic, I ran fixmbr off the XP recovery console.  Now it says something about not being able to find an operating system.
 
Grrr.
 
Live CD still shows what looks like a good system, but grub2 can't see it.
 
Why?

---

### Post by bogoid on 2009-11-18
I give up.
 
I'll reinstall karmic and swap as 1st & 2nd partitions, ensure that's working, then restore my XP w Symantec.
 
That should leave me with XP booting and a good karmic and swap.
 
Then I'll try to boot karmic using XP boot process.
 
We shall see.

---

### Post by oldfred on 2009-11-18
Your fixMBR may not have worked as you have to have the boot flag on windows, Ubuntu does not use the boot flag, although I have seen some strange boot systems that used the boot flag to define what partition to boot.

If you want to know how your system is booting this script runs all the commands and inspects MBR & PBR to let us find any issues.

Boot Info Script 0.34 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions 
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280) 
cd to directory saved to: 
chmod 755 boot_info_script034.sh 
sudo ./boot_info_script034.sh 
or as example if on desktop 
sudo bash ~/Desktop/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by bogoid on 2009-11-19
I reinstalled karmic desktop i386 to /dev/sda1 ~145GB, swap /dev/sda2 ~8gb.  Boots fine.
 
I resotred my Symantec XP Pro to /dev/sda3 ~160gb, growing to available space, options were: restore; resize; verify after restore; restore disk signature (what does this mean?]; activate partition.  I did NOT check restore MBR.
 
Booted to karmic, ran sudo update-grub, it found the XP partition and built grub.cfg including it.  Ran sudo grub-install --recheck /dev/sda, it seemed to run fine.
 
If I use a file browser, it finds /dev/sda2 and I can see the ntfs stuff inside as I would expect.
 
If I reboot, I get the grub menu, including the XP partition.
 
If I try to boot the XP partition, I get
[INDENT]error: no such device: 1280917180915c53
Press any key to continue...
[/INDENT]where the big hex num matches what's in grub.cfg for XP and what blkid shows for it.
 
If I edit the XP grub boot, taking out the "search --no-floppy ..." line and try to boot, I get
[INDENT]Booting a command list
error: out of disk
Press any key to continue...
[/INDENT]It seems to me that the guy(s) who is(are) setting up grub.cfg and so on from within karmic are seeing the expected stuff on the disk, but when grub2 itself runs, he's looking somewhere else.
 
If at the grub boot menu I get a command line and type ls -l, I get
[INDENT]Device hd0: Partition table
[INDENT]Partition hd0,3: Unknown filesystem
Partition hd0,2: Unknown filesystem
Partition hd0,1: Filesystem type ext2, Last modification time ..., UUID 0285...
[/INDENT][/INDENT]but all is groovy when in karmic.
 
Running fdisk shows what's expected
[INDENT][FONT=Courier New]/dev/sda1         1   18455  148239756  83  Linux[/FONT]
[FONT=Courier New]/dev/sda2     18456   19455    8032500  82  Linux swap / Solaris[/FONT]
[FONT=Courier New]/dev/sda3  *  19456   38914  156298240   7  HPFS/NTFS[/FONT]
[/INDENT]but grub2 doesn't see it.  Why is grub enumerating the partions backwards?
 
I will try the boot info script suggested in a previous post.
 
All this is complicated by the fact that my wireless is not picked up by the karmic install.  I'll chase that once I get the booting issues solved...
 
Although maybe if I got far enough to get an update on my karmic install it'll get all better.
 
Grasping at straws.

---

### Post by darkod on 2009-11-19
It might be a dumb question, but are you sure you can restore XP image on different partition/setup? If on your previous drive the system partition was the 1st, would it work on the 3rd as per your latest try?

You might need to reverse steps and restore XP first, confirm it's booting fine, and simply install karmic like you always had this 320GB drive with XP.

PS. I know you said you tried this, but another try might be worth it. And I would troubleshoot the "unknown filesystem" error rather than erasing and installing again.

---

### Post by bogoid on 2009-11-19
That's what I had done just before the first post to this thread.  I don't particularly want to go back there.  I will if I have to, but it's about a 4 hour job to get there.
 
And where I end up smells suspiciously like where I am now:  when in karmic, fdisk and the various grub2 setup guys see what's expected on the disk, but booting with grub2 sees something else.
 
Also note that the sequence
-- restore XP to healthy boot on /dev/sda1
-- install karmic desktop i386 to /dev/sda2, /dev/sda3
leads to nothing bootable: everything leads to "unknown filesystem", but where I am now at least I can easily boot into karmic.
 
I have not yet succeeded in trying to use the XP boot process to get into XP and karmic.
 
The more I think about it the more I believe grub2 is confused about where it should look on the disk for its stuff.  Maybe the boot info script will tell me something.
 
Sigh.

---

### Post by darkod on 2009-11-19
Check grub.cfg and look for the part starting 30_os-prober (probing for other OS).
There should be the enry for XP starting with menuentry Windows XP etc...
Copy that entry here, all the lines until the }.
You are right it's looking at the wrong place, lets see where is it looking.

---

### Post by bogoid on 2009-11-19
Here's the goesout from the boot_info script:
 
```
 
============================= Boot Info Summary: ==============================
 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
sda1: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  Grub1.97
    Boot sector info:  Grub1.97 is installed in the boot sector of sda1 and 
                       looks at sector 33942391 on boot drive #1 for core.img 
                       and on partition #1 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda2: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda3: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda3 has 
                       312576641 sectors, but according to the info from 
                       fdisk, it has 312596480 sectors.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2d012d00
Partition  Boot         Start           End          Size  Id System
/dev/sda1                  63   296,479,574   296,479,512  83 Linux
/dev/sda2         296,479,575   312,544,574    16,065,000  82 Linux swap / Solaris
/dev/sda3    *    312,545,280   625,141,759   312,596,480   7 HPFS/NTFS

blkid -c /dev/null: ____________________________________________________________
/dev/sda1: UUID="0285140f-62b2-47dc-9bb0-6eb6a91d4c6c" TYPE="ext4" 
/dev/sda2: UUID="fdc56fb0-3035-488b-bce1-b9fb8a86ac3b" TYPE="swap" 
/dev/sda3: UUID="1280917180915C53" LABEL="bogoso" TYPE="ntfs" 
=============================== "mount" output: ===============================
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bog/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bog)

=========================== sda1/boot/grub/grub.cfg: ===========================
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 0285140f-62b2-47dc-9bb0-6eb6a91d4c6c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###
### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
 set quiet=1
 insmod ext2
 set root=(hd0,1)
 search --no-floppy --fs-uuid --set 0285140f-62b2-47dc-9bb0-6eb6a91d4c6c
 linux /boot/vmlinuz-2.6.31-14-generic root=UUID=0285140f-62b2-47dc-9bb0-6eb6a91d4c6c ro   quiet splash
 initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
 insmod ext2
 set root=(hd0,1)
 search --no-floppy --fs-uuid --set 0285140f-62b2-47dc-9bb0-6eb6a91d4c6c
 linux /boot/vmlinuz-2.6.31-14-generic root=UUID=0285140f-62b2-47dc-9bb0-6eb6a91d4c6c ro single 
 initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda3)" {
 insmod ntfs
 set root=(hd0,3)
 search --no-floppy --fs-uuid --set 1280917180915c53
 drivemap -s (hd0) ${root}
 chainloader +1
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
=============================== sda1/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0285140f-62b2-47dc-9bb0-6eb6a91d4c6c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=fdc56fb0-3035-488b-bce1-b9fb8a86ac3b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=================== sda1: Location of files loaded by Grub: ===================

    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
================================ sda3/boot.ini: ================================
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
multi(0)disk(0)rdisk(0)partition(3)\Windows="Windows XP/2003"
=============================== StdErr Messages: ===============================
sed: can't read sda3/etc/issue: No such file or directory


```

---

### Post by darkod on 2009-11-19
In the windows menuentry I am not sure the drivemap command needs to be there.
Try this, a manual entry for XP, open 40_custom with:
sudo gedit /etc/grub.d/40_custom

At the end add:
menuentry "Windows XP (new)" {
insmod ntfs
set root=(hd0,3)
search --no-floppy --fs-uuid --set 1280917180915C53
chainloader +1
}

Save and close the file then run:
sudo update-grub

Reboot and see if the new entry work.

---

### Post by bogoid on 2009-11-19
I have a new hint and a new theory.  The hint:
 
I purged grub2 and instead put in legacy grub.
 
Using its command line stuff at boot time to try to boot XP, I got error 18, saying the BIOS would not let it read the stuff for /dev/sda3.  I guess that it's out beyond 135GB, and whatever BIOS is there has no mechanism for accessing beyond that old grotty limit.
 
So the new strategy:
 
Partition:
/dev/sda1 100MB, will be /boot
/dev/sda2 160GB, will be XP
/dev/sda3 ~145GB, will be /
/dev/sda4 ~8GB, will be swap.
 
Using LiveCD, I will partition off /dev/sda1, then restore XP to bootable, then install karmic.
 
Maybe that'll work.
 
Wish me luck.

---

### Post by darkod on 2009-11-19
That's actually very smart. You said you didn't wanna go back restoring XP to first partition so I wasn't suggesting this. :) Otherwise, as general rule, windows (especially XP) prefers to be on first partitions while linux doesn't mind being at the back of the drive. Windows does. Good luck. :)

---

### Post by bogoid on 2009-11-19
Ok.  I have a working recipe.
 
The problem was that I was using grub2 to do my booting, and grub2 uses the BIOS to do its disk i/o, and the BIOS on my machine is limited to some fraction of the full 320GB disk, possibly 135GB.
 
It may well be that there is a straightforward way to tell grub2 to use a different means than the BIOS to access the disk so it doesn't have the limitation, but I don't know of any such means.
 
That's the problem.
 
The fix was to ensure that anything I want to boot is within that early part of the disk.  So I concocted a /boot partion that's ~80MB as /dev/sda1, then my XP partition as /dev/sda2, of 160GB in my case.  After that is my / partition in /dev/sda3 of about 150GB, inaccessible to boot but grub2 doesn't need to look at it, followed by the swap partition of about 8GB.
 
So grub2 can see /boot and the XP partition, and everyone is happy.  Both boots work.
 
Before, with /dev/sda1 about 150GB or 160GB, as either karmic or XP, it could be accessed by grub2, but /dev/sda2 couldn't be, because it was beyond the 135GB (or whatever) limit..
 
I haven't played with booting at this level of detail in maybe 8 or 10 years, and I was aware then of this kind of problem, but I assumed (live and learn) that current BIOS technology had overcome such idiocies.
 
Sigh.
 
Anyway, thanks for your help.
 
I guess this thread should be marked as SOLVED if I can figure out how to do that.

---

### Post by drs305 on 2009-11-19
It could be the BIOS. I think the Grub limit was 1TB but even that was solved using the GPT module.

Speaking of solved, via the Thread Tools link at the top right of the first post.

---

