---
title: "multiboot on RAID mirror with XP SP3"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by Force Flow on 2008-11-05
I have a dell Dimension 5150 with an intel 82801GR/GH SATA RAID Controller running a RAID 1 Mirror.

I booted with the Kubuntu 8.10 CD, went through the installation process, selected the option to partition the drive for half XP half kubuntu (XP is taking up about 10GB on the 80GB drive)

When I went to start it up, I got the message "GRUB Loading stage1.5." repeat down the screen infinitely.

I booted up the live CD to check grub in the system config panel in the control panel GUI (I'm primarly a Windows user, so forgive me if I'm unfamiliar with the proper terminology for the moment), and it said it wasn't found.  Was that because it was a LiveCD and didn't have a boot sector or because GRUB really didn't install properly on the RAID array drive(s)?


Either way, it ended up destroying my primary drive, and had to restore by setting the old secondary disk as primary and rebuild the array. (This is a test workstation, so if I do lose the XP install, I just lose some time reinstalling it again)

I was hoping this would be an easy install, but it never fails that every time I try the new flagship distro, something goes terribly awry.  

So...what's the trick here?


Thanks :)

---

### Post by Force Flow on 2008-11-06
ok, I see that this is more software RAID than true hardware RAID.  I went ahead and opted to disable it to make things easier, as this seemed to be too much of a bother: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by psusi on 2008-11-06
You need to install to the raid device, not just the first disk ( /dev/sda ).  Also the livecd installer crashes when it tries to install grub at the end so you have to install grub manually.  I have heard that the alternate cd installer works fine though.

---

