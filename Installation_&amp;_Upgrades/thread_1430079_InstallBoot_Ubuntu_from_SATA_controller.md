---
title: "Install/Boot Ubuntu from SATA controller"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by Zaserov on 2010-03-14
Hello all,
I'm currently attempting to install Ubuntu onto an older PC I have to re-purpose it as a media server/htpc. As it is an older mobo, there is no on-board SATA support, so I went and got a controller card and a new Seagate hard disk. I then put Ubuntu onto a usb stick, as the cd drive seems to be out of comission as well. 

This all went well, and the Ubuntu shell from the flash drive boots up fine. The problem is that, not only does the installer not find the drive after it scans, I don't think Ubuntu sees it at all. I used the pci detector command, and it showed
"raid bus controller: device 0022:0000"
which  I'm guessing is the card, but am not sure. 

The system, as far as I can see:
Shuttle AN35N-Ultra mobo
Seagate 1.5 TB hard drive (jumped to 1.5 transfer)
Sabrent SBT-SRD2 2-port SATA PCI host controller card (with RAID function)

This a fresh install, insofar as there's only the one drive hooked up and it's fresh out of the box.  The driver disk that came with the controller says that Linux should automatically recognize it and have drivers.

I'm not entirely sure as to if this is even possible, as I bought then new stuff on a whim without really thinking about booting from a non-native disk transfer type. So the questions I have are
1) Is this even possible?
2) How can I get the OS to see the drive and then install to it?

Thanks much.

---

### Post by Zaserov on 2010-03-15
As an update, I've tested the hdd on my main computer, and it recognizes it without difficulty, so I know that isn't the problem.

---

### Post by Zaserov on 2010-03-17
I've now successfully installed Ubuntu on the drive, hoping that if I played with the boot settings that it could catch the new drive. But no such luck. Any suggestions?

---

