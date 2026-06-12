---
title: "removing Ubuntu"
date: 2005-02-13
forum: Installation &amp; Upgrades
---

### Post by alexj on 2005-02-13
Hi guys,

Here is the story.  Before install Ubuntu on my server (to replace Mandrake), I installed it on an old laptop. The old fella knows no comfortable retirement, and tests first every new idea under the sun. It takes Ubuntu, I like it, ubuntu goes on the server and the old laptop should get old NT 4 for something else.

I cannot install NT on the system any more! It says GRUB produces an error - my understanding it is still booting up using ubuntu loader!

How can I remove it???

Thanks

---

### Post by emperor on 2005-02-13
Fixmbr (on the NT cd) may work.
  
  Or you do a low level format using this floppy or CD based tool:
  
  [http://www.seagate.com/support/disc/drivers/discwiz.html]("http://www.seagate.com/support/disc/drivers/discwiz.html")
 
 Note: it works on non-seagate drivers as well; I used it on a WD and seagate driver recently.

---

### Post by hajo on 2005-02-13
Another option to clean it up:
(for all those, messing up the mbr with even more acient windows versions, like win98...)

call 
fdisk /MBR
from any bootable DOS-floppy, rescue disk or the Windows installation CD.
This is an undocumented option of the microsoft "fdisk" (not the linux version of course).

---

