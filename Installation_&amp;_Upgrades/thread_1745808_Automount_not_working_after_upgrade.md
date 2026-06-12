---
title: "Automount not working after upgrade"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by Greezael on 2011-05-01
Yesterday I upgraded from 10.10 to 11.4 Natty Narwhal, and everything went well.

But now I've noticed that my other partitions are not being displayed on Nautilus, nor I'm able to access any pen drive if not by mounting it by hand. Finally, the Disk Utility doesn't work anymore and I have a "floppy0" icon, linked to an "special device fd0", which seems to be "not found" if I try to access it.

My computer has previously lived the 10.4-10.10 upgrade without problems, and does have a floppy disk unit (disabled from the bios, although).

Any clue about this? I need my usb drives, and is not easy mounting them manually. Also I have a lot of programs, so a fresh install is not the best option.

Thanks in regard (and sorry for the english).

---

### Post by Greezael on 2011-05-01
So, bump and forgot to mention that the problem persist if I start Ubuntu with "classic" instead of "unity".

Please, help me -_-

---

### Post by Greezael on 2011-05-01
Last time I bump the thread.

Now, seriously, nobody here can tell me anything??? If the question is noob because of something tell me, please. In this moment I'm mounting manually all my drives, I cannot live like this forever :(


Now, please, I know somebody has to have the answer. Why everything related to automount is failing???

---

### Post by froehli on 2011-05-05
Hm, just had a similar problem with Ubuntu server - I have a configuration where my server automounts some shares on a NAS, and somehow it doesn't seem to work. I haven't looked into it yet, but I will do so right now :), maybe our problems are related!
Btw. I just remembered that I use autofs, no idea whether that's used on the Desktop as well, but I'll tell you what I find out!

**Edit:** I'm still not sure what exactly was wrong in my system, but it seems to work again after restarting the autofs service (sudo service autofs restart), at least for now, I'll keep on testing.

---

### Post by penguinus on 2011-05-06
I have the same problem with automount after upgrade. 

> **froehli said:**
> 
Btw. I just remembered that I use autofs, no idea whether that's used on the Desktop as well, but I'll tell you what I find out!

Desktop usually doesn't use autofs.

---

### Post by matt_symes on 2011-05-06
Hi

Have you checked the automount option is Gnome ? Open a terminal and copy and paste..

```
gconftool-2 -g /apps/nautilus/preferences/media_automount
```

If this returns false copy and paste this into the terminal

```
gconftool-2 -s -t boolean /apps/nautilus/preferences/media_automount true
```

Kind regards

---

### Post by penguinus on 2011-05-06
Thank you for reply. media_automount is true and I didn't change it before or after upgrade.

---

### Post by penguinus on 2011-05-07
Looks like this issue related to 
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/435136](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/435136)

gvfs-gdu-volume-monitor crashes with the following error in ~/.xsession-errors
> (gnome-settings-daemon:1976): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.GduVolumeMonitor: org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/gvfs/gvfs-gdu-volume-monitor received signal 6


It appears even from Natty LiveCD, but only on my home computer. When I start it on laptop, all works ok. 

So, will wait for the next gvfs update. I hope it will be fixed.

Thanks everybody for attention and sorry for my poor English

---

### Post by roshan18 on 2011-05-20
I have posted the alternatives I found here : [http://ubuntuforums.org/showthread.php?p=10839425#post10839425](http://ubuntuforums.org/showthread.php?p=10839425#post10839425)

---

### Post by wilmark on 2011-07-09
Had the same problem. Here's the easy fix that worked for me...
goto Settings => Removable Drives and Media => Storage
and tick the options you want. It seems during the upgrade, some preferences were lost.

---

### Post by jktrigg on 2011-10-16
Where do you find Settings?  I don't find it in either the main Gnome menus or the Nautilus menus.

---

