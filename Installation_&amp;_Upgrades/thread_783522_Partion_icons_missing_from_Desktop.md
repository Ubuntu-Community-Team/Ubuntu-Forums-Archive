---
title: "Partion icons missing from Desktop"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by stevethefiddle on 2008-05-05
Recently upgraded from Xubuntu 7.10 to 8.04 and the Desktop icons for my other partitions no longer appear. They are also missing from the "Places" menu.

The partitions ARE auto mounted correctly and I can read and write to these partitions. One is FAT32 and the other NTFS.

Tried uninstalling and re-installing ntfs-3g and the "NTFS Configuration Tool" but no difference.

The partitions are mounted in "Media" as sdb1 and sdb5.

I can create shortcuts to them as a work-around, but I would rather fix it.
Any ideas or suggestions of where to look?

---

### Post by Bruce M. on 2008-05-07
> **stevethefiddle said:**
> Recently upgraded from Xubuntu 7.10 to 8.04 and the Desktop icons for my other partitions no longer appear. They are also missing from the "Places" menu.

The partitions ARE auto mounted correctly and I can read and write to these partitions. One is FAT32 and the other NTFS.

Tried uninstalling and re-installing ntfs-3g and the "NTFS Configuration Tool" but no difference.

The partitions are mounted in "Media" as sdb1 and sdb5.

I can create shortcuts to them as a work-around, but I would rather fix it.
Any ideas or suggestions of where to look?

Applications > Settings > Desktop Settings

in Desktop Settings > Behavior

Near the bottom you'll see:

Show Icons for: and check what you want shown.

Restart you computer.

Bruce

---

### Post by stevethefiddle on 2008-05-09
Thanks for the reply Bruce M.

I already have all those options selected, but still no desktop icons for my ntfs or fat32 partitions.

Any other ideas?

---

### Post by Bruce M. on 2008-05-09
I have to admit I'm at a loss here.

I'll be watching to see what happens.
Now I'm curious.

Sorry I can't be more helpful.
Bruce

---

### Post by stevethefiddle on 2008-05-09
I'm not sure if this is related or not (hopefully someone can cast some light on this):

I have WINE installed and clicking on the Applications menu item 
"Wine>Browse C:\Drive "
I get this error message:
> Failed to open URL "~/.wine/drive_c".
The URL "~/.wine/drive_c" is not supported.

I've looked in "/usr/share/applications" and the desktop configuration file "Browse C: Drive" has the line:```
Exec=xdg-open ~/.wine/drive_c
```

Typing "xdg-open ~/.wine/drive_c" into a Terminal window opens the directory in Thunar (as expected) and returns the following line in the Terminal window:```
method return sender=:1.3 -> dest=:1.15 reply_serial=2
```

However, entering the same line (xdg-open ~/.wine/drive_c) at a command prompt (Alt+F2) produces the above error message.

 Entering the same line (xdg-open ~/.wine/drive_c) at a command prompt (Alt+F2) with "Run in Terminal" selected, produces the same error message but also the following line in the terminal window:
```
Error showing url: There is no default action associated with this location.
```
So how is it that Thunar is not the default application? Do I not have a default file manager?

I've searched on Google for what sets the default file manager, and the only references I can find suggest that the way to STOP Thunar from being the default is to remove "Thunar-folder-handler.desktop" from "/usr/share/applications/" 
However, looking in "/usr/share/applications/"  there is no file "Thunar-folder-handler.desktop". (but I have not removed it) :confused:

[Edit] Well actually there IS a file "Thunar-folder-handler.desktop", but it is not visible when browsing the folder with Thunar even though "show hidden files" is selected. It is listed if I list the files in a Terminal window. So why is this file "invisible"? Should it be invisible?

---

### Post by stevethefiddle on 2008-05-09
Fixed the WINE problem - and don't think it has anything to do with the other problem.
I edited the desktop configuration file "Browse C: Drive" and changed the line:
```
Exec=xdg-open ~/.wine/drive_c
```
to 
```
Exec=xdg-open /home/user/.wine/drive_c
```

Still looking for a solution to the missing desktop icons.

---

### Post by DarkPhoenix7878 on 2008-05-31
i haev same problem and couldnt solve it <_<
it used to work fine with 7.10 but with 8.04 cant see ntfs
is this a bug or what?
tell us how to fix it plz

---

### Post by kinemagician on 2008-06-01
I have the same problem and I don't know how to fix.
However, the Hard disks are mounted correctly.
Is this a new bug?
Can anyone help please?:confused::confused:

---

### Post by DarkPhoenix7878 on 2008-06-02
i think ill just get back to xubuntu 7.10 at least it dont have this unbelivable funny Bug or whatever it is in in 8.04

---

### Post by stevethefiddle on 2008-06-03
Just to say, I still have this problem and I've not found any solutions anywhere.

I've made "shortcuts" as a work around, but it would be nice to have it working properly.

Also, the problem with "Exec=xdg-open ~/.wine/drive_c" returns every time there is an update, but that's a different problem so I probably should confuse the issue (or are they are related?)

---

### Post by stevethefiddle on 2008-06-26
Do ANY Xubuntu 8.04 users have Desktop icons for their hard drives?
Is the absence of icons a *new feature*?

Does anyone have ANY information about how these icons are / not created?

I don't mind doing a bit of work on this, but I've Googled and can find absolutely NO information (other than other people with the same problem).

---

### Post by Vivaldi Gloria on 2008-06-27
Ubuntu doesn't generate a desktop icon for a drive mounted at /mnt/mountpoint (in fstab).

But it generates the icon if the drive is mounted to /media/mountpoint.

Of course you can always put a link to desktop or wherever you want.

---

### Post by stevethefiddle on 2008-07-07
Thank you for your reply Vivaldi Gloria, but my ntfs drive is mounted at /media/sdb1 and my fat32 drive is mounted at /media/sdb5 (but no desktop icons).

The drives are still mounted the same as they were in Gutsy (I had desktop icons then), but since updating to Hardy no desktop icons.

---

### Post by Vivaldi Gloria on 2008-07-07
> **stevethefiddle said:**
> Thank you for your reply Vivaldi Gloria, but my ntfs drive is mounted at /media/sdb1 and my fat32 drive is mounted at /media/sdb5 (but no desktop icons).

The drives are still mounted the same as they were in Gutsy (I had desktop icons then), but since updating to Hardy no desktop icons.

Can you paste your /etc/fstab ?

---

### Post by stevethefiddle on 2008-07-10
```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=7f61d8ba-a936-46a2-8cea-ef0557b0dd84 / ext3 defaults,errors=remount-ro,user_xattr 0 1
# Entry for /dev/sdb1 :
UUID=82B46F78B46F6E1B /media/sdb1 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
# Entry for /dev/sdb5 :
UUID=4691-3FD7 /media/sdb5 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/sda5 :
UUID=b277779e-a5e6-424e-9b53-09bee4966b34 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
```

---

### Post by Vivaldi Gloria on 2008-07-11
**1)** I have never used fat so I cannot comment on that line of fstab. But consider some of the things in 2) also for that entry.

**2)** About your ntfs line:

```
UUID=82B46F78B46F6E1B /media/sdb1 ntfs-3g defaults,locale=en_GB.UTF-8 0 1
```

The last digit needs to be 0 because it tells fsck to check the partition at boot and fsck cannot check ntfs. 

Try changing "defaults" to "auto".

You have created the directory /media/sdb1 by hand, right? It needs to be there.

Other than these I can't see a reason why ubuntu doesn't put a symlink on the desktop.

**3)** By the way, a clean Hardy 8.04 insall uses

```
UUID=7f61d8ba-a936-46a2-8cea-ef0557b0dd84 / ext3 relatime,errors=remount-ro 0 1
```

rather than "defaults,errors=remount-ro". This is something new in Hardy. I know this is not your problem now, just letting you know.

**4)** Do you know how to add items to places menu by hand? You open a nautilus window, drag the folder icon to the pane on the left. This makes that folder appear in the places menu. I've attached a snapshot to make it more clear. Why am I telling this? Read 5.

**5)** Why don't you try mounting things to /mnt/mountpoint rather than /media/mountpoint. This is the preferred way of mounting hard disks. You shouldn't be using /media to mount your hard disks to begin with. Linux Filesystem Hierarchy Standard says that

> This (/media) directory contains subdirectories which are used as mount points for removeable media such as floppy disks, cdroms and zip disks.  

Mount your disks to /mnt/mountpoint and then you can put a symlink to anywhere you want and add it by hand to places menu. I really suggest you do it this way.

---

### Post by stevethefiddle on 2008-07-11
> The last digit needs to be 0 because it tells fsck to check the partition at boot and fsck cannot check ntfs. 
OK - changed that.

> Try changing "defaults" to "auto"
I thought that "auto" was just used for automatically detecting the file system type on removable media (as in the floppy and CD drive entries), or do you mean something else?

> You have created the directory /media/sdb1 by hand, right?
No, these were created automatically when I first installed Xubuntu (feisty).

> By the way, a clean Hardy 8.04 insall uses ....
relatime,errors=remount-ro 0 1
rather than "defaults,errors=remount-ro". This is something new in Hardy. I know this is not your problem now, just letting you know.

I'll give that a go now - also removed the "user_xattr" since I'm not using Beagle now.

> Do you know how to add items to places menu by hand? You open a nautilus window, 
I've not got nautilus - Xubuntu uses Thunar, but yes I've done that as a workaround.

> Why don't you try mounting things to /mnt/mountpoint rather than /media/mountpoint. This is the preferred way of mounting hard disks. You shouldn't be using /media to mount your hard disks to begin with.

For some reason, /media/mountpoint is the default for Ubuntu (and Xubuntu). I don't know why, but since it is the default I left it like that.

As I said, I had desktop icons and disk icons in "Places" automatically in Gutsy, but upgrading to Hardy has wiped them out and I don't know why. Yes I can (and have) made links where I need them, but this looses some of the convenience that I previously had, such as being able to unmount a partition from the desktop icon (no big deal really, but it bugs me that something has changed and I can't find what it is, and I can't fix it).

I **do** have an icon for "File System" on the desktop - it seems to be some sort of link, but I don't understand how this differs from other links such as hard links or symlinks except that it appears as a directory and not as a link. :confused:

---

### Post by Vivaldi Gloria on 2008-07-12
Well, I don't know what else you can do. Does xfce have something like gconf-editor that you can use to fiddle around with desktop settings?

---

### Post by stevethefiddle on 2008-07-13
I've tried installing gconf-editor, but even with that I can't get the desktop icons.

---

### Post by stevethefiddle on 2009-01-29
I've now upgraded to Ubuntu 8.10 and the issue has gone away. I never did find the cause of the problem.

---

