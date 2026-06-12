---
title: "Need Help mounting a volume in nautilus"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by griffindj on 2007-10-16
Hey, let me say that I've been a fedora user for a few years.  I just installed 7.04 and I'm quite satisfied with the ease of use.

One problem I have is that I have two HDs.  My main is 120gb ext3 which has my ubuntu installation on it.  The second HD is 80gb and is formatted fat32 (I believe).  I couldn't figure out how to setup a 200gb logical volume so I just installed on the 80 and said I'd fix it later.  Well its now later.

In the nautilus gui is shows the 76.7gb volume.  When I right click it gives me only the option to mount.  It mounted successful in /media/disk however it was read only.  The only folder on the volume was lost+found.  While mounted I clicked the properties of the disk and edited the mount point (to go to /media/secondHD) and made secondHD -777.  When I closed the properties window it said I needed to unmount and remount for changes to take effect.  When I did I get this error.

Cannot mount volume - Unable to mount volume
Mount point cannot contain following charactors: Newline G_DIR_SEPERATOR (usually /).

I guess it didn't like me using /media/secondHD in the mount point text box.  Well unfortunately the only way I can get back to the properties window is when the volume is mounted.  And I can't mount it because of my screw up.

**Can someone please help me out by telling me how to mount this volume (and keep in mounted permanently) while having read/write permissions?**  This isn't a dual boot system and I only plan on reading data from the partition through smb/cifs which doesn't care what filesystem is used.

Thanks ubunters.

---

### Post by gsiliceo on 2007-10-17
Maybe is a problem with your fstab, i searched a while ago for a problem with user ownership in a fat32 mount and this line gave my user (not root) full control of my files.

/dev/sda2	/media/almacen	vfat	auto,rw,user,uid=1000,iocharset=utf8,gid=1000,umask=0 0 0

A few things to nice, my hard disk is /dev/sda2, but its probably better if you use UUIDS, to get the UUID of your drive use this command 

> sudo vol_id -u <partition>

so instead of> /dev/sda2	/media/almacen it says something like > UUID=6ff8a698-4c51-4c89-8578-854120155389

ALso you can get rid of the > ,iocharset=utf8 part, i added because i have spanish characters in my file names.

Hope it helps.

---

