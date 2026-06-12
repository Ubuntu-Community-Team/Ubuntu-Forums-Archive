---
title: "Will a new drive screw my grub?"
date: 2006-12-24
forum: Installation &amp; Upgrades
---

### Post by DirtDawg on 2006-12-24
Currently I have XP installed on a 40GB hard drive and Xubuntu on a 4GB drive. I finally got a new 40GB drive to replace the 4GB one. 

Here's the plan:
[LIST=1]
[*]Turn the computer off. Remove the 4GB drive.
[*]Install the new drive. 
[*]Turn on the computer, boot into live CD
[*]Install Ubuntu 
[*]Reboot, Grub intact, Windows intact, new Ubuntu intact.
[/LIST]

Now, I can see no problem with this plan, but I don't have a ton of experience with Grub and wondered if there's a problem I should know about (just to be safe). Any opinions would be appreciated.

Thank you.

P.S. The title of this thread is the greatest sentence I have ever written.

---

### Post by po0f on 2006-12-24
DirtDawg,

There shouldn't be a problem if the kernels are the same version/filename.  When installing Ubuntu, try to get what kernel version it is going to install.  Write this down and if you have to you can edit GRUB if the reboot doesn't work.

---

### Post by gonesolo on 2006-12-24
I can see no major problems during your proposed replacement. by installing Ubuntu it should write a new GRUB to the original 40GB drive (which I assume is your boot drive.)

As long as the old 4GB was a secondary (read non-boot) drive then your plan should go easily enough. If, however, the old 4GB was your boot disk then you may have problems but even then the reinstall of ubuntu should still recognise the FAT/NTFS partition that windows is installed on. 

I'd say at worst you may have to add an entry to your GRUB config file after install so that you can boot from windows from the GRUB menu.

EDIT: Edited to fix my crap spelling

---

### Post by DirtDawg on 2006-12-26
Everything ran smoothly. No problems at all.

Thanks guys.

---

