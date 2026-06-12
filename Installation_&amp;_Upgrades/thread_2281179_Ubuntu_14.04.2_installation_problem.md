---
title: "Ubuntu 14.04.2 installation problem"
date: 2015-06-05
forum: Installation &amp; Upgrades
---

### Post by wyatt5 on 2015-06-05
I recently downloaded and burned a copy of Ubuntu 14.04.2 and tried to install it on my system.  Installation runs and finishes without error, but when I try to load it up again without the disk, as the message after installation states, my computer doesn't recognize or boot to Ubuntu, but all the files seem to be in order...  Is this a common problem, or is it just my BIOS?

---

### Post by Bucky Ball on 2015-06-05
Welcome. More information please. Are you dual-booting with Windows? Did you install in UEFI or legacy mode? Have you got the install media out of the machine on restart after install and the BIOS set to boot from the hard drive, not the install media?

---

### Post by wyatt5 on 2015-06-05
Thank you, but no, I'm only running Ubuntu and I believe through UEFI, but I'm not entirely sure how to check...  But, I did take the install media out and set to boot from hard drive, but it didn't seem to change anything.

---

### Post by Bucky Ball on 2015-06-05
What does the computer do exactly when you boot? Black or blank screen, error message(s)? Do you get to a list of available kernels to boot? If not, try hitting shift (or it may be escape now) just after the manufacturer's splash screen. Do you get that list now? Did you 'Try Ubuntu' from the install media prior to installing and all went well?

---

### Post by wyatt5 on 2015-06-05
I tried Ubuntu before, and it did work well.  When I boot, it just comes up with the splash screen and everything, but I get an error message saying that there isn't any bootable media.  I can check the hard drive after installing and all the files are seemingly in place, rebooting gives me no luck.

---

### Post by Bucky Ball on 2015-06-05
I suggest you try [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair"). Apparently that deals with EFI pretty well now. Please note the address of the bootinfo boot repair creates and post a link here, please. 

When you installed, did you have fast start (called something like that) disabled in the BIOS? Boot to the BIOS and have a look around to see whether you have installed in UEFI. BIOSs vary so I can't tell you exactly where to look, but it should be there somewhere (legacy mode would be disabled and EFI or GPT or something like that would be enabled.

If you boot from the install media can you 'Try Ubuntu' without issue?

---

### Post by sudodus on 2015-06-06
> **wyatt5 said:**
> Thank you, but no, I'm only running Ubuntu and I believe through UEFI, but I'm not entirely sure how to check...  But, I did take the install media out and set to boot from hard drive, but it didn't seem to change anything.

If you are only running Ubuntu and in UEFI mode, and you do not intend to install Windows 8 or later, then I suggest that you try to switch to BIOS mode, often called CSM in the BIOS/UEFI menu. That will make it easier to install Ubuntu.

What partition table and file system are there on your hard disk drive? That and many other things will be shown in the bootinfo report, that Bucky Ball asked for in post #6.

---

