---
title: "OS-prober: cannot access /var/lib/os-prober/mount/boot"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by marking on 2010-01-06
Hello, 

I have have worked with Ubuntu 8.10 for a long while. With a dual boot to XP for some compatibility stuff.
A few weeks ago I wanted to upgrade to 9.10, to be sure I did a clean format of my hard drive.

Yesterday I needed to use windows 7 for some work, so I installed it on a different partition .
I installed it without problems, it took over my MBR, preventing GRUB to work. So I used 9.10 live CD to restore grub like written on the Ubuntu wiki.

However, I am unable to add Windows 7 to my list.
When I run update-grub2, I recieve the following message

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done
```

So, I tried to add windows 7 manually in the /etc/grub.d/40_Custom file from a snippet I found on the net somewhere:
```
menuentry "Microsoft Windows 7" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ntfs
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set e0d4a286d4a25e92
	chainloader +1
}
```

When I boot windows 7, I get an error indicating Bootmgr was not found. which I am sure was not the case before I restored Grub.

Googling for hours I was unable to find why my os-prober failed in the first place. This error doesn't show up anywhere, and as far as I know, I did nothing with this application. Reinstalling with apt-get didn't solve it either.

I hope someone might be able to help me!
Thanks!


Here is my Boot info script 44 result
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00026691

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     9,992,429     9,992,367  82 Linux swap / Solaris
/dev/sda2           9,992,430   209,985,614   199,993,185  83 Linux
/dev/sda3    *    209,987,584   210,192,383       204,800   7 HPFS/NTFS
/dev/sda4         210,192,384   824,387,583   614,195,200   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="131ff342-2567-4916-a64b-13bca2a542c3" TYPE="swap" 
sda2: UUID="f9f8bf18-b65a-4104-86d0-b9e7559784d2" TYPE="ext4" 
sda3: UUID="76484BEE484BABA5" LABEL="Door systeem gereserveerd" TYPE="ntfs" 
sda4: UUID="12EA518AEA516ACD" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/mark/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mark)


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
search --no-floppy --fs-uuid --set f9f8bf18-b65a-4104-86d0-b9e7559784d2
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set f9f8bf18-b65a-4104-86d0-b9e7559784d2
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=f9f8bf18-b65a-4104-86d0-b9e7559784d2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set f9f8bf18-b65a-4104-86d0-b9e7559784d2
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f9f8bf18-b65a-4104-86d0-b9e7559784d2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if sleep --interruptible 10 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Microsoft Windows 7 Ultimate " {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ntfs
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set e0d4a286d4a25e92
	chainloader +1
}
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
UUID=f9f8bf18-b65a-4104-86d0-b9e7559784d2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=131ff342-2567-4916-a64b-13bca2a542c3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


   5.1GB: boot/grub/core.img
   5.1GB: boot/grub/grub.cfg
   5.1GB: boot/initrd.img-2.6.31-14-generic
   5.1GB: boot/initrd.img-2.6.31-16-generic
   5.1GB: boot/vmlinuz-2.6.31-14-generic
   5.1GB: boot/vmlinuz-2.6.31-16-generic
   5.1GB: initrd.img
   5.1GB: initrd.img.old
   5.1GB: vmlinuz
   5.1GB: vmlinuz.old

=================== sda3: Location of files loaded by Grub: ===================


 107.5GB: boot/grub/core.img
```

---

### Post by john newbuntu on 2010-01-06
Change your /etc/grub.d/40_Custom file to:

menuentry "Microsoft Windows 7" {
   insmod ntfs
   set root=(hd0,3)
   search --no-floppy --fs-uuid --set 76484BEE484BABA5
   drivemap -s (hd0) ${root}
   chainloader +1
}

and run
sudo update-grub

Then reboot.

---

### Post by marking on 2010-01-07
Thanks john , that solved my problem! I didn't knew I had to use that small partition Windows creates.

Still wonder why OS-Prober failed though...
But since I was able to set this manually I don't need it any longer anyway :)

---

### Post by meierfra. on 2010-01-22
> sda3: 
 
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr /boot/grub/core.img


You have a "Boot" and "boot" folder on /dev/sda3.  This leads to confusion since "ntfs" partitions are case insensitive. See this link for the details:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

### Post by grummbaleena on 2010-10-03
Okay so I had this exact same issue, but I think the reason I had it is slightly different than the OP so I'll tell my story here in case it helps someone else.

I have had issues with Dell DataSafe Local Backup writing over the MBR, to fix this I reinstalled grub2 using a LiveCD as described at [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"). (As a side note I uninstalled Dell DataSafe in Windows.) I'm pretty sure I mistakingly installed grub into Windows boot partition, (sda2 for me). This didn't cause problems until today when I cleaned out some old kernel entries using Ubuntu Tweak and when I restarted I found out there was no entry for Windows 7 in the grub menu. I eventually found out that I had symptoms identical to the OP after running boot_info_script. 

original boot_info_script55.sh output:


To fix this I mounted the Windows boot partition (sda2) and removed the directory /boot, then updated the grub menu.

```
sudo mount /dev/sda2 /mnt
```- navigate to /mnt in nautilus and delete /boot folder. WARNING: do not delete the 
/Boot folder since it contains files needed by Windows to boot properly.

```
sudo umount /mnt
sudo update-grub
```- restart and voila, Windows 7 menu item returns.

---

### Post by ntiller on 2010-10-23
grummbaleena: 
Thank you so much for posting that! Fixed my issue up really quickly!

---

### Post by topet2k12001 on 2010-11-01
Hi,

Thanks for this solution. I have the exact same problem. Verified that the solution works!

---

### Post by buldozer911 on 2010-12-22
Thanks grummbaleena save the day for me....:popcorn:

---

### Post by bouncinglime on 2011-02-14
heh I broke my grub install somehow, but it was comment #4 that definitely helped me unbreak it. Many thanks! ^_^

---

### Post by michael.conner on 2011-02-27
> **meierfra. said:**
> You have a "Boot" and "boot" folder on /dev/sda3.  This leads to confusion since "ntfs" partitions are case insensitive. See this link for the details:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

Thanks for this. I love fixing problems in Debian by going to Ubuntu forums ;-)

---

### Post by jonnyvinyl on 2011-04-13
After upgrading from 10.10 to 11.04, grub gave errors when i tried to boot to my win 7 partition. 

This solution didn't work for me, but the one here did, may be useful to anyone working on the grub custom file :

[http://ubuntuforums.org/showthread.php?t=1662142](http://ubuntuforums.org/showthread.php?t=1662142)

Jonny

---

### Post by sagarsiddhpura on 2011-04-23
> **grummbaleena said:**
> Okay so I had this exact same issue, but I think the reason I had it is slightly different than the OP so I'll tell my story here in case it helps someone else.

I have had issues with Dell DataSafe Local Backup writing over the MBR, to fix this I reinstalled grub2 using a LiveCD as described at [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"). (As a side note I uninstalled Dell DataSafe in Windows.) I'm pretty sure I mistakingly installed grub into Windows boot partition, (sda2 for me). This didn't cause problems until today when I cleaned out some old kernel entries using Ubuntu Tweak and when I restarted I found out there was no entry for Windows 7 in the grub menu. I eventually found out that I had symptoms identical to the OP after running boot_info_script. 

original boot_info_script55.sh output:


To fix this I mounted the Windows boot partition (sda2) and removed the directory /boot, then updated the grub menu.

```
sudo mount /dev/sda2 /mnt
```- navigate to /mnt in nautilus and delete /boot folder. WARNING: do not delete the 
/Boot folder since it contains files needed by Windows to boot properly.

```
sudo umount /mnt
sudo update-grub
```- restart and voila, Windows 7 menu item returns.

After mounting the windows partition, I do not find /boot folder in it. Kindly tell where this /boot folder is located. I can only find mnt/windows/Boot folder.

---

### Post by oldfred on 2011-04-23
@sagarsiddhpura

If the above fixes have not worked for you, please start a new thread. And it would be helpful to include the results.txt from boot info script.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by janmae on 2011-05-15
ahhh...thankyou grummbaleena...i,ve tried to figure it out a whole day.luckily to found you... [-o<

---

### Post by subehsharma on 2011-07-24
Thanks alot man..It worked! I was getting worried as all my office stuff was on Widnows! :D

---

