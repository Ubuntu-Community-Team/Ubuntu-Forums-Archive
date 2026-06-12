---
title: "downgrading network manager from cd"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by bradch on 2010-01-03
Is it possible to downgrade the network manager from 9.10 to the one from 9.04 with the live cd? My sierra wireless 881 won't work with it, and is supposed to work with the one from 9.04. I just went from a wubi 8.10 install to a normal dual boot. I don't have other internet access except using windows with my aircard.I tried adding the 9.04 cd to repositories but id didn't recognize it. I have to keep my vista partition for work. Using an acer aspire 5737z. Thanks for any help. If I find someplace with wireless, can I downgrade it with aptitude?

---

### Post by ajgreeny on 2010-01-03
You could always try, but I suspect you will be doomed to failure, as many dependencies may be broken with the older NM.  Have a good read up about wicd, which in many cases seems to be better with certain hardware, but make sure you have all the packages that are removed first on your system locally, so you can get back to the default, just in case it all goes wrong.

You can do that by seeing what will happen using synaptic if you attempt to install wicd.  It will need remove **network-manager** and **gnome-network-manager**, I think, so before you go ahead, simply reinstall those two packages that will later be removed, so they are in /var/cache/apt/archives.  You can then reinstall them later if you need to without needing a network connection, as they will already be downloaded and available locally.

---

### Post by bradch on 2010-01-03
It sounds like it might be easier to go back to 9.04 completely.
Is that possible without screwing up my windows partition? I tried to just boot from the 9.04 cd but grub won't let it boot from cd. At least not as is.

---

### Post by MelDJ on 2010-01-03
to uninstall see: [http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)
did you set your bios to boot from the cd?

---

### Post by bradch on 2010-01-03
Ye I am set to boot from cd. I will try this. Thanks.

---

### Post by bradch on 2010-01-03
OK This didn't work. Deleted all partitions but the windows partition and the recovery partition. Grub still comes up but says error: no such partition. and then grub rescue>. Now I don't know how to fix this.

---

### Post by ajgreeny on 2010-01-03
You must be able to boot from a CD as you had 9.10 installed, presumably from a CD, so try again setting the CD as first boot device in the BIOS.

The reason you can't boot at all at the moment is that grub is still on the MBR of windows, but your grub config files which were in ubuntu are now gone with the partition.  You could always restore the windows MBR with the windows install disk if you have one, and then try again to get 9.04 running.

---

### Post by bradch on 2010-01-03
I have recovery cd's that I tried. They will only reinstall. Which I decided it was time to do anyway. I lost some files but nothing I can't replace with a little work. This didn't work same result. Ubuntu cd won't boot. I have puppy linux on a flash drive that will boot up. Is this any help? This is a little over my head but I guess it's a good learning experience.

---

