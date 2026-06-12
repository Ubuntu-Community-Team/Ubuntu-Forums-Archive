---
title: "windows 7 bootloader missing after ubuntu 9.10 install"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by yon2501 on 2009-12-17
i just installed ubuntu on a machine running windows 7 and for some reason grub wont load so it boots directly to the windows 7 bootloader but it says its corrupted, i checked my grub install manually and in terminal and stage1 is missing, what do i need to do to get windows 7 and ubuntu to play nice?

---

### Post by phillw on 2009-12-17
Hi, you'll want to be over here to get Win & Ubuntu 'playing' together --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Regards,

Phill.

---

### Post by presence1960 on 2009-12-17
> **yon2501 said:**
> i just installed ubuntu on a machine running windows 7 and for some reason grub wont load so it boots directly to the windows 7 bootloader but it says its corrupted, i checked my grub install manually and in terminal and stage1 is missing, what do i need to do to get windows 7 and ubuntu to play nice?

What version of Ubuntu are you running?

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by yon2501 on 2009-12-17
is there any way to force grub to take control, because i dont have a win7 disc on hand atm and even after taking the steps to recover grub2 for 9.10 the 7 bootloader still takes first priority.

---

### Post by presence1960 on 2009-12-17
> **yon2501 said:**
> is there any way to force grub to take control, because i dont have a win7 disc on hand atm and even after taking the steps to recover grub2 for 9.10 the 7 bootloader still takes first priority.

see [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"). you can download an iso and burn it to CD which will allow you to run ONLY Recovery Console.

Run the script also please.

---

### Post by yon2501 on 2009-12-17
thanks! ill try this when i get home.

---

### Post by yon2501 on 2009-12-17
ok so heres whats happening now, ubuntu is installed side by side with win7 but still grub wont actually boot, the computer simply boots directly into windows 7. btw its windows7 64bit and ubuntu 9.10 64bit

---

### Post by darkod on 2009-12-17
If you have more than one hdd maybe grub2 was installed on the other one. And if the hdd which is first in BIOS boot order has windows bootloader it will load windows straight away.

---

### Post by kansasnoob on 2009-12-17
Please post the results of the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by yon2501 on 2009-12-17
there are 2 harddrives a tb sata and a 160 ide, nothing is installed on the ide both windows and grub bootloaders are installed on the sata. windows has about 800 gigs and the rest i gave to ubuntu cept for 4 gigs of swap all on the sata. i shurnk the windows partition under win7 and set up the partition table with gparted on the live cd. am i missing something, i installed how i always do my dual boots, install windows, shrink in win, format in ubuntu, then install ubuntu. what else do i need to do to get dual booting working with windows7?

---

### Post by OrangeCrate on 2009-12-17
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

---

### Post by darkod on 2009-12-17
> **yon2501 said:**
> there are 2 harddrives a tb sata and a 160 ide, nothing is installed on the ide both windows and grub bootloaders are installed on the sata. windows has about 800 gigs and the rest i gave to ubuntu cept for 4 gigs of swap all on the sata. i shurnk the windows partition under win7 and set up the partition table with gparted on the live cd. am i missing something, i installed how i always do my dual boots, install windows, shrink in win, format in ubuntu, then install ubuntu. what else do i need to do to get dual booting working with windows7?

I am beginning to suspect grub2 is actually on your IDE drive. It doesn't need to have OS installed on it but the bootloader can end up there.
I guess the easiest way is to download the script in my signature, move it on desktop for example, and run it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file. Look in the file and on top it will say which bootloaders are installed on which drive. If you want to, copy the content here and wrap it in CODE tags for easier reading (with the text selected hit the # button in the toolbar above).

---

### Post by presence1960 on 2009-12-17
> **kansasnoob said:**
> Please post the results of the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

To the OP: That is twice now you have been asked to download and run the boot info script. Why aren't you doing it? It would be beneficial to those trying to help you and yourself if we saw exactly what you have in the way of setup and boot process. My experience in here shows me that what people say they have on their machine and what they actually have as reported by the boot info script are a lot of times not the same. I believe this is usually non-intentional but nevertheless it happens quite often. If you aren't going to run the script then I can not attempt to help you on conjecture.

EDIT 3 times now. I, kansasnoob and now Darko have asked.

---

### Post by yon2501 on 2009-12-17
ok here are the results

> ============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000ca3d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 1,851,119,706 1,851,119,644   7 HPFS/NTFS
/dev/sda2    *  1,851,121,755 1,945,712,474    94,590,720  83 Linux
/dev/sda3       1,945,712,475 1,953,520,064     7,807,590   5 Extended
/dev/sda5       1,945,712,538 1,953,520,064     7,807,527  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   312,576,802   312,576,740   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="1A046AAC046A8A99" TYPE="ntfs" 
/dev/sda2: UUID="e7312706-4b51-4a28-aace-29b904b8beac" TYPE="ext4" 
/dev/sda5: UUID="bfd2007d-1148-4a19-993f-8ff8cce34d35" TYPE="swap" 
/dev/sdb1: UUID="F84875BC487579E8" TYPE="ntfs" 

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


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root=(hd0,2)
search --no-floppy --fs-uuid --set e7312706-4b51-4a28-aace-29b904b8beac
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
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set e7312706-4b51-4a28-aace-29b904b8beac
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e7312706-4b51-4a28-aace-29b904b8beac ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set e7312706-4b51-4a28-aace-29b904b8beac
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=e7312706-4b51-4a28-aace-29b904b8beac ro single 
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
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set f84875bc487579e8
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=e7312706-4b51-4a28-aace-29b904b8beac /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=bfd2007d-1148-4a19-993f-8ff8cce34d35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 947.7GB: boot/grub/grub.cfg
 947.7GB: boot/initrd.img-2.6.31-14-generic
 947.7GB: boot/vmlinuz-2.6.31-14-generic
 947.7GB: initrd.img
 947.7GB: vmlinuz

---

### Post by darkod on 2009-12-17
See, there's your problem. You are not seeing grub because your 160GB drive is first choice in your BIOS boot options. You should make your 1TB drive first choice if you want to see grub.
And win7 doesn't boot properly because it seems it's boot process is broken. You have the boot files /bootmgr and /boot/BCD on /dev/sdb1 while they should probably be on /dev/sda1, your win7 system partition.

---

### Post by presence1960 on 2009-12-17
You have a strange set up for Windows 7. Half the boot files are on sdb1 and the other half are on sda1. Exactly which of those is the windows installation.

Also you are booting straight to windows because sdb is most likely set to boot before sda in BIOS. If you set sda to boot before sdb GRUB will take over. See here from your output:

```
============================= Boot Info Summary: ==============================

[COLOR="Red"]=> Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive
in partition #2 for /boot/grub.[/COLOR]
[COLOR="DeepSkyBlue"]=> Windows is installed in the MBR of /dev/sdb[/COLOR]
```
 Do you see why you are booting right to windows?

Now in order to get your windows fixed we need the answer to the million $$ questions. Why are your boot files split up. Usually when windows creates a boot partition it labels that partition as System Reserved. It did not do that this time. See here:

blkid -c /dev/null: __________________________________________________ __________

/dev/loop0: TYPE="squashfs"
[COLOR="Red"]/dev/sda1: UUID="1A046AAC046A8A99" TYPE="ntfs"[/COLOR]
/dev/sda2: UUID="e7312706-4b51-4a28-aace-29b904b8beac" TYPE="ext4"
/dev/sda5: UUID="bfd2007d-1148-4a19-993f-8ff8cce34d35" TYPE="swap"
[COLOR="Red"]/dev/sdb1: UUID="F84875BC487579E8" TYPE="ntfs" [/COLOR]

The second question : which partition sda1 or sdb1 is actually your windows partition?

I tend to think it is sda1 because you have sdb1 and it has a boot flag. Something is not exactly right though. Maybe if you can answer those questions we can get windows to boot.

---

### Post by presence1960 on 2009-12-17
LOL Darko I posted mine and then saw your reply. We both see the same thing!

---

### Post by darkod on 2009-12-17
> **presence1960 said:**
> LOL Darko I posted mine and then saw your reply. We both see the same thing!

Better both of us than nobody. :)

---

### Post by yon2501 on 2009-12-17
yeah im a bit confused about how it happened and i cant switch the drive boot order in bios for some reason. and i have no idea why the ide has any 7 files at all when i installed i installed only on the sata, i had to manually tell 7 to show the ide because by default it didnt. since i reformatted i havnt done anything with the ide i was planning just to use it as storage but havnt started yet.

---

### Post by darkod on 2009-12-17
Not being able to switch the order might be the reason. Windows is very picky about that, it installs the bootloader (and boot files) to the disk which is set as first option, even if windows system partition is not on that disk. I think that is what happened.
Grub is more flexible.
The problem is windows itself is confused how to boot, otherwise it would at least start successfully even with the boot files split. One alternative would be to disconnect the IDE drive, repair the win7 boot process with the win7 dvd. Test to make sure win7 is booting fine.
Then reconnect the IDE back. Boot with ubuntu cd, Try Ubuntu option, double check whether the /dev/sdb is still the 160GB disk, and install grub2 there, with:

sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

That way even if the IDE has to be first choice, grub2 will be there, it should be able to boot win7 from /dev/sda1 with no problem, and also ubuntu from /dev/sda2.

---

### Post by yon2501 on 2009-12-17
so all i have to work with is the windows 7 recovery disc i downloaded i dont have the installer disc atm. i tried unplugging the ide drive and booting with the recovery disc but it says it cant even detect the windows 7 instilation. although you were right grub will boot and i can go into ubuntu with the ide drive unplugged so until i can figure out how to change the boot drive in 7 i have to have the ide unplugged to use ubuntu. anyone know how to do this without having to reinstall 7?

---

### Post by yon2501 on 2009-12-17
ok so i cant find anything on changing 7's boot drive without reinstalling so is there a way to put grub over on the ide without reinstalling?

---

### Post by presence1960 on 2009-12-17
> **yon2501 said:**
> ok so i cant find anything on changing 7's boot drive without reinstalling so is there a way to put grub over on the ide without reinstalling?

Boot the Ubuntu Live CD, choose try ubuntu without any changes. when the desktop loads open a terminal and run ```
sudo mount /dev/sda2 /mnt
```
This will mount your Ubuntu root partition.

Then run in terminal ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```
This will put GRUB on MBR of the IDE disk so when you boot GRUB will take over.

Reboot without Live CD and boot into Ubuntu. Open a terminal and run ```
sudo update-grub
```
This will refresh your GRUB menu options.

---

### Post by yon2501 on 2009-12-17
ok so after i pluged the ide back in it booted to grub no problem and i was able to do a update-grub and 7's on so it seems to have fixed itself...thanks for the help tho everyone.

---

