---
title: "Root refuses to mount as ext4"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Aikon- on 2009-10-24
I am following the procedures here ([https://help.ubuntu.com/community/ConvertFilesystemToExt4](https://help.ubuntu.com/community/ConvertFilesystemToExt4)) for converting a few of my partitions from ext3 to ext4. I have successfully completed the change on one of the drives (Ironforge). I have updated my /etc/fstab to have ext4 for all three of the volumes of interest, and the next volume that I wish to add the ext4 features to is /, however it refuses to mount as ext4.

The attached screenshot shows the type of / as ext3, while my /etc/fstab is
```
sarmitage@ophelia:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>	<options>       <dump>  <pass>
# Proc
proc		/proc		proc	defaults        0       0
# Swap
UUID=54cd8bd5-b637-4e18-82b3-8938044db54c none            swap    sw              0       0
# Filesystems
LABEL=Darnassus	/		ext4	defaults,errors=remount-ro,relatime 0       1
LABEL=Ironforge	/home		ext4	defaults,relatime        0       2
LABEL=Stormwind	/media/storage	ext4	defaults,relatime        0       2
LABEL=Dalaran	/media/dalaran	jfs	defaults,relatime
# Removable media
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

I am hesitant to go ahead and add the ext4 features using
```
sudo tune2fs -O extents,uninit_bg,dir_index <dev>
``` without / first showing up as ext4.

Any advice?

-Aikon

---

### Post by mmcmonster on 2009-10-24
I know it's stupid, but why not just re-install the OS?  You already have /home on a separate partition, so you probably won't lost any data.  You just have to re-install the OS and any applications you add along the way.

This is the reason I keep the original /etc/apt/sources.list in my ~/ directory and create a symbolic link to /etc/apt/.  That way I just have to re-create the link once I install the OS and update the repositories and install my apps. :-)

---

### Post by Aikon- on 2009-10-24
> **mmcmonster said:**
> I know it's stupid, but why not just re-install the OS?  You already have /home on a separate partition, so you probably won't lost any data.  You just have to re-install the OS and any applications you add along the way.

This is the reason I keep the original /etc/apt/sources.list in my ~/ directory and create a symbolic link to /etc/apt/.  That way I just have to re-create the link once I install the OS and update the repositories and install my apps. :-)

For a couple of reasons; first, that just takes care of your third-party PPAs, not necessarily the specific applications that you have installed; second, and more importantly, I lose configuration of my applications. For example, I have MPD set up to work with my music library, to not totally destroy Pulse on startup, and to accept passworded network connections; for that matter, I have Pulse set up to act as a server.

I also have several databases in MySQL that would have to be backed up and then restored, and countless other tweaks here and there to make my system work properly. I don't want to have to do this every 6 months =P

---

### Post by oboedad55 on 2009-10-24
If it were my machine and everything works as well as yours I would leave it alone. I don't think having ext3 on one partition is going to make any noticeable difference.

---

### Post by Aikon- on 2009-10-25
> **oboedad55 said:**
> If it were my machine and everything works as well as yours I would leave it alone. I don't think having ext3 on one partition is going to make any noticeable difference.

Fair enough; and I agree, it probably won't make that much of a difference. This is pretty much the approach I was going to take anyway -- leave it as ext3 until I am confident that it will work.

OK, so basically, no one [that has seen this thread] knows why it is still loading the ext3 driver instead of the ext4 driver.

-Aikon

---

### Post by Aikon- on 2009-10-25
FYI, I managed to fix this problem by adding the following kernel option:
```
rootfstype=ext4
```

This can be done (assuming you are using Grub 2) by modifying /etc/default/grub to include this option in the GRUB_CMDLINE_LINUX parameter. Note that it must go here instead of GRUB_CMDLINE_LINUX_DEFAULT, because otherwise you won't be able to mount the ext4 file system in recovery mode.

I proceeded to convert / to ext4 without incident.

Regards,
-Aikon

---

### Post by LKjell on 2009-10-25
Could be you miss Shattrath and the Naru is a bit angry.

---

### Post by Aikon- on 2009-10-25
> **LKjell said:**
> Could be you miss Shattrath and the Naru is a bit angry.

Haha, cute =P

Incidentally, after adding the ext4 features to my / partition, I no longer need the `rootfstype=ext4` kernel option -- having the features enabled forces it to mount as ext4 regardless.

So, it seems that it is only a problem if you are trying to mount an actual ext3 volume as / using the ext4 driver; not a very common use-case.

-Aikon

---

