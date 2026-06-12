---
title: "Can't install Ubuntu 12.10 or 12.4"
date: 2012-12-07
forum: Installation &amp; Upgrades
---

### Post by wildonion on 2012-12-07
Hi,

I've been trying to install ubuntu, but when I select either "try w/o installing" or "install ubuntu," the screen just goes blank and my computer freezes. I've done a little research on this problem. For instance, I've tried inputting "nomodeset" into the boot prompt, but all that seems to do is list my computer's specs, and then I end up with a frozen computer again.

Another thing, the menu where it asks to select to install ubuntu is not showing in the usual purple ubuntu color scheme, but rather just a standard black and white prompt. Other computers I've installed ubuntu on have always just gone to the usual purple color scheme prompt.

The computer I'm trying to install on is very low-end also, so I'm sure that has something to do with it. It's a 64-bit amd-300 processor(about the equivalent of a intel celeron)with only 2gigs of ram. 

If anybody can try to help me out, it would be greatly appreciated.

Thanks,

Brian

---

### Post by Androzani1 on 2012-12-07
Can we have all/more of the PC specs please?

---

### Post by wildonion on 2012-12-07
Toshiba C855d
AMD E-300 APU with Radeon (tm) HD Graphics 1.30 Ghz
2.00 GB RAM
64-bit Windows 8 OS

---

### Post by Androzani1 on 2012-12-07
Did you disable secure boot?

---

### Post by wildonion on 2012-12-07
Yes, secure boot is disabled

---

### Post by wildonion on 2012-12-07
To be honest, my first choice was to install Linux Mint, but I can't even get that to boot from the cd. Instead, it just boots straight into windows. At least with Ubuntu, I'm getting some type of menu.

---

### Post by Androzani1 on 2012-12-07
Hmm... I'm sorry, but I'm out of ideas. It could be something to do with W8, but I don't know what. :/

---

### Post by oldfred on 2012-12-07
A lot of users seem to have issues, but a couple did get it to work.

[http://www.linlap.com/toshiba_satellite_c850-c855](http://www.linlap.com/toshiba_satellite_c850-c855)

Have you tried nomodeset or other boot parameters?

If Windows 8 is preinstalled then you really need to use 12.10 in UEFI mode not BIOS.

Post this:
       sudo parted /dev/sda unit s print
    
       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

