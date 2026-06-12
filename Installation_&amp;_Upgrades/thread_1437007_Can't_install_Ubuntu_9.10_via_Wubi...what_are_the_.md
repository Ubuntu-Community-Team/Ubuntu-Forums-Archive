---
title: "Can't install Ubuntu 9.10 via Wubi...what are the possible reasons?"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by huflor on 2010-03-23
Hi! I attempted to install Ubuntu 9.10 on my desktop by using Wubi. I downloaded it to my desktop...run wubi, insert a password for the new account, and clicked "install". The installation files (700MB) was downloaded and checked, after which I was asked to reboot. I selected Ubuntu at the boot screen. 

After that the Ubuntu icon showed up for about 30sec then suddenly disappeared...monitor went into sleep mode and my cpu silent. The installation is supposed to continue still for another 10-15 minutes and the machine should reboot again but unfortunately mine did not progress anymore. I've repeated these steps 5 times...still no joy. Is this hardware or driver problem? What's preventing my install to succeed? How do I troubleshoot this?

---

### Post by Mark Phelps on 2010-03-23
Best initial way to troubleshoot is to download a LiveCD image of 9.10, burn that to CD, and boot into that.  Do NOT install it.

This will give you a good feel for how well Ubuntu 9.10 detects your hardware and installs the proper drivers.

Anything that does not work in LiveCD mode is going to range from trivial to impossible to fix after installation.

If you report back with specific problems you encountered in LiveCD mode, we may be able to help.

---

### Post by Sef on 2010-03-23
What are your system specs?

---

### Post by huflor on 2010-03-23
even with liveCD mode its the same thing. 32bit, AMD Athlon dual core 4400, 2.30 GHz

---

### Post by sendblink23 on 2010-03-23
I wanted to test it out...

It happened to me as well, after running wubi... finishes downloading 9.10 & wubi finishes its stuff... then asks for restart... as soon computer boots up you select Ubuntu... right there after a few seconds Monitor goes to sleep(when its suppose to run the 9.10 installer... but it doesn't do anything - just monitor in sleep mode)


I still don't know why it does that, on past ubuntu versions it works perfectly fine with Wubi...  Eitherway....  through using a burned copy of Live CD 9.10 it runs fine(booting computer with live CD, not Running Wubi from CD or from what Wubi installed with ESC options)... so I'm guessing its an issue with Wubi + Ubuntu 9.10

Tested it on my desktop:
AMD Phenom ii x4 965be C3
MSI 770-C45 AM3
8gb 1600Mhz DDR3
ATI Sapphire Radeon HD 4650 1Gb DDR2 PCI-e
1TB 7200rpm Windows 7 Ultimate x64
400GB 7200rpm Snow Leopard 10.6.2
200GB 7200rpm Ubuntu 10.04 LTS beta
100GB 7200rpm for OS Experimenting

Anyways... this was just testing according to what the thread poster mentioned.. I wanted to test on my self to see if it happened to me... and yes it did too... Wubi works fine for 8.10, 9.04... but 9.10 gives Monitor in sleep mode. So for me Installing regularly Ubuntu 9.10 from Live CD that works perfectly fine.. but not through Wubi.

---

