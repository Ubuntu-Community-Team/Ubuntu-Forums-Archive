---
title: "Need a GRUB2 entry for booting karmic to RAM"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by last1 on 2010-03-30
Sup yall. I been following [this wiki page]("https://wiki.ubuntu.com/BootToRAM") to get a livecd iso of karmic loaded onto my ramdisk, and it worked well until the last step where I need to modify grub. The wiki was written a long time ago and does not cover GRUB2. I tried as best I could to get what I thought should be on there as an entry, and it boots ok at first but then hangs, saying "Waiting for root filesystem". I didn't specify that in the entry since I didn't know what to put. Can someone help me out? Here's what I've got in the entry so far-

menuentry "karmic ram session" {
         linux   /casper/vmlinuz toram splash
         initrd  /casper/initrd.lz
}

I guess that I'm supposed to set the root as something, but where? I got no idea where the root of a ramdisk is.

---

