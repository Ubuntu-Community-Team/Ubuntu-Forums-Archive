---
title: "Ubuntu installation on Legion 5-17IMH05H"
date: 2021-01-20
forum: Installation &amp; Upgrades
---

### Post by akash.98 on 2021-01-20
Hi,

This is a fairly documented issue by now (trying to dual boot the Legion laptops with Ubuntu). I realize that Lenovo doesn't extend any support for Linux distributions on these laptops, but for someone who for sure wants to boot up Linux systems on the legion laptops, I would really love to know the solution for this.

I have tried to install three different Ubuntu versions (16.04, 18.04, 20.04). For 16.04, the touchpad doesn't work. I presume this is a driver issue that the drivers for the Linux kernel are not pre-installed on the legion laptops. Is this issue resolved? If so what's the solution? In not, is there are get-away around this?

And for the other two (18.04 and 20.04), it's the ACPI BIOS error. The bootup screen freezes flashing that it's some X-509 certificate error (to be fair I don't completely get what the issue here is, but I presume that it has something to do with NVIDIA graphic settings customized to Windows). There are many such cases reported on other online forums. Something like this:

[https://askubuntu.com/questions/1279500/ubuntu-20-04-booting-issue-in-legion-5i](https://askubuntu.com/questions/1279500/ubuntu-20-04-booting-issue-in-legion-5i)

I tried all such solutions (even booting in safe mode) but unfortunately, none of them work for my laptop ( Legion 5-17IMH05H). Hence I am currently forced to use WSL to work in a Linux environment.

I would really like to know if there is a legitimate solution to this problem. If there exists one, can someone point out, of how to boot a Linux system on a Legion laptop?

Any help is highly appreciated,

Thank you

---

### Post by CelticWarrior on 2021-01-20
Welcome.

Some of your statements are incorrect either in form and/or contents
> [COLOR=#000000]For 16.04, the touchpad doesn't work. I presume this is a driver issue that the drivers for the Linux kernel are not pre-installed on the legion laptops.[/COLOR]
First of all, 16.04 will be out of support in April so there's no point in even trying it. And it should be quite clear that an old, 5 years old!!!, release likely won't have drivers to much newer hardware than itself. Clearly this is also the case here as you know, since the touchpad works as early as the 18.04 release.

And NO drivers are preinstalled in any computer, for Windows or any other OS. In Linux drivers ARE in the kernel or they aren't. There are no drivers "for the kernel" but there cab be user installable proprietary drivers that may require certain kernel versions to be installed.

> [COLOR=#000000]I tried all such solutions (even booting in safe mode) (...)[/COLOR]
What, exactly?

Anyway, there only a few things you must pay attention to in order to avoid the confusion that is your assessment:
- Always use NEWER releases and that means 20.04 or even 20.10 if the hardware is bleeding edge;
- Update FIRMWARE: UEFI ("BIOS") and also SSD's if applicable
- Make sure you install the Nvidia proprietary drivers

So, in a nutshell, the above is a summary of the accepted answer in the very same link you posted (but didn't read or understood apparently). The only correction I must do to the aforementioned answer is that the Nvidia drivers installation can now be enabled during the Ubuntu installation (third-party drivers, codecs, etc) and that Secure Boot in UEFI should be disabled. Also disable Fast Boot and make sure the drive mode isn't RAID or Intel RST but **AHCI**. That said, if you actually need to change it to AHCI you need to install AHCI support in Windows or it won't boot after the change (but the same setting can be changed back and then Windows will boot again as before).

This should be all you need to know. Please report back if you find any other issue.

---

