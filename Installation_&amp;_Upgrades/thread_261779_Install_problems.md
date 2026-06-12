---
title: "Install problems"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by samssf on 2006-09-20
I have a question I'm hoping someone can answer.

I have 3 hard disks, all SATA.

My first sata (when recognized by bios) holds windows XP.

Other 2 are on a RAID mirror setup.


When I tried to install Ubuntu a week or so ago, what happened is when I boot Ubuntu, it recognizes my disks in this order:
SDA = raid drive
SDB = other raid drive
SDC = Windows drive


However the other in bios is:
drive 0 = windows drive
drive 1 = raid drive
drive 2 = other raid drive


So, when I install linux I have to tell it to put GRUB onto HDC. Since thats the drive I boot to and I dont want to F with my raid drives (mirrored)

However after the install, when I get to grub.... the disks are in opposite order. so for "boot windows" option, grub config says:

root (hd2,0)
savedefault
map(blah blah)
map(blah blah)
chainloader +1

But when I wanted to boot windows, I would have to edit the first line to say:
root (hd0,0)

and to boot linux:
(hd0,1)


How do I avoid this in the future? I tried turning off the raid drives during install but it doesnt help.

Why? Not sure. I think when I plugged them back in the order and drive numbers got turned around at the grub screen.

I can do it manually but it's a pain and I'm afraid it will mess up my setup.

Any ideas?

---

