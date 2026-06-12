---
title: "dual boot problems, vista won't boot"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by ar87 on 2009-12-28
[SIZE=4][SIZE=2]Ubuntu and vista dual boot was working perfectly for a year. I decided to do a clean install of 9.10. 
[/SIZE][/SIZE][LEFT][SIZE=4][SIZE=2] After the installation, before I performed any updates, I was able to boot into Ubuntu and vista without any problems. After the updates (there was a grub2 update as well) I can still see the vista option on grub.  When I choose it, I see the normal green line and it seems that vista is booting normally, but at this point the computer reboots and I am back at the grub menu. Interestingly, sometimes I get this problem but sometimes vista successfully boots. Basically, I have 50% chance of successfully booting into vista. Ubuntu boots fine every time. [/SIZE][/SIZE]
[/LEFT]
[SIZE=4][SIZE=2] I have already reinstalled Ubuntu, and again after the updates this problem comes back. I am quite sure vista is not corrupted since before updates (or when I restore vista boot loader) it boots fine.
I have uploaded the sudo bash ~/Desktop/boot_info_script*.sh, file.[/SIZE]
[/SIZE]

---

### Post by oldfred on 2009-12-28
I think this is what is contributing to your problem:

Partition  Boot         Start           End          Size  Id System
/dev/sda1    *            [COLOR=Red] 63 [/COLOR]  402,186,718   402,186,656   7 HPFS/NTFS

XP and Linux start at 63 but Vista and Win7 start at 2048.

I am not sure if running checkdisk from windows will fix it or if you have to run the Vista repairs.

see this post for more info 
[http://ubuntuforums.org/showthread.php?t=1294230](http://ubuntuforums.org/showthread.php?t=1294230)
Herman's comments posts 9 & 10:
**The reason why** we should remove the check mark is because Windows Vista and Windows 7 partitions begin in sector 2048 instead of 63, which is different from tradition and rather unconventional.

**Even if we don't know or if we forget** to remove that checkmark, GParted will take a very long time and move the entire partition to the left, to make it start in sector 63 instead of 2048.
That will tie the computer up for a long time but it won't matter much, normally Windows Vista or Windows 7 will have a slight delay the next time it tries to boot but Windows can re-adjust itself in a minute or two and reboot and will usually recover just fine.
**On some occasions** if we're unlucky, it might be necessary to use a Windows Vista or Windows 7 CD to do some automatic readjustments. The repair tool in the CD user friendly and easy to use if you have the CD, (or DVD).
If you don't have the CD or DVD, a repair-only, (non-install) .iso image is available for free and it's only a small download, [Windows Vista Recovery Disc]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") from NeoSmart Technologies, (the makers or EasyBCD).

---

### Post by presence1960 on 2009-12-28
After looking at your results.txt file I concur with oldfred. It does appear that your Vista partition is moved to the left.

---

### Post by ar87 on 2009-12-29
Thank you for your help. I did the vista "startup recovery" and so far it appears that the problem has been fixed. I was able to boot vista 5 times already without any problems.

One question though, I did not use gparted but used vista to shrink the partition (no checkmark to remove). Why did the vista partition move to the left? Thanks.

---

### Post by oldfred on 2009-12-29
Vista should not have moved the partition. I thought we recommended the Vista or Win7 partitioner to prevent this type of issue.
Maybe whatever way you installed did, but that should not have moved it either. We may never know.

Glad you got it working which is the more important thing.

---

### Post by ar87 on 2009-12-29
It seems that I was too optimistic, the problem reappeared. So far I have tried "chkdisk" and "startup repair". Anything else I can try? thanks.

---

### Post by ar87 on 2010-01-05
I returned to Grub Legacy and the problem went away. For some reason vista did not like grub2. Now, everything boots fine. For now, I will stick with grub legacy.

---

### Post by DAFFEY on 2010-01-14
I too, am experiencing this problem, and thus far various fixes (rebooting in safe mode and then allowing Vista to do a restore) fix the problem momentarily.  Within a few boots it reappears.  I noticed that after a boot with a parted magic disc I experienced the same bug. This was before I installed Ubuntu 9.10 on a new drive and newly installed Vista.  (I wanted to eliminate the disc and original version of Vista) 
What is/how do you go to the old version of Grub ?

This is on a HP CQ60 us laptop. (wish it was XP/Ubuntu)

Has anyone successfully conquered this bug? (I'm a newbie to this )

---

### Post by presence1960 on 2010-01-15
> **DAFFEY said:**
> I too, am experiencing this problem, and thus far various fixes (rebooting in safe mode and then allowing Vista to do a restore) fix the problem momentarily.  Within a few boots it reappears.  I noticed that after a boot with a parted magic disc I experienced the same bug. This was before I installed Ubuntu 9.10 on a new drive and newly installed Vista.  (I wanted to eliminate the disc and original version of Vista) 
What is/how do you go to the old version of Grub ?

This is on a HP CQ60 us laptop. (wish it was XP/Ubuntu)

Has anyone successfully conquered this bug? (I'm a newbie to this )

Let's see what you have there Daffey. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by DAFFEY on 2010-01-15
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0b49f213

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    97,434,224    97,434,162   7 HPFS/NTFS
/dev/sda2         133,482,496   156,295,167    22,812,672   7 HPFS/NTFS
/dev/sda3         156,296,385   488,392,064   332,095,680   5 Extended
/dev/sda5         156,296,448   477,837,359   321,540,912  83 Linux
/dev/sda6         477,837,423   488,392,064    10,554,642  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="1CE21A55E21A338C" TYPE="ntfs" 
/dev/sda2: UUID="3CC3D677EAE4831F" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="6b7dd356-5abf-4e43-a5f3-dacd62f02639" TYPE="ext4" 
/dev/sda6: UUID="65fc6333-0169-4c4f-9583-3caa7875e697" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 6b7dd356-5abf-4e43-a5f3-dacd62f02639
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 6b7dd356-5abf-4e43-a5f3-dacd62f02639
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=6b7dd356-5abf-4e43-a5f3-dacd62f02639 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 6b7dd356-5abf-4e43-a5f3-dacd62f02639
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=6b7dd356-5abf-4e43-a5f3-dacd62f02639 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 6b7dd356-5abf-4e43-a5f3-dacd62f02639
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=6b7dd356-5abf-4e43-a5f3-dacd62f02639 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 6b7dd356-5abf-4e43-a5f3-dacd62f02639
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=6b7dd356-5abf-4e43-a5f3-dacd62f02639 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 6b7dd356-5abf-4e43-a5f3-dacd62f02639
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6b7dd356-5abf-4e43-a5f3-dacd62f02639 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 6b7dd356-5abf-4e43-a5f3-dacd62f02639
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6b7dd356-5abf-4e43-a5f3-dacd62f02639 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1ce21a55e21a338c
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 3cc3d677eae4831f
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=6b7dd356-5abf-4e43-a5f3-dacd62f02639 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=65fc6333-0169-4c4f-9583-3caa7875e697 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  80.0GB: boot/grub/core.img
  80.0GB: boot/grub/grub.cfg
  80.0GB: boot/initrd.img-2.6.31-14-generic
  80.0GB: boot/initrd.img-2.6.31-16-generic
  80.0GB: boot/initrd.img-2.6.31-17-generic
  80.0GB: boot/vmlinuz-2.6.31-14-generic
  80.0GB: boot/vmlinuz-2.6.31-16-generic
  80.0GB: boot/vmlinuz-2.6.31-17-generic
  80.0GB: initrd.img
  80.0GB: initrd.img.old
  80.0GB: vmlinuz
  80.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============
```

```

---

### Post by oldfred on 2010-01-16
Do you have an HP or Dell with any of this software running?

HP ProtectTools and Dell Recovery Tool write into MBR
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)
[http://ubuntuforums.org/showthread.php?p=8433673](http://ubuntuforums.org/showthread.php?p=8433673)
Found out today after numerous searches the issue. I found the answer here -- I had heard dynamic disk partioning may be the cause (which I don't have) or virus software (which I removed). I have a Compaq netbook -- HP product. Turns out they have HP Recovery tools that will overwrite parts of the MBR. The thing is, I uninstalled every single piece of their recovery software, sync software, etc, cuz I didn't want any of that crap. I went into services, and lo-and -behold -- there was the hpqwmiex service running. So I disabled it, did the update-grub thing again, logged into Windows then back into Ubuntu, and all is well!
Another windows issue that caused grub2 issues.
Looks like I found the culprit. It was Norton Ghost running in the background, that I had just recently installed. I disabled it during startup through msconfig and no more trouble. Thanks for the links!

---

### Post by DAFFEY on 2010-01-16
Turns out I do have (hpqwmiex service) running per the previous post. I have removed all HP related except wireless.  Will test this and return to this post.

---

### Post by presence1960 on 2010-01-16
> **DAFFEY said:**
> Turns out I do have (hpqwmiex service) running per the previous post. I have removed all HP related except wireless.  Will test this and return to this post.

Hi Daffey. I was not ignoring you. I got your mail and your PM. I had a lot on my plate the last day. I had 3 computers to repair plus I had a lot of work at the pro shop I run. Just got home about an hour ago.

---

### Post by DAFFEY on 2010-01-16
Same issue:  Vista boot issues with Ubuntu dual boot.reasonably confident this is a HP/Vista issue with Ubuntu(grub) as relates to this laptop (Compaq CQ60-210US), but what?

---

