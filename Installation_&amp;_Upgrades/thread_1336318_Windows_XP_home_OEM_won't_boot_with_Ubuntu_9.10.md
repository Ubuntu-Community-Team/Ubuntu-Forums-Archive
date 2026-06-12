---
title: "Windows XP home OEM won't boot with Ubuntu 9.10"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by ShinjiML on 2009-11-24
Hi,

I just recently tried Ubuntu 9.10 and instantly fell in love with Ubuntu and wouldn't mind using it as my sole OS, if it weren't for some of the Adobe and Apple programs that I needed. So, I tried to dual boot Win XP home OEM with Ubuntu 9.10, but have had no success after trying a number of combinations.

1st attempt: Installed Win XP OEM first, then installed Ubuntu 9.10, WITHOUT installing GRUB, I had wanted to modify windows boot loader to include Ubuntu. I thought this might be a less complicated option and might be less prone to problems. Upon rebooting, Win XP began to boot, disk check utility came up, ran without a problem, but upon finishing, gave me a blue screen for a split second before rebooting. After rebooting, I was left with options for "continue normally, safe mode, etc." None of the options worked, as they all resulted in a blue screen and reboot. Ubuntu booted normally, however.

2nd attempt: I deleted the previous Ubuntu 9.10 partition and installed a fresh Ubuntu 9.10 into that partition, this time WITH GRUB. After rebooting, GRUB loaded normally, Windows XP showed up on the list. I selected it, and Win XP began to boot, but after the logo disappeared, I got another blue screen and a reboot. Ubuntu booted normally...

3rd attempt: This time, I deleted my Win XP partition and the previous Ubuntu 9.10 partition (from 2nd attempt) and installed Ubuntu 9.10 onto the entire Harddrive, resized a partition for Win XP and installed Win XP. Upon rebooting, Windows boot loader never showed up and windows XP wouldn't boot past the logo before I got yet another blue screen. Ubuntu was again able to boot normally...

4th attempt: I deleted all partitions from my HD, reinstalled win XP fresh, which booted normally, then installed Ubuntu 9.10 on a / partition. Upon rebooting Win XP was selectable from GRUB, but won't boot past the logo before a flash of blue screen and auto reboot. Ubuntu 9.10 is still able to boot normally.

I really don't want to do a Wubi install >.>

Thanks in advance for any help offered!

---

### Post by dragos_iliescu_2005 on 2009-11-24
You need to know that:
- it is recommanded that W XP to be installed first and Ubuntu second;
- W XP follow general installation method, but for ubuntu think first about how you will partition the hard disk(s) - make a plan;
- think about RAM size, if less than 1G, then make one partition as SWAP;
- use the 'manual' installation for linux as recommanded

---

### Post by phillw on 2009-11-24
Try putting XP back in control by restoring it's MBR and seeing if it is stable. Running that way will leave your ubuntu area safe and sound, unless you re-format your entire disk !!

Once you have Win running happily, pop grub back in charge & you should be good to go.

The instructions for those steps are here -->  [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Regards,

Phill.

---

### Post by darkod on 2009-11-24
In your 4th attempt, when you installed XP clean did you install on small partition or on the whole drive and then resized the partition to make space for Ubuntu? Windows and especially XP can be very sensitive to shrinking its partition.

If you haven't already, try to install XP on the first primary partition, and the partition size to be just what you need for XP. Leave the rest of the drive unpartitioned.

Then check few times if XP is working normally and after that install Ubuntu in the free unpartitioned space and see how it goes.

---

### Post by presence1960 on 2009-11-24
Let's not speculate as far as your setup & boot process is concerned, do this:

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

