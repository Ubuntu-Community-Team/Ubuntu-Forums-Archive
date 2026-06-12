---
title: "Access Win-NTFS dir with diacritics in name?"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by Onderhil on 2007-10-31
Hi,

Just upgraded to 7.10 from 7.04 CD within nn minutes. However I seem to have erred somewhere in that path, I think even in installing 7.04, regarding the system charset (ISO vs UTF). 

Amarok (and Konqueror) doesn´t find mp3´s in my NTFS Win-XP partition that reside in dirs with a diacritic in its name, e.g. Händel, or Gilbert Bécaud (and I suspect mp3´s with a diacrit in their names won´t show either).

What must I do where to correct this (apart from breaking my iTunes in XP) in Ubuntu?
Thanks,
Mark

---

### Post by Onderhil on 2007-10-31
Hi again,
After more searching - triggerd by NTFS - I found this link:
[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+read+write](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+read+write)

So I installed ntfs-config through Synaptic, and started it through the menu under System. There I enabled both checkboxes (for internal and external), looked up Händel, and there he was!

So, problem solved, thanks for the attention.
Cheers,
Mark Onderhil

---

