---
title: "Live CD hangs on boot"
date: 2012-03-13
forum: Installation &amp; Upgrades
---

### Post by dsluser on 2012-03-13
Hi All, 

So this seems to be a huge issue with the latest kernel. I've found reports 

[https://bugzilla.redhat.com/show_bug.cgi?id=753456](https://bugzilla.redhat.com/show_bug.cgi?id=753456)

[https://bugzilla.redhat.com/show_bug.cgi?id=696513](https://bugzilla.redhat.com/show_bug.cgi?id=696513)

I have the same issue after installing an Nvidia GTX 580 and an Intel 510 SSD. Currently I'm stranded in the land of Windows and I'm desperately trying to get my dev box back up and running. (8GB RAM on a builder box so yes, I do need 64 bit)

Has anyone encountered this issue and found a work-around to allow the Nvidia drivers to be used? Is there an alpha or beta of 12.04 which may work?

---

### Post by wojox on 2012-03-13
Did you try the "nomodeset" added to the kernel line?

---

### Post by oldfred on 2012-03-13
Ever since (or maybe with ) version 10.04 I have had to add nomodeset with my older 9600gt nVidia card. First on CD, then I started using flash and needed nomodeset and now I boot ISO from hard drive and still need nomodeset. Then I need it again in grub on first boot.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

---

### Post by dsluser on 2012-03-13
From what I can tell it will still revert to the Intel drivers when Gnome 3 boots? I'll try now, what's the escape character to manually edit the kernel options from the newer live cd's? I just see try, install, check cd, check memory and boot to 1st hard disk

---

### Post by dsluser on 2012-03-13
Thanks Fred will try this, had posted the reply to wojox just before you posted :)

---

### Post by dsluser on 2012-03-13
Back up and running, thanks so much for the help. I installed the proprietary Nvidia drivers on boot and everything is working away fine without having to manually edit GRUB.

One thing I've noticed is that I no longer have the Gnome 3 option when logging in, just Unity and Unity2D but this is minor and I'm probably just missing the packages, I think I installed from a DVD originally and just the liveCD this time around.

Could I suggest putting this solution as a sticky for hanging liveCDs? From my research before this post it seems to affect Fedora 15/16 and Ubuntu 10.04 onwards and affects both ATI and Nvidia cards. There are many threads showing the correct GRUB options for ATI cards but this was the first time I met the nomodeset option.

---

