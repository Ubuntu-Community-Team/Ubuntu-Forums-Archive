---
title: "(Rant) Can't edit the mount points in the 11.04 installer? Why?"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by Mocker on 2011-08-21
I'm fuming about this again after doing my third install of 11.04, this time on one of my laptops. 

Why was the ability to edit mount points taken away in the 11.04 "Allocate Drive Space" portion of the custom install? In earlier versions, you could choose a mount point in the file system from a drop down (i.e. mount this partition as /, or /home, or /opt, etc.). You could also enter your own location to suit your needs. This allowed me to do tricks like mount my home partition under /media/home, to prevent my settings being clobbered by the installer (later, after integrating the settings created by the installer with the settings in my home directory, I could edit fstab to mount the home partition in its rightful /home location). Or to put my windows partitions under /media/WinXP... or put my old Linux parition under /media/oldlinux. I could do whatever I want. 

Now, I have limited options. I can only choose a location from the drop-down. I cannot edit it. Want to mount a partition under /media/home? Tough. Want to mount Window under /media? Nope. Can't. Instead, if I select an ntfs partition, I only get the choice of mounting it under /dos or /windows. Uh... WTF do I do if I have **three** windows partitions (like I do on my desktop)?

Listen, if I'm doing a custom install, and I know enough to partition my drive, don't you imagine I don't need the mount point option dumbed down for me? If I've gotten to this point, I obviously know what I'm doing (or, if I don't, I'm already screwed bcuase I'll probably nuke a partition that I want to keep)... limiting my choices here is stupid. 

Yeah, I know, I can clean this up afterwards by editing fstab or using some other tool... but my question is, why should I have to? What's the logic in removing this options from the user?

---

### Post by Morbius1 on 2011-08-21
They didn't remove it on purpose, it's a bug:
> The manual mount point entry box in the desktop installer's partitioner  does not accept keyboard input.  The drop-down still works, so various  standard mount points may be selected, and copying and pasting within  the entry box also works.  This was noticed too late to be corrected for  11.04.  In the meantime, you can mount partitions manually later, use  copy-and-paste, or use the alternate install CD. ([769043]("https://bugs.launchpad.net/bugs/769043")) 

---

