---
title: "Ubuntu 8.04 32 bit install problems (I/O FD error)"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by nazaryan on 2008-06-26
I am new to Linux and I have been trying to install the latest version of Ubuntu from the bootable cd without any success. I removed the quiet splash entry and it comes up with an I/O fd error when I try to install, then I just get busybox. I cannot even run the live cd part as that doesn't work either.
My PC specs are as follows:
Asus P5Q motherboard
E8400 CPU
4GB PC5300(1GB X 4)
8800GT Graphics card
2 X Samsung 500GB Hard drives

Please help as this is driving me crazy.

---

### Post by some12 on 2008-06-26
Hello all
Im not exactly new with Linux, but im having the same problems
Specs:
Asus P5Q motherboard
Q9300 CPU
4GB Ram
X850XT Graphics card
1 80 Giga Hard drive

Windows works nicely, except that my DWL-G520 Wlan card causes the system to freeze as soon as drivers are loaded. Im guessing its clearly a driver problem that ubuntu doesnt work...

---

### Post by nazaryan on 2008-06-26
I have sorted out the problem now, all I had to do was enable AHCI in the BIOS. The only thing is now I can't find any drivers for the onboard LAN so I have had to use an older PCI LAN card.

---

