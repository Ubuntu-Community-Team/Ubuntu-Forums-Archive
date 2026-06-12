---
title: "How do you remove Windows after installing Ubuntu?"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by jodybrown on 2011-10-30
[SIZE=2][FONT=Arial]Greetings,

I am coming from Windows, and I hate it tremendously. I am trying ti figure out how to remove Windows completely from my computer, and just use Ubuntu. Is there a way to do that?
[/FONT][/SIZE]

---

### Post by wojox on 2011-10-30
Use a Live-CD and Gparted. If your that new you may just want to keep dual booting for a little imho. :p

---

### Post by kurt18947 on 2011-10-30
> **wojox said:**
> Use a Live-CD and Gparted. If your that new you may just want to keep dual booting for a little imho. :p

wojox gives good advice.  If your Windows installation is working properly, resize (shrink) it using Windows' tools and leave some space beyond what Windows is using now.  Then use a LiveCD/LiveUSB  to create one or more partitions in the space vacated by Windows and install Ubuntu.  When GRUB is installed it should find the Windows boot info and incorporate that into GRUB's boot menu.

There are a few things that Ubuntu can't really do.  I had a perfect example a couple weeks ago.  There was a firmware update for a printer.  Even though the printer works great with Linux, the firmware upgrade was an .exe file. Stuff like that is a one-time event and I just didn't feel like "fighting City Hall" trying to do the update with Linux when that wasn't a presented option.

I think of Windows as the infrequently used implement or tool.  Seldom needed but sometimes for oddball hardware problems sometimes it's the only practical choice.

---

### Post by Mark Phelps on 2011-10-30
If you installed Ubuntu using Wubi, removing Windows will remove Ubuntu as well.

---

