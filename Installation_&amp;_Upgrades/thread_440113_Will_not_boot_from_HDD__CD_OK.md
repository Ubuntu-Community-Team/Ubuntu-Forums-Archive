---
title: "Will not boot from HDD / CD OK"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by cbojanower on 2007-05-11
I am trying to install Ubuntu 7.04 on my machine and for some reason it will not run off the Hard Drive (It works fine off the CD)

The machine is a AMD XP3000+ Processor, 1.5 gigs RAM, MSI K7N2G motherboard (nForce2 Chipset). Only one 120 GB WD hard drive in the machine. The drive is set to Master and is detected as the primary master drive during the boot.

I ran the installer off the CD, took all the defaults and reformatted the drive all seems to be OK (No errors) . I set teh bios boot order to HDD-0, (Also tried Hdd1 and 2) then CD. Rebooted and removed the CD.

The boot seems slow but eventually tries to boot off the CD, then the NVIDIA loader , then finally fails and tells me to check drives and cables. I tried booting off the CD again and select the bot off the first drive option. I get an error message:

ISOLINUX: Disk Error 05, AX=0000, Drive 80
Press any key to continue

I tried running FDISK -l and got an error about drive being out of sequnce (Or similar) 

Any suggestions?

---

### Post by cbojanower on 2007-05-12
Still hoping someone can direct me towards an answer.

---

### Post by mysior on 2007-05-12
i have the same thing...:(

i tried also to install kubuntu and i was ok (on the same drive), but when i'm installing ubuntu i get over and over the same error:

```

Booting from local disk...
isolinux: Disk error 05, AX = 0000, drive 80

Boot failed: press a key to retry...

```

any advise?? help or something.. :)

---

