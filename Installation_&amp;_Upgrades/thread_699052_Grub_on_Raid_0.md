---
title: "Grub on Raid 0"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by Nigmah on 2008-02-17
okay so im trying to get grub back up and running after setting up raid 0 (hardware) on two 750 drives. Now my os's are on a separate non raid drive. I've tryed repairing and reinstalling ubuntu itself, each time i do so it just takes my first raid drive out of raid and i have to completely shutdown the computer to get it back in, and it does not load grub it simply boots into vista.

Im running off of a 
intel quad core q6600 overclocked
4 gigs of ocz ram
GA-X38-DQ6
nvidia 8800 gts

---

### Post by Nigmah on 2008-02-17
bump?

---

### Post by Pumalite on 2008-02-17
I believe you have to setup your Raid first, then install Ubuntu. I don't think it will work the other way around. (I'm not a Raid user though)

---

### Post by Nigmah on 2008-02-17
my raid is setup im using it right now on vista. thats why i said i setup two drives in raid0.

---

### Post by kubug on 2008-02-17
ummm... since Vista is running on it, I assue it's not a Linux RAID, but rather a fakeraid (also a software raid, but it's made to look like a hardware raid).

Did you follow any how-to's for installing on a fakeraid??? It usually tells you how to setup GRUB as well.

---

### Post by Nigmah on 2008-02-18
unless i'm mistaken its hardware raid as i set it up in the bios not using software.

---

### Post by cashmoney on 2008-02-18
> **Nigmah said:**
> unless i'm mistaken its hardware raid as i set it up in the bios not using software.

I assure you it is a software raid unless you have your HDD plugged into a card and not the motherboard.

---

### Post by Nigmah on 2008-02-19
ok then i guess it is, my only problem is why can't grub work on on the non raid  hdd?

EDIT: well i installed and used easy bsd and i got into osx. any ideas on how to get osx to recognize the raid0?

---

