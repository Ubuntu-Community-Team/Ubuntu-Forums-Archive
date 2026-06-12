---
title: "Ubuntu boot from USB fails in every regard"
date: 2019-10-07
forum: Installation &amp; Upgrades
---

### Post by arsanian on 2019-10-07
Hello guys,

I'm using Ubuntu on my notebook for quite some time now and wanted to install it on my tower now too.
So I made a USB-Boot Stick for Ubuntu 19.04 via my Notebook's Ubuntu Installation and tried booting, but it just stays at the loading screen forever (the one with the ubuntu logo and the dots), it doesn't freeze though, just loads forever.

Now, when I press esc to see the progress, it seems like every initialization process failed, even when I try ctrl+alt+esc to reboot, shutdown fails. (see attached picture, sorry for screen photo :D)

[ATTACH=CONFIG]284159[/ATTACH]

I already tried reformatting the USB-Drive and installed the image via Windows with Rufus, but it doesn't change anything.
Also tried to run without installing and both options with safe graphics.
I tried chaning the BIOS mode from CSM to UEFI and disable secure boot, but it just scrambled the graphics and had the same outcome. 

The system in question:
Ryzen 5 3600 Processor
RTX 2070 
MSI x470 Mainboard
32GB RAM
128GB SSD (currently running Windows 10)
1TB SSD (For data and part of it should become a Ubuntu Partition)
1TB HDD

I hope there is a simple solution here that I just can't seem to find.

Thanks it advance!

Arsanian

---

### Post by oldfred on 2019-10-07
Have you updated UEFI?
And have you updated SSD firmware?

AMD UEFI/BIOS update for Ryzen 3000 series Aug 2019
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
> MSI has also put out BIOS updates last week as a "beta" though without explicitly acknowledging the Linux fix. 

Older similar model:
MSI Tomahawk B350 with Ryzen R5 1600 New UEFI required
[https://ubuntuforums.org/showthread.php?t=2390475](https://ubuntuforums.org/showthread.php?t=2390475)

If nVidia card, you typically need nomodeset boot parameter until you install correct nVidia driver after install.
The newest Ubuntu may now offer to install nVidia driver as part of install.

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by ubfan1 on 2019-10-07
Oldfred's UEFI update may fix things, but also try the beta Ubuntu 19.10 with the 5.0 kernel.  Actually, the 5.2 kernel may be the one you need for the Ryzen 3000 series, but you'd have to do that one yourself. The noacpi kernel flag  may help the initial boots before you update the UEFI, but with big drawbacks like only seeing one CPU.

---

### Post by arsanian on 2019-10-07
Thans for the replies! 

One thing I forgot to mention is, that, when booting the usb-drive with uefi enabled, there is very much input lag. That was especially notable when editing the boot parameters, since it only allows to scroll/type/erase one character every ~2 seconds. 

I updated the BIOS, which made the input lag a little better, decreased it to ~ 1 second per input. 

But sadly neither the BIOS-update, nor the nomodeset boot paramater seem to solve the problem.

During my research I also found out that my processor might not yet be officially supported by my mainboard, though Windows runs without any problems. Might still cause this problem though, so maybe I'll have to wait for a BIOS update to cover that.

I will try using the beta Ubuntu 19.10 tommorow and also get some DVDs, so I can rule out any problems with the USB-drive.

Thanks again for your replies :)

---

### Post by oldfred on 2019-10-07
Only a few hardware/motherboard manufacturers officially support Linux, but most work. But some need boot parameters.
And very new systems often need very new software, drivers & UEFI/BIOS updates as Linux developers do not have direct support from vendors in many cases.

---

### Post by arsanian on 2019-10-10
I tried installing Ubuntu 18.04 LTS now, which works, but doesn't seem to support the RTX 2070 graphics card, so I tried to upgrade to 19.04 from within 18.04 and it actually booted, but when I tried to login, it would show the desktop for a second and then show the login screen again. It was also pretty laggy.

Now I installed 19.10 and it seems to work fine, although I had to set nomodeselect for the installation. It even comes with Nvidia drivers now, which is nice :)

So thanks again for your input, this solved my problem!

---

