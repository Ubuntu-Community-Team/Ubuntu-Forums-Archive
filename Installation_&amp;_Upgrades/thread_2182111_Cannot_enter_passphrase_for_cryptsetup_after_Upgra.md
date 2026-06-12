---
title: "Cannot enter passphrase for cryptsetup after Upgrade to 13.10"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by neelson2 on 2013-10-20
After upgrading from 13.04 to 13.10 i cannot enter my password into the cryptsetup preboot prompt. It says "Enter passphrase:" but i cannot type anything in it although my keyboard works. After forcefully restarting i can choose in Grub "advanced options" and choose kernel 3.8.0-31 instead of 3.11.0-12 and then everything is fine. Could it be that the new kernel doesn't load the usb drivers? What can i do?

---

### Post by xiccarph on 2013-10-20
Hello.
I just upgraded and did not have any problem entering my password.  This was on my Dell Laptop which has always used a plain text version for the entry of the cryptsetup password.
On another machine which successfully uses the Plymouth graphical boot animation/logger, I would sometimes not see the password field for this entry.
I found if I pressed ESC so that I would be returned to the terminal with the boot output, I would have the opportunity to enter it.
I also found that on occassion I could type the password, carefully, when I saw no prompt or output, and the boot process would continue ok.
I also, for a period, had a very long wait time while the boot process insisted on running a full fsck on a btrfs partition on RAID which was very large.  It was a known bug, but the problem went away in 13.04.  Is it possible, especially if you have forced a restart or two, that your system is running a RAID rebuild or fsck?
Hope this helps.

---

### Post by neelson2 on 2013-10-21
Thanks for your information, but i have no RAID installed, just a plain ssd and i see the password field. It's just that can't type anything. Because it works with an older kernel i assume that the new kernel is somehow incorecctly configured and that some usb driver for the keyboard isn't loaded early enough. I found [https://bugs.archlinux.org/task/17700](https://bugs.archlinux.org/task/17700) where they suggest in archlinux to "hook sbinput in mkinitcpio.conf", but i don't know what that means or how to do it. Is there maybe a way to reset kernel or driver configurations?

Edit: I am glad i am not the only one. This problem is recognized in 
[URL="https://bugs.launchpad.net/bugs/229732"]https://bugs.launchpad.net/bugs/229732
[/URL]

---

### Post by xiccarph on 2013-10-23
Ok.
Sorry I wasn't of more help.
I did notice from the bug report that it implies there is a problem with the boot sequence and I wouldn't think an encrypted disk should qualify as a problem.
Can you plug in a ps2 keyboard?  They are recognized by the kernel throughout boot and I have had to do something similar in the past to get past a usb keyboard not being recognized.

If you can't use a ps2 keyboard I might try something more complicated as a temporary fix.
If you boot to a Live Ubuntu USB and added a keyfile to the encrypted disk, you could store the keyfile (temporarily as long as you aren't worried about physical security) on the boot partition.  Once you updated the /etc/crypttab to look for the keyfile the disk should be decrypted without keyboard input.  This isn't really a good solution, but if I couldn't get in any other way I might try it.  You would want to use a key that doesn't have a passphrase.
Do a man or search for instructions in using cryptsetup and crypttab, most instructions are pretty clear, and I'm happy to advise to the best of my ability if you have questions.

---

### Post by robb-txstate on 2013-10-23
If it helps to know, I do have exactly the same problem.

EDIT: Based on xiccarph's tip, I dug out a vintage PS/2 keyboard to replace the USB keyboard. Now I can enter the passphrase on boot.
Cheers.

---

