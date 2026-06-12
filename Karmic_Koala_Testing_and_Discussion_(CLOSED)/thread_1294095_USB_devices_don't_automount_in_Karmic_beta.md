---
title: "USB devices don't automount in Karmic beta"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by xjgnsdof on 2009-10-17
Every time I plug in a USB stick on my laptop (see sig), the device shows up in Disk Utility, but doesn't auto-mount in Nautilus. If I boot the PC with the USB stick plugged in, it is mounted, but if I remove and re-plug the stick, it won't auto-mount.

---

### Post by Jason Cook on 2009-10-17
I am not sure if this is correct but you may have accidental told the device to not auto mount on insert.

---

### Post by xjgnsdof on 2009-10-17
I doubt that; I installed Karmic fresh off of a USB stick. Vanilla kernel, too. Can I confirm this anywhere?

---

### Post by zefew on 2009-10-19
Karmic sucks when it comes to handling or recognizing USB devices. ([http://ubuntuforums.org/showthread.php?p=8127907](http://ubuntuforums.org/showthread.php?p=8127907) being one of the problems.) I wish there was an effective and easy way of filing a 
bug specifically for Karmic like this, but there isn't.

---

### Post by mobusby on 2009-10-19
There is a bug report here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442628](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442628)

Hopefully this gets fixed in time for the release.

---

### Post by gmc on 2009-10-20
I've added a little more information regarding this bug on launchpad.

G

---

### Post by sivlardemalle on 2009-10-21
+1, I have the same problem

---

### Post by gjoellee on 2009-10-21
I can confirm that external USB plugged devices does not automount. I don't get any output from ```
fdisk -l
``` either.

---

### Post by uBeer on 2009-10-21
Too bad, my desktop has this problem as well, so now I can't use my usb sound card on that pc. Luckily I have my laptop which actually works fine with the usb devices I 'throw' at it!

By the way, this is the first Ubuntu release that supports my Edirol UA25-ex OOTB! :D

---

### Post by VMC on 2009-10-21
I have no problem whatsoever. I just plugged in a very old 245 mb usb 1.0 and karmic mounted it without any problems.

---

### Post by ranch hand on 2009-10-21
I have an external enclosure with two 320Gb HDDs, an external CDRom, and an external DVDRom.  All USB and have no trouble at all with Ubuntu, including Hardy, Jaunty and Karmic, mounting them at all.

---

### Post by FoH on 2009-10-25
I **had** the same problem on my system, which is a clean install of a daily build from 20th of october (which seems to be the same as the RC). It's the normal desktop version of Ubuntu 9.10. My previous system had no such problems.

I've tried two pendrives and and external 2.5 inch hard drive, all formatted with FAT32. None of them was auto mounted, that is to say that *they didn't show up in Nautilus and no directories were created in /media*. Dmesg shows that they are recognized and settled.

The devices was detected in Palimpsest Disk Utility and removing a partition and creating it again resulted in a mounted partition. Upon removing and inserting the device it did not auto mount. However, I also noted that inserting a device, starting GParted and doing a "Refresh devices" (Ctrl+R) made them "auto" mount and showing up in Nautilus. This was the trick I used until today.

There is the possibility that today's updates fixed the problem (I can't remember if I rebooted after the update and tried inserting the devices, there was an devkit-disks update among the others) but I did a couple of other things as well:
[LIST]
[*]I removed /usr/share/hal/fdi/policy/10osvendor/20-storage-methods.fdi according to this bug report: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/450160](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/450160)
[INDENT]After restarting HAL I had, however, still the same problem.[/INDENT]
[*]I then proceeded with this bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/429257](https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/429257)
[INDENT]I simply wanted to see what the **udevadm monitor** command said when inserting the devices, and strangely enough the device was auto mounted as it should. Since invoking that command it seems my problem went away. After a reboot, everything still works.[/INDENT]
[/LIST]

So, the solution lies either in the update or the other two points above, maybe in conjunction. Can it be that udevadm created some needed files when invoked?

---

### Post by eschvoca on 2009-10-27
Hi,

I had the same problem.  For a potential solution see:

[http://ubuntuforums.org/showpost.php?p=8178272&postcount=7]("http://ubuntuforums.org/showpost.php?p=8178272&postcount=7")

Thanks.

---

