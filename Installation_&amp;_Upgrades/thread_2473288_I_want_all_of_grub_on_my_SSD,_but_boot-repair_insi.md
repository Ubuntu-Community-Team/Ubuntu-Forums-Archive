---
title: "I want all of grub on my SSD, but boot-repair insists on routing through my HDD"
date: 2022-03-30
forum: Installation &amp; Upgrades
---

### Post by halfbeing on 2022-03-30
I have Windows on my SSD (which Ubuntu sees as sdb). I have just installed Ubuntu on my HDD (sda), but I put /boot on the SSD (sdb4) because I want to boot from the SSD and I mostly want to use Windows. Unfortunately, the Ubuntu installer put GRUB on sda. To fix this, I used the boot-repair live USB, to put GRUB on sdb. This I was able to do.

The problem is that boot-repair only offers me two options for "OS to boot by default": "sda3 (Ubuntu…)", and "Windows (via sda3 menu)". This means that part of the boot process still depends on sda, even when I boot from the /boot partition that is on sdb into the OS that is on sdb. I don't want this. I want everything to do with booting to be on sdb because I don't want two possible points of failure for booting (two disks) instead of just one.

How can I remove sda entirely from the boot process (except, of course, when I actually want to boot into Ubuntu)?

---

### Post by tea for one on 2022-03-31
I think that you may be making this more complicated than necessary.

Each OS should be installed in UEFI mode with GPT
Each drive should have an EFI partition.
Each disk must contain a boot loader i.e. Windows boot manager on your SSD and Grub (for Ubuntu) on HDD.
Windows is your main OS, therefore you use your UEFI Settings to make this disk first in boot priority.
Ubuntu used infrequently can be booted via your dedicated key to access the one-time boot menu.

Each OS will boot independently of the other.

You mention that [COLOR="#0000FF"]I don't want two possible points of failure for booting (two disks) instead of just one[/COLOR].
If everything is controlled by one boot manager (i.e. Grub) then if Grub fails, you may not be able to boot either OS.
If two boot managers operating independently fail simultaneously, then that would be excessive bad luck.

---

