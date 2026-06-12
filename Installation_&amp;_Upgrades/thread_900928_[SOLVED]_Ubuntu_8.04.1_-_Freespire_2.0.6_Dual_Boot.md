---
title: "[SOLVED] Ubuntu 8.04.1 - Freespire 2.0.6 Dual Boot"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by Terraman on 2008-08-25
Dear Ubuntu Friends,

I've been using both OS Freespire 2.0.6 and Freespire 2.0.8. in their partitions and I could change between both OS.

Now, I want to change Freespire 2.0.8 to Ubuntu 8.04.1. When I've finished to install Ubuntu, I can choose Freespire 2.0.6, but it appears a lot of commands, which doesn't appear before, and it gets stuck. The Freespire 2.0.6 OS doesn't run.

So, I reinstall Freespire 2.0.8 and all works fine again.

Any ideas how can I solve this problem to make a try with Ubuntu?

My family are not used to Ubuntu. I gradually have to swap form one OS to the other.

Thanks in advance!

Terraman.

---

### Post by sandysandy on 2008-08-25
from what i can understand u want to dual or triple boot between the different linux distros.

u will have to make relevant entries of freespire in Ubuntu's menu.lst, so that while booting, the GRUB shows the different booting options - freespire , Ubuntu etc. (assuming u want to use Ubuntu's GRUB). if u want to use freespire GRUB make the entries for Ubuntu  in the menu.lst of freespire.

see this link for multiple booting

[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

have a look at Super Grub Disk also. [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

see super grub tutorials here

[http://www.supergrubdisk.org/wiki/Howto_Fix_Grub](http://www.supergrubdisk.org/wiki/Howto_Fix_Grub)

[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

ask for more info, if u require

regards

---

### Post by Terraman on 2008-08-25
The GRUB shows the different booting options, and I can choose. However, when I choose Freespire it gets stuck as explained above.

Regards,

Terraman

---

### Post by sandysandy on 2008-08-25
> **Terraman said:**
> The GRUB shows the different booting options, and I can choose. However, when I choose Freespire it gets stuck as explained above.

Regards,

Terraman


post output of [COLOR="Blue"]sudo fdisk -lu[/COLOR]

can u elaborate on which partitions u have installed the various OS, and what exactly happens when u  choose Freespire and it gets stuck. do u get any errors when it does not run.

it may be possible that the entries in menu.lst do not reflect the correct partitions.

regards

---

### Post by Terraman on 2008-08-26
I've already checked the menu.lst, and it seems to be fine.

Ubuntu is on partition hda 5

Freespire is on partition hda 6

It's difficult to explain what exactly happens when Freespire gets stuck. Aparently the OS were loaded and all the commands of the action are shown, which normally doesn't occur, then it halts in a command line with out running Freespire.

Regards,

---

### Post by Terraman on 2008-08-27
Dear Friends,

I could finally solve the problem. Apparently it was some Ubuntu instructions in the GRUP witch aren't compatible with Freespire. I copied the command lines from Freespire's GRUP to Ubuntu and vice versa and it starts to work.

Regards,

---

