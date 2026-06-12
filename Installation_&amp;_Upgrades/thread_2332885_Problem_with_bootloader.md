---
title: "Problem with bootloader"
date: 2016-08-05
forum: Installation &amp; Upgrades
---

### Post by giincat on 2016-08-05
I just installed Ubuntu. I'm very new to this but in the installation I installed the bootloader on the windows bootloader... (idk...) The thing is I can't run windows 10 now and I don't have a disk to fix it... Is there another way? I need help

---

### Post by Bucky Ball on 2016-08-05
Welcome. There are a lot of things that could be the reason for your problems so I will start at the beginning in the hopes a fix may be simple.

Are you getting a list when you boot the machine with OSs to select? If not, tap the shift key at boot. If still no list, try the escape key (which depends on whether you installed in UEFI or legacy). Can you boot into Ubuntu? If so, open a terminal and:

```
sudo update-grub
```

Reboot. Is it on that list now?

Failing that, the problem is generally with UEFI. Win10 is installed in UEFI mode. You need to switch off hibernation in Win10, switch off secure boot and faststart and anything else Win related in the BIOS and install Ubuntu in UEFI also. You may have omitted to do this.

More details about how you installed would be helpful and confirmation of the above UEFI/legacy details. You could also check the Boot Repair link in the first line of my signature, don't do a recommended repair but do run the bootinfo script and post the link it gives you back here, please. That will tell us all we need to know about how you've installed and hopefully what you're issue is.

Then again, although I'm sure you have backups of what you need, you may have inadvertantly wiped Win ... :-k Fingers crossed.

---

