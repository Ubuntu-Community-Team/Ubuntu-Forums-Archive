---
title: "Stuck in a bootloop, help!"
date: 2023-11-17
forum: Installation &amp; Upgrades
---

### Post by radee2k on 2023-11-17
Hej, 

After attempting a dual boot with Windows 10 and freshly installed Ubuntu my Thinkpad x240 is stuck in a bootloop, where "Reset System" appears regardless different BIOS startup settings. I ran boot-repair from a live-ubuntu as described in: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and got this report: [https://pastebin.ubuntu.com/p/j7P27ySmfz/](https://pastebin.ubuntu.com/p/j7P27ySmfz/). The problem persists. :lolflag:

I would greatly appreciate any help! :)

---

### Post by tea for one on 2023-11-17
> **radee2k said:**
> After attempting a dual boot with Windows 10 and freshly installed Ubuntu 
A surprising choice of Ubuntu 18.04 as a fresh installation?

it looks like you had Windows in old-fashioned Legacy mode and then installed Ubuntu in UEFI mode.
You also have msdos partition table rather than gpt.
More info [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

My suggestion :-
Back up all your personal data
Install Windows 10/11 in UEFI mode with GPT
Reboot and test
Install Ubuntu 22.04 in UEFI mode
Reboot and test

Then decide where to restore your personal data.

---

### Post by MAFoElffen on 2023-11-17
+1! --

Before reinstalling Windows in UEFI mode, remember to boot Windows, and go into regedit to find and backup your "product activation key", so you can re-activate you new install of Windows in UEFI mode.

Another consideration is to look at the Disk partition type, and covert it from MBR to GPT...

You can always install Ubuntu as Legacy BIOS mode, and be done with it, but this uncovered that the Windows installation was installed in the wrong boot mode, and to go forward without further problems with both OS'es, this would be the perfect time to correct that.

---

### Post by radee2k on 2023-12-02
Hi!
Thanks a lot for the replies.

> **tea for one said:**
>  A surprising choice of Ubuntu 18.04 as a fresh installation?


That's as 18 has a very light image size that fits on the only USB I had at hand.

> **MAFoElffen said:**
> 
Before reinstalling Windows in UEFI mode, remember to boot Windows 

The issue is that I am unable to boot it. Any os choice sends me back to the installed os table after screen blinks.

---

### Post by oldfred on 2023-12-02
If an old system with limited memory, better to use a lightweight flavor. ISOs are also smaller.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

