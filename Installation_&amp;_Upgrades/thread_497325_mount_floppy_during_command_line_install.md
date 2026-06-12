---
title: "mount floppy during command line install"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by najevi on 2007-07-10
I am trying to use a preseed.cfg file stored on a floppy to facilitate the install process, especially the partitioning steps. 

The text mode install fails at the "Load debconf preconfiguration file" step:  [FONT=Courier New]
could not retrieve file:///media/disk/preseed.cfg[/FONT]

So I select "Execute a shell" and temporarily escape to an 'ash' shell with nano as an available text editor. I try to mount the floppy using:
[FONT=Courier New]# mkdir /media/disk
# mount -t auto /dev/fd0 /media/disk[/FONT]
but I get the error:
[FONT=Courier New]Mounting /dev/fd0 on /media/disk failed: Invalid argument[/FONT]

Prompted by another post I decided to edit /etc/fstab to add the line:
[FONT=Courier New]/dev/fd0   /media/disk    vfat    user[/FONT]

then at the shell command line
[FONT=Courier New]# mount /media/disk[/FONT]
I get the error: 
[FONT=Courier New]Mounting /dev/fd0 on /media/disk failed: No such device[/FONT]

At this point I don't know what else to try.

[COLOR=Blue]Should I be able to mount removable media at this shell?[/COLOR]

[FONT=Courier New]# mount[/FONT]
reveals that the 
[FONT=Courier New]/dev/hdc on /cdrom type iso9660 (ro)[/FONT] 
is successfully mounted!

---

### Post by confused57 on 2007-07-10
May not work, but you can try:
```
mount /media/floppy0
```

---

### Post by najevi on 2007-07-10
> **confused57 said:**
> May not work, but you can try:
```
mount /media/floppy0
```
with no corresponding reference to /media/floppy0 in /etc/fstab I don't see how that makes any sense but I will try at my next opportunity.

---

### Post by confused57 on 2007-07-10
> **najevi said:**
> with no corresponding reference to /media/floppy0 in /etc/fstab I don't see how that makes any sense but I will try at my next opportunity.
You're right, there's no reference in fstab...Have you tried leaving out the arguments?:
```
mount /dev/fd0 /media/disk
```

---

### Post by najevi on 2007-07-11
Yes that was my first attempt. Then I went looking for other examples of using mount and noted the   -t auto   switch.

---

