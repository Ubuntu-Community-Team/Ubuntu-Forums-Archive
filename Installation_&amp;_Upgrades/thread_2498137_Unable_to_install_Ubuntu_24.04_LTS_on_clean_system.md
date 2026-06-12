---
title: "Unable to install Ubuntu 24.04 LTS on clean system"
date: 2024-06-01
forum: Installation &amp; Upgrades
---

### Post by terribull on 2024-06-01
**Core problem.** I can't successfully install Ubuntu 24.04 LTS on a clean machine via USB installer
**Where I'm stuck.** I get some combination of these three things whenever I power on the system:

[LIST=1]
[*]Flashes *error: file `/boot/` not found.* before I see the GRUB 2.12 boot loader
[*]Shows *error: you need to load the kernel first.* after choosing Try or Install Ubuntu
[*]Indefinite black screen after choosing Try or Install Ubuntu
[/LIST]
**System.** I'm building the computer from scratch. To minimize variables before installation, I only assembled the following:

[LIST]
[*]Motherboard: MSI Pro Z790-P WIFI, brand new
[*]CPU: Intel Core i3-12100 (integrated Intel UHD 730 graphics), with a GAMMAXX Series AG400 cooler
[*]RAM: 1 of 2 16GB modules of Corsair Vengeance DDR5 5200 Mhz, set in slot 2 as explained in the motherboard's manual
[*]Storage: 512 GB Kingston NV2 M.2 2280 internal SSD, installed in the primary storage slot
[*]Corsair 750W PSU, with motherboard and CPU connectors installed
[*]HDMI monitor connected to the motherboard's back panel I/O
[*]USB keyboard connected to the motherboard's back panel I/O
[*]USB installer connected to the motherboard's back panel I/O
[*]No case: I turn the computer on using a screwdriver, and use the power switch on the PSU to turn the computer off.
[/LIST]
Things I've tried so far. I did some Googling before getting to this point, and have tried the following:

[LIST]
[*]**Created multiple installers.** [Following this guide]("https://ubuntu.com/tutorials/install-ubuntu-desktop"), I've made one using balenaEtcher on Windows 11. Before that, I had made it using Rufus - and also tried the UEFI only flash setup.
[*]**Tried another USB stick.** Using a different USB stick and [following this guide]("https://ubuntu.com/tutorials/create-a-usb-stick-on-macos"), I've also made one using Etcher on MacOS.
[*]**BIOS configurations.** The computer successfully loads the BIOS, where I have disabled Fast Boot, Secure Boot, and changed boot priorities. I don't overclock my hardware, and I have flashed the BIOS a couple times to see if it would make a difference while I tested the different USB installers.
[*]**Tried different USB ports.** Whether USB 3.0 or USB 2.0, the results are the same.
[*]**Tried a different system (and it worked!).** With the balenaEtcher Windows 11 USB installer, I plugged it into my gaming desktop (Ryzen 5600X, GTX 3070 Ti) running Windows 11. After changing the boot order (seems like AMD or the specific mobo does not support Fast Boot or Secure Boot), I saw the GRUB 2.12 boot loader and selected *Try or Install Ubuntu*. After a few seconds, the machine booted into the Live Ubuntu OS. To me, that suggests the USB installer is working fine.
[/LIST]
So, if you're still here (and I thank you!), what can I do to get Ubuntu 24.04 LTS on my new system?

[LIST]
[*]Why is the installer not working on this Intel hardware but working fine on AMD?
[*]Is there any way to install Ubuntu 24.04 LTS onto the SSD without using the USB? I thought about installing the drive into the secondary M.2 slot of the AMD system, but if Ubuntu installs Intel-specific drivers and stuff that probably will mess things up...
[*]I'm just learning now that 24.04 LTS is pretty new - could it just be issues stemming from being a new release?
[/LIST]
Thanks much in advance for any guidance.

---

### Post by gezzer2 on 2024-06-01
you seem to have tried everything i would have tried 
have you checked in the BIOS to see if boot from USB is enabled ?

not of much help but its worth a look ..

---

### Post by tea for one on 2024-06-01
> **terribull said:**
> Why is the installer not working on this Intel hardware but working fine on AMD?
I would doubt if this is an Intel/AMD issue.
More likely something concerned with UEFI settings - more specifically Security Configuration or TPM or Platform Management
e.g. Platform Trust Technology, Firmware Platform Trust Module and similarly named settings
Some motherboards have extensive settings in all sorts of menus and submenus so it's difficult to offer exact advice without intimate knowledge of the device.
> **terribull said:**
> I thought about installing the drive into the secondary M.2 slot of the AMD system, but if Ubuntu installs Intel-specific drivers and stuff that probably will mess things up
Certainly worth a shot.
I had an nvme disk with Ubuntu 22.04 installed on Intel Core i3-8109U and I popped the drive in a PC with AMD Ryzen 7 7735HS, surprisingly everything worked.
I've also cloned the disk with Clonezilla and used the clone in the Intel PC - luckily still successful operation.

---

### Post by currentshaft on 2024-06-01
To me it sounds like Secure Boot. I've always had to turn it off to install Ubuntu, but on 24 LTS and recent hardware I had similar issues until it was enabled AND "third-party" CAs were trusted.

---

### Post by terribull on 2024-06-01
Okay, so some updates and twists.

**I successfully installed Ubuntu 24.04 LTS on the SSD** by inserting it into my AMD's machine's secondary M.2 slot and running the installer from that machine. I then put that M.2 drive back into the Intel machine... but even running from the M.2 drive, the Intel machine refuses to load into Ubuntu :(

A few notes:

[LIST]
[*]I chose the default erase and install option from the installer, which I think created an EFI boot loader and Ubuntu installation
[*]When I boot up the Intel machine, I see GRUB 2.12 with following options:
[/LIST]
```

*Ubuntu
 Advanced options for Ubuntu
 Memory test (memtest86+xx64.efi)
 Memory test (memtest86+x64.efi, serial console)
 Windows Boot Manager (on /dev/nvme0n1p2)
 UEFI Firmware Settings

```
[LIST]
[*]When I try the Ubuntu options, I get error: you need to load the kernel first.; when I try the other options, I get error: bad shim signature. error: you need to load the kernel first.
[*]I thought maybe updating the BIOS might help - it didn't. But if it helps the diagnosis, [the BIOS version]("https://www.msi.com/Motherboard/PRO-Z790-P-WIFI/support") is now **E7E06IMS.ACO** (dated 04/16/2024)
[/LIST]
 
> **gezzer2 said:**
> have you checked in the BIOS to see if boot from USB is enabled ?

I didn't see any options for that in my BIOS, but MSI's Click BIOS has a very clear Boot Priority section. When I was trying to get the installer to work, I would set the USB device to be the highest priority. I believe that worked properly, because I would see GRUB - it's just that selecting any of the options from GRUB were dead ends.

> **tea for one said:**
> I would doubt if this is an Intel/AMD issue.
More likely something concerned with UEFI settings - more specifically Security Configuration or TPM or Platform Management
e.g. Platform Trust Technology, Firmware Platform Trust Module and similarly named settings
Some motherboards have extensive settings in all sorts of menus and submenus so it's difficult to offer exact advice without intimate knowledge of the device.

So yes, the MSI Pro Z790-P WIFI has a Security section, with the following areas/options:
[LIST=1]
[*]**Administrator Password.** Didn't touch this, didn't seem relevant
[*]**U-Key - Disabled.** Didn't do anything with this.
[*]**Trusted Computing**
[LIST]
[*]Seems to be several items here, that broadly speaking say it has a TPM 2.0 device, with options for enabling or disabling SHA256, SHA384, and SM3_256 PCR banks
[*]I chose to disable Security Device Support, which disappeared all the configuration options.
[/LIST]

[*]**Chassis Intrusion Configuration.** Didn't do anything with this.
[*]**Secure Boot.** You can choose to enable or disable it. Disabling it did not seem to resolve my problem, and with enabling it there are many branches:
[LIST]
[*]You can choose two modes for Secure Boot: Standard or Custom. When I did try enabling it (unsuccessfully), the mode was set to Standard
[*]When I choose Custom, more options become available:
[LIST]
[*]Secure Boot Preset: Hardware/OS Compatibility or Maximum Security. The first option is default.
[*]Key Management. This seemed to expand into a bigger section that I know nothing about, but here's what I saw in textual form - each line seems to be an option itself
[/LIST]
[/LIST]
[/LIST]

```

Provision Factory Default keys [Enabled]
Enroll all Factory Default keys
Delete all Secure Boot variables
Enroll Efi Image
Save all Secure Boot variables

```
And then there seems to be a table made of text, again each option being something you can drill into - but i didn't touch:
```

Secure Boot variable | Size | Keys | Key Source
Platform Key (PK) | 817 | 1 | Factory
Key Exchange Keys (KEK) | 3884 | 3 | Factory
Authorized Signatures (db) | 3961 | 3 | Factory
Forbidden Signatures (dbx) | 17836 | 371 | Factory
Authorized Timestamps (dbt) | 0 | 0 | No key
OsRecoverySignatures (dbr) | 0 | 0 | No key

```

So, maybe there's a solution somewhere in this area - but I definitely lack the technical knowledge to know where to start.

> **currentshaft said:**
> To me it sounds like Secure Boot. I've always had to turn it off to install Ubuntu, but on 24 LTS and recent hardware I had similar issues until it was enabled AND "third-party" CAs were trusted.

Based on the fact that I was able to install it onto an M.2 drive on a non-Secure Boot machine, and then when I've tried to boot into Ubuntu on a Secure Boot machine I'm thinking similarly. But in my attempts, disabling Secure Boot doesn't let me get into Ubuntu and enabling Secure Boot with whatever the standard settings are also doesn't let me get into Ubuntu. Perhaps there are keys or files I need to hand to the BIOS?

---

### Post by currentshaft on 2024-06-01
Does your BIOS have an option to the effect of allowing third-party CAs? Because by default secure boot only allows Microsoft operating system, afaik.

How the bootable USB installer is made matters also. If you have access to another Ubuntu host, I recommend using startup disk creator for UEFI/secure boot compatible volumes.

---

### Post by terribull on 2024-06-02
> **currentshaft said:**
> Does your BIOS have an option to the effect of allowing third-party CAs? Because by default secure boot only allows Microsoft operating system, afaik.

How the bootable USB installer is made matters also. If you have access to another Ubuntu host, I recommend using startup disk creator for UEFI/secure boot compatible volumes.

I see no mention of third-party CAs in the manual for [MSI's Intel 700-series chipset BIOS 5]("https://download.msi.com/archive/mnu_exe/mb/Intel700BIOS.pdf"). But [this Reddit thread]("https://www.reddit.com/r/linux/comments/wacrv2/microsofts_rationale_for_disabling_3rd_party_uefi/") suggests I may need to [manually add my keys]("https://wiki.archlinux.org/title/Unified_Extensible_Firmware_Interface/Secure_Boot#Using_your_own_keys") pertaining to a distro. And there do seem to options for managing keys in the BIOS...

I do have a machine currently running Ubuntu (the one I'm trying to replace). I willgive that a go and see what happens...

---

### Post by tea for one on 2024-06-02
> Incompatible UEFI cases

32-bit Windows operating system - this motherboard supports only Windows 10/
Windows 11 64-bit operating system.
The text above is from page 3 of the link to your UEFI-BIOS
[s]Have MSI really locked this firmware to prevent the use of other operating systems?[/s]
Edit: Thankfully, not true - please see post 10 below

---

### Post by oldfred on 2024-06-02
Did you also update firmware on SSD? Even new drive may have an update available. Compare to vendors support site.
sudo lshw | grep -m 1 -A 5 "*-firmware" & 
udisksctl status

Do you also have Video card or just Intel video?
If separate video card then if UEFI Secure boot on, you have to set a MOK - machine owner key. Often easier to just have UEFI Secure Boot off.
Otherwise it should just install whether UEFI Secure Boot on or not.

If getting to grub menu, you are booting, but then often another driver issue.
Can you use grub's recovery mode?

When installing from a different system, installer will put UEFI boot entry into that system's UEFI. You have to use efibootmgr or reinstall grub to add UEFI boot entry into system, when not same system. You may be able to boot internal drive with  drive entry that uses /EFI/Boot/bootx64.efi which is what external drives, flash drive installers, etc use.

MSI Z790
[https://ubuntuforums.org/showthread.php?t=2494277&p=14175061#post14175061](https://ubuntuforums.org/showthread.php?t=2494277&p=14175061#post14175061)
MSI MAG Z790 TOMAHAWK WIFI Use Safe mode
[https://askubuntu.com/questions/1508950/ubuntu-23-10-i-cant-run-the-ubuntu-installer-on-my-pc](https://askubuntu.com/questions/1508950/ubuntu-23-10-i-cant-run-the-ubuntu-installer-on-my-pc)

MSI - many models Secure Boot issue
MSI has very insecure Secure Boot defaults
[https://github.com/Foxboron/sbctl/issues/181](https://github.com/Foxboron/sbctl/issues/181)

Older systems may have similar issues.
User found where MSI locked the boot order in the BIOS.
In the MSI UEFI BIOS Setting, Toggle from Advanced Mode to Basic Mode. Bottom of list                   
 MSI B450M Pro-Vdh Max Unable to install Ubuntu (Black Screen)  UEFI update required
[https://askubuntu.com/questions/1340556/unable-to-install-ubuntu-black-screen-uefi?noredirect=1#comment2290153_1340556](https://askubuntu.com/questions/1340556/unable-to-install-ubuntu-black-screen-uefi?noredirect=1#comment2290153_1340556)
MSI X570 ACE motherboard and Nvidia RTX 2070 SUPER GPU.Asus
[https://askubuntu.com/questions/1317921/ubuntu-20-04-lts-needs-bios-reset-after-each-reset-to-boot](https://askubuntu.com/questions/1317921/ubuntu-20-04-lts-needs-bios-reset-after-each-reset-to-boot)

some issues can be common across brands for similar model.
 ASUS PRIME Z790-P WIFI motherboard.
[https://www.phoronix.com/review/intel-14600k-14900k-linux](https://www.phoronix.com/review/intel-14600k-14900k-linux)
Asus Z790-V MB with 12th gen i9 
[https://ubuntuforums.org/showthread.php?t=2492106](https://ubuntuforums.org/showthread.php?t=2492106)

---

### Post by terribull on 2024-06-03
[FONT=Verdana]Okay, calling this one solved, though a pyrrhic victory at best.

[/FONT]
[FONT=Verdana]Core problem solved[/FONT][FONT=Verdana]. I installed Ubuntu 24.04 LTS onto a clean system via USB installer successfully.[/FONT]
[FONT=Verdana]Related problems (also solved)[/FONT][FONT=Verdana]. The Intel-based system (described in first post) boots into Ubuntu successfully and is fully operable as far as I can tell.[/FONT]

[FONT=Verdana]Summary of what has transpired since last update:[/FONT]

[LIST]
[*][FONT=Verdana]I followed currentshaft's advice of creating a USB installer from my current Ubuntu machine, but following [/FONT][[COLOR=#1155CC][FONT=Verdana]this guide that utilizes Startup Disk Creator[/FONT][/COLOR]]("https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu")[FONT=Verdana] as indicated. The only difference is that I downloaded and targeted a 24.04 LTS iso instead of what the guide showed. For whatever reason, this USB installer was able to run properly with secure boot enabled.[/FONT]
[*][FONT=Verdana][/FONT] I overwrote the installation I had previously done, shut down the computer and pulled out the USB installer.
[*]The machine booted into Ubuntu successfully(!) - I planned to document what my BIOS settings were at that point for the forum reply, but also at that time reviewed oldfred's link above about MSI having very insecure Secure Boot defaults
[*]I shut down the machine, went into BIOS, and made changes based on guidance I'd read that amounted to changing some security options. I believe this tweaking wiped out stuff the USB installer did to some combination of GRUB, its configuration, or enrolled keys. The net result: no longer booted into Ubuntu.
[*]After lots of trial and error and reading articles about how to use GRUB to try and run things, I stumbled upon [[COLOR=#1155CC][FONT=Verdana]this Boot Repair article[/FONT][/COLOR]]("https://help.ubuntu.com/community/Boot-Repair")[FONT=Verdana]. I found that I could still boot into an Ubuntu Live session when the USB installer was used, so I did that and then followed its instructions to install and run Boot-Repair[/FONT]
[*][FONT=Verdana][/FONT]I ran the diagnosis, clicked the Make Recommended Repairs button, and copypasted commands the tool asked me to. It then finished by telling me that before I try to boot into Ubuntu next, disable Secure Boot.
[*]Upon disabling Secure Boot, I now see GRUB - and when  I choose **Ubuntu*, it actually boots up!
[/LIST]

[FONT=Verdana]Final settings in the MSI Pro Z790-P WIFI BIOS:[/FONT]

[LIST]
[*][FONT=Verdana]MSI Fast Boot: disabled[/FONT]
[*][FONT=Verdana][/FONT]Fast Boot: enabled (theoretically doesn't matter because that's for Windows 10)
[*]TPM: enabled
[*]Secure Boot: disabled
[/LIST]

[FONT=Verdana]My read on the situation is that whatever methods balenaEtcher or Rufus use to create the Ubuntu installer on Mac/Windows does not jive with MSI’s firmware or implementation of Secure Boot, while Startup Disk Creator’s does. And it’s possible that when you do install from that USB installer, that installation could boot into Ubuntu with Secure Boot enabled.[/FONT]

[FONT=Verdana]But the Boot-Repair tool specifically makes changes and then tells you to disable Secure Boot. Following that guidance worked for me, even if it leaves the system overall less secure.[/FONT]

[FONT=Verdana]Thanks all for taking the time to help.[/FONT]

---

### Post by tea for one on 2024-06-03
Well done, terribull - admirable perseverance.

---

### Post by oldfred on 2024-06-03
Glad you got it working.

It sounds like Boot-Repair had you totally reinstall grub without the signed versions or for UEFI Secure Boot off.

Any idea what settings that the site recommended changing made issue worse?
Not sure if MSI would have fixed issues by now also, since that was from 2022?

For desktop that I have inside house I do not use UEFI Secure Boot.
But still am careful with clicking on any unknown emails or installing anything that is not known as standard Ubuntu software.

---

