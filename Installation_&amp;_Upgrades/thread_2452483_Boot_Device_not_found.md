---
title: "Boot Device not found"
date: 2020-10-23
forum: Installation &amp; Upgrades
---

### Post by asearle on 2020-10-23
Hallo everyone,

I am installing Lubuntu 20.04.1 on a HP 4540s laptop and, after an apparently successful install (clean install on a newly-formatted disk), I see the following screen ...

BootDevice Not Found
Please install an operating system on your hard disk.
Hard Disk - (3F0)
F2 System Diagnostics
For more information, please visit: [www.hp.com](www.hp.com) ...

I have googled the issue and followed advice saying to set the boot to "Legacy" but that didn't help.

My suspicion is that I need to tweak grub in order to get it working(?)  The system is probably looking for Windows(?)

Can anyone out there point me to a good HOWTO explaining how to do this?

Or maybe you have a different suggest to fix the problem?

Yours,
Alan in Cologne

---

### Post by tea for one on 2020-10-23
HP can sometimes be a little unfriendly with alternative operating systems.

Anyway, a few questions:-

Did you install in UEFI mode?
You mentioned a [COLOR="#0000FF"]newly formatted disk[/COLOR], is this an additional disk?
Have you removed Windows?

Try a quick test, power off and press F9 (repeatedly) when powering on again.

Do you see the system set up boot menu?

---

### Post by yancek on 2020-10-23
Many HP computers allow you to access boot options by tapping the Esc key on boot then selecting the F9 key.  Are you able to do this?  Do you have only the one drive you refer to in the computer?  Did you have a previous OS installed (windows)?

I had the same error on my HP laptop after one month of use.  Turned out to be a hardware problem with the motherboard and it took 2 months to get a replacement.

---

### Post by GhX6GZMB on 2020-10-23
HP laptops normally use F10 to enter the BIOS.

For a clean install you need to select the "Format" option during disk partitioning (for all partitions), file system should be ext4.

When you say "newly formatted disk", I suspect NTFS.

---

### Post by asearle on 2020-10-24
Many thanks for getting back to me.  To answer your questions ...

I installed several times. The last install was with "Legacy" rather than UEFI (in BIOS).  Or is there an option in Linux during install to select UEFI?  Or should I install with UEFi set?

The disk was the same one which had been working with Windows.  The disk was formatted by the Lubuntu install (not separately by me)

Yes, we removed Windows.  Maybe that was a mistake:  Would it have worked better with "dual-boot"?

Many thanks for any tips that you can give.

Yours,
Alan

---

### Post by asearle on 2020-10-24
I have found the various options (ESC, F9, F10) to enter BIOS and to change the boot.  Indeed, it was no problem to get the unit to boot from a USB drive.  It just seems to have a problem booting from the hard disk.

Or maybe I should simply run Linux from an external USB-drive?  That wouldn't really be the solution but would get me going. 

Yours,
Alan

---

### Post by tea for one on 2020-10-24
How you boot your usb = how the OS is installed.
Boot in legacy = installed in legacy
Boot in UEFI = installed in UEFI

Suggestion:-
Enter into your UEFI set up
Disable all three - Legacy, Secure Boot and Fast Boot

Boot your USB in UEFI mode and install again.

If the PC fails to boot as your original post, you should be able to press F9 and boot the internal hard drive from the UEFI Boot manager (i.e. using F9)

By the way, if you want GPT, you can prepare the disk while in your live session before the installation procedure.
Ubuntu has [COLOR="#0000FF"]gparted[/COLOR],  I'm not sure which utility is included with Lubuntu.

I would recommend GPT.

---

### Post by yancek on 2020-10-24
When you access the boot options with the Esc/F9 key combination, do you see an option for Ubuntu?
You should be able to install and boot either with Legacy/MBR or with UEFI although UEFI is the better option.
If your last install was Legacy, I would concur with the post above to do it again in UEFI.  Before doing so, disable Legacy boot in the BIOS.
Did you turn off hibernation/fastboot on the computer?  If you see no option for ubuntu in the BIOS boot options, Grub was not properly installed.

Reading through the information at the official Ubuntu documentation below should give you some basic understanding of UEFI.  Some of it is very specific to Ubuntu but there are general principles which apply to any Linux.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by asearle on 2020-10-24
Dear Tea-for-one,

Yes, that was exactly it!

In BIOS I set it to UEFI (instead of legacy) and then booted using the UEFI option which was the last entry in the boot menu of my installation media (a live boot on a USB-stick).

I then selected an "Erase disk install" and everything ran through fine: The install setup set the correct options.

Many thanks,
Alan

---

### Post by tea for one on 2020-10-24
Splendid - Can you mark the thread as solved?

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

