---
title: "System Hangs on all Ubuntu versions, please Help"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by tonypv on 2008-02-21
[SIZE="2"]Hi all,
           I was trying to install a version of Ubuntu on my home pc. But none of the Live CD can load fully. System totally hangs at the screen where, load process status is show using icons just after X is loaded. I tried version 5, 6.06 (both 64 bit and PC version), Ubuntu Ultimate 1.6, all same result. Can anybody help? I tried the noapic option also after searching on the net.
           My system configuration is 

AMD AMD Athlon 64 Processor 3000+
Asus A8N VM motherboard
768 MB DDR RAM
NVIDIA GeForce 6200 TurboCache (PCI Express 256MB)
SoundMAX HD Audio
250GB Seagate SATA Hard Disk
Liteon 20X DVDRW

             Any help will be highly appreciated. Thanks in advance.
                                                                                     Tony P V[/SIZE]

---

### Post by jim_in_dorris on 2008-02-21
I have the same or close to the same problem, and a similar hardware config.  I have...

AMD Athalon 64 3200+
ASUS MB
1 gig RAM
320GIG SATA2 hd
MSI NF6600GT Video
Sony DVDRW

I have 3 different Ubuntu disk, a version 5 Live CD, an install version of 5, and a 7.10 install, they all fail, but the install versions give me an error msg that says ... Kernal panic  eeek ??? 

I am new to Ubuntu, but have been working with computers for 30 years, including a 10+ year stint as a professional programmer, so I can usually figure stuff out, but this has me stumped.  Also during the install process, I see part of a message flash on the screen that says something about unable to allocate.



]

---

### Post by tonypv on 2008-02-21
Me too saw the kernel panic message. I tried knoppix 3.2 which came out to be the only one which could boot on my system. During that i saw a message IO APIC not connected.

---

### Post by jim_in_dorris on 2008-02-21
yeah, I think i will get a copy of Fedora from work and try it

---

### Post by Partyboi2 on 2008-02-21
try updating your bios 
or try another boot option
```
 acpi_skip_timer_override
```

---

### Post by tonypv on 2008-02-22
I tried Fedora 7 and OpenSUSE 10.2, they installed but hanged on booting. I somehow managed to get Fedora 7 working after disabling some services. The actual problem is still not clear. But i doubt its due to the service cpuspeed. because even after disabling firewall the system still hanged. only after disabling cpuspeed, it could boot.

I intend to try the Ubuntu 7.1 alternate install CD. Thanks for the help from all.

---

