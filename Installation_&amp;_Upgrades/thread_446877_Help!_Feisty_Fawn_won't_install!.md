---
title: "Help! Feisty Fawn won't install!"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by dkulchenko on 2007-05-17
I loaded the Live CD, installed Ubuntu successfully. Restarted the computer. I went through everything, and when the progress bar loaded, it stopped at about 1% and hung for a while, then loaded me into BusyBox. When I re-ran it in Recovery Mode, the last message was that it could not find my disk in /dev/disk/by-uuid/<MYUUID> which was passed through the boot parameters, as I later found out. I loaded up the LiveCD again(which works normally and where I am typing right now.) I went into /dev/disk on my hard drive and found only 2 folders: by-id and by-path. If I went into the liveCD's /dev/disk, I found: by-id, by-path, AND by-uuid. Therefore, it was not loading off my hard drive. Why? Can I fix this?

BTW, I did a clean install of Ubuntu.

---

### Post by bmartin on 2007-05-17
What did you format your Linux partition(s) as? I suspect your /etc/fstab file might have something to do with this. Please post the contents of that file... the question is: how can you do this if you can't boot into Ubuntu? If you can retrieve the contents of this file from BusyBox and post them here, that would probably help to solve your problem. If that works, please ignore the rest of these instructions. If you can't get to the output of the file using these instructions, try the ones below, which are a bit more complicated.


When the Live CD is booted, if your HD appears, look for that file. If you type **mount** in a terminal, you can probably see where you hard drive is mounted to. It's probably be under the /mnt/ directory somewhere. I'm at work on an XP machine :(, so I can't try this out myself.

One thing: the /etc/fstab on the Live CD will display the contents of the Live CD's fstab file. You need to find the one that's located in your Ubuntu install. If you look at **mount**'s output, it should show the mount device as /dev/hda1 or /dev/sda1 or something like that. Make sure you post the correct file.

---

### Post by dkulchenko on 2007-05-17
Here it is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8f6aee58-9071-4a3f-847e-34a7aaa39814 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=88706679-fb2e-4612-aeb3-f615cedc7c9c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by bmartin on 2007-05-17
OK, this is a bit sketchy, but it might be of help. I'm really at a loss as to how this problem could be explained. Try performing the following steps from inside BusyBox:

sudo vol_id -u /dev/hda1
sudo vol_id -u /dev/hda5

Then use an editor to replace the values inside your /etc/fstab with the newly-generated UUIDs. I'm not sure as to whether or not the UUIDs generated will be the same; my guess is that they will, and that you shouldn't have to edit the file at all. Also, let me know if this creates the appropriate entries in your /dev/disk/by-uuid/ folder.

If everything seemed to go all right during the installation, consider reporting this as a bug with the installer. This is a pretty serious problem.

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=**8f6aee58-9071-4a3f-847e-34a7aaa39814** / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5
UUID=**88706679-fb2e-4612-aeb3-f615cedc7c9c** none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

This idea was pulled from [this page]("http://ubuntuforums.org/showthread.php?t=311158&page=31").

---

### Post by mlind on 2007-05-17
Does your /boot/grub/menu.lst contain same UUID for root filesystem?

---

### Post by dkulchenko on 2007-05-17
Can i just create a symlink from by-uuid to the appropriate disks?

---

### Post by mlind on 2007-05-17
> **dkulchenko said:**
> Can i just create a symlink from by-uuid to the appropriate disks?

Why would you do that?

---

### Post by bmartin on 2007-05-17
I suppose, but that seems sloppy, and it might cause problems. If you're going to do it that way, make sure you create the links to the right places. I'd recommend using a cleaner method of fixing the problem.

---

### Post by bmartin on 2007-05-17
> **mlind said:**
> Why would you do that?
Did you read the entire post? The UUID directory is missing and the system is trying to mount the drives based on UUID, meaning that they're not being properly mounted and chaos ensues.

Seriously though, try the way I said; it really isn't that much work and if it fixes the problem, you're less likely to have future problems. If it doesn't work, you might want to try another method of installation. The might be more to this problem than simply missing symlinks.

---

### Post by mlind on 2007-05-17
> **bmartin said:**
> Did you read the entire post? The UUID directory is missing and the system is trying to mount the drives based on UUID, meaning that they're not being properly mounted and chaos ensues.

Yeah, and I guess this directory is automatically created by udev & friends, so it would be useless/not good idea to create it manually. I'd try to check if my initramfs image is corrupted.

---

