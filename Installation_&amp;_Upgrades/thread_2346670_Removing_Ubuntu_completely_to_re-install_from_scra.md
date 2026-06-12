---
title: "Removing Ubuntu completely to re-install from scratch (dual-booting)"
date: 2016-12-17
forum: Installation &amp; Upgrades
---

### Post by sommanker on 2016-12-17
Hi,
I am *very *new to Linux as a whole, and only even started looking into it last week as Windows started really annoying me.
I run Windows 10 and have UEFI, not bios.
Upon looking into Linux, I decided to dual-boot ubuntu. 
I installed it by burning the ISO to a USB and booting from that, after shrinking my C: drive (the same drive windows is installed to) by 25GB. Ubuntu was installed on that drive under two partitions.

I used the budgie-remix distro. However, after a couple of days I did something wrong with drivers, and it would freeze upon logging in.

As a result, being the idiot that I was, I decided to delete the partitions on which ubuntu was installed, and then re-install it.

I have now tried Xubuntu, WattOS, Mint, Budgie-Remix and Kubuntu and they all refuse to boot, getting to the screen with the logo and the loading before freezing there. This means that I cannot do anything to fix it using a linux terminal as I cannot even boot the live versions from the usb.
I get a few error messages before that comes up that disappear real fast, so the only one I can read before it disappears is something to do with 'broken bios suspected' - which I thought was weird, considering that I had no BIOS. 

I tried going back to a system restore point that I made before installing ubuntu, but was told that all of my restore points were invalid. So, I reinstalled Windows.
That made absolutely no difference, however.
I then messed something else up which meant by Start Menu wouldn't open when trying to fix the issue, and ended up reinstalling Windows *again*

Now, using the command prompt in Windows, I accessed my EFI partition and deleted the 'ubuntu' directory in there.
When I go to UEFI and tell it to boot using the device named 'ubuntu' now, it just boots Windows. (Before I deleted the ubuntu folder in EFI, it sent me to GRUB (without any option to boot, it just gave me a command prompt, and before I deleted the partitions on which Linux was installed, it gave me a menu allowing me to boot budgie).

I then tried installing mint again, but the same thing happens - it gives me a few errors which disappear fast, then goes to the loading screen and freezes, at which point I have to hold my power button in to turn off.

I can't find anything else online - all the guides I find either just allow you to boot windows instead of GRUB, which I already do but I still want to dual-boot, or only apply to BIOS systems, and not UEFI.

Anyone have any idea about what I can do to fix this and get Linux working again?
Thanks in advance :)

---

### Post by oldfred on 2016-12-17
Do you have UEFI secure boot off?
Do you have UEFI fast boot off. My system has seconds setting, so after reconfigured I changed to 3 sec delay, just so I have time to press a key to get into UEFI.
Do you have Windows fast start up off? Windows on updates may turn it back on, so you have to regularly check.

UEFI does have a BIOS mode called CSM or Legacy. Some brands still call UEFI as BIOS. That is to support older configurations or older hardware that was BIOS configured.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

UEFI also has settings for enabling USB and allowing USB boot. My system has setting for UEFI & BIOS boot from USB, but only the UEFI only setting would let me boot in UEFI mode.
If you update UEFI, you have to remember all the settings you changed as it resets to system defaults.

What brand/model system. And what video card/chip?

      
 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by sommanker on 2016-12-17
> **oldfred said:**
> Do you have UEFI secure boot off?
**Yes**
Do you have UEFI fast boot off. My system has seconds setting, so after reconfigured I changed to 3 sec delay, just so I have time to press a key to get into UEFI.
**I've tried both, the same error happens either way**
Do you have Windows fast start up off? Windows on updates may turn it back on, so you have to regularly check.
**That was on, I turned it off now and it changed nothing.**
UEFI does have a BIOS mode called CSM or Legacy. Some brands still call UEFI as BIOS. That is to support older configurations or older hardware that was BIOS configured.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

UEFI also has settings for enabling USB and allowing USB boot. My system has setting for UEFI & BIOS boot from USB, but only the UEFI only setting would let me boot in UEFI mode.
If you update UEFI, you have to remember all the settings you changed as it resets to system defaults.

What brand/model system. And what video card/chip?
**MSI GS40 6QE Phantom, Intel HD Graphics 530 and GTX 970M GPU (using optimus - in fact, it was when I tried installing NVIDIA drivers + bumblebee that Budgie stopped working in the first place)**
      
 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
BootInfo report is here: [http://pastebin.com/1yB18pGg](http://pastebin.com/1yB18pGg)
Somehow that booted, Mint still refuses.

EDIT: Just realised that means that I CAN now access a Linux terminal to run commands through that, if I need to.

---

### Post by oldfred on 2016-12-17
Did you run an old copy of Boot-Repair? Best to just add to live installer. Boot-Repair's live ISO is now older.

You have newer NVMe drive. Some have had issues.

But your issues is the nVidia. I do not know the dual video well.
Some links.

       bbswitch issues with kernel 4.8 Boot parameter pcie_port_pm=off
Dell XPS 15 9550, gpu is Intel HD 530 + GeForce GTX 960M.
[https://github.com/Bumblebee-Project/bbswitch/issues/140](https://github.com/Bumblebee-Project/bbswitch/issues/140)
16.04 Bumblebee
[http://www.webupd8.org/2016/08/how-to-install-and-configure-bumblebee.html](http://www.webupd8.org/2016/08/how-to-install-and-configure-bumblebee.html)
Bumblebee or Prime May 2016:
[http://askubuntu.com/questions/766745/do-i-need-to-install-bumblebee-for-hybrid-graphics-system-to-enable-optimus-on-u](http://askubuntu.com/questions/766745/do-i-need-to-install-bumblebee-for-hybrid-graphics-system-to-enable-optimus-on-u)
Bumblebee may not be required with nVidia Optimus which is installed automatically with newest nVidia driver.
Bumblebee has been depreciated in favor of nvidia-prime
Bumblebee - allows both nVidia & Intel to be used, nVidia Prime was just nVidia, but now updated:

---

### Post by sommanker on 2016-12-17
That's the thing,
I can't boot Linux, because it just freezes. The only one that worked was the boot-repair disk, which I got from here [https://sourceforge.net/projects/boot-repair-cd/?source=typ_redirect](https://sourceforge.net/projects/boot-repair-cd/?source=typ_redirect) .
So, what do I do about fixing those drivers exactly? Is there a way I can use the command prompt in GRUB before booting to stop it from loading the drivers?

---

### Post by oldfred on 2016-12-17
Is it Mint's installer that does not now boot , or actual install?

Can you boot recovery mode or second entry in grub menu.
These instructions are for standard nVidia, not sure if or what may be different for Optimus.

       Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices 
   If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
   sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX

---

