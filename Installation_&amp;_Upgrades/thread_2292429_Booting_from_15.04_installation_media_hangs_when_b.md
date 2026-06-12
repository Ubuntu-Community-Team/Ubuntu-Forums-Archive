---
title: "Booting from 15.04 installation media hangs when booting with UEFI"
date: 2015-08-27
forum: Installation &amp; Upgrades
---

### Post by Nathan_Martini on 2015-08-27
I want to dual boot my laptop with Windows 10 and Linux. I'm attempting to install ***Xubuntu 15.04 x64 ***but when I boot from the installation media it hangs on ***starting version 219*** then eventually my caps lock LED starts flashing and it reboots... rinse and repeat.

I've tried booting from CD and USB, both hang in the same spot. I've tried disabling ***secure boot*** and ***fast boot*** and it still hangs. The only thing I can get to work is if I enable ***UEFI with CSM (Compatibility Support Module)***, then the installation media will boot and I can start the install.

I would prefer to not have ***CSM*** enabled since Xubuntu 15.04 claims to work with EFI and I would like to use EFI only (actually I have to use only EFI because Windows 10 was installed as EFI). Anyone know what the deal is?

The laptops specs are as follows in case that might have something to do with it:


[LIST]
[*] Intel i7 5th gen processor
[*] 64 gigs system ram
[*] 2x Nvidia GeForce 980M with 8 gigs each
[*] Mostly SSDs configured in RAID 0 (Stripe)
[*] Secure Boot Enabled
[*] Fast Boot Disabled
[*] UEFI Enabled
[*] Windows 10 installed (was installed with UEFI enabled)
[*] Windows 10 Fast Startup is disabled
[*] Windows Boot Manager has lowest priority on boot
[/LIST]

**UPDATE**

I tried the same things as above but with ***Fedora 22*** and it produced the same results.

---

### Post by oldfred on 2015-08-28
Are the 980M in the same Maxwell family as the 980 cards?

Maxwell versions need new kernels, support software & video drivers. But 15.04 should be new enough, but you may need nomodeset on grub menu when you boot installer.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

    
       The GTX 970/980 Maxwell GPUs Light Up With Nouveau On Linux 3.19
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg)
NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)

    
 Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
sudo apt-add-repository ppa:graphics-drivers/ppa.

---

### Post by Nathan_Martini on 2015-08-28
nomodeset was the problem, thank you so much. I replaced quiet splash with nomodeset and it now boots into the installation.

---

### Post by Nathan_Martini on 2015-08-28
So it booted into the installation and I was able to connect to my wireless network and start installation but right after I click next after choosing to install updates while installing and to install 3rd party software, the laptop hangs and the caps lock flashes again.

---

### Post by Nathan_Martini on 2015-08-28
This is the error that is happening now. It seems to be sporadic and doesn't happen in the same place every time.

kernel panic - not syncing: timeout synchronizing machine check over cpus
shutting down cpus with nmi

---

### Post by oldfred on 2015-08-28
Did you add ppa & install nVidia driver?

this thread is on 750 Maxwell, but all Maxwell are the same.
 [http://ubuntuforums.org/showthread.php?t=2292419](http://ubuntuforums.org/showthread.php?t=2292419)

---

### Post by Nathan_Martini on 2015-08-28
How would I go about doing that when this is on installation media? It's not an installed instance so any changes aren't persisted so if a reboot is required then I'm back to where I was before.

---

### Post by oldfred on 2015-08-28
I thought it was after you installed.

If installer then you may need other boot parameters in addition to nomodeset.
What brand/model system. 

Does it boot with using internal Intel video chip? That would not need nomodeset but may need other settings. That would isolate video as issue or something else.

 Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support)
Xubuntu 14.04 - GRUB2 nomodeset brings wrong screen resolution - Acer TravelMate 4740 with Intel HD Graphics
[http://ubuntuforums.org/showthread.php?t=2240620](http://ubuntuforums.org/showthread.php?t=2240620)
kernel 3.19 which is implemented with all needed intel graphic stuff
[http://ubuntuforums.org/showthread.php?t=2271798&p=13258951#post13258951](http://ubuntuforums.org/showthread.php?t=2271798&p=13258951#post13258951)

   Mesa 10.5 vs. 10.7 Git, Linux 4.2 Kernel For Intel Iris Graphics 5100
[http://www.phoronix.com/scan.php?page=news_item&px=Mesa-10.5-10.7-HSW-5100](http://www.phoronix.com/scan.php?page=news_item&px=Mesa-10.5-10.7-HSW-5100)
Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)  Dell 17R
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1300349](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1300349)

---

### Post by Nathan_Martini on 2015-08-28
It's an ***MSI GT80 Titan*** laptop. It supposedly has an onboard intel video card but I've not seen a way to switch to that in the BIOS and it comes with a button to switch between the Nvidia cards and the onboard card but the button doesn't seem to do anything. I press it and the LED stays on; it's supposed to turn off when not using the Nvidia cards.

---

### Post by oldfred on 2015-08-28
Both the Optimus dual video and RAID 0 complicate the install.
I do not know details of either.

This showed dri_prime=1 parameter may be required?
[http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1)
older info:
       Dual graphics nVidia GT840M
[http://ubuntuforums.org/showthread.php?t=2262882](http://ubuntuforums.org/showthread.php?t=2262882)
Dual graphics install nVidia prime and newer nVidia driver
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

With RAID, grub may not correctly install, and you have to use Boot-Repair or manually install it. With UEFI it may work?

---

### Post by Nathan_Martini on 2015-08-28
I completely removed the RAID and nVidia cards out of the equation. It's not optimus it's an actual on off switch so when the nVidia cards are off, they're actually not there as far as the system is concerned. 

So, without RAID 0 and without the nVidia cards it boots into the desktop environment without the use of **nomodeset** but still gives the kernel panic.

---

### Post by oldfred on 2015-08-29
In addition to parameters suggested before, these may be required with Intel or laptops.
Use each of these instead of nomodeset. And then maybe add one of the others if required.

 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

---

### Post by Nathan_Martini on 2015-08-29
I tried a bunch of different combinations of what you suggested and nothing works. All of them give the same kernel panic except **i195.i915_enable_rc6=1**, that one gave a kernel panic with stack trace but I couldn't capture what it said.

I'm thinking the issue is either the **Intel Wireless AC 7260 w/bluetooth** or maybe the **Intel Rapid Storage RAID**?

---

### Post by oldfred on 2015-08-29
If you have turned off the RAID, you should have drives in AHCI mode.
The Intel SRT is usually seen as RAID and used to have major install issues, but recent versions  seemed to let Ubuntu install, but grub saw RAID and did not install correctly. Manual work around then required.

I thought newer Intel used this:
i915.i915_enable_rc6=1
Newest used this:
video=VGA-1:1280x1024-24@60
And not yet fully supported Skylake used this:
i915.preliminary_hw_support=1

---

