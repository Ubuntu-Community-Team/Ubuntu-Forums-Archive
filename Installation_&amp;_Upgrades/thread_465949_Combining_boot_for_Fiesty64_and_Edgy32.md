---
title: "Combining /boot for Fiesty64 and Edgy32"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by jeremynd01 on 2007-06-06
I'd like to merge the /boot directories from a new Fiesty-amd64 install with an old Edgy-i386 install.

I have been running Edgy-i386 for some time (avoiding a 64 bit version for annoyances like no 64 Flash player), but I'm ready to try something new.  I had a very simple, two-partition scheme: /boot on hda1, and the root (/) for the rest.   I installed Fiesty on it's own root partition (so I would still have my working copy of Edgy, but be able to reboot to Fiesty).  During install, I wanted Fiesty to share the /boot partition with Edgy, but the installer said it wanted to reformat /boot (thus throwing out my edgy kernels).  I wasn't having any of that, so I installed everything in Fiesty's root.  The result was Feisty hijacking the MBR and pointing it to its own /boot, somewhere in the vacinity of hda3.

I'd LIKE to merge the two boot mount points into the hda1 partition.  Is it ok to just copy over Fiesty's kernels and such to hda1, make a new grub configuration that points to all of the right root directories,  and then use the liveCD to re-instate hda1 as "the place" for booting?  

My concern is that the Feisty kernel does not bear any mention of it being AMD64 (it is tagged "-generic," just like the i386 kernels), so their may be problems with same-name kernel updates between the 64- and 32-bit versions.

---

### Post by kidders on 2007-06-07
Hi there,

> **jeremynd01 said:**
> My concern is that the Feisty kernel does not bear any mention of it being AMD64 (it is tagged "-generic," just like the i386 kernels)Lol you're right. That's a little ... well ... stupid (frankly!), isn't it?

In any case, sharing a /boot partition isn't generally a particularly wise idea because, in many ways, it would defeat the purpose of having one in the first place. It might be smarter to simply remove Edgy's boot partition (assuming your hardware configuration would allow you to do that) and copy its contents into the /boot directory on its root filesystem.

At the very least, you might like to share /boot/grub between both OSs, and tweak both your systems so they overwrite each others' bootloaders. The result would be be that you'd never be quite sure whose grub you were looking at when you start up ... but it wouldn't make any difference.

> **jeremynd01 said:**
> During install, I wanted Fiesty to share the /boot partition with Edgy, but the installer said it wanted to reformat /bootThat's irritating as hell! At the same time, I suppose, it's easy to understand why the installer would insist on performing the format.

> **jeremynd01 said:**
> Is it ok to just copy over Fiesty's kernels and such to hda1, make a new grub configuration that points to all of the right root directories,  and then use the liveCD to re-instate hda1 as "the place" for booting?The answer is no, imo. I don't think sharing /boot would be workable. You shouldn't need a LiveCD to reorganise how your system boots though.

[SIZE="1"][COLOR="Silver"][UAResolved][/COLOR][/SIZE]

---

