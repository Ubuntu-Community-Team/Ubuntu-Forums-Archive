---
title: "Using boot repair to try to fix boot problems"
date: 2022-01-28
forum: Installation &amp; Upgrades
---

### Post by bobdc2 on 2022-01-28
Running Ubuntu 20.4.3 on a Lenovo Ideapad 5 laptop, I was getting bootup messages like these:

   error: /boot/vmlinuz-5.11.0-46-generic has invalid signature.
   error: you need to load the kernel first"

I then booted from a thumb drive and tried to follow the directions on [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). I got ahead of myself and clicked "Recommended repair" before I clicked "Create a Bootinfo summary" and that led to a message box that said  "grub-efi purge cancelled." 

Then I found that I should have created a Bootinfo summary first, so I did and it's at [https://paste.ubuntu.com/p/5Wrj4vVnj4/](https://paste.ubuntu.com/p/5Wrj4vVnj4/) . Can anyone suggest something I might try based on that BootInfo summary?

Thanks,

Bob

---

### Post by oldfred on 2022-01-28
Signature is normally related to having UEFI Secure Boot on.
But Boot-Repair says Secure boot is off. Is that correct?

Separately you show UEFI entries for Windows & Linpus Lite.
You can delete those UEFI entries with efibootmgr.

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B

Since only one install grub will not normally show menu.
Can you press escape right after Lenovo logo but before grub menu would show and get grub menu.
But you may have made that impossible by changing grub to 0 in nvme0n1p2/etc/default/grub, I use 3, just so I have time to get a grub menu if I have issues, so I can try to boot recovery mode.

---

### Post by bobdc2 on 2022-01-28
I appreciate your quick response. You're right about the signature; the error messages shown were what started me on this journey of trying to straighten this out, and along the way (before I created the BootInfo summary) I turned Secure boot off because some searches showed that that seemed related to similar boot problems. 


Long story short, via the grub menu I eventually got to the  (initfamfs) prompt, fsck showed me where the problem was and then helped me fix it. (For now!)

---

### Post by MAFoElffen on 2022-01-28
So this is "Solved" now?

---

### Post by bobdc2 on 2022-01-29
To summarize, I was able to boot into the Ubuntu GUI, but only through a convoluted series of steps, and after it ran for a bit it told me that the whole disk is a read-only file system. Even a redirect of an echo command to a file wouldn't work. I ran through the steps again and it's been working properly for about two hours, but I'm backing up a lot and waiting for this read-only problem to happen again. 


More detail:


If I just turn the computer on, first I get a grub menu with Ubuntu as the first choice (which doesn't work), Advanced Options for Ubuntu,  Firmware. Advanced Options gives me  four pairs of of choices, each pair having "Ubuntu, with Linux 5.11.0.**-generic" (with ** being 38, 43, 44, and 46) with and without "(recovery mode)". 


Picking the first one, without "(recovery mode)", gives me "Loading Linux 5.11.0.46-generic, Loading initial ramdisk..." and it seems to just be frozen there. If I pick an older one I eventually get to a (initramfs) prompt with a lot more messages along the way, including fsck output that /dev/nvmd0n1p2 contains a file system with errors. I ran fsck /dev/nvmd0n1p2 and after that I seemed to be able to boot OK yesterday, but today the same thing happened: couldn't boot up normally, booted in recovery mode, got an error message about /dev/nvmd0n1p2, run fsck again on it, then went into recovery mode with 43-generic or 44-generic and got to the Ubuntu GUI as if everything was fine. Half an hour it looked fine but wouldn't let me or any program write to any part of the disk anymore. I went through the whole process again and the Ubuntu GUI has been running fine for 2  hours. I'm backing up everything I do a lot because I'm bracing myself for this to happen again. 

Thanks,

Bob

---

### Post by MAFoElffen on 2022-01-31
Go into recovery mode > Mount filesystem with netwrking... The drop to root promt. Check to see if you can access the filesystem as more than just readonly...

Oh... Read the rest of the last post.

So this is working now?

---

### Post by bobdc2 on 2022-02-01
As described above, I got to the GUI via recovery mode and have been using Ubuntu normally. It goes in and out of sleep mode OK, but I'm afraid that if I do a complete shut down it will be hard to start up again. (I have not tried since getting to the GUI via recovery mode.)

---

