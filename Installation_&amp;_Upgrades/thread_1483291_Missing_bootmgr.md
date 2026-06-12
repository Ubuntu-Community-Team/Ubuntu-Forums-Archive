---
title: "Missing bootmgr"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by 10ghost on 2010-05-14
Hi all,
just noticed this problem on my system after terminating the installation of a new theme it gave me this error

BOOTMGR MISSING
press ctr+alt+delete to restart

I believe the solution to my problem is installing the bootloader(GRUB) again.
The question now is how would i do this and what are the safty precautions you would advise me about this?

---

### Post by darkod on 2010-05-14
Nope, bootmgr is a boot file from win7/vista. Get your win7/vista install dvd and read here to repair the boot process:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I think just the first command listed there will finish the job. Try not to execute the second, /fixmbr, because after that you will need to reinstall grub2 to the MBR (windows will overwrite it).

But if the repair didn't work without the second command, try again and execute both of them, because reinstalling grub2 to the MBR is easy. The main thing is to get /bootmgr back.

If you need the commands later to reinstall grub2, just ask. By the way, they are on the same page on that link.

---

### Post by 10ghost on 2010-05-14
Ok 
I would do just that.

---

