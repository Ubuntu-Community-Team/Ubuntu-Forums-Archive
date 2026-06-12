---
title: "GRUB error"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by Przemian on 2010-01-25
Hi,

I install 9.10 from CD, chose to partition whole drive (40GB) for the Ubuntu and upon restart and after removing the CD  i hit enter. The next thing i get is:

error: no such device: 89c3f82e-3483-453f-a2df-be7770efdc00
Press any key to continue...

So I reboot again, with CD inside, run Ubuntu from CD and it loads the system to desktop. I see Applications Places System and icon for Firefox. I chose places and below Computer and Floppy Drive entries I find 38GB Filesystem. I click that and I get a widow titled:

89c3f82e-3483-453f-a2df-be7770efdc00 - File Browser

with file, edit, view, the whole bag. I see folders in there so I assume the system is installed onto my harddrive. Right clicking on 38GB Filesystem I can unmount it.

What do i need to do to run Ubuntu from my HD?


This is IBM thinkpad T-40

---

### Post by zolo on 2010-01-25
Two thoughts: Are you completing the Grub install? It will flash a message the Grub install was completed. Also are you installing the mbr of your hard drive, which I believe is the grub default?

---

### Post by meierfra. on 2010-01-25
Try this:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by presence1960 on 2010-01-25
Do you get a GRUB menu when you boot?

EDIT: Nevermind meierfra linked you to the same solution I was going to give if you get a GRUB menu. I read it somewhere else and made a text file of it. But now I bookmarked meierfra's link. Thanks.

---

### Post by Przemian on 2010-01-26
> **meierfra. said:**
> Try this:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)


This worked. Updated grub and now I can login into my first HD based session of Ubuntu. AWSOME.

Thanks for fast replies.

P.S. now onto configuring my wireless connection...

---

