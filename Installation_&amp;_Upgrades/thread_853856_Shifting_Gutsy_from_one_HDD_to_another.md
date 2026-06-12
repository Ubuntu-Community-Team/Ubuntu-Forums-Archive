---
title: "Shifting Gutsy from one HDD to another"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by Horza on 2008-07-08
I used Acronis DD to shift a gutsy installation from one HDD to two partitions in another (one for the system, one for the swap) that has Win2000 as its main OS, and then installed Hardy into that.  The grub that Hardy installed finds Win2000, Hardy and Gutsy, and installs the first two correctly, but for gutsy, the start screen displays and then freezes.

The filesystem for the gutsy installation is there and navigable by hardy; I edited the fstab to:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3      /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5      none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

which is where (and what) gparted seems to think the gutsy installation files are.

So what could be going wrong here?  Using Acronis rather than gparted?  Some idiotic error in the fstab?

One factoid is that Hardy's grub wants to label the partisions sdaX instead of hdaX; I've tried various obvious combinations of names without success.

The reason for doing all this is that there's a lot of stuff in the gutsy installation that I want to keep using as a transfer the functionality to hardy, which will take some time.

Thanks

---

### Post by mikewhatever on 2008-07-09
I believe both Hardy and Gutsy label partitions as sdX. To see why the boot process freezes, remove the splash screen by editing the appropriate line in GRUB's menu.lst. Just delete 'splash' at the end of the line and reboot.
> /boot/vmlinuz-2.6.24-19-generic root=UUID=XXXXXXXXXXXXXX ro quiet [COLOR="DarkRed"]splash[/COLOR]


---

### Post by logos34 on 2008-07-09
Just to add to what mikewhatever suggested, you might also change your Gutsy fstab to UUID format also, to avoid any confusion when you boot into gutsy and the system tries to mount the partitions, because Hardy and usually (but not always) Gutsy see ide drives as scsi devices ('**s**dx').  ([More here on the changeover to the libata scsi storage driver]("https://blueprints.launchpad.net/ubuntu/+spec/libata-for-all-ata-disks")).  Your Gutsy is like mine was, i.e. still sees ide as 'hdx', but something may have changed have happened since the copy.

e.g.:

sudo blkid 

ls -l /dev/disk/by-uuid

> title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,2)
kernel     /boot/vmlinuz-2.6.22-14-generic [COLOR=Blue]root=UUID=xxxxx-xxxx-xxxx-xxxx-xxxx[/COLOR] ro splash
initrd       /boot/initrd.img-2.6.22-14-generic
quiet(or whatever gutsy kernel version you're using)

and gutsy fstab:

>  # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 proc            /proc           proc    defaults        0       0
# /dev/hda3      
[COLOR=Blue]UUID=xxx-xxxx-xxxx- xxx[/COLOR] /               ext3    defaults,errors=remount-ro 0       1
[COLOR=Blue][COLOR=Black]# /dev/hda5[/COLOR]
UUID=xxx-xxxx-xxxx- xxx[/COLOR] none            swap    sw              0       0If it still freezes, then the issue is elsewhere.  Maybe run fsck on gutsy sda3 from the live cd.

---

### Post by Horza on 2008-07-09
Bingo!  grub had somehow misidentified the partition in menu.lst, so when I substituted the uuid gotten by the blkid command (same in  gutsy livecd or working hardy), it worked.

Thanks very much!

---

