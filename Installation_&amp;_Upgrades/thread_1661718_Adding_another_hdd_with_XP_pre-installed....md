---
title: "Adding another hdd with XP pre-installed..."
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by Baldrick_NZ on 2011-01-07
I have a 500Gb HDD which currently has only Ubuntu 10.04LTS installed on it. I also have another 80Gb drive with a fresh copy of XP on it (which isn't currently connected to the motherboard).

Both drives will connect via sata leads (currently I have only one sata lead and that is being used exclusively by Ubuntu), I'm buying another sata lead tomorrow for the XP drive.

When I finally connect both drives up to the motherboard, and boot, will the grub menu automatically see the XP drive (as well as Ubuntu) and ask which OS I wish to boot to? Or, will I have to somehow inform grub that XP is also an option now? If so, how would I do this?

Cheers & thanks in advance...

---

### Post by dino99 on 2011-01-07
its not automatic, you need to open a terminal & run:

sudo update-grub

then you will see a grub menu each time you boot (dual booting)

---

### Post by Baldrick_NZ on 2011-01-07
> **dino99 said:**
> its not automatic, you need to open a terminal & run:

sudo update-grub

then you will see a grub menu each time you boot (dual booting)

Thanks Dino,

So, once the XP hdd has been installed, do I boot to Ubuntu first then run the 'sudo update-grub' command? or, would I boot to Live CD and run the command from there?

Cheers.

---

### Post by presence1960 on 2011-01-07
> **Baldrick_NZ said:**
> Thanks Dino,

So, once the XP hdd has been installed, do I boot to Ubuntu first then run the 'sudo update-grub' command? or, would I boot to Live CD and run the command from there?

Cheers.

Yes, and make sure the XP disk is set to second in the hard disk boot priority in BIOS. Your ubuntu disk needs to be set as first, if it is not your machine will boot right to XP.

---

### Post by Baldrick_NZ on 2011-01-07
Wow - that was easy!!

Thanks guys..

---

