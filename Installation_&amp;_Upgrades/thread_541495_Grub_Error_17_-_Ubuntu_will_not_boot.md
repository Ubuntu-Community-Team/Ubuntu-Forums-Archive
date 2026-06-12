---
title: "Grub Error 17 - Ubuntu will not boot"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by goldtech on 2007-09-02
I've be trying about 10 hours to figure out grub and am getting frustrated. I expected it to just work...

IS there a simple way to dual boot? I put GRUB in (h0,0) and the tried GAG which "saw" GRUB fine but when I got to the GRUB menu i get error 17. I renewed my MBR in XP, no change

It would seem to me someone smart must of figured out a way by now to make this painless by now?

I will give you any data you need to figure it out. What do you need to know?

Thanks,
Lee G.

I got one SATA drive and one ATA drive. XP is on the sata, Ubuntu is on the ATA(IDE).

hd0 = /dev/hdc
hd1 =/dev/sda
according to some listing routine in GRUB whose name I can remember...

---

### Post by Pumalite on 2007-09-02
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

Try this from a terminal (Applications/Accessories/Terminal):

Code:

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

Substitute your results from the find command for (hdx,x). It will probably be (hd0,1].

---

### Post by goldtech on 2007-09-02
Tried that exactly from a previous post - Did not work.

Anything else to try?

---

### Post by Pumalite on 2007-09-02
setup (hd0,0)

---

### Post by goldtech on 2007-09-02
Again, I tried that - it did not work.

I think the problen lies in the BIOS vs. Grub. Just a guess.

Does H0 mean that the IDE w/Ubuntu on it is IDE0 in the bios?

---

### Post by goldtech on 2007-09-03
Solved it. Got to go into BIOS and look for setting that adjusts boot order of hard disks. AFAIK not the setting that enables CD or floppy boots before HD but a specific setting swapping order of multiple Hard Disk booting. 

Put the one w/GRUB first - that fixed it for me.

---

### Post by logos34 on 2007-09-03
> **goldtech said:**
> Solved it. Got to go into BIOS and look for setting that adjusts boot order of hard disks. AFAIK not the setting that enables CD or floppy boots before HD but a specific setting swapping order of multiple Hard Disk booting. 

Put the one w/GRUB first - that fixed it for me.

It seems a lot of people confuse those two, the device boot order and the hard disk boot priority menu

---

