---
title: "reinstalling 22.04 got Grub Rescue"
date: 2023-01-19
forum: Installation &amp; Upgrades
---

### Post by scpatl4now on 2023-01-19
I decided to do a clean install due to problems I was having and now I can't boot at all.  I have tried boot-repair from a usb stick but it throws an error nvram locked.  I have been working on this for a couple of hours and I just dont know what to do.  Originally  boot repair was complaining about no efi partition, so when I went to reinstall I created one in the front of the SSD drive but now at the end of the install it says there is a fatal grub error and I am back to grub rescue

---

### Post by oldfred on 2023-01-19
If grub error and you had no ESP - efi system partition, you must have grub in MBR.
Is drive gpt? As that is preferred now.
The only time to use the very old MBR(msdos) if your system is over 10 years old & you have to install Windows in BIOS boot mode. And most 10 year old systems will not run newer Windows well.

What brand/model system?
What video card/chip?

We have seen multiple issues with locked NVRAM, but most seem to go away.
This user documented the changes he made.
HP Zbook 15 NVRAM locked, install issues
[https://ubuntuforums.org/showthread.php?t=2482555](https://ubuntuforums.org/showthread.php?t=2482555)

---

### Post by scpatl4now on 2023-01-20
Thanks for your response.  I figured it out.  It's been quite a while since I did a clean install, and I had been troubleshooting an issue a couple of hours before that.  I had forgotten that when I use the USB stick to boot, there are 2 options in the bios.  UEFI or not.  My BIOS makes it look like 2 separate things. They are on separate partitions of the usb stick.  Once I chose the non-uefi everything was good

---

