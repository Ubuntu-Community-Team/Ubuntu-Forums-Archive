---
title: "Weird Install Fussiness"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by Perrako on 2007-10-29
So, I just got through installing Ubuntu 7.10 on a SATA hard drive partitioned with XP on the other half (ubuntu replaced sabayon, so I know I can boot between these fine.) However, when I boot now, it posts, goes black, and then restarts. No GRUB, no bootloader, nothing. Even weirder is that if I boot from the ubuntu cd and choose the last option (boot from first hard disk), everything's fine -- I can boot to ubuntu or XP. What's wrong? What can I do?

Specs:
Mobo: Asus p5n-e sli
VIdeo: Geforce 7950 GT
Processor: C2D E6400
2 GB G.Skill RAM

---

### Post by Doomguy0505 on 2007-10-29
Install 7.04 instead, clearly 7.10 is unstable

---

### Post by Perrako on 2007-10-29
Is that really the only solution? I'm inclined to try just a little bit harder.\

EDIT: So, I've tried a few things. I tried setting the boot flag on the linux partition to bootable. Exact same problem. The other issue is that whenever I make a small modification in gparted, it crashes (but still shows the changes on reopening). GRUB says it installs to hd0, so I tried setting hda to bootable to no avail. My BIOS is all good, so what else can I do?

---

### Post by Perrako on 2007-11-01
So, I just ran sudo grub-install /dev/sda (my sata drive) and grub shows up. However, I now get error 22, no such partition. It's booting from (hd 2, 2), which is right. I cannot boot any of my partitions, however. I can still boot from the "boot from first hard disk" option on the ubuntu cd just fine -- also booting from (hd 2, 2). My /boot is /dev/sda3, so I'm baffled as to why this is happening. Thoughts?

---

