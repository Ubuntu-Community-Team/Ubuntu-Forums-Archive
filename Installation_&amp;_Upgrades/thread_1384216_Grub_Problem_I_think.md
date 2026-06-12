---
title: "Grub Problem I think"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by starchills on 2010-01-18
Hello,
Have just installed 9.10, again, many failed attempts previously.
Cannot get to boot up and show menu on dual boot with Vista initially,

However when I delete the grubenv file the system boots ok and works fine.
But does not show the grub menu to choose boot up choices.

Got the information to delete the file on some posts elsewhere about booting problem, and tried a longshot and got into Ubuntu for the first time from trying to install now for 3 months!

The problem is the file grubenv is created each time so on subsequent boot ups the sytem fails to boot again.

The Grub version is 1.97 beta 4, most up to date for Karmic I think, I have seen a version 1.98 but dont think its for Karmic?

Is there a way to modify the grub.cfg file to stop this problem ( all posts say dont touch this file???)

Or install a script to delete the grubenv file on shutdown as a workaround for me, (I have no idea how to do this whatsoever, I'm not familiar with linux at all)

I did read that this problem was fixed/patched in Grub version 2, but dosn't seem
so on my system afetr I updated it when I got into Ubuntu.

I couldnt find the patch or fix, I got the information I am on about from this post:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784)

It seems to say it was fixed or patched by Colin Watson reading through, but I don't really understand whats being said or how to get the patch on my system if indeed there is one?

Sorry for being a bit thick about all this, its a bit beyond my brain now, hope somebody can help out as I have enjoyed my brief bit of fun in Ubuntu, thanks alot.

---

### Post by mikewhatever on 2010-01-18
The bug report you linked to says 'Fixed released', and indeed, a fix had been committed according to post #32 back in October. Have you tied updating the system? Reinstalling grub?

---

### Post by starchills on 2010-01-18
Thanks for responding, yes I have updated the system, when I got in that one time, I updated grub straight away as I thought I would solve the problem with the updated version but not so.

The Grub version is 1.97 beta 4, most up to date for Karmic I think, 
I have seen a version 1.98 but dont think its for Karmic?

---

### Post by kansasnoob on 2010-01-18
> **starchills said:**
> Hello,
Have just installed 9.10, again, many failed attempts previously.
Cannot get to boot up and show menu on dual boot with Vista initially,

However when I delete the grubenv file the system boots ok and works fine.
But does not show the grub menu to choose boot up choices.

Got the information to delete the file on some posts elsewhere about booting problem, and tried a longshot and got into Ubuntu for the first time from trying to install now for 3 months!

The problem is the file grubenv is created each time so on subsequent boot ups the sytem fails to boot again.

The Grub version is 1.97 beta 4, most up to date for Karmic I think, I have seen a version 1.98 but dont think its for Karmic?

Is there a way to modify the grub.cfg file to stop this problem ( all posts say dont touch this file???)

Or install a script to delete the grubenv file on shutdown as a workaround for me, (I have no idea how to do this whatsoever, I'm not familiar with linux at all)

I did read that this problem was fixed/patched in Grub version 2, but dosn't seem
so on my system afetr I updated it when I got into Ubuntu.

I couldnt find the patch or fix, I got the information I am on about from this post:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784)

It seems to say it was fixed or patched by Colin Watson reading through, but I don't really understand whats being said or how to get the patch on my system if indeed there is one?

Sorry for being a bit thick about all this, its a bit beyond my brain now, hope somebody can help out as I have enjoyed my brief bit of fun in Ubuntu, thanks alot.

I would very much like to see what's going on here. If you would please post the results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

That should help us sort this out.

Note: I'll be unavailable until this PM.

---

### Post by starchills on 2010-01-18
Hello here is the output you requested, have put comment in where I have commented out lines in order to boot up ok.

I see the grub menu ok but it dosnt have the vista on it, because of my 'tinkering'

Also I change the 1st drive in my bios, to use Ubuntu, and then switch back if I want vista.
Thanks for your assistance, much appreciated.

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sdb1 and 
                       looks at sector 22044367 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sdb and 
                       looks on partition #1 for /boot/grub.
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

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc2d4c2d4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00068656

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   153,468,944   153,468,882  83 Linux
/dev/sdb2         153,468,945   160,071,659     6,602,715   5 Extended
/dev/sdb5         153,469,008   160,071,659     6,602,652  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="38645E9A645E5AA8" TYPE="ntfs" 
/dev/sdb1: UUID="f33b315f-7039-49cf-a465-de6f29853070" TYPE="ext4" 
/dev/sdb5: UUID="109c32c8-5abf-4fc5-af3f-543dbe75af83" TYPE="swap" 

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
gvfs-fuse-daemon on /home/trainschi/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=trainschi)


=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then    ((((((Starchills has commented out this, and the 2 lines below)))))))))))
  have_grubenv=true                   ((((((to be able to boot without the live CD                  )))))))))))
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
search --no-floppy --fs-uuid --set f33b315f-7039-49cf-a465-de6f29853070
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1600x1200
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
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
#        recordfail=1
#        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f33b315f-7039-49cf-a465-de6f29853070
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=f33b315f-7039-49cf-a465-de6f29853070 ro  splash vga=799  quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
#        recordfail=1
#        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f33b315f-7039-49cf-a465-de6f29853070
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=f33b315f-7039-49cf-a465-de6f29853070 ro single  splash vga=799
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
#        recordfail=1
#        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f33b315f-7039-49cf-a465-de6f29853070
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f33b315f-7039-49cf-a465-de6f29853070 ro  splash vga=799  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
#        recordfail=1
#        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f33b315f-7039-49cf-a465-de6f29853070
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f33b315f-7039-49cf-a465-de6f29853070 ro single  splash vga=799
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
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
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
UUID=f33b315f-7039-49cf-a465-de6f29853070 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=109c32c8-5abf-4fc5-af3f-543dbe75af83 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz

---

### Post by kansasnoob on 2010-01-18
Just now looking at this, I know we can find a true solution.

I first want to try keeping you on grub2 because I think that's best, but if we can't we'll fairly easily set you up with legacy grub.

I must first complete some xorg bug testing and then I'll get right back on this.

I guess I should add, only one thing really concerns me, look here:

> sdb1: __________________________________________________ _______________________

File system: ext4
Boot sector type: Grub 1.97
Boot sector info: [B]Grub 1.97 is installed in the boot sector of sdb1 and
looks at sector 22044367 of the same hard drive for
core.img, core.img is at this location on /dev/sdb and
looks on partition #1 for /boot/grub.[/B]
Operating System: Ubuntu 9.10
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

Which makes me think you initially installed grub2 to a partition rather than just the mbr of the drive. We should be able to deal with that, just give me a bit.

---

### Post by kansasnoob on 2010-01-18
Just to show that I'm willing to blow up my own stuff to find a solution:

> lance@lance-desktop:~$ sudo grub-install /dev/sda11
[sudo] password for lance: 
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
lance@lance-desktop:~$ 


That is the true output of the terminal! I didn't change a thing!

Then again it didn't stop me with a "y or n" (yes or no) to proceed. IMHO that's a bug ,,,,,,, **a really huge, gigantic bug**.

So I'm going to take time out to file a bug report. That's the only way things get fixed.

I'll be back :)

---

### Post by kansasnoob on 2010-01-18
Well that certainly caused me to be unable to boot. Then after handing boot back to the mbr "sudo grub-install /dev/sda" I still experienced a much slower boot time.

Note to all: **do NOT install grub or grub2 to a partition!**

I already knew that but the proof's in the pudding.

---

### Post by kansasnoob on 2010-01-18
OK what you need to do is set your BIOS to boot the Ubuntu drive, both drives must be plugged in!

Once booted into Ubuntu run the following commands in the terminal (be patient and let each command complete):

```
sudo mv /boot/grub /boot/grub_backup
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub-pc grub-common
```

```
sudo apt-get install grub-pc
```

```
sudo update-grub
```

```
sudo grub-install /dev/sdb
```

That should get it sorted. If not I guess it's time to give legacy grub a try.

Grub2 should never have been installed to a partition rather than the mbr of a drive!

---

### Post by starchills on 2010-01-19
Hello Kansasnoob,
Many thanks for all your help it is much appreciated,
I didnt know about the partition thing, or really understand but its a steep learning curve I feel, these simple things that easily trip up newbies like me can leave a bad taste and put people off coming away from MS, I am thankful for ppl like you to help sort this stuff out.
After all most people that come from MS are mainly mouse operators and know nothing of OS's.

I have followed your instructions to the letter and very well explained and set out thanks, very sadly and unfortunatly it didn't work, I re-booted and got the same error message:

out of disk
failed to boot default entries
press any key to continue.

Thanks again.

---

### Post by kansasnoob on 2010-01-19
I know it's a bit of a pain, but could I get you to run the Boot Info Script again and post the new output. More than anything to help me.

This may end up being one of those corner issues where it's necessary to revert to legacy grub:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Note: remember you want to install grub to /dev/sdb not sda as it says in the HowTo because your Ubuntu is on sdb1 and you're setting the BIOS to boot sdb first.

Another note: since we previously used "/boot/grub_backup" use something else when you rename/move "/boot/grub" like:

```
sudo mv /boot/grub /boot/grub_backup2
```

Have you ever worked with legacy grub before?

If not you'll need to add Windows to it's menu.lst. Good idea to back it up first:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

Then to edit:

```
sudo gedit /boot/grub/menu.lst
```

At the very bottom you should see:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

Edit so it looks like this:

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry added for a non-linux OS on /dev/sda1
title		Windows Vista
rootnoverify	(hd0,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader	+1
```

Be sure to click on Save, then File > Quit.

Then install startupmanger as described in the HowTo and you'll find it in System > Administration:

[http://www.psychocats.net/ubuntu/images/sum09.png](http://www.psychocats.net/ubuntu/images/sum09.png)

Be sure you change the Timeout to something appropriate in seconds (generally 10 seconds or longer) and be sure to tick the Show bootloader menu box. You'll notice that can also be used to select the default boot.

I am assuming of course that you can somehow get booted into Ubuntu to make the changes. Am I wrong?

---

### Post by starchills on 2010-01-19
Hello,
Here is the output of the script,
I had to boot from the live CD this time and edit the grub.cfg file then boot back in, ill give the legacy grub a go as you have said and report back.
thank you.

---

### Post by starchills on 2010-01-19
Hello again,
I worked through that all fine and it worked very smoothly without problems thanks to your clear instructions.

I can now boot up consistently into Ubuntu thanks to you!

I have a question though, If I update grub in the future will it destroy all the hard work we have put in, are there any precautions I should be taking like not updating grub or something.

Also a very minor point, when I choose vista from the menu I get an error 
Error 29: Disk Write Error, press any key......

This dosn't really matter because I can always change the boot drive in the bios when I start the machine, it dosnt bother me at all, just thought you should be aware.

I am very grateful for all your help and support, nice to find somebody that knows what they are doing.
All the best

---

### Post by kansasnoob on 2010-01-19
> **starchills said:**
> Hello again,
I worked through that all fine and it worked very smoothly without problems thanks to your clear instructions.

I can now boot up consistently into Ubuntu thanks to you!

I have a question though, If I update grub in the future will it destroy all the hard work we have put in, are there any precautions I should be taking like not updating grub or something.

Also a very minor point, when I choose vista from the menu I get an error 
Error 29: Disk Write Error, press any key......

This dosn't really matter because I can always change the boot drive in the bios when I start the machine, it dosnt bother me at all, just thought you should be aware.

I am very grateful for all your help and support, nice to find somebody that knows what they are doing.
All the best

> If I update grub in the future will it destroy all the hard work we have put in, are there any precautions I should be taking like not updating grub or something.

No, it shouldn't. Grub2 and legacy grub share the package grub-common so it's possible but it hasn't happened yet. Since grub2 uses the package "grub-pc" and legacy grub uses the package "grub" any update to the package grub-pc should have no effect.

> Also a very minor point, when I choose vista from the menu I get an error 
Error 29: Disk Write Error, press any key......

While booted into Ubuntu please post the output of the following commands:

```
cat /boot/grub/menu.lst
```

```
ls /boot/grub
```

```
sudo fdisk -l
```

That should be something we can work around.

---

### Post by meierfra. on 2010-01-19
Use this entry in menu.lst:

# This entry added for a non-linux OS on /dev/sda1
title		Windows Vista
rootnoverify	(hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader	+1


Explanation: Error 29  can be caused by  "savedefault" on menu.lst. Luckily the savedefault command is not used for anything. So you can just remove it. Also, since  you are booting from the Ubuntu drive, the Windows drive is (hd1). So you have to use "root (hd1,0)".

---

### Post by kansasnoob on 2010-01-19
Looking in my grub "bible":

> Quoted from the GNU/GRUB manual

    29 : Disk write error
        This error is returned if there is a disk write error when trying to write to a particular disk. This would generally only occur during an install of set active partition command. 

This error can also occur when the 'savedefault' command is used to try to write to the file called /boot/grub/default so GRUB will remember the last operating system you had booted.  If the file called 'default' does not exist, or you are using GRUB from a CD-ROM (CDs can't be written to), or WINGRUB (GRUB for WIndows, it may be in an NTFS partition, so can't be written to) then you may see this error.
To continue booting anyway, you can press 'e' for edit, select the line of the 'savedefault' command, press 'd' for delete, and 'b' for boot.
If this problenm will re-occur, it would be best to either hash out, or delete the 'savedefault' commands from the menu.lst file involved. They aren't often important anyway. You may be better off without them.

This is actually the first time I recall seeing that. We can rule out the first part of that because we're not using grub from a CD, nor are we using WINGRUB.

**[COLOR="Red"]It appears that I'm wrong about you not having WINGRUB in Vista so ignore this for now.[/COLOR]**

Do you understand this:

> To continue booting anyway, you can press 'e' for edit, select the line of the 'savedefault' command, press 'd' for delete, and 'b' for boot.

That would only provide a temporary fix but it would show us what the problem might be. If that is the problem we'd just comment out the savedefault" like this (used red only for visibility):

```
# This entry added for a non-linux OS on /dev/sda1
title		Windows Vista
rootnoverify	(hd0,0)
**[COLOR="Red"]#[/COLOR]**savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader	+1
```

At least that's what it says.

---

### Post by kansasnoob on 2010-01-19
Something I overlooked before and I'm not really familiar with:

> sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows Vista
Boot files/dirs: /bootmgr /Boot/BCD /Windows/System32/winload.exe /**[COLOR="Red"]grldr[/COLOR]**


I need to do a little studying on that. Had you perhaps tried WINGRUB or maybe something from a Super Grub Disk?

I'll do some studying here on my end.

---

### Post by kansasnoob on 2010-01-19
When I google grldr this comes up so I guess I was wrong to assume we weren't dealing with WINGRUB:

[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial).

I've never used it so I'm a bit lost there. Can you provide any info about that, what you may have done?

Maybe we'll get lucky and meierfra will see this.

---

### Post by kansasnoob on 2010-01-19
I found this:

> If you use 1st method (grub4dos) after getting back to your Ubuntu distro and reinstalling grub you need to remove “grldr” “grldr.mbr” “boot.ini” & “menu.lst” from your Windows “C:\” partition. If you don’t remove them, trying to boot into Windows will just throw you back into GRUB.

Here:

[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

So in your case maybe just removing grldr would remedy the problem. Can't swear to anything though. I've never used grub4dos.

---

### Post by kansasnoob on 2010-01-19
> **meierfra. said:**
> Use this entry in menu.lst:

# This entry added for a non-linux OS on /dev/sda1
title		Windows Vista
rootnoverify	(hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader	+1


Explanation: Error 29  can be caused by  "savedefault" on menu.lst. Luckily the savedefault command is not used for anything. So you can just remove it. Also, since  you are booting from the Ubuntu drive, the Windows drive is (hd1). So you have to use "root (hd1,0)".

Did you see the "grldr" thing? That was a new one on me :)

BTW I'd missed your post until just now.

---

### Post by meierfra. on 2010-01-19
I did see the "grldr" and as far as I know, it should not cause any problems. So  edit "menu.lst" as I suggested in my first post and you  should be all set.

---

### Post by kansasnoob on 2010-01-19
> **meierfra. said:**
> I did see the "grldr" and as far as I know, it should not cause any problems. So  edit "menu.lst" as I suggested in my first post and you  should be all set.

Cool. I'd never seen that before.

---

### Post by starchills on 2010-01-19
Hello Both,
I did the edit as meierfra sugested and all is working as it should be, :P:D:P

I booted a couple of times in and out of both os's and all seems to be fine,

I can now get to grips with Ubuntu and spend some quality time with it.

thank you very much for all your help.:KS

---

### Post by meierfra. on 2010-01-19
> all is working as it should be

Great.


To help me with a similar case, I'm currently working on, could you clear up something for me :

From your RESULTS.txt:


> ### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then ((((((Starchills has commented out this, and the 2 lines below)))))))))))
have_grubenv=true ((((((to be able to boot without the live CD )))))))))))
load_env
fi


It does not look like you actually commented out those line. Instead you commented out these lines:

> # recordfail=1
# if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1

Could that be true?

---

### Post by starchills on 2010-01-19
Hi, here is what I did, put as shown below:

#if [ -s /boot/grub/grubenv ]; then 
  #  have_grubenv=true 
  #  load_env

Just those 3 lines comented, hope that helps
all the best

I was guessing at taking out references to the grubenv rather than delete the file that was re-created anyway

---

### Post by meierfra. on 2010-01-19
> #if [ -s /boot/grub/grubenv ]; then
# have_grubenv=true
# load_env

That's  exactly what  you needed to do.   But  you still were not able to boot into Ubuntu after you did that?

Well, it seems I have to  do some more research. I'm hoping to  find a way to fix the problem without reverting to Grub Legacy.

---

### Post by starchills on 2010-01-19
Sorry I think we missunderstood each other somewhere,

That DID work for me, and booted into Ubuntu ok, whe updated grub it obviously
overwrote the file and couldn't boot again till I did the comments

just had to change the bios to get to vista

sorry for any confusion

---

### Post by kansasnoob on 2010-01-19
> **meierfra. said:**
> That's  exactly what  you needed to do.   But  you still were not able to boot into Ubuntu after you did that?

Well, it seems I have to  do some more research. I'm hoping to  find a way to fix the problem without reverting to Grub Legacy.

That would be great. The benefits of grub2 far outweigh the hassles we're dealing with now IMHO.

---

### Post by meierfra. on 2010-01-19
> That DID work for me, and booted into Ubuntu ok,

Great. So just for anybody who has the same problem and wants to keep Grub 2:

(Edit:  Here is a slightly better solution: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write))


Open a terminal and  open the file "00_header" via

```
gksudo gedit /etc/grub.d/00_header
```

Look for

```
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
```

(should be around line 40) and  add a "#" in front of each of  those four lines:
```
[COLOR="Red"]#[/COLOR]if [ -s /boot/grub/grubenv ]; then
  [COLOR="Red"]#[/COLOR]have_grubenv=true
  [COLOR="Red"]#[/COLOR]load_env
[COLOR="Red"]#[/COLOR]fi
```

Save the file. Then back in the terminal:

```
sudo update-grub2
```

---

### Post by meierfra. on 2010-01-19
Just one more thing. Your problem seems to have been slightly different than  the one in the bug report you mentioned. Do you remember the error message you got when booting failed? Was it

error: invalid: environment block 

or 

error: biosdisk write error, failed to boot default entries.


or something else?

---

### Post by starchills on 2010-01-21
Hi sorry for the delay in responding,

It was as you said the second option:

error: biosdisk write error, failed to boot default entries.

---

### Post by meierfra. on 2010-01-21
> error: biosdisk write error, failed to boot default entries.

That was my guess.  Thanks for letting me know.

---

