---
title: "[SOLVED] Installing Ubuntu (MATE) 15.10 on &quot;UEFI-only&quot; Windows 8.1 laptop"
date: 2016-02-07
forum: Installation &amp; Upgrades
---

### Post by paulvbrown on 2016-02-07
Hi all. Debated long about what to call this.

I have here an "Acer Aspire E 15 Start" or "ES1-512-22KW", depending on which of those (if either) is the more relevant way of explaining what laptop I have. It currently has Win 8.1 500G hard drive in it.

_**What we want**_
WANT to install Ubuntu MATE 15.10 on here.  Don't care if Windows 8.1 dies a terrible death in the process.

**_shut out of bios settings_**
It is a customer's laptop, has an InsydeH20 "bios" with an **unknown** supervisor password, but a **known** user password.  The set boot mode is UEFI, with Secure Boot ENABLED.  As the customer doesn't know the supervisor bios password, the only thing to be done in the bios at this point is to change the date and time -- no access to anything else.

_**Latest attempt**_
Most recently I got UbuntuMATE 15.10 on a USB-stick, and installed it alongside Windows 8.1, seemingly successfully, but on reboot, the laptop just boots into Windows.

Then I tried booting into 15.10 as a live session, installed Boot-Repair, and ran the suggested repair.  The record of that is here: [http://paste.ubuntu.com/14958724/](http://paste.ubuntu.com/14958724/)

**_Other things that may be helpful to know_**
When we first started with this laptop we were intent on trying to get the bios reset somehow, in order to gain access to settings.  I *believe* we actually updated to a new version, but this did not clear the supervisor pw. Have also used some "backdoor" trick to get a code to input as the password, but that didn't work, either. I would *swear* that at some point the SecureBoot was actually NOT set, but then I don't understand how we could have activated it since we have at no point been able to get supervisor access to the bios.

ANY help greatly appreciated.  I'll continue to scour other threads for similar problems, and please point me in the right direction if you know of a pre-existing solution.  Just not sure what to even search for.

---

### Post by sudodus on 2016-02-07
A workaround might be to boot from USB and via that system get into an installed system. I have made a system, that uses the Ubuntu iso files boot system to boot both a live system and an installed system. In my case the installed system is in the USB pendrive. There is a USB 3 port in the computer (according to a review I found via the internet, so you could run a fast USB 3 pendrive or an SSD connected via USB 3 (and an external box).

Another alternative is to make your own system similar to my system, but with the installed system in the internal drive. This should not be too hard for you; replace the installed Ubuntu by Ubuntu MATE! I can try to help you by answering questions ...

Download a compressed image file, flash it into a USB pendrive and try it :-) See these links

[Portable installed system that boots in UEFI as well as in BIOS mode](http://ubuntuforums.org/showthread.php?t=2213631)

A pendrive with a live **and** an installed system, that works in UEFI and BIOS mode:

[A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode]("http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506") and

[Compressed image file with a live Ubuntu 14.04.2 and an installed Ubuntu 15.10](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13426191#post13426191)

---

### Post by grahammechanical on 2016-02-07
Can you not do this as suggested by boot repair?

> If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi


Grub has detected the Windows OS. So, if you can get Grub loading you should get options for both Windows & Ubuntu Mate

> Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.2.0-27-generic
Found initrd image: /boot/initrd.img-4.2.0-27-generic
Found linux image: /boot/vmlinuz-4.2.0-16-generic
Found initrd image: /boot/initrd.img-4.2.0-16-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi

Regards.

---

### Post by paulvbrown on 2016-02-07
> **grahammechanical said:**
> Can you not do this as suggested by boot repair?


Hey Grahammechanical -- yeah, I actually tried that as well -- "bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi"

I *presume* that {bootmgr} should be replaced in this command with "the boot manager", but should it?  And what would that be??  Something like "/dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi"?

Have to admit I just "played it dumb" here and forged ahead using the curly brackets and "bootmgr" and when the command didn't throw any errors, I thought maybe it's just supposed to be put in just like that, verbatim.

---

### Post by paulvbrown on 2016-02-07
Alright, solved.

Went looking for that bcdedit command and came to the following site:

[http://sattia.blogspot.fi/2014/12/2-ways-to-fix-uefi-bootloader-when-dual.html](http://sattia.blogspot.fi/2014/12/2-ways-to-fix-uefi-bootloader-when-dual.html)

Tried the other option where we use grubx64.efi instead of shimx64.efi:

```
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
```

It worked! BTW, to be clear, yes, "{bootmgr}" verbatim, also "path" verbatim -- no substituting of different strings needed anywhere, just the command as you see it here.

THANKS to all!  Now if I can get rid of the Windows partition I'll be even happier!

---

