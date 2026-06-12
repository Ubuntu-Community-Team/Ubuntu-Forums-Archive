---
title: "initrd reverting to old version"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by richardcrewe on 2011-09-13
Hi,

I'm trying to create a custom installation disk to test some hardware. I've rebuilt the kernel with the changes I need and created a new initrd with the modules for the new kernel.

All works well for the first use, the system boots from the USB drive using the modified kernel and initrd. Second use, it fails with missing modules. It appears that the initrd has been modified during the first boot to remove all the modules associated with the new kernel version.

What's causing this and how can I stop it?

-- 
Richard Crewe

---

### Post by dino99 on 2011-09-13
disable automatic updates from synaptic

---

### Post by richardcrewe on 2011-09-13
It's probably not off-site updates. I've not actually installed anything, I'm just trying to repeatedly boot the installation disk without it changing its contents.

-- 
Rich

---

### Post by richardcrewe on 2011-09-13
It appears that /scripts/casper-bottom/43disable_updateinitramfs can be persuaded to think it's running on a CDROM. Then it will create a script that announces that can't update the initramfs rather than linking to a script that does update it.

-- 
Richard Crewe

---

### Post by mörgæs on 2011-09-13
Good, please mark the thread 'solved' using 'thread tools'.

---

