---
title: "GRUB won't launch Ubuntu or recovery, goes to purple screen (windows 8 dual boot)"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by pennyknuckle on 2013-10-28
I'm currently attempting to install Ubuntu 12.04.3 on my MSI GE40 20C-009US Laptop (i7-4702MQ, Nvidia GTX 760M, 8 GB RAM, Windows 8.1). GRUB launches while in UEFI mode and boots into Windows fine, but if I attempt to run Ubuntu I am greeted by a frozen purple screen. Running Ubuntu recovery has the same effect, except with a black screen. I've tried nomodeset as suggested in numerous previous posts, the Boot-Repair utility, and every other fix I could find on this forum and the web at large (including a non-graphical boot). None of these seem to make any difference. I first installed Ubuntu in Legacy BIOS mode, and when it was installed like that I could boot into Ubuntu with the Legacy BIOS selected, and windows with UEFI. I then used Boot Repair to make it boot in UEFI. Now that GRUB comes up in UEFI, I can only boot windows and windows recovery, but neither of the Ubuntu options. 

I'm hoping there's a fix or workaround to this, and its not just a problem of incompatibility of my graphics card with Ubuntu. 

Here are the pastes of the boots I've tried, all of which have the same problem:
paste.ubuntu.com/6316251
paste.ubuntu.com/6316407
paste.ubuntu.com/6316435
paste.ubuntu.com/6316466
 


Thanks!

---

### Post by oldfred on 2013-10-28
With nVidia the nomodeset works, but do you have dual video and it is booting with Intel video?
That requires different boot options for the newest intel chips.

Users have posted these & I have reposted and users have said they work for Intel, but I do not know which works for which model.
 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

   Some other Intel boot options
acpi_osi=Linux  acpi_backlight=vendor

---

### Post by pennyknuckle on 2013-10-28
Thanks for the quick response. I do have dual video, and I would assume you are correct about it booting with the Intel HD instead of the Nvidia card. However, I attempted all of the changes to boot parameters you suggested, and nothing seemed to change the system's behaviour. I entered all of them as both boot parameters (next to quiet splash and nomodeset) and options on separate lines, to no success.

---

### Post by oldfred on 2013-10-28
If you remove quiet splash and use one of the boot settings do you see it starting to boot? Often last line is not issue, but a few lines up may be. Then whatever that is may need other boot settings in addition to video.

This should be a basic video mode.
        xforcevesa or nouveau.modeset=0

Is your UEFI/BIOS to most current from vendor. 
I might also see if vendor has similar issues?

Some with very new systems also found 13.10 worked better. It does have some updates in kernel & from Intel.

Older issue:

 MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)

---

### Post by pennyknuckle on 2013-10-28
The UEFI is the most current one available. I tried xforcevesa and noueveau.modeset=0 both in the boot line and several lines up. It does the exact same thing if I remove quiet splash, so I figure the problem must be above the boot line.

---

### Post by oldfred on 2013-10-28
You can only enter the boot options as replacing quiet splash or right next to them with space & no comma.
Any other place in boot stanza will corrupt it and it will not work.

---

### Post by pennyknuckle on 2013-10-28
Ok. I've tried every argument that way still with no success. I also tried all of the same possibilities in recovery mode, but it will flash two lines then go to a black screen.

---

### Post by oldfred on 2013-10-28
Are you booting from UEFI in BIOS/CSM mode or UEFI. You do have grub installed to MBR left over from early attemp, but Boot-Repair or a reinstall converted it to UEFI.

---

### Post by pennyknuckle on 2013-10-28
I'm booting from UEFI. If I boot in UEFI w/ CSM, the same thing happens, but if I boot in Legacy moot, GRUB won't load and instead displays an error "Invalid arch independent ELF magic", and then gives me a grub rescue terminal.

---

### Post by oldfred on 2013-10-28
That error would be correct as your install is now configured for UEFI boot, so booting with CSM/BIOS should give an error.

Were you able to boot into live installer and run it in live mode. I thought that was the VESA mode, but is some very low level video mode.

---

### Post by pennyknuckle on 2013-10-29
I can run it in live mode through a disk, that works fine. And I'm pretty sure the install isn't corrupted or anything, because before I set GRUB to boot from UEFI, linux booted fine in legacy mode.

---

### Post by oldfred on 2013-10-29
Can you in BIOS change to nVidia or is it automatic how it switches? Then nomodeset should work.

---

### Post by pennyknuckle on 2013-10-29
There's no visible option in the UEFI to determine which graphics processor it uses, unfortunately.

---

### Post by oldfred on 2013-10-29
I have only seen one or two systems where users could not install Linux in UEFI mode. A few have never reported back it it worked or not, but most have made it work.

Some were only able to install Ubuntu in BIOS mode with older versions of Ubuntu as UEFI, kernel & drivers were not up to date for the very newest hardware. They then could only dual boot from UEFI menu or one time boot key as UEFI and BIOS are not compatible. Once you start booting in one mode you cannot switch so if both are not in same mode, you cannot use grub menu.

---

### Post by pennyknuckle on 2013-10-29
I'm realising that when I said it booted from the live disk I should have specified that it booted from the live disk only in Legacy mode. In UEFI mode, the live disk shows the text menu, but selecting any of the options just results in a black screen. Could this be indicative of something?

---

### Post by oldfred on 2013-10-29
It is the same issue. If nomodeset or any of the Intel video settings did not work on live installer then it is the same issue. Something with UEFI and video.

UEFI works totally differently than BIOS, so software has to work with the difference.

---

### Post by pennyknuckle on 2013-10-29
So is there any hope of a fix, or do I just have to try Ubuntu 13, and if that doesn't work give up?

---

### Post by oldfred on 2013-10-29
Try 13.10 as a lot of changes were made including many by Intel to make it work with newer Intel systems.

---

