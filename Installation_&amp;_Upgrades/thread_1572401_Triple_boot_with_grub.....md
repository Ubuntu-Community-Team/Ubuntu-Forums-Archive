---
title: "Triple boot with grub...."
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by leeman101 on 2010-09-11
Hi,
I have (only bc i have to) windows vista, also Ubuntu 10.04 on the same drive, and dual-booting is no issue at all.
But after I installed Mandriva 2010 to try to triple boot, i couldn't find Ubuntu anymore :(
so I got rid of mandriva, and grub was messed up bc I deleted all mandriva partitions.
So then I installed Xubuntu 9.10 (because it is a quick install) to recover grub, and with Xubuntu, Ubuntu, and vista, Grub sees all three OSes no problem.  So what would I have to do to make Grub work this way when I install Mandriva?

Thanks in advance..

Lee

---

### Post by leeman101 on 2010-09-11
Can no one help me with this? :(

---

### Post by Rubi1200 on 2010-09-11
There was no need to remove Mandriva!

All you had to do was reinstall GRUB and bingo!

Here is the guide for future reference:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by leeman101 on 2010-09-11
Thanks Rubi..
So if I reinstall mandriva, now that I have deleted it (oops) and then reinstall grub 2 using the guide you linked me to, then I should be all set? 
I will try it and hopefully it will work :)

---

### Post by tanush on 2010-09-11
> **leeman101 said:**
> Thanks Rubi..
So if I reinstall mandriva, now that I have deleted it (oops) and then reinstall grub 2 using the guide you linked me to, then I should be all set? 
I will try it and hopefully it will work :)

sweet and simple just  execute sudo update-grub command.

---

### Post by Rubi1200 on 2010-09-11
> **leeman101 said:**
> Thanks Rubi..
So if I reinstall mandriva, now that I have deleted it (oops) and then reinstall grub 2 using the guide you linked me to, then I should be all set? 
I will try it and hopefully it will work :)
Assuming you have a regular setup (no RAID or other stuff) then yes it should be fine.

As tanush pointed out, don't forget to run ```
sudo update-grub
``` after rebooting into Ubuntu. GRUB should then pick up Mandriva and you are good to go.

Best of luck!

---

