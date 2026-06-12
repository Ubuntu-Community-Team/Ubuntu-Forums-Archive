---
title: "New kernel found my XP."
date: 2010-01-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dagrump on 2010-01-20
What I thought was a setting or just a bios issue, must have been software related. I was having to change boot order in the bios, as grub2 wasn't seeing the XP install. But, after todays updates, I rebooted & about fell out of my chair.
And it may have helped my wireless functioning, it seems to be working well w/o turning power management off.
I always love a nice surprise from an upgrade, sure beats those oh whoops ones.

---

### Post by phillw on 2010-01-20
> **dagrump said:**
> What I thought was a setting or just a bios issue, must have been software related. I was having to change boot order in the bios, as grub2 wasn't seeing the XP install. But, after todays updates, I rebooted & about fell out of my chair.
And it may have helped my wireless functioning, it seems to be working well w/o turning power management off.
I always love a nice surprise from an upgrade, sure beats those oh whoops ones.

You've got hand it to those devs ... they're a good bunch :D

10.04 is just getting better & better. I'm sure they deliberately put glitches in just to see f we're paying attention.
:lolflag:

Regards,

Phill.

---

### Post by cariboo on 2010-01-20
It probably showed up because update-grub was run when the new kernel was installed.

---

### Post by dagrump on 2010-01-20
I tried putting grub on sda & on sdb with the install, & tried to run update-grub. It just never could see it, I fought it for several hours one night & finally resigned myself to change boot order in the bios if I needed the scanner (reason for XP).
This mobo has some weird chipset, & I can't locate the book to make sure of the settings. But whatever was going on with it was automagicly fixed.
I'm too lazy to try ranch hands custom config tricks, in fact I was fine changing it in the bios as I didn't think it had anything to due with ubuntu. I would of sworn it was the mobo or something along that line. 
It's a prefect testing candidate it wasn't being used & had an empty drive. Now it has A2 on sdb with grub installed on that drive & the windows bootloader on sda. So if I toast the ubuntu I can still change boot order and use the scanner. I like it!!

---

