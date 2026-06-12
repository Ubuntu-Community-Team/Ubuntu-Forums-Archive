---
title: "USB Stick Upgrade"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by zipher on 2011-02-03
Hi, I am trying to upgrade my Ubuntu distro from a dodgey Jackalope, using a bootable USB stick (256Mb) and my target version will be Lucid.

(I am using an old laptop that doesn't write to CD ROM's, and moreover, when upgrading from Hardy many months ago I tried going straight to Koala and ended up with a non-functioning option in my chainloader options... the upgrade to jaunty worked, just, but there's learning to do!!)

I followed the official instructions on partitioning my memory stick, copying 

[B]vmlinuz
initrd.gz[/B]

and a **config file**

followed by

**mini.iso**

It doesn't work.
I have questions as follows, all pointers gratefully received.

**Questions**
(1.) When copying the small image to the USB stick, typically businesscard ubuntu i.e.

mini.iso

should this be burnt as an image onto the pen? If so, how?

(2.)My BIOS system, mentions booting from floppy devices of which there are none, and does not mention USB at all. I have set the boot order to floppy (legacy) drives, followed by the other stuff.
Upon booting I get

Error reading diskette...

Hence: How does one update BIOS if possible or no?

Thanks     ;)

---

### Post by zvacet on 2011-02-03
I don´t know do you can boot usb if you don´t have it as option in BIOS.If you still have Jaunty you can upgrade to Karmic (previous try from Hardy to Karmic failed because you skip version) following [this]("https://help.ubuntu.com/community/EOLUpgrades/Jaunty") guide.

---

