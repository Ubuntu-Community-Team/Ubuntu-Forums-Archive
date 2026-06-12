---
title: "Can't seem to boot 20.04 Live Session Dell XPS 8900"
date: 2022-03-23
forum: Installation &amp; Upgrades
---

### Post by jetman350 on 2022-03-23
I'm struggling to boot Kubuntu 20.04 Live Session on my Dell XPS 8900.  I think it has something to do with either Secure Boot or more likely the NVIDIA GeForce GTX 745? Isn't there a Key Combo that will get me into Compatibility Mode?  Will someone help me understand why and what I should be doing to get it too boot. I actually got it to boot, and chose Try out Kubuntu, everything was really slow and then got some PCI Error in long strings, now nothing. It finally came up but said something about a file system error.  Also, is it normal for the Live Session to do a File System Check on every boot? I made the flash drive with Balena Etcher. I'm also using an M.2 SATA Drive.

---

### Post by oldfred on 2022-03-23
Have you updated UEFI to latest from Dell?
And updated SSD firmware?

Dells typically require multiple UEFI setting changes.
It needs UEFI setting for drives changed to AHCI, not Intel RST nor RAID. But if dual booting with Windows you must first install AHCI drivers into Windows or it will not boot.
Often better to have UEFI Secure boot off. And UEFI fast boot off, as that assumes no system changes & you are changing system.
Newer systems need legacy off to boot in UEFI mode.
And in Windows you need Windows fast start up off as that sets hibernation flag and then Linux NTFS driver cannot see the NTFS partitions. Note that Windows updates may turn fast start up back on.
Older Dell seemed to need legacy on, but still select UEFI to boot (without secure boot). 

Are you booting live installer in UEFI mode?
UEFI boot options for flash drive should have UEFI: xxx or xxx where xxx is name or label of flash drive. You want the UEFI option.
And if you have nVidia you want to use Safe Boot option. Not sure which version added that. Before that option you had to add nomodeset boot parameter. And during install choose to include proprietary drivers so nVidia driver installed. Before to boot install, you again had to use nomodeset & manually add nVidia in the install.

---

### Post by jetman350 on 2022-03-23
I will do that!

Yes, booting Live Installer in UEFI Mode as I already have Windows 10 Home Installed.  I'm thinking about a Dual Boot with Kubuntu.  Where are the Tutorials on booting Live Session with Nvidia?  I looked at all the official Ubuntu stuff but none of it is any good!  I guess I just push any key to get into Safe Boot Option (though I don't think that is what it is called?)  Honestly I've never had many issues booting a Live Environment before, maybe a long time ago, so don't really know what to think of all this.

Thanks

---

### Post by oldfred on 2022-03-23
I forget which version added the safe boot option.
But if it is there then it is one of the grub menu items.

If no Safe Boot option use nomodeset boot parameter on the linux line in grub menu.

Safe Graphics Boot option on installer adds nomodeset.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If you need nomodeset boot parameter, you will also need it after install and until you install the correct nVidia driver.
Only install nVidia driver from Ubuntu repository.

sudo ubuntu-drivers autoinstall

---

### Post by jetman350 on 2022-03-23
I don't understand the logic with installing AHCI Drivers, they are already installed as are all system drivers?  Are you saying in case they are not?  All Devices in Device Manager are taken care of.

---

### Post by oldfred on 2022-03-23
For whatever reason, new systems often ship with RAID or Intel RST driver, even if just one drive.
Windows has AHCI driver, but it is not installed by default.

Linux needs AHCI driver to work, not Intel RST or "fake RAID" (motherboard based RAID). If you have multiple drives & want RAID better to use software RAID, but that does not work with dual boot Windows.

---

### Post by jetman350 on 2022-03-23
What about Boot Loader placement, does it go on /sda or EFI?

---

### Post by jetman350 on 2022-03-23
> **oldfred said:**
> For whatever reason, new systems often ship with RAID or Intel RST driver, even if just one drive.
Windows has AHCI driver, but it is not installed by default.
Yes, I've noticed this for sometime now and still don't fully understand it.  I just seen the Safe Graphics Option booting Live Session, so that is good.  Don't know how I missed it before.

> **oldfred said:**
> Linux needs AHCI driver to work, not Intel RST or "fake RAID" (motherboard based RAID). If you have multiple drives & want RAID better to use software RAID, but that does not work with dual boot Windows.
Whoops, I missed this one, thanks!  I would love to get this tower on Kubuntu and don't need raid, and don't even fully understand it though I've read many articles on it.  

Just booted with Safe Graphics Mode and all is still super slow to come to a desktop, something is not right.  Will go back and see if I can Enable Legacy in some capacity but I'm sure that is not supported on Dell Computers.  I am in now and running live, but it is still not right, slow and can't get certain things to work, freezing.

---

### Post by oldfred on 2022-03-23
Do you have nVidia driver installed. That often is the major issue.

But some other settings that may improve system:

Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

[https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster](https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster)

---

### Post by jetman350 on 2022-03-23
This is just a live session, no drivers installed yet, can't even get that far!

---

### Post by jetman350 on 2022-03-23
[THIS FIX]("https://forums.linuxmint.com/viewtopic.php?t=221225") allows me to use the Live Session well now in Safe Graphics Mode.  Now will look up some info on installing as EFI, I know it is not well documented like everything else linux.

---

### Post by oldfred on 2022-03-23
Did you look in the link in my signature below? :)

---

### Post by jetman350 on 2022-03-23
> **oldfred said:**
> Did you look in the link in my signature below? :)
No I didn't, sorry, I'm a bit absent minded due to my health.  I will look over your links and hope I can find what I'm looking for.  It would be better if someone would answer my questions so I could understand the whole thing.

For instance, with an already installed Windows 10, not allowing me to change the size of the boot partition (worried about it filling up adding the Linux boot stuff) should I create a Linux Boot EFI, and if so do I point the boot loader to that partition.  So in essence the system will be only using the new linux boot partition.

---

### Post by oldfred on 2022-03-23
Only one ESP per device/drive.

If only using Windows & Ubuntu with grub, you will not have an issue with the size of the ESP.
Do not confuse a Linux boot partition which must be a Linux format with an ESP - efi system partition which must be FAT32.
Most desktop installs do not need a separate /boot partition. If a server install or using full drive encryption (more difficult with dual boot as then not full drive) then you may want a /boot partition.

UEFI suggests 500MB for an ESP. Older Windows installs used 100MB and many have dual booted with that. I think Windows now uses a larger ESP if it sees a larger drive.

I use a larger ESP as my drives are larger, but normally use very little. For a full install to a flash drive, I typically only have one install and have a small ESP.
I do like a larger ESP, as with Linux only I had to download UEFI updates to a FAT32 partition. I was then able to use my ESP, but could have used a flash drive or created another FAT32 partition for that purpose.

Some install systems that use SystemD boot instead of grub. I believe it requires more space in the ESP as it has more files. But have seen those in another partition also. Do not know details of SystemD boot.

---

### Post by jetman350 on 2022-03-23
Okay, so where to point the boot loader, /sda or EFI?

---

### Post by oldfred on 2022-03-23
Whether UEFI or BIOS you always specify a drive like sda, never a partition like sda1.
But with UEFI any selection does not matter. It finds ESP on first drive and installs grub2's boot files into that ESP.

If you want grub anywhere else you have to do one of various work arounds.

---

### Post by jetman350 on 2022-03-23
Got it, thanks!

Should I start another thread on the best way to install and get the newer Nvidia Driver?  I assume to boot and install from Safe Graphics Mode, then reboot and install the suggested driver from the built in driver installer?  Or do I have to append nomodeset to grub on reboot?

---

### Post by oldfred on 2022-03-24
Newest Ubuntu has Safe Boot and then a choice to install proprietary drivers which will install correct nVidia driver.
Otherwise you have to use the old boot parameter nomodeset.

Safe Graphics Boot option on installer adds nomodeset.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

