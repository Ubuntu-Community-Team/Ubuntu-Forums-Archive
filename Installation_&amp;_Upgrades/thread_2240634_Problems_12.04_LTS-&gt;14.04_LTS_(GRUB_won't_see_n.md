---
title: "Problems 12.04 LTS-&gt;14.04 LTS (GRUB won't see new kernel, no sound, no sudo from GUI)"
date: 2014-08-21
forum: Installation &amp; Upgrades
---

### Post by RecceDG on 2014-08-21
Good morning all.

Last night I pulled the trigger on an upgrade from 12.04.3 to 14.04.1 LTS. Historically these upgrades have gone very well, aside from a few self-generated Weird Harolds. Well, last night's upgrade has generated a few problems that have proven stubbornly resistant to troubleshooting.

I am not a Linux or Ubuntu n00b; I have been running one flavour of Linux or another since 1997. I say this mostly to set the stage for troubleshooting assistance - you won't have to describe how to open a shell to me.

OK, the Weird Harolds:

1. The box has a software RAID array. The /boot partition is on one of the RAID array disks, but is not itself RAID. The / filesystem is located on the RAID array.

2. I use Gnome as my desktop, via the flashback packages.

3. I'm using the AMD Catalyst display drivers, manually installed. to provide 3D and multi-monitor support.

4. I use a manually-edited /boot/grub/menu.lst. This is due to historical reasons - for a while a few years ago, newer kernals wouldn't boot this machine (it wound up being a BIOS upgrade thing) so I didn't want Ubuntu changing my kernals out from under me and the machine refusing to come back from a reboot. As well, up until very recently, the Catalyst drivers were very picky about kernal versions and a kernal upgrade meant re-installing Catalyst as part of the upgrade procedure.

5. I'm on a 32 bit installation - because it works, and there's no easy upgrade path from 32->64 bit. I was running the pae flavour kernals to be able to see the full 8Gb of RAM in the machine.

6. I have a lot of software installed other than the base distro and everything Just Works, so I'm not all that interested in wiping the machine clean and doing a fresh install.

So with that out of the way, here are the problems I've identified so far:

1. During the upgrade, the installer correctly identified the manually-edited /boot/grub/menu.lst and presented me with the keep, discard, merge option. Examining the changes that the installer wanted to make, it looked like it had the wrong UUID for the / filesytem. So I elected to keep the old menu.lst, and post-install but before rebooting, examined the contents of the /boot partition. I saw that all the required bits were there, so followed my usual procedure for a kernal upgrade by manually editing menu.lst keeping the proper / UUID. Upon reboot however, GRUB did not recognize the new kernal and did not display it as an option in the menu. The machine booted with 3.2.0-67 just fine, and after selecting Gnome-Compiz from the login screen, I even got my old multi-screen, Catalyst desktop back. Manually editing menu.lst, I was able to get it to recognize changes (I tried deleting an old menu entry for an older, backup kernal, and it took) but nothing seems to work in getting GRUB to present me with the option of booting to the new kernal, and I can't see where GRUB is hiding any error messages.

2. Since the upgrade, I have lost the ability to run programs as administrator/root from the GUI (with one exception). I am getting errors about freedesktop.org policy not being found. I discovered that the policykit was no longer in the Gnome startup programs, and added it manually, but that did not work. I have lost all sound too, and I suspect that this is related (I bet pulseaudio is not being run with the correct permissions). The only exception is the AMD control centre app, which correctly puts up the "enter the admin password" dialogue box when run, but nothing else will - Upgrade Centre, Ubuntu software centre, etc.

If we start with those two, I bet they will fix a bunch of other stuff (the permissions one I bet is a big issue)

I've done the usual Google-fu but have yet to find anything that works.

Lil help?

DG

---

### Post by RecceDG on 2014-08-21
Some troubleshooting data:

```

sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ac88c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      415806      207872   83  Linux
/dev/sda2         2050048   616450047   307200000   fd  Linux raid autodetect
/dev/sda3       616450048   632834047     8192000   82  Linux swap / Solaris
/dev/sda4       632834048  1953521663   660343808   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d90a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     2050047     1024992+  83  Linux
/dev/sdb2         2050048   616450047   307200000   fd  Linux raid autodetect
/dev/sdb3       616450048   632834047     8192000   82  Linux swap / Solaris
/dev/sdb4       632834048  1953523711   660344832   fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn                                                        't support GPT. Use GNU Parted.


Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn                                                        't support GPT. Use GNU Parted.


Disk /dev/sdd: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/md2: 3000.5 GB, 3000457035776 bytes
2 heads, 4 sectors/track, 732533456 cylinders, total 5860267648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md0: 314.4 GB, 314438385664 bytes
2 heads, 4 sectors/track, 76767184 cylinders, total 614137472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md3: 676.1 GB, 676058693632 bytes
2 heads, 4 sectors/track, 165053392 cylinders, total 1320427136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md3 doesn't contain a valid partition table

```

```

cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md3 : active raid1 sda4[2] sdb4[0]
      660213568 blocks super 1.2 [2/2] [UU]

md0 : active raid1 sdb2[0] sda2[2]
      307068736 blocks super 1.2 [2/2] [UU]

md2 : active raid1 sdc1[0] sdd1[1]
      2930133824 blocks super 1.2 [2/2] [UU]

unused devices: <none>

```

```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /boot was on /dev/sda1 during installation
UUID=b8f4b4ab-2e59-426e-b380-791f36ba473c /boot           ext2    relatime        0       2

# /boot2 was on /dev/sdb1 during installation
UUID=e9768910-bfd5-4e04-a244-db4a2da9b215 /boot2          ext2    relatime        0       2

# /home installed on mdraid device by DG. Consists of /home and /homebak partitions (/dev/sda5 and /dev/sdb5)
# Changed to new 3Tb array Jun 2013 by DG
/dev/md2        /home           ext4    relatime        0       2

#New root system directory RAID device
/dev/md0        /       ext4    relatime,errors=remount-ro      0       1

# Old home raid array now mounted as backups array
/dev/md3        /home/backups       ext4    relatime        0       2

# swap was on /dev/sda3 during installation
/dev/sda3       none            swap    sw              0       0

# swap was on /dev/sdb3 during installation
/dev/sdb3       none            swap    sw              0       0

# new SATA DVD burner
/dev/sr0        /media/dvdrw    udf,iso9660 user,noauto,exec,utf8,owner         0       0

```

```

uname -a
Linux karzai 3.2.0-67-generic-pae #101-Ubuntu SMP Tue Jul 15 18:04:54 UTC 2014 i686 athlon i686 GNU/Linux

```

```

cat /boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=0bffc411-e143-4d25-bc59-b8b9fabb788a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b8f4b4ab-2e59-426e-b380-791f36ba473c

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##\
title           RAID Ubuntu 14.04.1 LTS, kernel 3.13.0-34-generic
uuid            b8f4b4ab-2e59-426e-b380-791f36ba473c
kernel          /vmlinuz-3.13.0-34-generic root=UUID=5c28a69c-2fdf-4d5d-b95e-8a9ed773d3f5 ro quiet splash bootdegraded=true
initrd          /initrd.img-3.13.0-34-generic
quiet

title           RAID Ubuntu 12.04.3 LTS, kernel 3.2.0-67-generic-pae
uuid            b8f4b4ab-2e59-426e-b380-791f36ba473c
kernel          /vmlinuz-3.2.0-67-generic-pae root=UUID=5c28a69c-2fdf-4d5d-b95e-8a9ed773d3f5 ro quiet splash bootdegraded=true
initrd          /initrd.img-3.2.0-67-generic-pae
quiet

title           Ubuntu 12.04.1 LTS, memtest86+
uuid            b8f4b4ab-2e59-426e-b380-791f36ba473c
kernel          /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by oldfred on 2014-08-21
It may be time to make the leap to grub2. I resisted grub2 back when it first came out, but now use it for everything. Not sure how well they are updating it for the newer systems, I doubt if anything is done anymore.

I do not know RAID/servers. but updating to grub2 should be just a uninstall of all grub and reinstall of grub2. And with separte /boot outside of the RAID, it should be just a standard update. You can use a live Desktop installer with Boot-Repair, or just run it from command line yourself. Best to have working live installer of your current version, so in live mode you can make emergency repairs.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[URL="https://help.ubuntu.com/community/Boot-Repair"]https://help.ubuntu.com/community/Boot-Repair

      [/URL]
 sudo apt-get update
sudo apt-get upgrade
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
grub-install /dev/sda

    
Does grub legacy work with the gpt partitioned drives? It seems like it must if you have been using it. I know Ubuntu updated grub legacy to work with ext4 with last version of grub legacy they used as default boot loader.

I use gksudo nautilus for example on the occasion I need admin/root privileges on a gui app. But do not run gui apps as root normally.

---

### Post by RecceDG on 2014-08-22
> **oldfred said:**
> It may be time to make the leap to grub2. I resisted grub2 back when it first came out, but now use it for everything. Not sure how well they are updating it for the newer systems, I doubt if anything is done anymore.

I suspect you are right. Grub2 seems a lot more complex, but it IS maintained.

If it turns out I have found some obscure grub-legacy bug, there's no way to get it fixed.

OK. I'll try that. More to follow later. Thanks.

DG

---

### Post by RecceDG on 2014-08-22
OK, progress.

Grub2 is now installed and working.

I had to do [http://forums.fedoraforum.org/archive/index.php/t-283709.html](http://forums.fedoraforum.org/archive/index.php/t-283709.html)

And [https://gist.github.com/LeahCim/9332432](https://gist.github.com/LeahCim/9332432)

But now I get the Grub2 menus and it boots - most of the time. Every once and a while this happens: [https://answers.launchpad.net/ubuntu/+question/248396](https://answers.launchpad.net/ubuntu/+question/248396) Apparently there is a problem with madmin.conf... to be confirmed.

Thanks for that initial assist.

So we are left with:

1. I am constantly getting a pop-up window with "System Problem Detected. Do you want to report the problem now? [Cancel] [Report Problem...]" with no indication of what the problem actually is. Any idea where this problem is being logged?

2. No sound.

3. Attempting to run privileged applications, like Update Manager, no longer open an admin password window, but instead fail with "insufficient privileges" 

4. The CPU Frequency Scaling Monitor applets in my top bar no longer show text

I'm going to keep plugging away at these as best I can, but any assistance would be appreciated.

DG

---

### Post by RecceDG on 2014-08-22
OK, progress.

Grub2 is now installed and working.

I had to do [http://forums.fedoraforum.org/archive/index.php/t-283709.html](http://forums.fedoraforum.org/archive/index.php/t-283709.html)

And [https://gist.github.com/LeahCim/9332432](https://gist.github.com/LeahCim/9332432)

But now I get the Grub2 menus and it boots - most of the time. Every once and a while this happens: [https://answers.launchpad.net/ubuntu/+question/248396](https://answers.launchpad.net/ubuntu/+question/248396) Apparently there is a problem with madmin.conf... to be confirmed.

Thanks for that initial assist.

So we are left with:

1. I am constantly getting a pop-up window with "System Problem Detected. Do you want to report the problem now? [Cancel] [Report Problem...]" with no indication of what the problem actually is. Any idea where this problem is being logged?

2. No sound.

3. Attempting to run privileged applications, like Update Manager, no longer open an admin password window, but instead fail with "insufficient privileges" 

4. The CPU Frequency Scaling Monitor applets in my top bar no longer show text

EDIT - More!

5. Firefox constantly crashes on certain websites (wefixbugs.com is one of them). I Disabled all plugins - no change. Upgraded Java to V8 - no change. Verified that Flash works.

6. indicator-application is one of the programs that keeps crashing

EDIT - Still more!

7. glib is unable to load icons that are .png. The files are fine (verified with GIMP) Reinstalled glib and libpng to no effect.

8. Steam is gibbled too...

I'm going to keep plugging away at these as best I can, but any assistance would be appreciated.

DG

---

### Post by oldfred on 2014-08-22
I would look in log files for issues, but then there are a lot of log files. Boot issues are often in dmesg.
 sudo nano /var/log/dmesg 

There are many threads on sound. But I have not kept track as mine just works.

Only with gui apps use gksudo or gksu do you get the password Windows. Terminal just is at terminal. And you should not use sudo with gui apps. You may have to install gksu.

What gui are you using. I only use gnome-panel as my old monitor is 4:3 and top & bottom panels make more sense, plus I like menus.

---

### Post by RecceDG on 2014-08-23
> **oldfred said:**
> What gui are you using. I only use gnome-panel as my old monitor is 4:3 and top & bottom panels make more sense, plus I like menus.

Gnome-Compiz.

The latest change is now the system has lost the ability to load .png images - so no icons, background images....

I got Steam working, but Civ V now segfaults at startup where it used to work perfectly....

Some upgrade!

---

### Post by oldfred on 2014-08-23
Two years ago I added a 60GB SSD to my part 2006 part 2009 system. SSD made it enough faster I could not justify my plan to then build a new system. I may soon.

But with SSD I have two / (root) partitions. One currently is 12.04 & the other is 14.04. I just changed full time to 14.04 a week or so ago and can not say I notice much difference. It just works for what I do which is mostly Firefox, email and a bit of python. No games other than solitaire occasionally, so I do not need a high end system.

---

### Post by RecceDG on 2014-08-23
Aha!

Running pam-auth-update restored sound and the ability to run programs as root.

More progress!

Now if I could just fix this whole "gtk can't load .png" thing....

Portal2 worked.

---

### Post by RecceDG on 2014-08-23
Aha!

Reinstalling shared-mime-info fixed that part.

---

