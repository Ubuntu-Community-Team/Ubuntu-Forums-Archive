---
title: "Adding HD to FSTAB"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by SgtT on 2006-07-02
I am very new to linux.  I have two hadrdrives that will not mount.  I recieve an error:

mount: can't find /dev/hdb1 in /etc/fstab or /etc/mtab
mount: can't find /dev/hdc1 in /etc/fstab or /etc/mtab

Below is my fstab file, how do I add these two harddrives so that they will mount?


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by woedend on 2006-07-02
gksudo gedit /etc/fstab


ok first you need to know what kind of filesystem is on each and replace it below where the word "type" is.
win2000/xp is probably ntfs
win 9x is probably vfat
linux is probably ext3

you must also choose where to mount it, and the folder must exist.  its probably easiest to mount them to your home folder.  so in this case you would make a directory in your home folder called hdb1 and one called hdc1(they can be named anything, though).. and use it in place of /directory/ofchoice:

/dev/hdb1   /directory/ofchoice  type  defaults  0  0
/dev/hdc1   /directory/ofchoice2  type defaults  0  0


so lets say they are windows xp disks, and your username is sgt, and youve made the folders hdb1 and hdc1 in your home folder...the exact lines would become
/dev/hdb1 /home/sgt/hdb1 ntfs defaults 0 0
/dev/hdc1 /home/sgt/hdc1 ntfs defaults 0 0

let me know if this doesnt help you.

---

### Post by SgtT on 2006-07-02
Thank you for your help.  I get a new message when I try to mount the drives using Konqueror.

mount: only root can mount /dev/hdb1 on /home/rob/D
mount: only root can mount /dev/hdc1 on /home/rob/E

Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1 	/home/rob/D 	vfat 	defaults 	0 	0
/dev/hdc1 	/home/rob/E 	vfat 	defaults 	0 	0

Thanks,

---

### Post by SgtT on 2006-07-02
I was reading through some other posts and executed a sudo mount -a command and that did the trick.

I'm going to look and see if I can somehow automount the two hd's.

---

### Post by woedend on 2006-07-02
sgt T, yes you must always use sudo to mount/unmount
they should be automounted when you restart your computer.

---

### Post by SgtT on 2006-07-04
Thanks for the help, I'm able to access both drives now.  When I was using Suse 10.0 the drives were recongnized automatically and available right away, I wonder why Ubuntu isn't the same, would make things so much easier.

---

