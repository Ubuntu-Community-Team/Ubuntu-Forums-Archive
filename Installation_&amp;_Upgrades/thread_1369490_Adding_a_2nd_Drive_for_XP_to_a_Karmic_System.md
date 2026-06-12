---
title: "Adding a 2nd Drive for XP to a Karmic System"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by wdavro on 2010-01-01
A local store built a brand new dual core system for me about a month ago with a 1TB drive and installed Karmic on the entire drive.  I now have a piece of external hardware that requires XP and simply will not work in XP in Virtualbox.  I have purchased another 1TB drive, and my thinking is to create an XP partition of about 2-300GB and leave the rest of the drive for another Karmic partition and dual-boot.  I don't care which drive is primary (unless there is a reason I should).

I was thinking of unplugging the karmic drive and putting the new drive in it, installing XP on it, then adding the Karmic drive back to the system and editing one of the boot files to add the other operating system.

Is that even possible?  If so, which boot file should I edit?  Which drive should be primary?  Or, is there a better, easier way to do this?

Thanks,

---

### Post by chrisme52 on 2010-01-01
sounds like it should work fine
i have karmic and xp both on seperate drives but i use the boot menu from my motherboard instead of configuring grub...

Instead of buying one large drive, I would buy 2 small (say 160 or whatever) drives and install the os'es on them.(install xp first and then when you install linux grub will pick it up) then format the 1tb as nfts so both linux and windows can access it.

At the moment i have 2 10k 74gb western digital drives for my installs, great setup

hope it works out

---

### Post by wdavro on 2010-01-02
You're right!  It worked perfectly.  And I never thought to use the BIOS boot menu.  Made it so much easier to get going.  I really love the idea of the smaller, separate boot drives, but I have no other sata drives and don't want to take the time to set that all up right now anyway.  But I definitely will on my next opportunity.

Thanks very much for the response and help.

---

### Post by chrisme52 on 2010-01-02
Glad to have helped, you never stop learning with linux

---

