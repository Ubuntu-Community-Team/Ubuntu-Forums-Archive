---
title: "Dual Booted Windows 7 with Ubuntu 14.04 - Windows Not Booting"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by malina3 on 2014-04-24
I had Windows 7 on my computer (Lenovo T430s, UEFI), I needed to isntall some software for my job that required Ubuntu. I had dual booted in the past, parting and installing with a USB Key multiple times and never had an issue. This time I had an issue when I attempted to use GParted, it couldn't recognize the partition table my computer was using. I used a utility to convert it to GPT without data loss and proceeded to partition the drive and install Ubuntu 14.04 (Which has since been dialed back to 13.04 for software compatability). Ubuntu started fine, Windows has started since, instead it says:

```
Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:
   1. Insert your Windows installation disc and restart your computer.
   2. Choose your language settings, and then click "Next."
   3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

   File: \Boot\BCD
   Status: 0xc000000e
   Info: An error occured while attempting to read the boot configuration data.
```

Of course, following the steps ends in more failure, every Windows recovery method I've tried has ended in a message prompt relating to incompatability.

I've been working on this for too long, I need Windows back but I need to keep Ubuntu. I would prefer to repair Windows rather than replace it, software would take forever to reinstall, but I have backed up everything I need if it's the only reasonable option. Earlier today I attempted to reimage my drive using a disk provided by my school, however it failed for unknown reasons.

Ask whatever you need to, offer any advice you have and thank you for reading, sorry if I missed anything big.

Boot Repair Info: [http://paste.ubuntu.com/7326163/](http://paste.ubuntu.com/7326163/)

---

### Post by fantab on 2014-04-24
>  I used a utility to convert it to GPT without data loss and proceeded to partition the drive and install Ubuntu 14.04

May I ask you WHY you've converted the drive to GPT? any particular need?

It is neither simple nor advised to convert your HDD to GPT if it has an OS on it. OS Boot on GPT is different from 'MBR'.
**Windows will NOT boot **from a GPT drive in BIOS/Legacy/CSM mode (which is what you had before you converetd the drive to GPT). It need to be installed in UEFI mode if you want it to work from GPT.
Ubuntu or GNU/Linux on the other hand can boot from a GPT in Legacy mode but it needs a 'bios_grub' partition.

If you don't want to install Windows in UEFI mode then convert back the GPT drive to MBR.

---

