---
title: "bootmgr missing"
date: 2012-06-09
forum: Installation &amp; Upgrades
---

### Post by vistanarvas on 2012-06-09
hi 

ive been trying to install ubuntu on my pc but it does not work
iv did it on my laptop and had no problems
on my pc ive tryed everything to get it work
i have 2 hard disk there on one i have windows vista
and on the other im trying to install ubuntu i format it and trying to boot from it but it keeps saying bootmgr missing
ive googled it but nothing helped or i could use
i can still boot in withe the disk with windows on it so that is how i can edit the disk with ubuntu only i dont know what i can do

i hope someone can help
vista

---

### Post by Basher101 on 2012-06-09
> **vistanarvas said:**
> hi 

ive been trying to install ubuntu on my pc but it does not work
iv did it on my laptop and had no problems
on my pc ive tryed everything to get it work
i have 2 hard disk there on one i have windows vista
and on the other im trying to install ubuntu i format it and trying to boot from it but it keeps saying bootmgr missing
ive googled it but nothing helped or i could use
i can still boot in withe the disk with windows on it so that is how i can edit the disk with ubuntu only i dont know what i can do

i hope someone can help
vista

I think Grub got installed on the other hard disk, while the one with Vista gets booted first. Can you confirm this? or does your "ubuntu" hard drive boot first`?

---

### Post by vistanarvas on 2012-06-09
> **Basher101 said:**
> I think Grub got installed on the other hard disk, while the one with Vista gets booted first. Can you confirm this? or does your "ubuntu" hard drive boot first`?

i can make one boot first by switching some wires

---

### Post by vistanarvas on 2012-06-09
but if i look in the ubuntu map and all there are maps saying grub but there empty

---

### Post by Basher101 on 2012-06-09
> **vistanarvas said:**
> but if i look in the ubuntu map and all there are maps saying grub but there empty

ubuntu map?

and you do NOT need to change wires to change the boot order of hard disks, you can change it in the BIOS.

---

### Post by vistanarvas on 2012-06-09
> **Basher101 said:**
> ubuntu map?

and you do NOT need to change wires to change the boot order of hard disks, you can change it in the BIOS.

in the bios it only says hard disk and there is only one option for it

and yea the Ubuntu map
ive got computer/F/Ubuntu/ more maps

---

### Post by Basher101 on 2012-06-09
> **vistanarvas said:**
> in the bios it only says hard disk and there is only one option for it

and yea the Ubuntu map
ive got computer/F/Ubuntu/ more maps

i still do not know what these maps are supposed to be, first time hearing about any "maps" in ubuntu. Can you make a screenshot and post it to clear me up?

---

### Post by vistanarvas on 2012-06-09
> **Basher101 said:**
> i still do not know what these maps are supposed to be, first time hearing about any "maps" in ubuntu. Can you make a screenshot and post it to clear me up?

[ATTACH]219430[/ATTACH]

this worked for my laptop

---

### Post by Basher101 on 2012-06-09
> **vistanarvas said:**
> [ATTACH]219430[/ATTACH]

this worked for my laptop

Ooooh

this is just the WUBI install!

it makes a virtual partition INSIDE of windows, you do not install ubuntu "for real". Ubuntu boots through windows in the Wubi installation. To make an actual install of Ubuntu you need to boot from the Live CD. Change the bootorder in your BIOS to CD/DVD drive and install it from there to your partition.

---

### Post by vistanarvas on 2012-06-09
ok thanks

---

### Post by vistanarvas on 2012-06-09
> **Basher101 said:**
> Ooooh

this is just the WUBI install!

it makes a virtual partition INSIDE of windows, you do not install ubuntu "for real". Ubuntu boots through windows in the Wubi installation. To make an actual install of Ubuntu you need to boot from the Live CD. Change the bootorder in your BIOS to CD/DVD drive and install it from there to your partition.

ok i did the live usb thing but its stuck
and its saying

[ATTACH]219432[/ATTACH]

---

### Post by vistanarvas on 2012-06-09
> **vistanarvas said:**
> ok i did the live usb thing but its stuck
and its saying

[ATTACH]219432[/ATTACH]

nvm solved

but I have a new problem but ill make a new thread for it
ill mark this one as solved

thanks for the help

---

