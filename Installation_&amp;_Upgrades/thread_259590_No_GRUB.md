---
title: "No GRUB"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by alecjw on 2006-09-17
I repartitioned my disk, shrinking my ext3 partition by 10GB so that I could reinstall windoze. And then I did reinstall windoze. Now, it boots from my windoze partition (hda2) whereas Ubuntu and GRUB are on hda1, meaning that I can't boot ubuntu. How do I install GRUB on hda2 and add windoze to the grub menu?
Thanks in adavnce.

---

### Post by randell6564 on 2006-09-17
Hi!
Boot into Ubuntu using the CD. Open a terminal and type:

'**sudo grub**'
Then type
'**find /boot/grub/stage1**'
whatever it returns ie.,hd0,0, that is what you want to enter with this next step.  So if it returns (hd0,0), you would type:
'**root (hd0,0)**'
then
'**setup (hd0)**'
then
'**quit**'

That should Overwrite the windows boot loader with GRUB, back to your MBR.

---

### Post by alecjw on 2006-09-17
Thanks. And will windoze be added to the list automatically?

---

### Post by randell6564 on 2006-09-18
> **alecjw said:**
> Thanks. And will windoze be added to the list automatically?

Not sure about that, but after reinstalling GRUB on my own system, I had my dual-boot option without doing anything to the GRUB menu.

---

