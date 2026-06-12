---
title: "Having trouble dual booting ubuntu and windows vista"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by Ildanach on 2010-08-10
I'm installing Ubuntu 10.04 for a friend, dual booting it with windows vista. The installation was going just fine up until the 4th step- partitioning the drives. After designating space for vista and ubuntu and running it, it popped up the window and displayed 0%... for the next hour. After looking around on ubuntu forums for a solution, I tried manually partitioning the drives in vista. Vista wouldn't let me, saying that access was denied. I tried using gparted next, which had an error with it as well. Does anyone know what i can do to work around this?

---

### Post by galfly on 2010-08-10
You might have accidentally deleted vista paging partition, vista uses a separate partition, I'm guessing it would be around 2-3% of hard disk space, usually seen at the right hand side at ubuntu partitioning page.

I'd recommend fixing vista first and re-installing ubuntu without messing with the paging partition

maya--

---

### Post by Ildanach on 2010-08-10
I don't seem to be finding a paging partition, however, there is another partition that does use only 2% of the hard drive, could this be it?

---

### Post by oldfred on 2010-08-10
Resize Vista partition
If problems, try disabling system restore, pagefile, (in advanced settings in computer properties) and hibernate option (in power management). Don’t forget to turn them on back later.
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
shrink the primary partition from the Windows MMC.

Resize windows partition info:
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)

---

### Post by Ildanach on 2010-08-12
Thank you so much! Those tutorials worked perfectly. It looks great now.

---

