---
title: "Is there a HOW TO for..."
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by oliwally on 2006-06-03
Just wondering if anyone has written a decent beginners HOW TO for foolproof installation of K/Ubuntu in a dual boot arrangement with XP, on a separate hdd so that Grub doesn't mess with XP's original MBR. I love that arrangement because it doesn't touch my XP hdd at all, and if something goes wrong I just simply switch my BIOS to boot from my XP hdd again (rather than booting from my K/Ubuntu hdd using GRUB). 

Mingus helped me to achieve this once and it's still running on my computer at present. I just love it. It seems like a really low-risk way of installing Linux for those of us who just must use XP for work etc but like using K/Ubuntu whenever possible. The tread where Mingus helped me is [here]("http://ubuntuforums.org/showthread.php?t=43528"). But it's all a bit messed up and a lot of reading. Perhaps some guru could write a neat HOW TO. Or perhaps there is one already? Please tell me where.

---

### Post by rcarring on 2006-06-03
Use the alternate install cd, install grub on a floppy.

The alternate install cd allows you to pick where you want grub to live. This choice is not available in the Live CD installation by design, and grub is placed on the MBR of the first bootable hard disk.

Hope this helps. Please note, the installation process is described in detail in ayisu's pages below his signature, also there are detailed guides on wiki.ubuntu.com

---

### Post by confused57 on 2006-06-03
My system is set up like this:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by oliwally on 2006-06-03
> Use the alternate install cd, install grub on a floppy.
I'm glad you told me about that! I had no idea and would have been frustrated using the desktop cd.
> 
My system is set up like this:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

That's great - some excellent info there already. 

Thanks so much for your help.

---

