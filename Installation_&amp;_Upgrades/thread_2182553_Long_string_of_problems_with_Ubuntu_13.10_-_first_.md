---
title: "Long string of problems with Ubuntu 13.10 - first time user."
date: 2013-10-21
forum: Installation &amp; Upgrades
---

### Post by 13377331 on 2013-10-21
Background: This laptop is called Acer Aspire V5-572G and it has a dual graphic switching between Intel and Nvidia 720M. This laptop runs on Windows 8 with EFI and I have disabled secureboot.

What I did:

Booted into Windows 8, then booted into UEFI to disable secureboot.

Booted back into windows 8 then booted into USB stick containing Ubuntu 13.10.

Selected option for installing. It just goes into blank screen with no LCD backlight.

Searched for this problem, found a solution - to use nomodeset option when booting. It worked.

Installed Ubuntu on 100GB partition. 

It asks me to restart it. K I'll do it. The laptop just boots into windows 8 directly without option of Ubuntu.

I boot into Ubuntu (GRUB menu isn't it?), but nomodeset doesn't work this time. [s]It just shows a blank screen with no LCD backlight[/s] It just boots into command line version of Ubuntu without GUI. I tried startx, it threw up an error saying it cannot find the screen and its fatal error.

Again, searched for solution. Found solution, it was to boot up using acpi_osi=Linux acpi_backlight=vendor. It worked, no problem.

Boot into Ubuntu. Everything worked well, although I didn't like desktop since it was "too  big" (Icons, and graphic things are big). No bother I'll fix that later  anyway. 

I notice my graphic card isn't showing on additional drivers option where it installs graphic card driver for me. I check system info and notice it shows I'm using Intel with no mention of Nvidia.

I'll leave that later. For now I'll need to fix the boot up problem so it gives me the option to boot into windows 8 or Ubuntu. I tried boot repair and followed all instructions correctly without any problems.

Reboot - it goes straight into windows 8. K let's leave it for later.

Now back to graphic card problem, I realise it might be dual graphic card switching problem so I decided to install Optimus, but I found out it doesn't exist on Linux. I tried to install BumbleBee but it refuses to install saying something like the terminal not finding it.

I get annoyed. No worries, for now I need to install graphic card driver manually (through terminal). Guess what? It has made the problem worse, now after I login, it shows a black screen.

AND now I can no longer to fix the problem any further since I can't login into Ubuntu now.

---

### Post by 13377331 on 2013-10-22
Bump.

---

### Post by oldfred on 2013-10-22
I do not have dual video. The very new nVidia version that has limited Optimus support needs the newest kernel which is in 13.10. Otherwise bumblebee is best choice.

 Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

---

### Post by grahammechanical on 2013-10-22
I find this interesting

> [COLOR=#000000]Booted back into windows 8 then booted into USB stick containing Ubuntu 13.10.[/COLOR]

[COLOR=#000000]Selected option for installing. It just goes into blank screen with no LCD backlight.[/COLOR]

Do you get a Grub menu? You may be looking at an attempt to re-install. 

From within Windows 8? Then you were trying to install wubi.exe which is incompatible with Windows 8.

[http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows](http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows)

Hybrid graphics have been an issue for many months (a couple of years?) now mainly because Nividia refused until a few months ago to provide a video driver for it Optimus technolgy. Further more Nvidia do not seem to be in a hurry to perfect it.

[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

By the way Ubuntu 12.10 was the first Linux distribution to have secure boot support. Every version since then should install with secure boot enabled but it seems that is can be tricky.

> [COLOR=#000000]Again, searched for solution. Found solution, it was to boot up using acpi_osi=Linux acpi_backlight=vendor. It worked, no problem.
[/COLOR][COLOR=#000000]Boot into Ubuntu. Everything worked well, although I didn't like desktop since it was "too big" (Icons, and graphic things are big). No bother I'll fix that later anyway.[/COLOR]


That means that Ubuntu loaded without a video driver, either Nouveau or a proprietary driver. Ubuntu was using a kind of fall back mode based upon a subset of Nouveau called llvmpipe. That is what it looks like.

Can you bring up a Grub menu? Can you not enter Recovery Mode? It is the Advanced Options for Ubuntu sub-menu.

Regards.

---

### Post by 13377331 on 2013-12-06
Sorry for abandoning this thread because the laptop broke due to some unrelated reasons so had to send it off. Now I have it back but the old laptop was unfixable so they replaced it with new one, same model.

I installed Ubuntu using nomodeset option. It worked well... Until I rebooted (required by the installer), it boots in fine but once after GRUB menu, it turns the LCD backlight off.

So, pretty much same problem as before. But this time I have managed to get GRUB menu show up so I have option of dual booting (I did this on UEFI through booting priority changes). 

> **grahammechanical said:**
> I find this interesting



Do you get a Grub menu? You may be looking at an attempt to re-install. 

From within Windows 8? Then you were trying to install wubi.exe which is incompatible with Windows 8.

[http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows](http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows)

Hybrid graphics have been an issue for many months (a couple of years?) now mainly because Nividia refused until a few months ago to provide a video driver for it Optimus technolgy. Further more Nvidia do not seem to be in a hurry to perfect it.

[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

By the way Ubuntu 12.10 was the first Linux distribution to have secure boot support. Every version since then should install with secure boot enabled but it seems that is can be tricky.



That means that Ubuntu loaded without a video driver, either Nouveau or a proprietary driver. Ubuntu was using a kind of fall back mode based upon a subset of Nouveau called llvmpipe. That is what it looks like.

Can you bring up a Grub menu? Can you not enter Recovery Mode? It is the Advanced Options for Ubuntu sub-menu.

Regards.
Thanks for helpful information. Yes, I can bring up a Grub menu and I can enter Recovery Mode.
I disabled secure and fast boot.
> **oldfred said:**
> I do not have dual video. The very new nVidia version that has limited Optimus support needs the newest kernel which is in 13.10. Otherwise bumblebee is best choice.

 Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

I'm installing Optimus right now using acpi_osi=Linux acpi_backlight=vendor as boot up option, I'll report back to see how it goes.

**EDIT 1:** I booted in without "acpi_osi=Linux" flag, it booted fine and the graphic icon and items on the desktop looked normal, I guess this is because graphic card is working with "default" backlight mode?

---

### Post by 13377331 on 2013-12-06
Well, I installed latest NVIDIA driver for 720M, it boots up fine but it still needs acpi_backlight=vendor and after logging in, it shows a black screen but backlight is on. Surely this is NVIDIA driver issue? Am I installing wrong driver?

---

### Post by oldfred on 2013-12-06
Typically Linux has to work around proprietary vendors and how they do things. And the proprietary video drivers for Linux are not as up to date as the Windows versions, but it now is getting better. 

 New Intel driver installer (only with 13.04)
[http://www.phoronix.com/scan.php?page=news_item&px=MTQyNTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTQyNTQ)
Intel "Haswell" System 76 Iris Pro Linux Graphics Yield Some Wins Against Windows
[http://www.phoronix.com/scan.php?page=article&item=intel_irispro_linwin&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_irispro_linwin&num=1)
NVIDIA's Linux Driver On Ubuntu Is Very Competitive With Windows 8
[http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1)

---

### Post by 13377331 on 2013-12-06
> **oldfred said:**
> Typically Linux has to work around proprietary vendors and how they do things. And the proprietary video drivers for Linux are not as up to date as the Windows versions, but it now is getting better. 

 New Intel driver installer (only with 13.04)
[http://www.phoronix.com/scan.php?page=news_item&px=MTQyNTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTQyNTQ)
Intel "Haswell" System 76 Iris Pro Linux Graphics Yield Some Wins Against Windows
[http://www.phoronix.com/scan.php?page=article&item=intel_irispro_linwin&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_irispro_linwin&num=1)
NVIDIA's Linux Driver On Ubuntu Is Very Competitive With Windows 8
[http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1)

Thanks for the link.

So, I had to reinstall Ubuntu 13.10 as it would show a blank black screen (with backlight on) if booted into text only mode.

So... once it finishes installing, I'll give bumblebee a try and see what happens.

---

