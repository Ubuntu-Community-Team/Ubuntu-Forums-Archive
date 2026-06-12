---
title: "Continuous Rebooting, Wubi install messed up"
date: 2016-09-03
forum: Installation &amp; Upgrades
---

### Post by 0kyleobrien on 2016-09-03
I think I know where I went wrong, I just can't find anything on how to fix it. I installed Ubuntu alongside my Windows 7 install which have incompatible formats if I recall correctly. When I boot my computer it hangs on the BIOS for much longer than normal, with my caps lock and num lock keys constantly blinking. Once it does that for a minute or so, it goes to a black screen and flashes a message (it includes the words environment batch (or block)). It goes away so quickly I can't tell what it says. 

I tried booting from my Ubuntu disk but it gives this message:
Loading boot logo...
error setting up gfxboot

When I try booting from a Windows 7 install USB it says:
error: no such device: then a string of letters and numbers
grub rescue>
with a prompt. 

I feel so dumb right now and just want to save this computer, I just bought it from Craig's List and was trying to install my favorite OS. If it's possible to save the data, that'd be fantastic, but I just want to save the computer. Thanks for any help, right now I just feel like I bricked it. I've googled around a ton and can't find something similar to my issue.

---

### Post by yancek on 2016-09-03
The official Wubi documentation is at the site below.  Wubi has not been supported for several years.  Did you actually do a wubi install?  Which release of Ubuntu are you using?  Your Ubuntu operating system will have absolutely no effect on your BIOS.  If you are getting a grub prompt when you boot then you must have at least tried to install Ubuntu.  A wubi install will create a boot menu entry for Ubuntu in the windows bootloader which is what you would see when you boot.   There isn't enough information for anyone to do more than guess so I would suggest you go to the site below and get the boot repair software by following the instructions on the page, downloading and running it.  Make sure not to try to make repairs but select the Create BootInfo Summary option and post a link to the output here.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by 0kyleobrien on 2016-09-03
> **yancek said:**
> The official Wubi documentation is at the site below. Wubi has not been supported for several years. Did you actually do a wubi install? Which release of Ubuntu are you using? Your Ubuntu operating system will have absolutely no effect on your BIOS. If you are getting a grub prompt when you boot then you must have at least tried to install Ubuntu. A wubi install will create a boot menu entry for Ubuntu in the windows bootloader which is what you would see when you boot. There isn't enough information for anyone to do more than guess so I would suggest you go to the site below and get the boot repair software by following the instructions on the page, downloading and running it. Make sure not to try to make repairs but select the Create BootInfo Summary option and post a link to the output here.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thank you for your quick response, I had this CD from awhile back I suppose and after reading about the Wubi issues I now know it was a bad idea. I am using 12.04. What happened exactly was I completed the install, with a reboot (removed disc and all), ran apt-get update and upgrade when my trackpad stopped working (it completed) at which point I hard reset the computer. This may be unrelated as I was able to get the disc to load by putting in "live" to that prompt and the trackpad is still not working. I'll try to figure out that one. 

I'm trying to find a way to install Boot-Repair as this is my only computer with Internet access, I am currently on my phone, and don't have a mouse handy. Thank you for the help so far.

edit: I found a mouse and currently just trying to write over the previous install I had
edit 2: this fixed it, albeit I'm sure we're both wondering what caused it lol.

---

### Post by hakuna_matata on 2016-09-04
> **0kyleobrien said:**
> edit 2: this fixed it, albeit I'm sure we're both wondering what caused it lol.
Maybe, an explanation:

There is a difference between the boot loader chain for Ubuntu installations with Wubi: 
```

MBR -> Windows Boot Manager -> Windows (default)
                            -> GRUB4DOS -> GRUB2 -> Ubuntu

```
and without Wubi:
```

MBR -> GRUB2 -> Ubuntu (default) 
             -> Windows Boot Manager -> Windows

```
As you see, if you use Wubi you should use an MBR which loads the Windows Boot Manager. If you installed Ubuntu with Wubi, some scripts of package lupin-support prevent that GRUB2 overwrites the MBR. But of course, it is still possible to do it manually or with the help of some repair tools. 

Additionally, if you try to repair something with live CDs/DVDs/USBs, package lupin-support is available but not installed by default.

But if it happened, it is still not a problem to fix MBR for Windows. see [How to fully fix the Windows bootloader using a Windows disk]("https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader#How_to_fully_fix_the_Windows_bootloader_using_a_Windows_disk").

---

