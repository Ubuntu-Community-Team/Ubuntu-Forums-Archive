---
title: "Install over previous installation"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by blue_shift on 2006-06-29
I'd like to install Kubuntu 6.06 onto my hard drive, from the liveCD environment. I currently have a partition running Ubuntu 5.10 (hda6). Can I install directly to hda6 using the liveCD installer, and then boot as usual?

Grub executes the following currently:
```
root=(hd0,5)
kernel /vmlinuz root=/dev/hda6
initrd=initrd.img
```

Will this be sufficient to simply type this at grub after install and then edit menu.lst once installed?

Can the kubuntu installer install grub to the root of hda6 for me as opposed to the mbr? Currently the windows bootloader boots grub and I'd prefer to keep it that way.

Finally, the kubuntu live CD won't boot except in graphical safe mode. I have an ATi Radeon 9250 (9200Pro) for primary display device. The booter says "accessing restricted drivers" in text mode, then returns to the loading menu with the blue kubuntu logo but no text is present and nothing happens.
Does this mean an underlying error or will it be okay if I just install normally?

Many thanks.

---

### Post by aysiu on 2006-06-29
If you install over your old installation, your old installation will no longer exist in any way.

Did you want to upgrade instead? If so, you need the Alternate CD (not the Desktop CD).

---

### Post by blue_shift on 2006-06-29
Well I would upgrade if I had the Alternate CD, but since I don't have the CD nor the bandwidth to get the iso, I won't.

---

### Post by aysiu on 2006-06-29
That's fine. You don't have to upgrade if Breezy works just fine for you.

---

### Post by blue_shift on 2006-06-29
I will install Dapper over Breezy, it's just I can't do an upgrade pe se. Plus, I'm switching from Ubuntu to Kubuntu, so it would become messy I imagine.

---

### Post by wifiabc on 2006-06-30
The liveCD would install grub to the MBR.

---

