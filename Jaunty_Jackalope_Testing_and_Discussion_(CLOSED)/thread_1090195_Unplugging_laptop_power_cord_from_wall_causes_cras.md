---
title: "Unplugging laptop power cord from wall causes crash?"
date: 2009-03-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nixie Pixel on 2009-03-08
I have a Compaq Presario A909US running Jaunty, and when I unplugged my power cord from the wall to switch outlets, my desktop crashed and threw me back to the login screen after a few seconds of weird graphics flashes.

Is this a known error?

Thanks!

---

### Post by nyarnon on 2009-03-08
No, just made sure and tested it on my eeepc but it responds as expected, to me this sounds as a current issue (a current spike) throwing you hardware from it's feet. I suggest till you know what is happening to shut down first to protect your hardware.

---

### Post by ssam on 2009-03-08
could be a range of things. does anything interesting show in
```
dmesg
```
or
```
cat /var/log/Xorg.0.log.old
```
after you log back in.

please file a bug.

---

### Post by afv on 2009-03-08
That happened to me two or three times last week:

Two days ago I removed the cord, waited some seconds (because I was already expecting this to happen) and then removed the USB mouse: when I removed the mouse there was "full" disk activity (activity light always on) and then X restarted and brought me back to the login screen.

Before this it happened when I wasn't using the mouse. It happened when I unpluged the cord and also when I pluged it in. Full disk activity that never ended (or I didn't wait the necessary time) and if I can remember using SysRq to reboot didn't work.

I'll try to reproduce it.

**edit:**
Unplug: nothing
Plug:   nothing
Unplug: nothing
Plug:   nothing
Unplug: nothing
Plug:   breakage.

[full disk activity on the last minutes with dmesg full of I/O errors and won't stop... have to reboot. be right back]

**edit2:**
Nothing special on Xorg.0.log.old (I think that due to I/O errors nothing was stored)... What other files should I look for?

Nixie Pixel, can you reproduce it? Looks like a similar problem but not the same...

---

### Post by Nixie Pixel on 2009-03-10
I haven't been able to reproduce it, and so I haven't been able to give any more info on this...

Anyway, thanks for the suggestions.

---

### Post by ronacc on 2009-03-10
have you got kerneloops installed ? if not try it it may catch something . Don't you just love things that don't leave tracks you can follow ?

---

### Post by afv on 2009-03-16
Moments ago, when I connected the power cord:

> [15132.988120] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[15132.988135] ata1.00: cmd c8/00:10:5d:cd:62/00:00:00:00:00/e0 tag 0 dma 8192 in
[15132.988138]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[15132.988144] ata1.00: status: { DRDY }
[15138.044065] ata1: link is slow to respond, please be patient (ready=0)
[15143.028067] ata1: device not ready (errno=-16), forcing hardreset
[15143.028080] ata1: soft resetting link
[15143.210279] ata1.00: configured for UDMA/133
[15143.210300] ata1: EH complete
[15143.223422] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[15143.223461] sd 0:0:0:0: [sda] Write Protect is off
[15143.223467] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[15143.223518] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

