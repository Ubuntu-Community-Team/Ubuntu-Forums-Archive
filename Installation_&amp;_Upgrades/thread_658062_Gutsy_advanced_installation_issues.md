---
title: "Gutsy: advanced installation issues"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by Aqualung on 2008-01-04
Alright, it looks like I have to resort to advanced installation options when installing Gutsy. I'll be installing it on its own exclusive SATA Raptor HDD. The system is a Woodcrest-based Xeon, with 7 HDDs, 4 of which are (legacy) IDE on a Promise IDE card. The rest of three HDDs are all SATA, two of which are Raptors: one for Vista and the other for Ubuntu/Gutsy. I'll be going with a manual choice in the "Prepare disk space" window, since I'll be using the ReiserFS format. I'll be doing away with a SWAP partition, as I have enough RAM.

The Big Question so far is: since going with the default settings for Grub screwed up my Vista MBR, I am thinking that I should choose the "Advanced..." button  installation options for Grub in the "Ready to install" window. The default choice there is (hd0), which I do not know what it means, as all my hard drives are seen by Gutsy as sda, sdb ... all the way to sdg (or SCSI1-7 (or is it 0-6?)). The Ubuntu Raptor shows up as either sdc or sdg, and I have not been able to tell why is it that it changes its "drive letter" between reboots. I tried entering (sdc) (or (sdg), as the case may be), but Grub doesn't get installed.

What am I doing wrong please?

---

### Post by njparton on 2008-01-04
hd0 is the master boot record on the first hard drive detected in your PC. In your case probably the MBR on sda (/dev/sda).

You can use gparted to see how sda, sdb etc map to your hard drives or 

```

fdisk -l

```

in a terminal.

If I were you I'd unplug all but one hard drive, install to that and then plug the rest back in when you're ready.

---

### Post by Aqualung on 2008-01-04
> **njparton said:**
> If I were you I'd unplug all but one hard drive, install to that and then plug the rest back in when you're ready.Thanks, I did that, but then the only way to dual-boot between Gutsy and Vista is to change the boot sequence in the BIOS. Surely, there's gotta be something more elegant and convenient than that, right? I even tried using EasyBCD with this scenario, but even though GRUB gets installed where I want it, it looks like it's not configured properly: I get Grub Error 17 whenever I choose the Ubuntu entry in EasyBCD's bootup menu. It's obvious that Grub points in this case to the wrong HDD.

Or is it that the next step you were going to suggest would have been to roll up my sleeves and proceed at editing Grub's settings? 

(At this point, I wish my mobo supported BIOS profiles: that would save me a lotta grief with all these boot managers and all that crap. Sadly it doesn't.:()

---

### Post by njparton on 2008-01-04
Grub can boot both windows and linux, correct.

If you had your windows hard drive connected during installation then Ubuntu is smart enough to detect it and add it to grub for you.

HOWEVER, to avoid Windows MBR overwriting issues, it's far safer to install ubuntu without the windows drive installed and then to add an appropriate windows entry to grub yourself.

Search this forum for how to do this.

---

