---
title: "kernel panic after updating kubuntu"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by mistafeesh on 2007-04-25
After fiddling around a bit with Ubuntu and Kubuntu, I decided to install kubuntu on my laptop. Using the CD sent from Canonical, I installed it fine, and was well on the way to getting everything set up how I want it. Then I saw that there was a little icon on the taskbar (or whatever you call it!) with an explanation mark. It told me I needed to let it run some updates. I did this. After lots of downloading and churning, it said it had finished but that there was an error in the update process. Now when I try to boot it, it gets as foar as "Ok, booting the kernel" then I get this message:

[17179569.184000] ACPI: Unable to locate RSDP
[       29.658728] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[       29.658821]



any ideas what I can do? If need be I can put the HDD in another computer to work on it from, and I'm OK with the terminal as long as it's not too complex!!


thanks,

Dan

---

### Post by pepsi_max2k on 2007-04-25
may be a problem with your boot manager (i'm assuming grub). check /boot/grub/menu.lst to make sure the ubuntu entry is ok, especially whether it has the right kernel version and partition.

---

### Post by mistafeesh on 2007-04-26
soory to be a pain, but I tried to rummage around using the boot CD and had trouble even mounting the disk so I just bit the bullet and did a complete reinstall. I'm a bit shy of updates now though!

---

