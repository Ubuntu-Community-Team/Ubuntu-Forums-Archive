---
title: "Wubi 10.04 on Windows Vista, grub update troubles"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by zzephyr on 2010-08-05
Hi,

I just installed Wubi 10.04 on my computer running Vista. I booted into Wubi/Ubuntu fine, then went to the updater. A grub update asked me to select drives to install it to: one I figured was either Drive C or D (both hard drives), another was an external flash drive that boosts Window's performance. I didn't choose the flash drive, but checked the first. I thought it interesting that there were only the 2 drives to choose from, but I figure that's because I installed Wubi on 7 GB of Drive D, not C, and it could read the external anyway (??? drive C was invisible to it???).

Anyway, upon restart, I NO LONGER get the screen asking which operating system I wish to boot, Ubuntu or Windows.
I get a black screen saying:

blah blah blah
Verifying DMI Pool Data ............
error: no such device: ###letters-### etc. {{{I'm figuring this is Drive D}}}
grub rescue>

I have no idea what to do. I've read some other forums/solutions, but they seem different than my problem by slight degrees, and I want to be sure that what I do won't ruin my system/the data on it further before I proceed.

I have a Windows installation disc, but am unsure if the "System Restore" would allow me to revert to a point before I had Wubi that would still keep my personal data (like an idiot, I haven't backed up my drives, so restoring from an external source is out). 

Anyway, any guidance would be appreciated. 

Thanks

---

### Post by bcbc on 2010-08-05
You just need to reinstall the windows bootloader. The grub bootloader should not be installed with wubi.

boot from your windows disc into recovery prompt and run: bootrec.exe /fixmbr

that should get things working again.

---

### Post by zzephyr on 2010-08-05
Thanks!!! that worked. 

Now I just need to be careful NOT to install grub on any updates of my Wubi Ubuntu, eh?... lol

Perhaps I'll back up my drives now........... =)

Thanks again

Edit: Any clean-up I need to do, like removing grub or anything?...

---

### Post by bcbc on 2010-08-05
> **zzephyr said:**
> Thanks!!! that worked. 

Now I just need to be careful NOT to install grub on any updates of my Wubi Ubuntu, eh?... lol

Perhaps I'll back up my drives now........... =)

Thanks again

Edit: Any clean-up I need to do, like removing grub or anything?...

You're welcome :) No cleanup required. Don't remove grub. You actually need this to boot wubi, just not the 'bootloader' part.

---

