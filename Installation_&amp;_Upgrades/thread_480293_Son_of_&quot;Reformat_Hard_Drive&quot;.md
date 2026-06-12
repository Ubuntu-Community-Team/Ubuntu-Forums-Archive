---
title: "Son of &quot;Reformat Hard Drive&quot;"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by Robotman on 2007-06-21
I have a situation similar to the one in this earlier post:
[http://ubuntuforums.org/showthread.php?p=2818597#post2818597](http://ubuntuforums.org/showthread.php?p=2818597#post2818597)
Still the same dual-boot system but now I want to reformat the remaining Windows "C" drive so I can use it in Ubuntu.  Since that is the boot drive, I'm guessing I'll have to make some changes to either the GRUB loader or BIOS.  Also, with Windows finally banished from this machine, I won't need the dual boot capability any longer.  What are some things I should know and steps I should take before I reformat?

---

### Post by coffeecat on 2007-06-21
By 'boot drive' I presume you mean the boot flag in the erstwhile Windows C: partition. Banish all such thoughts from your mind! :) Linux doesn't need the boot flag. The boot flag tells the Windows bootloader which partition to boot from. In Linux the Grub configuration file tells grub where the bootable Linux root partition is. This is why Linux can boot from a logical partition where Windows can't.

Also, where you refer to 'Windows C: drive', what you mean is the partition that Windows is installed to, commonly the first or secondary primary partition on the first hard drive. Windows uses a bad terminology. If you are going to use Linux it's best to get into the habit of thinking of partitions for partitions and drives for whole drives. Makes sense, doesn't it? :wink:

No changes to BIOS necessary. You may need to edit the grub configuration file which you can find at /boot/grub/menu.lst. And to be able to mount the reformatted ex-Windows partition you will need to edit /etc/fstab. There is an excellent howto for this on this forum. I'll edit this post as soon as I have found it.

**Edit:** Here's the link to the howto. [On the forum](http://ubuntuforums.org/showthread.php?t=283131&highlight=understanding+fstab). Or [on the UDSF wiki.](http://doc.gwos.org/index.php/Understanding_fstab)

Once you've decided what to do with the reformatted partition and if you need help editing those files, just post your present menu.lst and fstab and someone will help you. Be warned that fstab in Feisty references partitions with UUIDs and you'll need to edit fstab anyway if you reformat the Windows partition and it is referred to in fstab. You'll get a nasty error on bootup if you don't. There are several ways around this, either by finding out the UUID of the reformatted partition before you reboot or by using another way of referencing the partition.

---

### Post by Robotman on 2007-06-24
Thanks for the help.  Looks like I have some reading to do. ;)
I've changed my mind on what I want to do though.  Now I would like to make that primary hard drive (hda) my main Ubuntu partition and have the other two drives in my computer (hdb, hdd) available as storage.  This is because I fear the drive where Ubuntu is currently (hdd) may fail soon.  So now, I need to know if there's a simple way I can move the current Ubuntu installation from "hdd" drive to "hda".

---

### Post by coffeecat on 2007-06-24
> **Robotman said:**
> So now, I need to know if there's a simple way I can move the current Ubuntu installation from "hdd" drive to "hda".

This is Linux, my friend. There are **many** ways. :wink: Off the top of my head you can use ghost4linux, partimage or, from the command line, cp, tar or dd. No doubt others will have other suggestions. This is Linux. :lol:

However, cloning/moving your installation from one drive or partition to another will involve editing menu.lst, possibly reinstalling grub to the mbr (not a problem) and editing fstab.

None of this is horrendously difficult but it can be a bit daunting if you're not used to such things. Have a think about it. Do you want to reinstall or do you want to attempt this?

---

### Post by Robotman on 2007-06-24
Thanks for the quick reply. ;)
A total reinstallation from the live CD would be easiest for me, but I'm guessing I'd have to also reinstall all the software and take the time to get all the many settings the way I have them now.  Also, I'm wondering if that would make two bootable Ubuntu systems on this computer, and I don't want that.
I think I'd rather just reformat "hda" to the ext3 file system and move the entire contents of "hdd" to that drive.  Then I'd like to wipe "hdd" and use it for storing things I already have backed up.  I must confess I'm not good at figuring out the command line interface, so I'd need lots of help step by step if I started to monkey around in there. ;)

---

### Post by coffeecat on 2007-06-25
> **Robotman said:**
> A total reinstallation from the live CD would be easiest for me, but I'm guessing I'd have to also reinstall all the software and take the time to get all the many settings the way I have them now.  Also, I'm wondering if that would make two bootable Ubuntu systems on this computer, and I don't want that.

Sorry I didn't get back to you earlier. You're quite right about having to reinstall all the software but you could backup /home and copy that back to the new installation which would give you all your old settings back. Settings are held in hidden files in /home.

You won't have two bootable systems unless you choose to. The installation CD gives you unlimited scope for setting up your hard drives exactly the way you want. If you intend to nuke Windows (what a lovely feeling :) ) then you could work out what your ideal partition layout would be and use the Gnome partition editor on the live CD to reformat and partition your drives before you go into the installation utility. You then tell the installer which partitions you want to use for what and it creates all the mount points for you.

> **Robotman said:**
> I think I'd rather just reformat "hda" to the ext3 file system and move the entire contents of "hdd" to that drive. Then I'd like to wipe "hdd" and use it for storing things I already have backed up. I must confess I'm not good at figuring out the command line interface, so I'd need lots of help step by step if I started to monkey around in there.

If that's the way you want to go I would suggest using the live CD for a lot of the process. The steps would be:

1 Reformat hda so that you have root and swap partitions on it (plus any others you might want).

2 Make mountpoints for old hdd root partition and for new hda root partitions and mount them.

3 Copy the entire contents of hdd / partition to hda / partition with 'cp -a' command.

4 Make yourself a cup of coffee while it copies.

5 Edit /etc/fstab and /boot/grub/menu.lst in the hda partition.

6 Reinstall grub to the mbr.

7 Log out of the live CD and reboot, praying all the while that it will reboot into the cloned installation on hda. :wink:

8 If you successfully boot into the hda installation, use Gparted (if installed) from that to reformat hdd. Or reboot into the live CD to reformat hdd.

9 Now you must re-edit fstab so that the hda installation will mount the new hdd partitions on bootup. You must do this from the live CD if you've used this to format hdd or from the hda installation if you used that. Rebooting without editing fstab first **may** cause a whoops - depending on what's in fstab in the first place.

You could simply do everything including wiping hdd from a single live CD session, but you'd burn your boats if the copy to hda has gone wrong.

Still game? If so post your old fstab and proposed partition layout and we'll take it from there. Also the appropriate stanzas from menu.lst. Don't bother with the commented stuff (a hash at the beginning of the line). There's too much of this and it serves no real purpose except to explain what's going on.

---

### Post by Robotman on 2007-06-25
Thanks coffeecat.  I'm going to try that 2nd method with the 9 steps you outlined.
I've got step 1 completed.  HDA is now formatted and partitioned the way you described.  I don't know how to go about step 2 though.
EDIT: here are the contents of the "fstab" file from HDD:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=d69b3389-019c-4b7b-9234-79a815999513 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=ca3443c2-106a-47a0-bdbe-cde7fa50e0de none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
I think now is a good time to mention another issue, and that is that each time I boot Ubuntu, I have to manually mount an additional storage drive (HDB).  Can adding HDB to fstab make it mount automatically when Ubuntu loads?

---

### Post by coffeecat on 2007-06-25
I will assume you've mirrored what you've got on hdd and you've set up hda1 for root with ext3 and hda5 = swap. If you've done it differently, just amend accordingly. By the way, it's interesting that Feisty is calling your ide drives hdx. Most of the time it uses the new libata drivers and calls them sda. With the old drivers it used to be that only scsi and sata drives were referred to as sdx. I have three machine with ide drives. In one Feisty says hdx and the other two sdx. Such is the joy of Linux. :roll: But I digress..... :)

Step 2:

```
sudo mkdir /media/hda1
sudo mount /dev/hda1 /media/hda1
sudo mkdir /media/hdd1
sudo mount /dev/hdd1 /media/hdd1
```Step 3:

```
sudo cp -a /media/hdd1/* /media/hda1
```Step 4:

```
sudo gedit /media/hda1/etc/fstab
```and change the lines referring to hdd1 and hdd5 to become thus:

```

/dev/hda1         /                       ext3         defaults,errors=remount-ro   0 1
/dev/hda5         none     swap     sw                                           0 0
```Note how I suggest you take out all that UUID guff. There are pros and cons to using the UUIDs - search the forums if you want to know more - but the new hda partitions will have different UUIDs and it's simply easier at this stage to use /dev/hdax references. That can always be changed later.

With regard to hdb - no problem. It's not being automounted because there are no fstab entries - or on second thoughts I don't know. My Feisty will automount partitions on hda that are not in fstab **if** I go into Places > Computer and double-click on an icon. Whatever - post details of the partition layout and we can put entries in fstab or double-check that trick with Places > Computer.

That's enough for now. You'll have to edit the hda1 menu.lst and reinstall grub before you can reboot into the copied partition, so post the menu.lst as I said before and we can go from there.

---

### Post by Robotman on 2007-06-25
Ok, I've done the steps you posted.  Here is my menu.lst file: (password blanked out)
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d69b3389-019c-4b7b-9234-79a815999513 ro
## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false
## Xen hypervisor options to use with the default Xen boot option
# xenhopt=
## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d69b3389-019c-4b7b-9234-79a815999513 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d69b3389-019c-4b7b-9234-79a815999513 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d69b3389-019c-4b7b-9234-79a815999513 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d69b3389-019c-4b7b-9234-79a815999513 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


```

---

### Post by coffeecat on 2007-06-25
To continue:

Step 5b:

```
sudo gedit /media/hda1/boot/grub/menu.lst
```Edit the appropriate parts of menu.lst so that they look like this:

```

title        Ubuntu, kernel 2.6.20-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet
```Go over it **very** carefully. Note

a): the grub convention for naming partitions in the root lines
b): that I suggest you take out the UUIDs in the kernel lines - same argument as for fstab - but the root statement has to follow the Linux convention.

While you're about it you could delete the Windows entries entirely.


Step 6 - Setup Grub:

```
sudo grub
```The grub prompt appears.

```
root (hd0,0)
setup (hd0)
quit
```Now reboot without the CD and pray. :? Earlier I said that fstab would need further editing but as you've only got entries for hda1, hda5 and hdc (your optical drive) this shouldn't be necessary. We can add entries for hdb and hdd later.

If it all boots up fine OK. If not, reboot with the live CD to find out what's gone wrong. At the very worst we can re-install grub so that it boots back into your hdd partition.

If it does boot into hda1 OK I suggest the first thing you do is to install Gparted so that you can re-format hdd from the cloned installation rather than having to muck around with the live CD.

Best of luck! :)

---

### Post by Robotman on 2007-06-25
Success! :D
Ubuntu has booted into hda, and everything looks exactly like it was before I started.  I already have Gparted installed, so I'm ready to add the other 2 drives to fstab.  How do I add them?

---

### Post by coffeecat on 2007-06-25
Excellent news. You need to understand the principles of what you are doing so I'll just give you the outline and you can fill in the details. I'm sure you can do that. And, since I don't know how you've formatted hdb and hdd (if you've already done that), I can't give you the details anyway! :wink: 

Read through the fstab howto that I linked to in my first post. It's not as daunting as might appear at first sight. And before you do anything, double-check what I said about Places > Computer and double-clicking on icons. You might not need to put entries in fstab. Also scroll down in that howto and have a look at the  'How to Label' bit. You might think about labelling your partitions. It can be useful.

Anyway - principles:

1 Create mountpoints for each partition. You know how to do this already. :wink: Assuming you have just hdb1 and hdd1, then:

```
 sudo mkdir /media/hdb1 /media/hdd1
```See how you can create more than one at a time. Add more mountpoints according to whatever partitions you have made on hdb and hdd.

2 Now to make a backup copy of fstab before editing it (just in case):

```
sudo cp /etc/fstab /etc/fstab.backup
```Now edit fstab:

```
sudo gedit /etc/fstab
```As an example I'll give you one line that will work for the ext3 filesystem and one for vfat. Adjust for your partitions/filesystems as necessary. If you've used other filesystems, study that howto. If really stuck, post back.

These are the new lines. Simply add them to the end of the file without changing the present lines. Make sure there is a carriage return at the end of the file. Use spaces and/or tabs to separate the six fields: 
```
/dev/hdb1      /media/hdb1     ext3       defaults      0 1
/dev/hdd1      /media/hdd1     vfat       defaults,utf8,umask=007,gid=46    0 0
```And that, I hope, is about that. One word of warning. You may run into permission problems if you try to write files directly into the ext3 partition rather than into folders in the partition.

---

### Post by Robotman on 2007-06-25
Thanks so much coffeecat, your help has been invaluable! I made the changes to fstab without a hitch, and now  both hdb and hdd are automatically mounted at startup.  That must have fixed something else too because now it takes under a minute to load ubuntu again.  And it does feel nice to be rid of Windows on that machine. :D

---

### Post by coffeecat on 2007-06-25
> **Robotman said:**
> And it does feel nice to be rid of Windows on that machine. :D

You mean you've kept Windows on another machine! :shock: Tut, tut! :wink:

I'm glad it all worked. Just a few thoughts though. It's worth doing some homework into this UUID business, just in case. On my laptop with Feisty, the hard-drive was originally sda, briefly morphed into hda after one kernel upgrade and then morphed back into sda after the next. That wouldn't have been a problem and I would have been blissfully unaware of this except that I had edited my fstab very much along the lines that you've just done - for slightly different reasons. So I had what might be called - ahem - an interesting time with those two upgrades. :( Partly my own fault perhaps, but Ubuntu is simply out of kilter with most of the rest of the Linux world on this one. There are good reasons for using UUIDs, but there are equally good reasons not to. As I said, do a forum search if you're interested.

Best wishes for your further Ubuntuing. :)

---

### Post by Robotman on 2007-06-25
Thanks, I'll check out the info and keep that in mind. ;)

---

