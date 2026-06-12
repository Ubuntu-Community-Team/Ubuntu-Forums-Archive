---
title: "installation problem"
date: 2004-10-31
forum: Installation &amp; Upgrades
---

### Post by roelof on 2004-10-31
Hello, 

Im trying to install Ubuntu Warty. 
Everything is going well to the part where the reboot takes place.
First on startup i get the following error message: 

Modprobe: fatal: error inserting pciehp .... : Operation not permitted.
Modprobe : fatal : error inserting shpchp ... : Operation not permitted.

After that the startup is going till the part where is can see the welcome message and where i must press ok. Then my computer is hanging.

I have a AMD K6-II processor. Nvidea graphical card and 256 MB Memory.

How can is solve this problem ??

Roelof 

I puzzeled out that my ps-2 keyboard is freezing.

---

### Post by dorris on 2004-10-31
yeah, i'm in a similiar situation, but the reverse applies to me!!!

mine hung up on install, until I tried the expert , and noticed the input locale was where it hangs, popped out usb keyb, swapped with ps2, and all is good, once in gnome, I pluged in the usb keyb, and it detects, and works great.

BUT, as long as the usb keyb is in during boot sequence, it consistently hangs on boot.

No such device ! hwrandom.ko

I tried playing in bios to remove plug and play Os, but these p4 bios have removed that option!
I tried removing usb keyb support in bios, still no love!

As suggested in the bugzilla, I tried looking for a USB legacy mode, did not find one on my board!


any help, this ps2 keyb I'm using is an old clicky key type, and i'd rather smooth out install than go find another ps/2 keyboard i'm comfortable with.

---

### Post by roelof on 2004-11-05
hello, 

After talking on IRC i discovered that is was propaply a bug. Therefore i post this problem on the bug-page. 

Roelof

---

### Post by ctof on 2004-12-21
hi, 
excuse me
i have the same pb
is there a workaround before the official path of this bug

i think it is the same pb here: [http://www.ubuntuforums.org/showthread.php?t=1648&highlight=Operation](http://www.ubuntuforums.org/showthread.php?t=1648&highlight=Operation)
i have the same error without any usb device plug into my computer

Thx
Christophe

---

