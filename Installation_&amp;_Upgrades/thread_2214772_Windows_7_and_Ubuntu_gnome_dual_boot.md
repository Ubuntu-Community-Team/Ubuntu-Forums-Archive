---
title: "Windows 7 and Ubuntu gnome dual boot"
date: 2014-04-03
forum: Installation &amp; Upgrades
---

### Post by xXIntelXx on 2014-04-03
Hi,
I've tried to dual boot Windows7 and Ubuntu Gnome, but after I've installed Ubuntu Gnome, it goes directly to it. Also, when I press delete to go into the BIOS, it shows up the grub with:
Ubuntu
Ubuntu with advanced something
Setup (BIOS)
And no Windows 7..anyone know why?
Already done "sudo apt-get upgrade grub2"

---

### Post by ajgreeny on 2014-04-03
Let's see the output of **sudo parted -l** in terminal to make sure windows still exists on the machine.

---

### Post by presence1960 on 2014-04-03
> **xXIntelXx said:**
> Hi,

Already done "sudo apt-get upgrade grub2"

The actual command is ```
sudo update-grub
``` to detect and update your OSs in GRUB.

---

### Post by xXIntelXx on 2014-04-03
Actually I have to reinstall Windows 7 and then Ubunt Gnome, I will as soon as I can because I'm not at home right now.

---

### Post by xXIntelXx on 2014-04-03
Ok, I'm going to give up. This time, directly windows, no grub. My last option is to install Windows not from "DVD: dvd-rw" but from "UEFI DVD: dvd-rw". I don't know, EVERY linux distro I have to install, I have to select "UEFI DVD" in the boot override and set nomodeset (manually in the boot options) and without it the installation doesn't even start. I don't know what the hell happened, maybe Windows forgot something to format..I would try to format everything with gparted..

---

### Post by oldfred on 2014-04-04
Post this:
sudo parted -l

If you installed with UEFI one time then drive was converted to gpt partitioning. Then if you install again in BIOS mode with Windows it incorrectly converts to MBR(msdos) and Ubuntu will not install unless you remove the left over gpt data.
Or if Windows is in UEFI mode, you have to install Ubuntu in UEFI mode.
If Windows is in BIOS mode you have to install Ubuntu in BIOS mode.
How you boot install media is how it installs.
Windows DVD normally just installs in BIOS mode, but can be copied to flash drive and updated to be a UEFI installer.
UEFI and BIOS are not really compatible, so if both systems are not same boot mode, you cannot boot from grub menu. But you could boot from UEFI/BIOS, but may have to turn on/off UEFI or turn on/off CSM/BIOS/Legacy boot modes.

---

### Post by xXIntelXx on 2014-04-04
This is the problem:
I install windows WITHOUT UEFI. Bios is set up on CSM, because I deleted the old Windows 8. After I install Windows 7 I put the Ubuntu DVD, without UEFI first, but there isn't the screen to select "try" or "install" ecc. It goes directly to boot the installation and than it blocks: [http://postimg.org/image/c3mf1i3wf/](http://postimg.org/image/c3mf1i3wf/)
Instead, when I select UEFI in the boot override, it goes to this screen: [http://postimg.org/image/ysw3t3fdj/](http://postimg.org/image/ysw3t3fdj/) like..I already have grub? WTF? I only have Windows 7..so that's it..now I try all with UEFI but CSM Bios (no sense but at least I try, if it doesn't work I format EVERYTHING with gparted, than I make a whole partition, NTFS, and another one ext4 and we'll see.

Btw yes, I delete the GPT tables because if not, gparted doesn't show me the partitions.


--update 1--
UEFI all ok, then I start installation of Ubuntu without UEFI, it doesn't work, with UEFI (and nomodeset) ok, but..that's not how it should have to start..why do I have the grub at start without any linux install? I don't have the classic screen of Ubuntu for the first time..

--update2-- 
Trying to install Ubuntu is going to take a lot of time, because I can't access to the BIOS, I press DEL but nothing happens. I'm trying for 3 fu***ng hours.

--update3--
Without UEFI: [http://postimg.org/image/3qmp6tj7t/](http://postimg.org/image/3qmp6tj7t/) and then all black. 
With UEFI: [http://postimg.org/image/ysw3t3fdj/](http://postimg.org/image/ysw3t3fdj/)
At least now I try with UEFI..

--update4--
UEFI was a bad idea, reinstalled windows without UEFI and now I'm using a live CD of Ubuntu 12.04 (13.10 gnome or not seems to have some problems)

--update5--
I can't install Ubuntu Gnome because it's based on Ubuntu 13.10 who doesn't want to f****** fit in my notebook, so, I installed Ubuntu 12.04.4 where I will install Gnome Desktop.

I would say that the problem is solved.

---

### Post by oldfred on 2014-04-04
Hope it is resolved.

Main part of issue is that your hardware is both UEFI and BIOS. But Windows 7 DVD is only BIOS.

Ubuntu installer is both UEFI or BIOS depending on how you boot it and will install in the same mode as how you boot. And in UEFI mode it uses grub to boot, so you immediately get grub menu on installer. In BIOS mode you get purple screen.
And if you need nomodeset or other boot parameters you have to hit any key when tiny accessibility icons are at bottom of screen, then f6 and add nomodeset. If in UEFI mode you have to manually edit grub linux boot line to add nomodeset.

---

### Post by xXIntelXx on 2014-04-04
> **oldfred said:**
> Hope it is resolved.

Main part of issue is that your hardware is both UEFI and BIOS. But Windows 7 DVD is only BIOS.

Ubuntu installer is both UEFI or BIOS depending on how you boot it and will install in the same mode as how you boot. And in UEFI mode it uses grub to boot, so you immediately get grub menu on installer. In BIOS mode you get purple screen.
And if you need nomodeset or other boot parameters you have to hit any key when tiny accessibility icons are at bottom of screen, then f6 and add nomodeset. If in UEFI mode you have to manually edit grub linux boot line to add nomodeset.
Well, correct what you say but without UEFI I didn't have the purple screen to manually set nomodeset, and that even blocked my installation for linux mint 16 and many others new distros.

---

### Post by oldfred on 2014-04-04
In UEFI install mode you edit grub the same way you edit the grub boot stanza on first boot after install.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.

---

