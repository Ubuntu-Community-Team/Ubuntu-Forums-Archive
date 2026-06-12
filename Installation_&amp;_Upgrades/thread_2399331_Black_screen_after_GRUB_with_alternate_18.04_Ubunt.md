---
title: "Black screen after GRUB with alternate 18.04 Ubuntu Server install image"
date: 2018-08-24
forum: Installation &amp; Upgrades
---

### Post by Gabriel_Smith on 2018-08-24
I have just gotten a new laptop (Lenovo X1 Yoga 3rd Gen), so time to install Ubuntu on it! I like to build up from a minimal install so I typically install Ubuntu Server and then build up from there. I like to leave the Windows install that comes on the laptop on there and dual boot. As the new "standard" server installer only seems to allow you to wipe a drive to a clean slate when installing and I want to keep the existing Windows install, the alternate installer is my only option.

My problem comes about when I try to actually boot the installer. I can easily get to the GRUB prompt, and after selecting the "Install" option the screen goes black (though is still obviously on) and nothing is displayed. I have tried removing the "quiet" kernel options and setting "--verbose text" to see if I get any output that I can work with to no avail. I have also tried the classic "nomodeset" with no improvement. To give insult to injury, the "standard" server installer boots fine and lets me get far enough to show me that it wants to nuke my drive. The desktop live "CD" also boots without issue and was actually used to begin with to resize the existing Windows partition to make way for Ubuntu.

I have tried a handful of USB drives, burning the ISO to them using Rufus 3.1.1320. I have Secure Boot disabled and the boot mode set to UEFI only. I have attempted to boot from server install "disks" for 17.10 and 16.04 with the same issue.

So, any advice on how to debug this further or other avenues I could look at for installing Ubuntu without wiping my drive?

Thank you in advance.

---

### Post by Gabriel_Smith on 2018-08-25
I have "solved" my issue by using the "new" server installer to install  to a throwaway USB stick and then copying the partitions over and  modifying the requisite files for GRUB and fstab. I can't say I enjoyed  spending an evening doing this, but everything seems to be booting fine.

---

### Post by donlucacorleone on 2018-10-17
Hi, what's the "new standard" server installer? I can't find it in Ubuntu releases, only the official one Ubuntu 18.04.1 LTS.
I'm facing same issue, of course...
Thanks

---

