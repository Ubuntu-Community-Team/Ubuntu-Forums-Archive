---
title: "Cannot boot after updating with file manager"
date: 2013-12-03
forum: Installation &amp; Upgrades
---

### Post by Corvair on 2013-12-03
I have Ubuntu 12.04 loaded on a desktop AMD64. After updating with file manager I cannot boot anymore. When I insert the 12.04 disk this is what I get.
Bad Bios checksum
Starting Bios recovery
Checking for CD Rom
CD Rom found
Reading file P5RP.ROM
File P5RP"rom NOR FOUN

It keeps going into this loop and I cannot enter into the BIOS.

Without the CD in:
Checking for CD-Rom
CD_Rom not found
Checking for USB devide
USB device not found
Continually in a loop also.

I would reinstall Ubuntu 12.04 if only I could start anew from the CD, bnut I cannot enter the BIOS.

How can I get out of these loops and enter BIOS?
HELP HELP HELP PLEASE!!!!

---

### Post by fantab on 2013-12-03
More info about your computer will be helpful, like RAM, Graphics etc, model and make?
You don't need a CD/USB to 'enter' BIOS. You need to press/de-press key, like F2 or F10 or ESC. Find out what key works for your BIOS.

Reburn the ubuntu.iso to a new DVD/USB again.... and try again.
Also confirm with your MoBo manufacturer's website to see if you have the latest BIOS. You can choose to either 're-flash' the same BIOS version you have or upgrade it to the latest.
(However, before you upgrade your BIOS I suggest that you try the other options I pointed to, like entering BIOS with right key and redownload and reburn the ubuntu.iso to a new DVD).

---

### Post by Corvair on 2013-12-04
> **fantab said:**
> More info about your computer will be helpful, like RAM, Graphics etc, model and make?
You don't need a CD/USB to 'enter' BIOS. You need to press/de-press key, like F2 or F10 or ESC. Find out what key works for your BIOS.

Reburn the ubuntu.iso to a new DVD/USB again.... and try again.
Also confirm with your MoBo manufacturer's website to see if you have the latest BIOS. You can choose to either 're-flash' the same BIOS version you have or upgrade it to the latest.
(However, before you upgrade your BIOS I suggest that you try the other options I pointed to, like entering BIOS with right key and redownload and reburn the ubuntu.iso to a new DVD).

Thanks for your reply.  The computer is equipped with an ASUS P5Q Premium motherboard, 4XOCZ PC2 8500 2GB RAM, 2X 500GB hard drives, XFX GF 7300GT grafics board.
Usualy the F2 key should enter into the BIOS but now it has no effect. What if I diconnect the hard drive with the OS and try loading the OS on the other hard drive?

---

### Post by oldos2er on 2013-12-04
Look up updating BIOS (or possibly clearing CMOS) for your motherboard; since BIOS loads before any OS or hard disk changing them won't help.

---

### Post by Corvair on 2013-12-04
> **oldos2er said:**
> Look up updating BIOS (or possibly clearing CMOS) for your motherboard; since BIOS loads before any OS or hard disk changing them won't help.

Thanks for your reply. I used the P5Q Premium Intel P45 Chipset Suppoort DVD and was able to read file P5QP.ROM this time and the BIOS was reset apparently. Then it asked to restart the computer, which I did. I got the same result as before, file P5QP not found. So I tried the support disk again with the same result. After restarting the computer now I don't have anything comming to the monitor. Looks like the BIOS is completed corrupted. I really don't know what to do next.

---

### Post by holycow131415 on 2013-12-05
Sounds like your motherboard died.

---

### Post by oldos2er on 2013-12-05
> I really don't know what to do next.

I'd contact ASUS support.

---

