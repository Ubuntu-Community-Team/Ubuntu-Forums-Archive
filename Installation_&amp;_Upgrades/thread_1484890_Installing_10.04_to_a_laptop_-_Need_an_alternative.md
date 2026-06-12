---
title: "Installing 10.04 to a laptop - Need an alternative method"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by Centipeed on 2010-05-16
Currently I've got Windows XP and Ubuntu 8.04 (I believe) on my laptop, with two separate partitions.

I want to format the laptop and only have Ubuntu 10.04 installed on there, but since the CD drive is broken, I've just been trying to do it from USB.

There must be something wrong with my laptop/booting from USB, because I've tried two different programs used to create Live USB installations (UNetbootin and Universal-USB-Installer). Both of them load the menu, let me select to install or run the Live CD, but neither of them get past the purple-ish Ubuntu loading screen. The screen just goes black (But stays lit), and nothing else happens.

So I'm wondering if there is different, easy-ish method for installing Ubuntu 10.04 to this laptop. It's got a working network adapter, so I could plug it into my home network if that will help.

---

### Post by badaveil on 2010-05-16
If networking is possible, why don't you try to place the installation CD in another LAN computer and install from your computer via LAN?

---

### Post by howefield on 2010-05-16
> **Centipeed said:**
> Both of them load the menu, let me select to install or run the Live CD, but neither of them get past the purple-ish Ubuntu loading screen. The screen just goes black (But stays lit), and nothing else happens.

When booting with the USB, try pressing F6 after selecting your language, and select the nomodeset option. Then continue booting, if that doesn't work, press the Esc key after pressing F6 as above, and remove "quiet splash" from the end of the boot line.

Can't quite remember, it may be quiet splash --, but hopefully will be obvious.

---

### Post by Centipeed on 2010-05-16
> **howefield said:**
> When booting with the USB, try pressing F6 after selecting your language, and select the nomodeset option. Then continue booting, if that doesn't work, press the Esc key after pressing F6 as above, and remove "quiet splash" from the end of the boot line.

Can't quite remember, it may be quiet splash --, but hopefully will be obvious.

I never get to a language option. It boots, shows me the menu to install, I select install, it shows a splash screen, and then the black screen.

Is there any more information on installing from a CD drive on another networked computer, to my laptop? I didn't know that was possible.

---

### Post by C.S.Cameron on 2010-05-16
Would it be an option to delete windows and use gparted to expand the Ubuntu partition and then just upgrade to 10.04?
I guess you would need to still boot Ubuntu live or gparted Live to do this.

Unless you removed the hard drive and connected it to another computer for the procedure.

---

### Post by Centipeed on 2010-05-16
> **C.S.Cameron said:**
> Would it be an option to delete windows and use gparted to expand the Ubuntu partition and then just upgrade to 10.04?
I guess you would need to still boot Ubuntu live or gparted Live to do this.

Unless you removed the hard drive and connected it to another computer for the procedure.

I really want to do a clean install in order to get all of the crap off there.

And my laptop doesn't make it easy to remove the harddrive, so I'd prefer not to.

---

### Post by s_maqbool on 2010-05-16
I install Ubuntu Netbook remix on my netbook via a flash USB drive. The file is around 1GB. You need to download some software to format the USB stick in the right way and then put the Ubuntu file on there and it works like a Live CD. You check it out whiles it installs.

I would recommend that, plus there is a new version of Ubuntu out called LTS 10.4 I think. I just upgraded to that today.

---

### Post by C.S.Cameron on 2010-05-16
Often such problems are due to a bad iso download.
It might be worth checking the MD5SUM.

---

### Post by oldfred on 2010-05-16
if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by Centipeed on 2010-05-16
> **oldfred said:**
> if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Doesn't the fact that I've got a copy of Ubuntu already installed on the laptop mean that it's not the graphics card? When the CD drive was still working, I had no problems installing Ubuntu.

---

### Post by oldfred on 2010-05-16
On my desktop my monitor would turn off but the USB key I installed from kept flashing. I added nomodeset and it installed. then the same happened on first boot, so I added nomodeset on kernel line in grub and it booted to low graphics mode and I was able to install nvidia and it works.
The link shows similar issues for other video cards but different settings may be required.

---

### Post by jvector on 2010-05-16
> Doesn't the fact that I've got a copy of Ubuntu already installed on the laptop mean that it's not the graphics card?No, it's specifically reported as a new issue with 10.04 on the Intel 82852 graphics cards (somewhere in the release notes). So the workarounds in [that link]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes") are relevant. ( I use the first one listed, and it seems have worked so far (i.e. this evening :-) ))

---

