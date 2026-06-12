---
title: "Dual boot with 7!!!!"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by redcodefinal on 2009-11-15
HI! I'm new to Ubuntu but am a bit of a tech guru. I had Windows 7 installed on my 300gb drive and havea 200Gb drive lying around. I installed Ubuntu on the 200GB but, now Windows 7 won't start up... I see all my Windows 7 system files are still there. I really need to know how to dual boot oir fix this. I tried the repair CD but, I figured out I need to configure GRUB to look on my Win7 partion. I need the way to figure out what hda(?,?) it is on and how to configure GRUB. 

Thanx
-Ian

---

### Post by Herman on 2009-11-15
First if you have IDE hard drive(s) and CD/DVD drive(s) check and make certian you have them plugged in and  jumpered correctly.

Secondly, to see what device numbers and file systems you have you can use the blkid command from a terminal in Ubuntu,
```
sudo blkid
```and/or fdisk
```
sudo fdisk -lu
```

---

### Post by Herman on 2009-11-15
Did you install the most recent version of Ubuntu, 'Karmic Koala 9.10' ? (recommended).

All previous versions of Ubuntu used GNU GRUB 0.97 as the default boot loader, and Ubuntu 9.10, 'Karmic Koala' uses GRUB 1.97 beta4.

There's a world of difference between the two versions of the Grand Unified Boot loader, so anyone wanting to help you will need to know which one you're using. 

If you installed 'Karmic Koala' you should try running 'sudo grub-mkconfig -o /boot/grub/grub.cfg' and see if it picks up your Windows 7 boot loader and adds it automatically to the boot list. If it does your computer will be all fixed. Easy as that! :D
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

---

### Post by redcodefinal on 2009-11-15
It does pick up Windows 7 on \dev\mapper\nvidia_eafbjcee1! :KS How do I configure GRUB to load a boot menu? I heard you have to edit manu.lst but, i couldn't find it. I'm guessing thats because I am using the newer GRUB.
> **Herman said:**
> Did you install the most recent version of Ubuntu, 'Karmic Koala 9.10' ? (recommended).

All previous versions of Ubuntu used GNU GRUB 0.97 as the default boot loader, and Ubuntu 9.10, 'Karmic Koala' uses GRUB 1.97 beta4.

There's a world of difference between the two versions of the Grand Unified Boot loader, so anyone wanting to help you will need to know which one you're using. 

If you installed 'Karmic Koala' you should try running 'sudo grub-mkconfig -o /boot/grub/grub.cfg' and see if it picks up your Windows 7 boot loader and adds it automatically to the boot list. If it does your computer will be all fixed. Easy as that! :D
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

---

### Post by darkod on 2009-11-15
When you say you tried the repair CD do you mean windows repair cd or ubuntu cd? Just to make sure you haven't written the MBR again with windows bootloader.

So the current situation is that grub menu shows up but there is no windows option right? Or not?

---

### Post by redcodefinal on 2009-11-15
There is no GRUB menu at all. However when I did what Herman suggested it said it saw my Winb 7 install.

---

### Post by darkod on 2009-11-15
Thee is no grub menu and it loads ubuntu or win7 directly?

---

### Post by redcodefinal on 2009-11-15
Ubuntu. I just ran the command and rebooted. I saw the menu but now when I choose win7 it came up with "error:invalid signature" what do i do?

---

### Post by dennis55 on 2009-11-15
Ian, i chickened out of the Dual boot scenario................i have Vista 32 and Windows 7 64 on Raid 0.
tried installing ,it but it was messing with system.
i'm using Vmware and Ubuntu 9.04 right now,trying to wean myself offa Windows!..(cold turkey is a mean bitch!).

dennis






> **redcodefinal said:**
> HI! I'm new to Ubuntu but am a bit of a tech guru. I had Windows 7 installed on my 300gb drive and havea 200Gb drive lying around. I installed Ubuntu on the 200GB but, now Windows 7 won't start up... I see all my Windows 7 system files are still there. I really need to know how to dual boot oir fix this. I tried the repair CD but, I figured out I need to configure GRUB to look on my Win7 partion. I need the way to figure out what hda(?,?) it is on and how to configure GRUB. 

Thanx
-Ian

---

### Post by darkod on 2009-11-15
Sorry, no idea. There is a nice Grub II link in Herman's signature. There are instructions how to reinstall grub2 there, if you want to go for it.

PS. Just for information, I am dual booting with Win7 and everything went perfect. Of course, Win7 first installed, then Ubuntu. Everything was set up automatically.

---

### Post by redcodefinal on 2009-11-15
Thats what I did. Win7 then ubuntu.... I'm going to try the win7 startup fix disc again. maybe that will work.

---

### Post by darkod on 2009-11-15
You are aware that windows startup fix discs can't help with linux right?
It will write the MBR with windows bootloader which can't see linux (and doesn't want to :) ). It should put the system back like only windows is installed.
After that you would still need solution to get a grub boot menu with both windows and ubuntu options.

---

### Post by redcodefinal on 2009-11-15
I see win7 in the boot options for grub but, i can't boot to it. I get a error:invalid signature.

---

### Post by redcodefinal on 2009-11-15
OH! Think this will help. updatede grub2 and os-prober when the grub2 install was done i got this 
```

hd0)    /dev/sda
(hd1)    /dev/sdb
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/mapper/nvidia_eafbjcee1
grub-probe: error: no mapping exists for `nvidia_eafbjcee1'
done


```

nvidia_eafbjcee1 is my windows 7 install. Any ideas?

---

### Post by darkod on 2009-11-15
Sorry, didn't express myself correctly. I meant working options in grub menu. :)
How about reinstalling grub2?
Also, are both drives SATA? Is there any difference between them which can help to decide whether to install grub on one or the other?
Because you are free to have grub on the MBR of the windows disk even if Ubuntu is on entirely different physical disk. And since you were booting up windows from the windows disk successfully so far, maybe it's better grub to be there. Just thinking...

PS. No ideas from me. I think it shouldn't be found on mapper but I have no much experience with this. Try googling with the exact error message grub-probe error etc.

---

### Post by redcodefinal on 2009-11-15
Ok i'll clarify this. My 300gb is split into two partions 
28GB -win7
269 - torrent
the 300gb is a SATA drive on SATA 0

I have a IDE drive 200 GB that contains ubuntu on the whole thing. 

When I unplug the IDE drive GRUB still loads, however ubuntu cannot be loaded. When I unplug my SATA drive it won't boot anything. I'm guessing Ubuntu installed grub to my 300gb drive somewhere. I have tried reinstall GRUB2, It still comes up with error:invalid signature. I believe the problem has to do with my earlier post. However I know little about Linux so I'm not sure. 

EDIT: I also googled the error. No one else has had the same problem.

---

### Post by darkod on 2009-11-15
How about entering windows entry manual? Up for that?
Since ubuntu is working, open terminal and run:
sudo gedit /etc/grub.d/40_custom

At the end of the file add:

menuentry "Windows 7 (new)" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set CFFCFF9EECFF7F49
chainloader +1
}

NOTE: in root=(hd0,1) you need to change values depending where your windows partition is. hd0 is first drive, hd1 second, etc. Partition numbers start from 1. Also you need to change the CFFC... value with the UUID value of your windows7 partition.

You can find out UUID by running in terminal:
sudo blkid

If you don't know where your win7 partition is, you can see list of all drives and partition with:
fdisk -lu

After you enter the correct partition and UUID in the above menu entry, save the file and close it.

Then run in terminal:
sudo update-grub

And reboot to see if option Win7 (new) is there and whether it works.

---

### Post by darkod on 2009-11-15
OK, leave both drives plugged in and do the above post. fdisk will show you both drives and their partition the way linux is looking at them, for example the IDE might be considered first drive and SATA second.

If you are not sure post the result of sudo blkid and I'll look at them to help you with the manual entry for win7.

---

### Post by redcodefinal on 2009-11-15
> **darkod said:**
> OK, leave both drives plugged in and do the above post. fdisk will show you both drives and their partition the way linux is looking at them, for example the IDE might be considered first drive and SATA second.

If you are not sure post the result of sudo blkid and I'll look at them to help you with the manual entry for win7.

I can't get fdisk to work... I type in fdisk -lu and nothing happens.

EDIT: Also when i sudo update-grub i get the same error. grub-probe: error...

---

### Post by darkod on 2009-11-15
How about:
sudo blkid

Copy the result here.

PS. About the fdisk command the parameter was actually -l (small L), not -lu. Sorry, my mistake. :)

---

### Post by oldfred on 2009-11-15
I have had issues with mixed Sata & Pata drives. Ubuntu, windows and grub, and BIOS do not always map the drives the same. If you BIOS allows you to set the pata before the Sata install grub to the Pata and repair the windows boot in the Sata. The update grub will modify the grub entry for windows boot to make windows think it is still the first drive. I alway like having an operating system on each drive (or more) and have the MBR of that drive point to that operating system.

If you still are having problems we can see exactly how your system is configured with this script, you can download and run from the liveCD or if in Ubuntu run from there:

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

### Post by redcodefinal on 2009-11-15
sudo blkid

```
/dev/sdb5: UUID="01f5019d-d4ad-4952-9ed7-a859ad8601c5" TYPE="swap" 
/dev/mapper/nvidia_eafbjcee1: UUID="06B81D0FB81CFEBD" TYPE="ntfs" 
/dev/mapper/nvidia_eafbjcee5: UUID="01CA43A771DC41A0" LABEL="Torrents" TYPE="ntfs" 
/dev/sda: TYPE="nvidia_raid_member" 
/dev/sdb1: UUID="bb880219-9c1f-400c-becd-f383ddff032f" TYPE="ext4" 

```fdisk -l

```
Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3b8e3b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3863    31029516    7  HPFS/NTFS
/dev/sda2            3864       36483   262020150    f  W95 Ext'd (LBA)
/dev/sda5            3864       36483   262020118+   7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdf29521d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23781   191020851   83  Linux
/dev/sdb2           23782       24792     8120857+   5  Extended
/dev/sdb5           23782       24792     8120826   82  Linux swap / Solaris

```

EDIT: for boot_info_script*.sh

```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=bb880219-9c1f-400c-becd-f383ddff032f)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe3b8e3b8

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    62,059,094    62,059,032   7 HPFS/NTFS
/dev/sda2          62,059,095   586,099,394   524,040,300   f W95 Ext d (LBA)
/dev/sda5          62,059,158   586,099,394   524,040,237   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdf29521d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   382,041,764   382,041,702  83 Linux
/dev/sdb2         382,041,765   398,283,479    16,241,715   5 Extended
/dev/sdb5         382,041,828   398,283,479    16,241,652  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda: TYPE="nvidia_raid_member" 
/dev/sdb1: UUID="bb880219-9c1f-400c-becd-f383ddff032f" TYPE="ext4" 
/dev/sdb5: UUID="01f5019d-d4ad-4952-9ed7-a859ad8601c5" TYPE="swap" 
/dev/mapper/nvidia_eafbjcee1: UUID="06B81D0FB81CFEBD" TYPE="ntfs" 
/dev/mapper/nvidia_eafbjcee5: UUID="01CA43A771DC41A0" LABEL="Torrents" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/redcodefinal/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=redcodefinal)
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=redcodefinal)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set bb880219-9c1f-400c-becd-f383ddff032f
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
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set bb880219-9c1f-400c-becd-f383ddff032f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=bb880219-9c1f-400c-becd-f383ddff032f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set bb880219-9c1f-400c-becd-f383ddff032f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=bb880219-9c1f-400c-becd-f383ddff032f ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/mapper/nvidia_eafbjcee1)" {
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows 7 (new)" {
insmod ntfs
set root=(hd1,1)
search --no-floppy --fs-uuid --set 06B81D0FB81CFEBD
chainloader +1
}

### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=bb880219-9c1f-400c-becd-f383ddff032f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=01f5019d-d4ad-4952-9ed7-a859ad8601c5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda5



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory

```

---

### Post by darkod on 2009-11-15
Arghhh. raid.

Why is there RAID on the 300GB drive? Are you using it?

There were reports with the error you are seeing if raid is involved, I was ignoring them while googling.

PS. I don't have experience with RAID (or fake RAID) and I might give you wrong advice. You can read this, I think it is for similar situation. If there was no RAID on your 300GB drive probably grub would have picked up your win7 already ages ago.
[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/463112](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/463112)

PPS. My recommendation is, if you don't use the raid, and what kind of raid you would use with only one disk, get rid of it. The supplied link clearly says that the disk can bring raid setting on itself if not properly removed from raid where it was once. Just unplugging the disk does not remove raid settings.

---

### Post by redcodefinal on 2009-11-15
> **darkod said:**
> Arghhh. raid.

Why is there RAID on the 300GB drive? Are you using it?

There were reports with the error you are seeing if raid is involved, I was ignoring them while googling.

PS. I don't have experience with RAID (or fake RAID) and I might give you wrong advice. You can read this, I think it is for similar situation. If there was no RAID on your 300GB drive probably grub would have picked up your win7 already ages ago.
[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/463112](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/463112)

PPS. My recommendation is, if you don't use the raid, and what kind of raid you would use with only one disk, get rid of it. The supplied link clearly says that the disk can bring raid setting on itself if not properly removed from raid where it was once. Just unplugging the disk does not remove raid settings.
I don't know why RAID is on my drive.... How would I clear it up?

---

### Post by darkod on 2009-11-15
Wouldn't know to tell you that, sorry.

But even with the raid, you might give it a shot, it might work.

In my post for the menu entry, it remains root=(hd0,1) and instead of CFFC... value put 
06B81D0FB81CFEBD.

See if that will work. My post #17. Do the menu entry in 40_custom file as explained and the sudo update-grub command. Hope it helps.

---

### Post by redcodefinal on 2009-11-15
Thanks but it didn't work.... I stil;l get a grub-probe error. any suggestions on how to wipe out Ubuntu and fix my win7?

---

### Post by darkod on 2009-11-15
No need to delete Ubuntu, not right now. Unplugg the ubuntu drive, boot the computer with Windows 7 DVD and it will offer Repair Computer (or similar). That will restore windows bootloader on the MBR of your windows drive. Same as before installing ubuntu.

---

### Post by darkod on 2009-11-15
It is also a good idea to check your BIOS just in case it really has some raid setting enabled. Go into BIOS and look around, especially where the settings for the drives are. Look for anything suspicious that raid is enabled.

---

### Post by redcodefinal on 2009-11-15
OK! Turned off raid and turned on SATA/PATA Combonation. And I now see the windows 7 (new) option in GRUB. However when I goto it it begins loading win7 and then it restarts my comp. I repaired startupo but, to no avail...

---

### Post by darkod on 2009-11-15
The new entry plan was when we had no clue about the raid setting.
If you do:
sudo update-grub

Then the automatic win7 option in grub should work fine (not the new we created manually). The raid was messing up the auto process.

IF the other option for win7 is in the grub menu and it works, open again 40_custom
sudo gedit /etc/grub.d/40_custom

and just delete the manual win7 entry. Of course, after that you need to do:
sudo update-grub

again.

---

### Post by darkod on 2009-11-15
One additional thought: With all the things we tried I am not even sure if os prober is enabled or disabled right now.

Just in case, to enable it execute:
sudo chmod +x /etc/grub.d/30_os-prober

After that:
sudo update-grub

Watch the lines it returns and if you see something like Windows 7 (/dev/sda1) that means you got it, grub2 found it and it will be in the grub menu like before (only before it didn't work). For the time being you can leave your manual entry for win7 there even if it doesn't work.

It is easy to remove it with editing the 40_custom file as explained in my previous post. Cheers.

---

### Post by redcodefinal on 2009-11-15
it produces this

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/mapper/nvidia_eafbjcee1
grub-probe: error: no mapping exists for `nvidia_eafbjcee1'
done

```i'll reboot in a sec, but i don't think it worked.... The new win 7 entry showed the starting windows 7 screen...  it would just restart

---

### Post by redcodefinal on 2009-11-15
didn't work....

---

### Post by oldfred on 2009-11-15
Found Windows 7 (loader) on /dev/mapper/nvidia_eafbjcee1

That is still a raid setup. Have you checked with gparted to see if the windows partition is still set up as raid?

---

### Post by darkod on 2009-11-16
Unfortunately your options seem very limited at the moment.
You said you disabled raid in BIOS but the disk still has raid properties associated with it. I was afraid that might happen, as I said, I haven't worked with these software motherboard raids. And I'm still puzzled what were you doing with raid with only one drive, no raid configuration is working with one drive to my knowledge.
Anyway... the raid property of the disk will keep making problems.
Options:
1. Try something called dmraid, raid utility for Ubuntu, but I haven't used it and wouldn't know to give you instructions. In theory if it can recognize the setting it might start booting Win7. But even if that is working, it will be something like faking raid with only one drive in the setting. Not what I would like to do.
2. Attempt repair of the MBR with Win7 DVD and keep using only Win7. We wouldn't like you to do that right? :)
3. Think about reinstalling Win7 from scratch. But that would mean you have to install all your software back. This raid setting seems will not go away except with formatting, and that means clean install. Further more, the other partition on the drive will also need to formatted to get rid of the setting, something you usually don't need to do for a windows clean install. That means you would need to unplug the windows sata drive, plug it into a working windows pc and copy everything you need.
From there it is simple. Put it back in your pc, boot with ubuntu cd and create the two ntfs partitions for win7 again. I prefer to use gparted because win7 will try to create small 100MB boot partition with no real use. But since you will install ubuntu on completely different drive, the 100MB partition doesn't make a difference. Basically create the win7 partition any way you like, just make sure it's not in raid setting (gparted would show you immediately their 'linux' names, if they are sda1 and sda2 excellent, no raid). After finished with win7 plug in your ide drive, boot with ubuntu cd and install ubuntu on it, selecting grub2 to be installed on the sata, /dev/sda, in the last screen before clicking Install button for ubuntu. More or less, that would be it. Most probably you will not have these problems once the raid partitions are gone.

Those are the options I can think of right now...

---

### Post by darkod on 2009-11-17
in case you are still looking for a way to remove the raid properties, look at post #4 here:
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)

Thr person says all data was still there on the drive after the operation which means you could save your win7. :)

---

### Post by redcodefinal on 2010-05-10
Hi, I wanted to let you guys know that I ended up just loggin in as root (I know its bad) and editing grub.cfg by hand. Everything works now.

---

