---
title: "Having a hard time installing Ubuntu - can't see disks"
date: 2024-05-09
forum: Installation &amp; Upgrades
---

### Post by kb0wwp on 2024-05-09
I am having a heck of a time installing Ubuntu on a new machine I built.  Keep in mind, I have installed Ubuntu on dozens of different computers since version 14.04 and never had an issue.  I suspect the root of my problem is the Gigabyte GA-J1900N-D2H Quad Core Celeron mini ITX motherboard.

I am using two new drives - a Patriot Burst Elite 240GB and a Western Digital Red Plus 6TB.  I have verified that the SATA is set to "AHCI" in the BIOS, and that the BIOS recognizes both drives.

I have tried installing 22.04 Server from a USB drive, and Ubuntu 22.04 Desktop from a USB drive.  I have even tried installing 16.04 Server from a USB drive just to see if an older version would see the drives.

Ubuntu Desktop gives this message: "You need at least 14.8 GB disk space to install Ubuntu.  This computer only has 7.9 GB." (That's the size of the USB drive.)
Ubuntu Server gives this message: "Block probing did not discover any disks"

I googled the "block probing" and a few sites sent me to a page about a bug where I need to unmount the USB drive.  I tried that and it only showed me the USB drive as space available to install Ubuntu.

I would appreciate any help you could provide.

---

### Post by MAFoElffen on 2024-05-11
Which release are you trying to install?

In the BIOS Setting menu, please take a photo with your phone showing where is see's you attached drives, and what is says your SATA Mode is. 

We'll do the diagnostics from a Desktop Edition Live Image so that we have more abilities to exchange information easily. That way you can cut/paste the command into a Graphical terminal session, and cut/paste the output within the Code Tags of a post in a browser...

Please boot from a Desktop Installer LiveUSB, > Try > Open a terminal session.

From there, please post the results of this command, posted within Code tags:
```

lsblk -e7 -o name,label,size,fstype,mountpoint,model

```

---

### Post by oldfred on 2024-05-11
Have you updated UEFI and SSD firmware to latest available?
Even new models may have an update.

New systems typically need new kernel & driers that are only in newer distributions.
So testing with an old obsolete versions is not worth the effort.
I might then try 24.04 even though those with servers like to wait for 24.04.1 release for stability.

Is SSD a NVMe type? Those often conflict with a SATA port. Check manual.

---

### Post by MAFoElffen on 2024-05-11
I can verify that I did not see any surprises in DEV-Noble Server. It was stable.

---

### Post by tijiva on 2024-05-12
Hi,
It seems the motherboard is old and may have some dependencies to install new Ubuntu versions. The 'block probing' bug is a known bug of Ubuntu. You may try this [thread]("https://askubuntu.com/questions/1452315/dual-boot-ubuntu-22-04-in-legacy-bios-mode-mbr-partition") for enabling legacy mode and boot.

---

