---
title: "Installer crashes during GRUB installation; tries to use EFI GRUB"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by anj-tuesday on 2014-04-18
Hey...

I don't know why, but Ubiquity appears dead set on attempting to install the wrong bootloader (grub-efi, not grub-pc) and then crashing, installing no GRUB at all. I do have a UEFI machine that came with Windows 7, but the harddisk was partitioned the old-school way without hidden recovery partitions, system partitions, boot partitions, or any other new-to-me shenanigans. The "UEFI BIOS" (sorry, but that's what it calls itself) is likewise configured for maximum old-schooliness in the boot department... although for some unexpected reason I haven't run into issues with "secure boot". 

This happens a lot -- the last time was with Ubuntu Gnome 14.04. I boot the live disc, it very briefly complains about something EFI-related before popping up its own GRUB, I boot, I start installing the OS, it crashes while attempting to install GRUB, I reboot into an existing OS, run update-grub from there, it picks up the new OS, I reboot into the new OS and install grub-pc from there. Annoying, but if I didn't *have* an existing OS this would be fiddlier. Super GRUB Disc and some similar tools I've tried won't boot, possibly due to the same or a related bug :/

Since I could always get it to work I really don't feel like reformatting the HD the EFI way and reinstalling both a fairly customised Ubuntu (and Windows 7 with a sketchy recovery disc. + all the [s]applications[/s] games). Not to mention there's no guarantee that *that* would work better...

---

### Post by kc1di on 2014-04-18
Hi Anj-tuesday,

I would go[ here ]("https://help.ubuntu.com/community/Boot-Repair")and download a copy of boot-repair and run that it should fix the problem for you,  It sounds like you may have gotten a win7 machine that has uefi enabled. just a guess though boot-repair has been pretty good here at sorting out uefi problems for me. good luck.

---

### Post by oldfred on 2014-04-18
If you have system configured for BIOS boot with MBR partitions, you will not have gpt partitions with the required efi partition for grub-efi to install.
And how you boot installer either UEFI boot mode or BIOS boot mode is how it installs. You need to be sure to boot in BIOS mode, if you want to install BIOS boot with grub-pc not UEFI boot with grub-efi.

If first install screen is grub you have booted in UEFI mode. If you get tiny accessibility icons and purple screen you are in BIOS mode.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by anj-tuesday on 2014-04-19
> **oldfred said:**
> If you have system configured for BIOS boot with MBR partitions, you will not have gpt partitions with the required efi partition for grub-efi to install.
And how you boot installer either UEFI boot mode or BIOS boot mode is how it installs. You need to be sure to boot in BIOS mode, if you want to install BIOS boot with grub-pc not UEFI boot with grub-efi.

If first install screen is grub you have booted in UEFI mode. If you get tiny accessibility icons and purple screen you are in BIOS mode.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Hm. Then the installation USB does boot in UEFI mode, although I can't figure out what else I could reconfigure about my computer to keep it from doing that. I've already switched all the available boot options to "Legacy first, then UEFI" or "Legacy only" (where possible). And my harddisk is indeed MBR, not GPT partitioned.

---

### Post by anj-tuesday on 2014-04-19
> **kc1di said:**
> Hi Anj-tuesday,

I would go[ here ]("https://help.ubuntu.com/community/Boot-Repair")and download a copy of boot-repair and run that it should fix the problem for you,  It sounds like you may have gotten a win7 machine that has uefi enabled. just a guess though boot-repair has been pretty good here at sorting out uefi problems for me. good luck.

Thanks, that could be useful the next time considering I can boot Ubuntu live discs but none of the various rescue/repair/grub live discs I've tried.

Provided that boot-repair doesn't likewise attempt to install grub-efi instead of grub-pc...

---

### Post by oldfred on 2014-04-19
If UEFI is set for Legacy only then you should boot in BIOS mode.

---

