---
title: "grub/dual boot problems"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by jhpope on 2007-02-18
Hello,

I'm a total ubuntu/linux n00b.  I've searched a bunch of the forums here and googled my problem but to no avail. I know there are alot of grub posts but I think mine is kinda unique.

I built a new system last weekend and decided it would be a good time to try out linux.  I have a 500GB SATA HD to which I made a bunch of partitions. One 200GB partition for Windows, one 200GB partition for games and storage, and One 100GB partition for ubuntu.

I successfully installed XP, then installed ubuntu on the 100GB , made a / for the root, /swap, and /boot.  Seemed to work ok but when I started up the system it went straight to windows. Out of nowhere yesterday when i restarted grub would load and i could choose which OS to load, before I had to boot from the ubuntu disc then choose to boot from the main HD and ubuntu would load.

I had to restart and I got a windows error something about ../system32/config or something like that i don't remember exactly, i had to repair from the windows disc.

Now it boots straight to windows again, when I boot from the ubuntu disc then choose to boot from the main HD it boots to grub and I can boot to ubuntu from there.

What the heck is going on and how do I make my computer boot to grub so I can choose my OS!

---

### Post by jhpope on 2007-02-18
i think i figured out my problem but not how to solve it.

i also have an 1 IDE drive that i keep for storing my music and running torrents.  i went into bios and booted straight from there and the grub loaded.

now...how do i get it to boot grub from my sata drive, and also i guess how do i get rid of that on my IDE

---

### Post by confused57 on 2007-02-18
> **jhpope said:**
> i think i figured out my problem but not how to solve it.

i also have an 1 IDE drive that i keep for storing my music and running torrents.  i went into bios and booted straight from there and the grub loaded.

now...how do i get it to boot grub from my sata drive, and also i guess how do i get rid of that on my IDE

I'd recommend you leave things set up the way they are, it doesn't hurt anything for grub to be installed on the IDE mbr...this way, you'd always be able to boot Windows by selecting your SATA drive to be booted first.

---

### Post by Coelocanth on 2007-02-18
Grub's on the MBR of your IDE drive. If grub's giving you the option to boot Ubuntu or XP, I'd go with Confused's advice and just leave the BIOS set up to boot your IDE drive first.

---

### Post by jhpope on 2007-02-19
yeah i suppose i can live with that. bothers me a little but i guess as long as it can work. now if i could only get my edimax ew-7581 wireless card to work. haha

thanks

---

