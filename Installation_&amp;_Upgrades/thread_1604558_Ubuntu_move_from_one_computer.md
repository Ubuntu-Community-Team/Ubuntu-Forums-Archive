---
title: "Ubuntu move from one computer"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by nusch on 2010-10-24
I need to send my notebook to warranty service, I can't stay without computer and my data, I need it for work so I will buy a PC, with 500GB disk instead my laptop 320GB, and I would like to clone system from laptop disk to PC one by raw copying whole disk. 
Currently I have:
Intel Core2Duo P8400  @ 2.26GHz
I would like to buy AMD Athlon 3200+ for PC.
Both CPUs are 64bit but second one have only one core. Does it matter somehow or only the architecture is significant?
Does anybody have experience with such moving system? What's more potential problems could appear? I've read something about grub and disk UUID's, probably I'll need to reconfigure xorg, but after correcting those will my system fully working in new setup?

---

### Post by P4man on 2010-10-24
Yeah, it should work if you disable proprietary video drivers first, and you might bump in to grub/uuid issues, but other than that, it should work without issues. Be sure the AMD machine has Athlon 64 3200+ cpu though, there have been Athlon XP 3200+s, and those do not support 64 bit.

---

### Post by coffeecat on 2010-10-24
If you raw copy the disk you should preserve the UUIDs.

If, by any chance, you do need to reassign a UUID and you know what you want, you can do so from the terminal with:

```
sudo tune2fs -U UUID /dev/sdaX
```Insert your UUID for 'UUID' and change sdaX as needed.

Where you might need to do this is where you have cloned an installation but the UUID(s) of the partition(s) have changed somehow. From a live-CD, read the /boot/grub/grub.cfg and /etc/fstab files to get the UUIDs you need and then use the above command in the live session.

In the old days of legacy grub, I would simply edit /etc/fstab and menu.lst from the live CD if the UUID had changed after I had done a system clone, but it's such a kerfuffle with grub2 that directly changing the UUID is quicker now.

---

### Post by nusch on 2010-10-24
Thanks all for fast reply, problem solved

---

