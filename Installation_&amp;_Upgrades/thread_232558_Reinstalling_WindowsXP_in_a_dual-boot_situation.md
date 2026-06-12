---
title: "Reinstalling WindowsXP in a dual-boot situation"
date: 2006-08-08
forum: Installation &amp; Upgrades
---

### Post by groggyboy on 2006-08-08
well, the title kinda says it all!

I intend to reinstall windows XP tomorrow, but this is the first time I'm installing windows onto a computer that already has linux installed.  I like my current partition scheme, and would rather not wipe my whole harddrive if i don't have to.  i heard, tho, that installing windows in a dual boot situation onto a computer that already has linux can be tricky.  I was wondering if anyone had any advice or could post some helpful links.

Here's my setup:
>Windows XP: 10gig (primary partition)
>Ubuntu 6.06: 10gig (primary partition)
>OSShare filesharing parition: 35gig (logical parition)
>Linux /home directory: 3.5gig (logical partition)
>Linux swap: 1.5gig (logical partition)

Ideally, I would like to just erase the first partition and reinstall windows, but if I have to erase linux as well, it won't be the end of the world (as long as I don't have to erase the last three partitions).  Also, I love GRUB and would like to keep using it.

thanks!
groggyboy

---

### Post by catlett on 2006-08-08
Just put in the XP installation disk and it will select the first partition for installation. It will tell you there is an installation of windows on the partition, do you want to delete and install to the C partition. That is pretty much it for the windows side. It will install and over write grub. But I finally figured out how to re-install grub after a windows install. The grub guys hid it deep inside the grub manual but I got to it.
Anyways I made it into a little how to so I could just link people to it instead of repeating it in each post. [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by confused57 on 2006-08-08
Shouldn't be a problem to reinstall Windows to the first partition, then reinstall grub:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

You'll need to add the Windows entry to your /boot/grub/menu.lst in order to boot Windows after reinstalling grub...there's an example listed in your menu.lst file that would probably work.

I haven't actually done this, if you'd rather wait for someone to reply who has.

Edit: catlett beat me to it...gotta sharpen those typing skills.

---

