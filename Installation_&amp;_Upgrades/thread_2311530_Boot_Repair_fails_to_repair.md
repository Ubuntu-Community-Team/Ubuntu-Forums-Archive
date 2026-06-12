---
title: "Boot Repair fails to repair"
date: 2016-01-28
forum: Installation &amp; Upgrades
---

### Post by evanfmanuella on 2016-01-28
I'm currently using a Lenovo t450s. Initially, it had windows 7 installed. I upgraded to 8. 

I then re partitioned the drive and added Ubuntu 14.04. 

It is worth noting at this point that GRUB did not recognize windows 8- I had to manually interupt boot in order to boot windows 8.

Here's where the trouble begins.

I then decided to reinstall ubuntu. Now, when I boot grub does not launch ubuntu, but gives me a prompt.

I burnt a disk image of boot-repair to a disk, and attempted to repair.

Boot-repair launched, and informed me that my PC was booting in legacy mode and it needed to be switched to EFI mode.

I changed the settings in the BIOS from "Both" to UEFI Mode Only.

This resulted in Boot-Repair not being able to boot.

It would either sit on a blank screen (with a few pixels displaying shades of purple) or reset the computer.

I'm not sure how to proceed.

I'd prefer not to wipe the entire computer, but I'm at a loss of what I can do to remedy this issue.

pastebin:
[http://paste.ubuntu.com/14686377/](http://paste.ubuntu.com/14686377/)

---

### Post by Dreamer Fithp Apprentice on 2016-01-28
> **evanfmanuella said:**
> I'd prefer not to wipe the entire computerDefinitely don't.

> **evanfmanuella said:**
> I'll try and get a pastebin posted from Boot-repair ASAP.Definitely do.

You may get advice later from someone well informed about UEFI. I'm not. But if it was working before, I'd return the bios setting to what was working regardless of what Boot Repair says.

You didn't say how you installed or attempted to reinstall Ubuntu. I wonder about the media you installed from. Maybe check the hash on the download, burn a new clean disk, and check it again with the built in self check. Then reinstall. Ubuntu really has an excellent installer, better than its parent Debian even. I've never had it fail to recognize another OS. I don't think I can say that about ANY other OS I've tinkered with and there have been maybe a couple of dozen. Be very careful to read everything on the screen and consider what it means before you click the next button. Let it install grub. I'd be surprised if it didn't work.

---

### Post by ajgreeny on 2016-01-28
Your machine is set up with UEFI mode boot and uses a GPT partition table, so you will have to return the boot system to UEFI to install ubuntu and also to be able to boot to Windows, which will not work at all in legacy BIOS mode if it is using GPT partitions.
Can you also confirm that this is a 64bit Ubuntu that you are installing.

I recommend that you make another USB install medium and then boot to that in UEFI mode.
See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
and for more detailed info [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by evanfmanuella on 2016-01-28
@gjgreeny : Yes this is 64 bit Ubuntu. There's also a "Both - CSM" option within the BIOS options. Which from what I'm reading I should enable.

@dreamer : I've matched the hashes.

I'll revert to previous settings and see if that rectifies this issues.

Update   : I've reverted to defaults and disabled secure boot. Boots straight into windows without GRUB. I'll try and mess with the boot order.
Update 2: When I boot directly to disk, grub does not start- just windows boot manager. Creating new install medium to boot from.

---

### Post by oldfred on 2016-01-28
Boot-Repair is telling you what changes you need.
Boot Ubuntu live installer in UEFI mode and add Boot-Repair. Your link shows you booted in BIOS boot mode.

UEFI & BIOS are not compatible, once you start booting in one mode, you cannot change. Or from grub menu booted in BIOS mode, you cannot load Windows in UEFI mode. You can dual boot only from UEFI boot menu. And some  systems may require you to turn on/off UEFI/CSM mode to match install.

You now have a copy of grub in the gpt's drive protective MBR. That is only for BIOS boot. You need to use Boot-Repair and reinstall grub-efi-amd64 as Boot-Repair suggests. You need to make sure Internet is also working for Boot-Repair to do its updates. Often better to use hard wired Ethernet for installs & major updates.

So always boot your system in UEFI mode, both flash drives & internal hard drive. Also grub will only let you boot Windows from grub menu in UEFI mode if secure boot is off. If you want it on then boot from one time boot key often f10 or f12, check your manual for correct key.

---

### Post by evanfmanuella on 2016-01-28
oldfred : Thanks! Solved.

---

