---
title: "Toshiba T110  - dvd hangs on install"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by lonewolf88 on 2010-12-12
Toshiba T110 laptop, Win 7 Pro.

Runs Suse ok alongside Win 7, boots up with GRUB.

Deleted the Suse partition, reformatted to NTFS, and changed the MBR so that now boots to Win 7.

Tried to install 10.10 from the cover of Linux Format magazine.

Booted from cd, selected the variant; hangs almost immeditely with atext screen of single line messages;  the last of which reads as follows:-

[   0.172736] [<c 010363e7] kernel_thread_helper +0x6/0n0

At this stage keyboard etc. completely unresponsive; to close down I must turn off laptop.

Tried same procedure in Dell mini notebook, installed ok, except for screen bleed issues (I have read that Ubuntu doesn't support that particular Dell model, so I am not concerned with this.)

As stated above, both Win7 & Suse happily lived alongside each other previously;  what do I need to do to get Ubuntu installed?

---

### Post by lonewolf88 on 2010-12-18
> **lonewolf88 said:**
> Toshiba T110 laptop, Win 7 Pro.

Runs Suse ok alongside Win 7, boots up with GRUB.

Deleted the Suse partition, reformatted to NTFS, and changed the MBR so that now boots to Win 7.

Tried to install 10.10 from the cover of Linux Format magazine.

Booted from cd, selected the variant; hangs almost immeditely with atext screen of single line messages;  the last of which reads as follows:-

[   0.172736] [<c 010363e7] kernel_thread_helper +0x6/0n0

At this stage keyboard etc. completely unresponsive; to close down I must turn off laptop.

Tried same procedure in Dell mini notebook, installed ok, except for screen bleed issues (I have read that Ubuntu doesn't support that particular Dell model, so I am not concerned with this.)

As stated above, both Win7 & Suse happily lived alongside each other previously;  what do I need to do to get Ubuntu installed?

Err.... Anyone?

---

### Post by lonewolf88 on 2010-12-26
> **lonewolf88 said:**
> Err.... Anyone?

Sigh ...looks like Ubuntu not ready for big time yet - back to Windows.

At least it works!

(Not trolling, just stating a fact!)

---

### Post by Vulcaneer on 2010-12-29
I have a Toshiba T110 (Celeron 743) with exactly the same problem. Attempting to boot Fedora 14 from live CD also brings up the same error. There seems to be a number of Toshiba laptop owners reporting broadly similar faults and citing ACPI or BIOS related issues. That would seem to make some sense as the other distros I tried (Mandriva 2010.1 and Opensuse 11.3) left me without battery data or any ACPI key functions. 

I'm still crawling over other posts for a fix. Till then I'm stuck with Win7...

---

### Post by Vulcaneer on 2011-01-29
Finally had some success booting linux on a Satellite T110 - in the form of Opensuse 11.4 milestone 6, which has the 2.6.37 kernel. Judging by other posts in ubuntuforums and the info on the page below it looks as though a number of Toshiba laptops may continue being hard to get Ubuntu running on until we see 11.04.  

DSDT corruption workaround on all Toshiba Satellite - 
[https://patchwork.kernel.org/patch/217842/](https://patchwork.kernel.org/patch/217842/)

Having said that, if anyone can point me in the direction of a method to get Maverick running on a T110 I'd be hugely grateful.

---

### Post by davide123 on 2011-02-11
Try passing "acpi=off" from the bootloader. Worked for me.

---

### Post by lonewolf88 on 2011-02-11
Thanks, in the meanwhile managed to get Suse 11.3 working, but having issues with wireless and sound cards at present.

Had to allow multiple versions of the kernel - latest release update was fritzing the installation.

---

### Post by Vulcaneer on 2011-03-23
davide123's 'ACPI=off' trick worked for me. I got Ubuntu 10.10 installed and updated to a later kernel so I'm very grateful for the tip. Haven't yet got as far as controlling screen brightness using the hotkeys yet (I'm having to resort to running ugly scripts at login to drop screen brightness to 80 per cent) but the basics - including sound, headphones and wireless - are all working fine. What a relief to get shot of the 2 minute Windows 7 boot time and all that Toshiba bloatware...:D

---

### Post by Vulcaneer on 2011-04-02
... and then I ran into more ACPI related problems, including the fan not working. As much as it pains me to do so, I've had to go back to Windows 7. Ubuntu maverick is excellent but it can't run properly on a Toshiba T110 without major additional work and I'm not skilled enough to work round whatever DSDT / ACPI issues are causing the problem.

---

### Post by ejtauri on 2011-04-06
I have a Toshiba Satellite A665D and was trying to install Ubuntu 10.10 from an iso I burned.  It just hangs on boot with black screen and underline cursor blinking.

How would I go about passing the boot parameter (acpi=off) on a clean install from CD?

Thanks.

---

### Post by p_code on 2013-03-11
> **ejtauri said:**
> I have a Toshiba Satellite A665D and was trying to install Ubuntu 10.10 from an iso I burned.  It just hangs on boot with black screen and underline cursor blinking.

How would I go about passing the boot parameter (acpi=off) on a clean install from CD?

Thanks.

You can find the information you need in this thread --

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

For my laptop, the magic settings were nolapic, and nomodeset, but the same menu is also used to disable acpi=

Note the warning however, that on at least some laptops, disabling acpi messes up the thermal management by killing the fan control.

Also I am not sure if you go ahead and do the install after using the above cheat codes to boot, if the installer is then smart enough to incorporate those settings into your permanent grub boot settings (knowing Ubuntu, probably NOT).

So scan down through the thread and note how to PERMANENTLY change your grub settings.

This is a royal pain because after the install you will probably also have to do a little finger dance and interrupt your first hard drive grub boot, to supply the same boot options to grub manually (this uses a totally different sequence than with the live CD boot options, check the online Grub2 documentation)

Without this, Ubuntu will probably crash, just as it does when booting the live CD without the codes - and if it doesn't crash outright, there may still be lingering issues that could lead to things like the corrupted files you are seeing - so if you find a boot option that cleans up your live CD session, I would definitely take the time to add the same boot options via grub (even if the system boots without them) just to avoid long term problems.

The good news is that, once you manually supply the cheat code boot options manually the first time, you can edit the grub configuration text file, and then run grub to write the changes permanently to your boot loader, and then Ubuntu should startup and run seamlessly after that. :rolleyes:

---

