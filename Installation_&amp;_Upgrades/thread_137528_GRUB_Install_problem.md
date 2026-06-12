---
title: "GRUB Install problem"
date: 2006-02-28
forum: Installation &amp; Upgrades
---

### Post by capdog on 2006-02-28
Hi there

I'm trying to get GRUB to install on my primary hard disk and dual boot WinXP and Breezy 5.10. Everytime it installs to the MBR and I reboot, I get a screen of recurring, repeating "GRUB"s, like "GRUB GRUB GRUB GRUB GRUB GRUB...." etc to infinity.

Can anybody help me with this please? Lilo works fine but I would like to use GRUB. 

Cheers,
capdog

---

### Post by schmappel on 2006-02-28
This might help:

"According to airhead this can be caused by having your bios detect your disks automatically. Try to set your bios entry to User Type HDD.

Another possibility is that you had Grub installed on your MBR and tried reinstalling it (for instance due to hard disk changes) but used the wrong setup and root commands."

Found [here]("http://www.gentoo.org/doc/en/grub-error-guide.xml#doc_chap7").

---

### Post by capdog on 2006-02-28
Thanks, I've tried changing the HD to user but it doesn't work. 

As for installing GRUB incorrectly, it's done by the Ubuntu installer so I dunno what it's doing. 

Maybe I should just give up and use Lilo..

---

### Post by schmappel on 2006-02-28
Well, it *should* work, right? I myself have set up a WinXP / Breezy dual boot without too much hassle...

Found this on another forum:
"Some other people have had this problem when they have SCSI RAID and IDE drives on the machine."

On another site i found some more info about the 'user HD' scenario:
"when GRUB fails to load the operating system and instead fills the screen with an endless sequence of GRUB GRUB GRUB, the problem is very likely due to the BIOS being set to detect hard drives automatically. Changing the BIOS setting from "Auto" to "User" was what finally solved the problem. [..] Somehow (I'd love to hear a detailed explanation if anyone know) this auto detection makes GRUB load its own loading code instead of the next loader stage, causing an infinite loop. I'm told something similar happens with LILO as well; perhaps it's a common BIOS problem causing wrong or exotic disk geometry values to be reported."

Also, check out [this]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub") wiki article.

Last but not least you could always try reinstalling Breezy from scratch (i know its not exactly heroic but hey, it *did* do the trick on a couple occasions...)

Good luck!

---

