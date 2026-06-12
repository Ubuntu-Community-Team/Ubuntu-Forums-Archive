---
title: "/etc/fstab automated?"
date: 2009-01-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by taavikko on 2009-01-21
Is development gearing towards automated mounts?
Since some users are reporting empty file, and still partitions get mounted.

I were missing line containing my cd/dvd drive, and it still worked.

something related to usb-install as it didn't use cd-drive?
As I did fresh install on alpha3, created it by using usb-creator, on already up-to-date jaunty (last fresh-install were somewhere hardy alpha2-alpha3)

and if this is the case, automated mounting, where does the system looks up this info (device, mountpoints, options, etc)?
Should have paid attention to all the udev-updates, since that's my guess, where this is going to...
If someone catches this one in **aptitude changelog udev**
I'll give a huge hug...


Just wondering.
Thanks for in advance for all the well educated guesses :)

---

### Post by jfernyhough on 2009-01-21
In my (somewhat limited) experience in this area, fstab is used for setting mount options and mount points. This is important for anything mounted as / or at a specific place in the tree, e.g. /home.

If the device is not in fstab HAL or udev or whatever it is will do its best to have a sane guess - it needs to do this anyway when you plug in a USB pen, external hard drive, or similar. Hence, any internal partitions/devices that are not in fstab will be treated in the same way and mounted with sane defaults under /media.

---

### Post by taavikko on 2009-01-21
Thanks, that was a good reply,
Just wondering, since no discussion has met my eyes concerning debrecation of /etc/fstab (similar to /etc/X11/xorg.conf)

So have to poke those chabgelogs of hal and udev whats going on.
If someone else has a idea, more than willing to hear...

---

### Post by petteriIII on 2009-01-21
Earlier I believed that fstab is needed for Ubuntu to operate, because when there is no fstab Ubuntu really doesn't operate properly. But when fstab is empty Ubuntu operates and even you can do www, USB automounts and so on. But of course some points are not there. 
Actually when copying the whole system with tar you may take advantage of this; there is some vaque advice in net. Now that i know that fstab is needed but it may be empty I must experiment again. Tomorrow may be busy day.
But I did try this in Intrepid as well as in Jaunty and there seems to be little difference. Anyhow amazing thing, and I certainly hope that there is some progress going on.

---

### Post by taavikko on 2009-01-21
> **petteriIII said:**
> Earlier I believed that fstab is needed for Ubuntu to operate, because when there is no fstab Ubuntu really doesn't operate properly. But when fstab is empty Ubuntu operates and even you can do www, USB automounts and so on. 

Fstab is needed to set static mountpoints, Most important / partition.
Hal is for dynamic devices such as usb-stick and other hdd-type things (lost for words there, since not an native language)

This still remains a mystery, but be happy to hear your testing results:)

---

### Post by Kow on 2009-01-21
I never once touched fstab until I started forcing my ext3 partition to be mounted using the ext4 driver. It already gets populated automatically.

---

