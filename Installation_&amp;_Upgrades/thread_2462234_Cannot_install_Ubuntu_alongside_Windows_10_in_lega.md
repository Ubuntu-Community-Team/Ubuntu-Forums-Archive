---
title: "Cannot install Ubuntu alongside Windows 10 in legacy mode."
date: 2021-05-17
forum: Installation &amp; Upgrades
---

### Post by achim_59 on 2021-05-17
I bought a laptop with Windows 10 pre-installed. The installation is in legacy mode and won't boot if I turn legacy mode off. I want to keep the Windows installation, because some software is simply not available for Linux (Tom Tom Home for example). When I tried installing Ubuntu 20.04 the Ubuntu live O/S stated "No other O/S was detected" and gave 2 options. 1. Wipe the disk and install Ubuntu. 2. Something else.

I have searched and checked a number of sites with information on how to install Ubuntu alongside Windows 10 but nothing quite seems to fit. There is a detailed guide spread over a number of pages which starts [on this page]("https://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html"). The difficulty with the approach here is that it assumes Windows has been installed in EFI mode, which is not the case on this machine. I did create the the suggested backup/recovery disk for Windows and shrunk the Windows partition to about half the available space (the machine has a 256GB SSD drive), but after that got no further, due to the legacy mode issue.

Another site which seemed quite promising at first [is this one]("https://itsfoss.com/install-ubuntu-dual-boot-mode-windows/"), which allegedly explains how to install Ubuntu alongside Windows in legacy mode. However, when I finished the partioning as described and wanted to coninue with the installation, I got the message "There is no efi/system partition" or words to that effect, with a warning that if I continue then the machine will probably not boot.  I suspect that's not quite true, because it's still in legacy mode and the MBR for Win 10 should still work. But that doesn't help with Ubuntu. If I add the efi/system partition, then I can probably boot Ubuntu by turning legacy mode off, but then Windows won't work... unless I go into the UEFI settings every time I want to switch the O/S. That's also not guaranteed, but I suspect it would work

With every other site I visited, the assumption is always that Windows has been installed in EFI mode.

Does anyone have a suggestion for me? Can Ubuntu 20.04 be installed in legacy mode? I'm happy to provide any further information if required.

---

### Post by CatKiller on 2021-05-17
> **achim_59 said:**
> When I tried installing Ubuntu 20.04 the Ubuntu live O/S stated "No other O/S was detected" and gave 2 options. 1. Wipe the disk and install Ubuntu. 2. Something else.
This is likely completely unrelated to your UEFI/Legacy dilemma. Windows doesn't shut down by default, it simply hibernates. It calls that option "Fast Startup." Partitions in use when a machine is hibernated are marked as dirty so that nothing else (including the Ubuntu installer) will inadvertently change them. They don't exist as far as the installer is concerned. Turn off Windows' Fast Startup and try again.

---

### Post by achim_59 on 2021-05-17
I forgot to mention that... I already turned the fast startup option off. That was one of the steps mentioned in the first link I posted. So the problem has nothing to do with fast startup. 

The difficulty I have is that Ubuntu does not recognize that there is already an O/S on the machine. I am pretty certain that this is due to the CSM setting in the BIOS (that's the legacy mode setting).

---

### Post by Topsiho on 2021-05-17
I think there is a lack of partitions in legacy mode.
In legacy mode the limit is 4 partitions, and Windows probably has used them all.
The way to have more than 4 partitions is to sacrifice one, and in that partition you can create all necessary logical partitions.
As I don't know a thing about Windows I can not say that I put my finger on the sweet spot.

Topsiho

---

### Post by tea for one on 2021-05-17
> **achim_59 said:**
> I bought a laptop with Windows 10 pre-installed. The installation is in legacy mode and won't boot if I turn legacy mode off
Very, very unusual to read of pre-installed Windows 10 in Legacy mode - Is this a recent purchase?
> **achim_59 said:**
> Does anyone have a suggestion for me? Can Ubuntu 20.04 be installed in legacy mode? I'm happy to provide any further information if required.
[U]Observations
[/U]
Did you boot Ubuntu in Legacy mode?

_Suggestions_

Back up and re-install Windows 10 in UEFI mode with GPT
Windows host and Ubuntu in a VM
Convert Windows to UEFI and GPT (if you trust the guide)
[https://www.windowscentral.com/how-convert-mbr-disk-gpt-move-bios-uefi-windows-10](https://www.windowscentral.com/how-convert-mbr-disk-gpt-move-bios-uefi-windows-10)

In your position, I would join the modern world and back up and re-install Windows 10 from scratch. I would then have a reasonable amount of control during the process.

---

### Post by Impavidus on 2021-05-17
May I assume you didn't buy that laptop with preinstalled Windows 10 in legacy mode from a reputable retailer? Because Microsoft has demanded all retailers to always install Windows in UEFI mode since Windows 8. And as I wouldn't trust random people selling computers with a preinstalled OS (they might hide malware), I would wipe the harddrive and reinstall the OS – in UEFI mode.

Having said that, you can install Ubuntu alongside Windows 10 in legacy mode. It works the same way as with earlier Windows versions. Install Ubuntu in legacy mode too, by booting the live disk in legacy mode. The installer shouldn't ask you for an EFI partition (it didn't when I installed Xubuntu 20.04 with manual partitioning a year ago on my legacy laptop), but I've seen some reports about the installer creating an EFI partition anyway when doing things automatically. In legacy mode, that EFI partition isn't actually used. And FastStartup must indeed be off. Don't confuse it with the similarly named fast boot, which is a different setting, and you probably want that off too.

Keep in mind that systems dual booting Windows 8 or later and Ubuntu in legacy mode on a single hard drive are rather fragile. You should have repair disks for both Windows and Ubuntu ready.

---

### Post by achim_59 on 2021-05-17
> **Topsiho said:**
> I think there is a lack of partitions in legacy mode.
In legacy mode the limit is 4 partitions, and Windows probably has used them all.
The way to have more than 4 partitions is to sacrifice one, and in that partition you can create all necessary logical partitions.
As I don't know a thing about Windows I can not say that I put my finger on the sweet spot.

Topsiho

I'm not that up to date with Windows either, but I do know there is no 4 partition limit. After my second attempt (where I got the "no efi/system partition" message from Ubuntu) I already had 5 partitions. Windows doesn't really care what other partitions exist, it only cares about its own.

---

### Post by achim_59 on 2021-05-17
@tea for one
> Very, very unusual to read of pre-installed Windows 10 in Legacy mode - Is this a recent purchase?
Yes, it is. 

> 
Did you boot Ubuntu in Legacy mode?

Indeed I did.

> 
Back up and re-install Windows 10 in UEFI mode with GPT
Windows host and Ubuntu in a VM
Convert Windows to UEFI and GPT (if you trust the guide)
[https://www.windowscentral.com/how-convert-mbr-disk-gpt-move-bios-uefi-windows-10](https://www.windowscentral.com/how-convert-mbr-disk-gpt-move-bios-uefi-windows-10)

In your position, I would join the modern world and back up and re-install Windows 10 from scratch. I would then have a reasonable amount of control during the process.
Thanks for the tip... I'll check it out.

@Impavidus

I bought the machine from a reputable second hand dealler. They've been in business for 20 years and this isn't the first time I bought a machine from them.
> 
...you can install Ubuntu alongside Windows 10 in legacy mode. It works the same way as with earlier Windows versions. Install Ubuntu in legacy mode too, by booting the live disk in legacy mode. 
That was exactly what I tried last time, but I'm obviously missing some vital point here. Otherwise I wouldn't get that "no efi/system partition" message.
> 
And FastStartup must indeed be off. Don't confuse it with the similarly named fast boot, which is a different setting, and you probably want that off too.
Fast startup is a Windows system setting and it is turned off. Secure boot is a BIOS setting and that, too, is turned off. I'm not sure what "fast boot" is, so I'll have to do some more research, I guess

---

### Post by tea for one on 2021-05-17
> **achim_59 said:**
> I bought the machine from a reputable second hand dealler. They've been in business for 20 years and this isn't the first time I bought a machine from them.

This PC was a second hand machine **not** brand new?
I imagine that the dealer installed Windows 10 in Legacy mode?

By the way, there are a few [COLOR="#0000FF"]fast[/COLOR] start up, boot methods and they are not consistent among all OS systems and UEFI/BIOS iterations.
I have come across these 3 so far............

Fast boot (UEFI settings)
Fast start up (Windows setting - hibernation)
Fastboot (grub setting to prevent file system check)

Anyway, I still recommend that you install Windows 10 in UEFI mode with GPT.

---

### Post by oldfred on 2021-05-17
If installer wants an ESP - efi system partition, then you did not boot Ubuntu in BIOS/Legacy/CSM mode. It only wants ESP in UEFI boot mode to install UEFI version of grub into that ESP.

Post this:
sudo parted -l

If using Rufus to create USB installer, it creates installer in UEFI only mode or in BIOS only mode. Most installer create a flash drive that can be booted in either boot mode, but then in UEFI you have to select which mode you want. How you boot install media UEFI or BIOS, is then how it installs.

One more vote for reinstalling Windows in UEFI boot mode.

---

### Post by ubfan1 on 2021-05-17
Windows in legacy mode is on an MSDOS partitioned disk, which has a maximum of four primary partitions.  If one of those primary partitions is an extended partition, it may contain more logical partitions, and Ubuntu may be installed on those without problem.  The problem is that shrinking some other primary partition will create unallocated space which is not within the extended partition, so is not usable to make an Ubuntu partition (if all four primary partitions are already in use). For a "new" machine, I'd really consider switching to UEFI/gpt partitioning and avoid those sorts of "old" issues.  That said, I run W10/Ubuntu 18.04 in legacy on my primary disk, but normally boot Ubuntu 20.04 off an SSD in UEFI mode -- too lazy to make the change on a 10 year old machine.

---

### Post by achim_59 on 2021-05-31
My apologies... I've been away for a bit over a week. No chance to do anything regarding this issue in that time.

*@tea for one*
> Anyway, I still recommend that you install Windows 10 in UEFI mode with GPT. 
I tried that a while back. I only got as far as step 3. There it says to select the "volumes" tab. Unfortunately the wasn't any such tab available. I seem to have a rather obscure Win 10 installation on this machine. If I didn't need Windows for two programs, I'd wipe the whole disk and just use Ubuntu Linux. I'll try going through the procedure anyway and I'll post the results.

*@old fred*
>  If installer wants an ESP - efi system partition, then you did not boot Ubuntu in BIOS/Legacy/CSM mode. It only wants ESP in UEFI boot mode to install UEFI version of grub into that ESP.
I hate contradicting someone who is obviously an expert, but CSM (legacy mode) is definitely enabled. I tried it once without CSM, but when I discovered that Windows won't boot without it, I switched it back on. The Ubuntu installer never-the-less complained with the "no efi/system partition" message. I will post the results of your suggested "sudo parted -l" once I've tried the suggestion from *tea for one*

*@ubfan1*
Thanks for the detailed info on DOS partitions. When I last tried the Ubuntu installation, I had the Widows "system reserved" partition (I assume that contains the MBR), the main drive (c:\ ) and "the rest" on  which I created logical partitions for boot, swap, and root.

---

### Post by oldfred on 2021-05-31
The very newest Ubuntu 21.04 does seem to create a FAT32 partition on MBR drives. Not sure why.

But how you install UEFI or BIOS totally depends on which boot mode you select when booting live installer from UEFI boot menu.
Most tools create an installer that will boot in either UEFI or BIOS boot mode. 
But some like Rufus only create installer in one mode or the other and then you only have that one option in UEFI boot menu.

The setting in UEFI settings for boot mode, if for your installed system.

---

### Post by achim_59 on 2021-06-01
Despite the fact that the instructions in the link provided by *tea for one* ([https://www.windowscentral.com/how-c...efi-windows-10](https://www.windowscentral.com/how-c...efi-windows-10)) did not quite fit to my Win 10 installation, I tried to follow through the steps, ignoring the bits that don't fit. Just looking at the partitioning, I couldn't imagine that the setup was anything other than a standard legacy mode setup. I therefore skipped the check at step 3 and just called up the admin console, followed the instructions and, presto, I had successfully converted the BIOS to EFI.

Next step was the installation of Ubuntu. This time it did show me the expected option "install alongside Windows". Of course, it couldn't be quite that simple. I had already shrunk the Windows partition and now Ubuntu wanted to install itself on the shrunk partition rather than in the free space. 

Once again, I selected the option "Something else" and went through the steps to create the required partitions in the free space. as a guide I used the instructions at [https://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html]("https://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html") (only the partitioning). I created a swap partition and a root partition and allowed grub to install in the same partition as the windows boot manager. That's about the simplest setup that you can get away with.

Once the installation was complete, everything worked as expected. I get the grub boot menu at the start and I can boot either Windows or Linux.

My thanks to all who contributed to this thread, especially *tea for one*, who came up with the vital tip for converting Windows to a UEFI bootable system. Once again, I've learned a lot and also solved my problem.

---

