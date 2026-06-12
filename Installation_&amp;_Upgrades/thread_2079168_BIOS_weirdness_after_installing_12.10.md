---
title: "BIOS weirdness after installing 12.10"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by Sorvin on 2012-11-01
Hi.
This is a bit of a weird story. I bought a laptop (Fujitsu AH532), and it comes with no OS pre-installed. So, I started off with trying Windows 7 on it. Installed fine, and then I decided to inspect the BIOS, nothing seemed out of the ordinary.
Removed Windows 7, installed Ubuntu instead (dd if=/dev/zero of=/dev/sda bs=1M count=1 before I started the Ubuntu installation). Once Ubuntu installed (detecting all my hardware perfectly btw, unlike Windows 7. w00t), suddenly I can't enter the BIOS anymore. F2 responds with "Please wait" but goes to grub. Moreover, F12 (boot menu), suddenly doesn't show any real devices. All it shows is an "applications"(?) menu, with
1. ubuntu
showing, and that's it.
Now before you scream at me that I'm being a silly person because BIOS is unrelated to the OS on the disk - I know it already.
It theoretically can be simply a coincidence, but to make things weirder:
I removed the HDD, all removable media, and rebooted, and I *still* see the same boot menu, with:
1. ubuntu
When I try to load it, it of course fails, but still, I found it exceedingly weird to see ubuntu listed in my BIOS F12 menu, with my HHD removed.
What am I missing here?
Assumption 1 - Weird Phoenix BIOS keeps something on the disk itself??
Assumption 2 - Ubuntu installation mocked about with the BIOS (stupid, I know, I'm just at a loss)

Btw, any attempt to boot from removable media and flash the BIOS with the images from Fujitsu's site have failed. It only boots from the HDD, or nothing at all..

Cheers!

---

### Post by Sorvin on 2012-11-01
OK, this was definitely a BIOS issue. I shorted the BIOS on the motherboard and suddenly I have my original boot menu again.
I still can't enter the BIOS itself, but at least now I can boot from other devices and flash the BIOS.
After it's back to its original form (hopefully), I will install Ubuntu again to see if it is indeed Ubuntu that's causing this.

Still, if anyone knows something I don't regarding Ubuntu messing with BIOS stuff, I'd be happy to know.

Thanks.

---

### Post by oldfred on 2012-11-01
The new replacement for BIOS is UEFI. And UEFI often shows and entry of ubuntu as the boot device so do you have UEFI not BIOS?

With both Ubuntu & Windows you can install to new UEFI systems in UEFI or BIOS mode and mixing them causes problems.

Windows only installs in gpt partitioned drives if UEFI. Ubuntu will boot from gpt partitioned drives with either BIOS (needs bios_grub partition) or UEFI (needs efi partition).

Ubuntu would not mess with BIOS, but I suspect you have UEFI??

---

### Post by Sorvin on 2012-11-01
Hi, thanks for your reply.
The BIOS is a Phoenix SecureCore Tiano, which is indeed listed as a UEFI BIOS, but still, after installing Ubuntu, I can't even see the BIOS anymore. F2 doesn't work.
So what you're saying explains the Boot list menu, but it doesn't explain why I can't enter the BIOS settings anymore..

---

### Post by oldfred on 2012-11-01
Some have reported similar issues when changing thing around a lot. Most found total cold boot, power down then works.
If a laptop you may have to remove battery for a bit.

---

### Post by Sorvin on 2012-11-04
Well, I managed to re-install the BIOS now.
But Ubuntu definitely changed something in the BIOS itself (UEFI or whatever), since even without a disk present it still said Ubuntu on the boot menu.
Quite weird.

---

### Post by grahammechanical on 2012-11-04
My guess is that this is something to do with 'secure boot.' Which, when you think about it, must require an operating system that is being installed to do something to the BIOS memory chip and not just put files onto a hard disk. Otherwise secure boot could be over come by formatting or replacing a hard disk.

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/]("http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/")

> For now, we have a technical solution in 12.10 that solves the parts of the problem that we can solve.

The first-stage UEFI bootloader on 12.10 install media is a build of Matthew Garrett's shim code, embedding a Canonical UEFI CA and signed by Microsoft. This is pretty much the same as the Fedora solution, just with a different key and a binary built on the Ubuntu build infrastructure rather than Fedora's. If Secure Boot is not enabled, the second-stage bootloader is booted without applying any checks. If Secure Boot is enabled, the signature is checked on the second stage before passing control, as expected.

The second-stage bootloader is GRUB 2.

I would guess that in 12.10 the first stage UEFI bootloader with a key signed by Microsoft is being put into part of the BIOS memory chip and that is where the word Ubuntu is being generated. No hard disk needed unless you wanted the boot to proceed, then you would need a certified Ubuntu kernel image to be accessible.

As regards not being able to access the BIOS setup, could this also be a function of secure boot? What good would secure boot be if anyone could access the BIOS set up program and disable secure boot. Yes, it should be possible for the user to disable secure boot. That is part of the specification but there must be a secure way of doing it and a way of preventing unauthorised disabling of secure boot. It makes sense. What does the motherboard user guide say about all of this?

Regards.

---

### Post by oldfred on 2012-11-04
Only new computers with Windows 8 have the new secure boot, so unless a very new computer it should just be UEFI/BIOS. 

UEFI retains either in its memory or the FAT32 efi partition the boot files and if one is ubuntu then it would still show it. Somewhat like still having grub in the MBR after deleting the Ubuntu partition.

---

### Post by Beeresh on 2013-02-20
I too have similar BIOS issue, where I install ubuntu 12.04 LTS and bios is missing (F2 do not work). BIOS is a Phoenix SecureCore Tiano and laptop model is Lenovo G580. I would like to know how to reinstall BIOS.

---

### Post by timschumi on 2024-04-19
I've recently looked into fixing this issue, and came up with a consistent way of restoring the laptop to full operation.

The boot menu entries can be partially restored by bridging the "CL1_CL2" test point  that is located under or next to the RAM slots.
It may be required to have the laptop powered (or even powered on) while bridging the contacts for the test points to have any effect.
This brings back the  device-based boot menu entries, but does not yet restore access to the  BIOS Setup menu.
For that, a USB stick with [Fujitsu's BIOS update tool]("https://support.ts.fujitsu.com/")  (search by serial number to make sure you find the correct hardware revision) needs to be prepared, booted from, and run.
This restores most BIOS  settings to their default, including the missing BIOS Setup menu.

Alternatively, if the currently installed Linux system is still  bootable, one can use [this tool]("https://github.com/timschumi/ah532-biostools") to restore all entries  without having to go through a BIOS update and reset.
This works by manually  rewriting all broken EFI variables with their expected content.
Please do make note of the list of supported configurations and of the  disclaimer (and let me know in case the tool does or doesn't work on  some previously untested configuration).
In case you want to know more about this works, there is a [post explaining the underlying details]("https://blog.timschumi.net/2024/01/20/ah532-bios-investigation.html").

Lastly, a [workaround for the issue]("https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=f45812cc23fb74bef62d4eb8a69fe7218f4b9f2a") has been merged into the Linux  kernel, which should keep this from occurring on any new  installations.
This patch already ended up in the current installation  media for the Ubuntu 24.04 beta (which I have confirmed to be not affected), and it will presumably be included in  all installation media going forward.

---

