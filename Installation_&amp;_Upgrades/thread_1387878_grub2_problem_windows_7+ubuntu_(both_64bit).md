---
title: "grub2 problem windows 7+ubuntu (both 64bit)"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by alkisx on 2010-01-22
Although I found some similar threads, no one seems to be of any solution of me:

I had windows 7 64bit installed on one sata2 disk.
There is one "Recovery" partition first (about 100 Mbytes), and then the windows partition followed by a third partition using to store my files.

there is also another disk for misc use also ntfs (sata2).

I have a third sata 2 disk also, for use olny for ubuntu.

So I installed ubuntu (9.10 64bit), rebooted, selected to boot into ubuntu from grub menu, and works fine.

The problem is when I want to boot windows 7. I got a grub error such us "device id.... not found", also mentioned in other threads.

When I select to edit an os boot from grub pressing "e", delete the line containning the UUID, I got a partition not found error. Ok, I found then that the partition hd(0,1) was not on the grup paritions list and try to set it right by setting the existent one hd(0), as was also a solution to another thread in here.

But then again problem. editing lines on grub (on boot menu using "e"), if I delete the line with uuid press Ctrl-x or Ctrl-s it will save that deletion.
If I delete the uuid line and edit the line for the hd, it will save it, but it will set back the line containing the uuid and so back the device id... not found. And enldess loop.

I cannot delete the uuid line and also edit the hd(..) line.

Also tried [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search"), but commenting the lines it says just remove the addition of the uuid line, resulted on boot loader not to be able to find a kernel to load. Booted with live cd to fix it.




Any help?

---

### Post by drs305 on 2010-01-22
Are you trying to edit two lines in a menuentry via the "e" option?

If so, you can hold down the DEL key on the "search" line until it is gone, then use the up/down cursor arrows to move to another line and make a change there.  Make all your changes before pressing CTRL-x. 

Any time you press CTRL-x it will attempt to boot using the parameters currently existing. The changes are not saved.

Any time you press ESC any changes you make are lost.

Edit: Removed

---

### Post by darkod on 2010-01-22
The 100MB is not recovery partition (not much recovery data you could fit in there). That's the "famous" win7 boot partition that holds the initial boot files. When pointing grub1 or grub2 to boot win7, you need to point it to that partition, and not your win7 system partition (when the 100MB exists).

As for the rest of the problem. Giving advice "blindly" can mess it up further. I would suggest to download the script in my signature, move it on desktop for example, and execute it in terminal with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with detailed info about your boot process. Copy the content here and wrap it in CODE tags for easier reading (with the text selected hit the # button in the above toolbar while writing the reply).

---

### Post by alkisx on 2010-01-22
I thought the recovery partition isn't about recovery, it is just that is labelled "System Recovery" <-- sorry wrong, it is "System Reserved".

I just want to change the hd() line on the grub because it is pointing to a non existing device, but it won't save the changes.

Anyway, here is the output you asked for:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=016d6bf6-7669-4ae4-ba25-0d967f2c9323)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xde7ca03b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   614,399,999   614,193,152   7 HPFS/NTFS
/dev/sda3         614,400,000 1,953,521,663 1,339,121,664   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              34       262,177       262,144 Microsoft Windows
/dev/sdb2         262,178   390,887,178   390,625,001 Linux or Data
/dev/sdb3     390,887,179 1,914,324,679 1,523,437,501 Linux or Data
/dev/sdb4   1,914,324,680 1,953,523,898    39,199,219 Linux Swap

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sdc1 ends after the last sector of /dev/sdc

GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdc1              34       262,177       262,144 Microsoft Windows
/dev/sdc2         264,192 1,953,523,711 1,953,259,520 Linux or Data

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8EF0B8D0F0B8C02F" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="62B8D86DB8D840E9" TYPE="ntfs" 
/dev/sda3: UUID="10000B1D000B0A04" LABEL="Work" TYPE="ntfs" 
/dev/sdb2: UUID="016d6bf6-7669-4ae4-ba25-0d967f2c9323" TYPE="ext4" 
/dev/sdb3: UUID="16baa7f9-2dd9-418d-9033-fa3ac75ba399" TYPE="ext4" 
/dev/sdb4: UUID="19d57cb5-a6df-4e86-b620-6313aad3f3ac" TYPE="swap" 
/dev/sdc2: UUID="1016440F1643F3EE" LABEL="Storage" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb2 on / type ext4 (rw,errors=remount-ro)
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
/dev/sdb3 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/alkisx/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alkisx)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root=(hd1,2)
search --no-floppy --fs-uuid --set 016d6bf6-7669-4ae4-ba25-0d967f2c9323
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
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 016d6bf6-7669-4ae4-ba25-0d967f2c9323
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=016d6bf6-7669-4ae4-ba25-0d967f2c9323 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 016d6bf6-7669-4ae4-ba25-0d967f2c9323
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=016d6bf6-7669-4ae4-ba25-0d967f2c9323 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 016d6bf6-7669-4ae4-ba25-0d967f2c9323
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=016d6bf6-7669-4ae4-ba25-0d967f2c9323 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 016d6bf6-7669-4ae4-ba25-0d967f2c9323
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=016d6bf6-7669-4ae4-ba25-0d967f2c9323 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8ef0b8d0f0b8c02f
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=016d6bf6-7669-4ae4-ba25-0d967f2c9323 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=16baa7f9-2dd9-418d-9033-fa3ac75ba399 /home           ext4    defaults        0       2
# swap was on /dev/sdb4 during installation
UUID=19d57cb5-a6df-4e86-b620-6313aad3f3ac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
    .1GB: boot/grub/grub.cfg
    .1GB: boot/initrd.img-2.6.31-14-generic
    .1GB: boot/initrd.img-2.6.31-17-generic
    .1GB: boot/vmlinuz-2.6.31-14-generic
    .1GB: boot/vmlinuz-2.6.31-17-generic
    .1GB: initrd.img
    .1GB: initrd.img.old
    .1GB: vmlinuz
    .1GB: vmlinuz.old
```

---

### Post by darkod on 2010-01-22
Nothing too much wrong with it. But you do have ubuntu on /dev/sdb and grub2 on the MBR of /dev/sda. While it can work that way, it's better to be on the same drive.
But before trying to sort that out, boot into your ubuntu and in terminal do:
sudo update-grub

That should sort out the wrong UUID problem for you. See how it goes.

---

### Post by alkisx on 2010-01-22
I don't think they have to be on the same drive. I 've made lots of installations of ubuntu that way.

update-grub does nothing, just set the same configuration.

My question is: How to change the configuration on boot, to remove the "...uuid..." line and change the drive to search for "hd(..)" and SAVE it.

What ever I do it won't be saved upon C-x.

How can I save the edited grub configuration???

---

### Post by darkod on 2010-01-22
> **alkisx said:**
> I don't think they have to be on the same drive. I 've made lots of installations of ubuntu that way.

update-grub does nothing, just set the same configuration.

My question is: How to change the configuration on boot, to remove the "...uuid..." line and change the drive to search for "hd(..)" and SAVE it.

What ever I do it won't be saved upon C-x.

How can I save the edited grub configuration???

They don't have to be, but it's better. Grub searching for its grub.cfg file on another disk creates delay usually.
As a short term solution you can edit grub.cfg directly but be careful unless you know what you're doing. Saving grub.cfg will keep the changes until the next time update-grub is run which will generate new grub.cfg.
If I'm not mistaken, you can delete the whole line
search -no-floppy ...... UUID

and that way it won't search for it. Make a copy of grub.cfg as you have it right now before doing any changes so you have the original version if you need to put it back in /boot/grub.

You can open the file for editing with:
sudo gedit /boot/grub/grub.cfg

Remember, this is not the preferred way. :)

---

### Post by alkisx on 2010-01-22
Thanks for your reply.

I found a way at least to add a menu option to grub, by adding a new menuentry on the /etc/grub.d/40_custom file (no uuid line, and: hd(0)) .

But to luck again. uppon seleting that option, grub waits for a few seconds and then get me back to the menu. It really looked strange to me setting just the disk and not also its partition (hd(0)), but since I found on this forum a same situation that was solved I said to try.

So, if there is supposed to be an hd(0,1) partition as grub configured it, why grub doesn't see it? It only sees partitions on the hd(1) (eg hd(1,1), hd(1,2) etc) and not from the hd(0) where windows is installed.

---

### Post by darkod on 2010-01-22
Not sure. Also another thing I noticed in the results. Your /dev/sdb and /dev/sdc have GPT partition table, not MBR. As far as I know, GPT was recently introduced for larger hdds. Not sure how it's working and whether that can make these problems.

The manual entry you were trying still should have had a partition number, not just hdd, something like:
rootnoverify (hd0,1)

---

### Post by kansasnoob on 2010-01-22
My thought would be to try a custom entry (or entries) in /etc/grub.d/40_custom. To explain a bit, this is from your grub.cfg:

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8ef0b8d0f0b8c02f
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

You see your current Windows entry is in /etc/grub.d/30_os-prober, whereas /etc/grub.d/40_custom is, just as it says, "custom" and does not get updated by os-prober.

So working with your current entry:

```
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 8ef0b8d0f0b8c02f
	chainloader +1
```

We could make some changes and add it to /etc/grub.d/40_custom using gedit:

```
gksudo gedit /etc/grub.d/40_custom
```

**Note:**do not edit the existing lines:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

```

Now, working out exactly what those changes should be I'm not totally sure, maybe as simple as:

```
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	chainloader +1
}
```

Meierfra had some menu entry suggestions in another thread (look at post #14):

[http://ubuntuforums.org/showthread.php?t=1384618&page=2](http://ubuntuforums.org/showthread.php?t=1384618&page=2)

Remember when editing with gedit to click on Save, then File > Quit, and also after each and every change run:

```
sudo update-grub
```

Is any of that even clear as mud :confused:

Of course once you find the proper menu entry to boot your Windows we'll want to do some cleanup to get rid of what you don't want, but I need to do some testing on my end first. More about that later.

---

### Post by kansasnoob on 2010-01-22
Just FYI if all else fails we should be able to revert you to legacy grub but you'd have to set the Ubuntu drive to be the first to boot in BIOS.

I'd really prefer working out the issues with grub2.

---

### Post by alkisx on 2010-01-22
Thanks again for your replies.

Thanks for your effort cansasnoob, but if you read one of my posts above, I already did that.

That is not the problem. The problem is that grub does not see hd(0) partitions, only hd(1) and hd(2) AS I already mentioned.

I don't know if the existence of MBR and GPT partitions together is a problem, I think not, because I have already installed a customized slackware with both MBR and GPT using grub legacy.

maybe is the grub2? Also I've noticed that the grub2 main package is not installed with the default ubuntu installation, but some programs grub-*. Should I install the main grub2 to try detect the non detected partitions, or will this mess up the system?

---

### Post by alkisx on 2010-01-22
I'will try to put it first on bios, but now I am not at work, where I am having this problem.

But still, I want grub to just detect the partitions in order to go further.

I will try it on Monday, but if anyone seeing this has something else to suggest?

---

### Post by drs305 on 2010-01-22
You have asked how to permanently get rid of the "search" line. This may or may not be helpful in providing a solution to your overall problem but here is how you can eliminate the "search" line from appearing in grub.cfg and the menu entries:
Open /usr/lib/grub/grub-mkconfig_lib.
```
gksu gedit /usr/lib/grub/grub-mkconfig_lib
```
Find this section and place comment symbols **[COLOR="DarkRed"]#[/COLOR]** at the start of the lines:
> 
**[COLOR="DarkRed"]#[/COLOR]**if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
**[COLOR="DarkRed"]#[/COLOR]**    echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
**[COLOR="DarkRed"]#[/COLOR]**  fi

Save the file and update-grub.

The "search" line will no longer be incorporated in the grub.cfg menu.

---

### Post by meierfra. on 2010-01-22
> That is not the problem. The problem is that grub does not see hd(0) partitions, only hd(1) and hd(2) AS I already mentioned.

I  run into this problem in my virtualbox maschine, and I blamed  it on  the messed up Bios of the Virtual maschine. Until I read: 

> I don't know if the existence of MBR and GPT partitions together is a problem, 

So I   did 

```
insmod part_msdos
ls

```
in the grub shell and all my partitions showed up. Seems Grub only loads the module for one of the partitions tables. 

I haven't read  through this thread yet, so it will take me a little bit to figure out whether you  need to use  "insmod part_msdos" or "insmod part_gpt".

---

### Post by meierfra. on 2010-01-22
Try this:

Open ""00_header" via

```
gksudo gedit /etc/grub.d/00_header
```

Add the line "echo  insmod part_msdos" right after the initial comments:

> ...
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

echo insmod part_msdos

transform="s,x,x,"


Save the file.  

It also seems that your device.map is wrong.   That leads to wrong "set root= " lines. That does not really matter since they  get overwritten by the "search" commands. But you might as well fix it:

```
gksudo gedit /boot/grub/device.map
```

and change it to

(hd0) /dev/sda
(hd1) /dev/sdc
(hd2) /dev/sdb

At least that's what I think it should be. There was some conflicting information, so I'm not 100% sure.
 (hd0) needs to be the boot drive, (hd1) the next one in the boot order in the bios and (hd2) the last one.

Save the file and the run

```
sudo update-grub
```


Hopefully that will take are of your problem.

---

### Post by alkisx on 2010-01-23
meierfra seems that your two last posts may be very helpful. I will check on the pc on Monday and let you also know.

---

### Post by alkisx on 2010-01-26
Thank you very much meierfra.

The module part_msdos wasn't loaded, and as a result grub could not see mbr partitions, although on update-grub it was seeing the windows partition.

Possibly a serious bug on grub? This must be fixed. It is really bad.

Adding the line you suggested for loading the module fixed my problem!

---

### Post by meierfra. on 2010-01-27
> Adding the line you suggested for loading the module fixed my problem!
Great.


> Possibly a serious bug on grub? This must be fixed. It is really bad.
You might consider filing a bug report.

---

### Post by meierfra. on 2010-02-01
A slightly better solution:

Open /etc/default/grub via

```
gksudo gedit /etc/default/grub
```

and add the line

GRUB_PRELOAD_MODULES="part_msdos"

to the  end of the file. Save the file and update "grub.cfg" via

```
sudo update-grub
```

(The resulting grub.cfg is actually the same as in the previous solution)

---

