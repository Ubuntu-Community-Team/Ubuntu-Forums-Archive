---
title: "Ubuntu installer won't display external usb hard drive"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by Jester2006 on 2006-06-26
hi all,
currently have XP Pro on my acer laptop and have also bought an external 250gb hard drive, which i want to install ubuntu 6.06 on.
i go into my bios and set my external hd to boot before my internal and my cd/rom to boot first before all hd's. My prob is when i come to the partition part of the install, only my internal drive is listed. i've tried epert install but no success (not sure if i did it correct though).
This is really frustrating me as this is my first time using linux and i'm not totally literate with it yet, but getting there.
Any help REALLY appreciated
thanx

---

### Post by jvl on 2006-06-26
do you use alternate install cd? are usb modules loaded?

---

### Post by Jester2006 on 2006-06-26
no, its the iso img from this site. i've installed in onto my internal harddrive before and all went fine, so i kno the img is fine.
how do i load the usb modules??? probably something simple but i'm  innocent noob :)

---

### Post by jvl on 2006-06-26
I'm not saying that the cd image is bad, I'm just saying that the alternate install cd may be able to detect external usb devices. I haven't tried this myself. 

You could also search the forums or wiki, I've seen usb disk installation howtos around...

---

### Post by Jester2006 on 2006-06-26
cheers for the help, im just downloading the alternate cd now and will try that. Didn't know it existed. I tried most of the HOWTOs on external usb but with no prevail, although following them to a 'T' lol. will post back with after i try the alternate install, thanx again jvl

---

### Post by Jester2006 on 2006-06-27
alternate install cd didn't work, still won't read my usb hd. i don't think i've loaded my usb module because (in expert mode) when i 'detect hardware' (ie hd's + partitions) it asks which modules to load and only linux floppy is selected, which only displays my internal hd.
any help loading usb modules would be great great great

---

### Post by jvl on 2006-06-28
load these modules (from the top of my head): with modprobe:

ehci-hcd
usb-storage
scsi_mod
sd_mod

---

