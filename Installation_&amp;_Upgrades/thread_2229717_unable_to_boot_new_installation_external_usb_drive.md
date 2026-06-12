---
title: "unable to boot new installation external usb drive 14.04 or 13.04"
date: 2014-06-14
forum: Installation &amp; Upgrades
---

### Post by Al-Man on 2014-06-14
Hi I wonder if anyone can help me with this problem? I have all ready spent ages trying to solve it. My computer is a ASUS M50sv laptop which dual boots windows 7 and Ubuntu 12.04. I have been trying to install 14.04 to an external usb 500gig WD passport drive from a live bootable usb thumb drive. The install goes smoothly with the bootloader being installed to the external drive and 14.04 being installed to the first partition (ext4). There is also a swap partition on this drive. After the install has finshed and I reboot I am unable to boot the external drive by either booting it directly from the bios. This results in the grub rescue prompt with Error:file /grub/boot/i386-pc/normal.mod not found. If I try and boot from grub on my internal drive I get error: file not found load the kernel first. i have searched and searched and have not been able to find and solution to this. Any help with this would be greatly appreciated.

Many Thanks. Al-Man

---

### Post by yancek on 2014-06-14
You installed Grub to the master boot record of the external drive, correct?
When you select this drive from the BIOS setup, you get the error?
You ran sudo update-grub from the 12.04 on the internal with the external plugged in and when you try to boot, get the 'file not found'?
 This seems to be a fairly common problem based on a quick online search.  The link below has a suggestion which apparently worked.

[http://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found](http://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found)

---

### Post by oldfred on 2014-06-15
Did you only create / & swap on 500GB drive? 

Some systems seem to have issues with BIOS, USB and very large / (root) partition. Better to have either a smaller / at beginning of drive or a separate /boot. I suggest a 20 or 25GB / partition and use rest of drive as /home or a shared data partition.

---

### Post by Al-Man on 2014-06-17
Thank you for your reply yancek. I have set up a separate grub partition after following your link. Excellent. I am still no closer to booting the drive.

---

### Post by Al-Man on 2014-06-17
Thank you oldfred for your reply. I do have a swap partition on my internal drive. I will try your solution when I have some time. Flat Out at the moment

---

### Post by Al-Man on 2014-08-30
Thanks yancek & oldfred for your help. It was a BIOS, USB and very large / (root) partition problem. I shrunk my root partition to 125gb and now all is working ok. Please accept my apologies for the incredibly late reply.
Thanks Al-Man.

---

