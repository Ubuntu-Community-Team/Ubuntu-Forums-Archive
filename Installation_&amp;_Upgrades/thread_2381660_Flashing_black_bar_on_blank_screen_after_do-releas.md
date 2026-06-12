---
title: "Flashing black bar on blank screen after do-release-upgrade"
date: 2018-01-03
forum: Installation &amp; Upgrades
---

### Post by xpope on 2018-01-03
So luckily I had a Kali live disk lying around, so that I could access a web browser to ask you guys for a bit of help.

I was running 16.04LTS as my daily driver on a Dell Precision M4800. No other drives than a 480GB SSD and no dual boot etc (I do all in Vbox VMs). It's a pretty straightforward partition system, done through encrypting and setting up LVM after a clean install around 6 weeks ago. The hard drive is also encrypted and I believe that's what is causing the issue I'm having.

After running do-release-upgrade as I wanted to go from 16.04 to 17.04 (then to 17.10, but obviously didn't get that far) it came to the reboot, but doesn't at any point ask for my Cryptsetup password. I'm simply given the flashing cursor in the top left. I believe this is due to the fact that it can't get in to the container as no decryption has taken place and as such, can't see the boot sector.

I've tried going to Advanced Options in the Grub bootloader - which is still the purple 16.04 one and chosen recovery mode of both the available kernels (4.4.0-42 & 4.4.0-104 in that order too). I've tried repairing package options, fsck runs etc, yet still no boot, or request to enter Cryptsetup password.

Could any of you good folk help me figure out whether I'm sniffing in the right direction for an answer.

Thanks in advance.

---

