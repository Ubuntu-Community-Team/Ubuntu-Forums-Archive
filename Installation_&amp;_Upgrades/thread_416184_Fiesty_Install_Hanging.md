---
title: "Fiesty Install Hanging"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by ydoucare on 2007-04-20
Been trying to install Fiesty overtop of a botched Edgy -> Fiesty upgrade.  I can boot into the livecd ok, start the installer, and setup partitions (basically just formatting the current ubuntu partition and installing there)  but when I get to the point where it begins the install, it gets to 15% at "Detecting File Systems..." and just hangs.  I'm not sure the system is totally frozen though, as the CD keeps spinning up and spinning down, almost in a loop or like the system is out of memory or something.  Cursor is frozen, but I did see it move once or twice over the course of 15 min while i sat and waited.

I'm installing on a somewhat old laptop:
Toshiba Satellite 5005 S504
PIII 1.1 GHZ
256 MB mem
40 GB HD
GF 2 Go

Burnt the CD twice, first at Max speed, 2nd at 8x, both do the same thing.

Edgy installed fine with no issues.  Any suggestions?

---

### Post by Cariboo1938 on 2007-04-20
> **ydoucare said:**
> Been trying to install Feisty over top .....  Any suggestions?
Maybe you'll find some help [HERE]("http://www.ubuntu.com/getubuntu/upgrading")!!

---

### Post by ydoucare on 2007-04-20
Thanks, but i'm not exactly sure how that's supposed to help me.  I'm not doing an actual upgrade, I'm doing a clean install.  Installing over top = formatting the partition for a clean install.  The partitioner should format it, but It hangs before it even touches the partition.

---

### Post by Cariboo1938 on 2007-04-20
> **ydoucare said:**
> Not exactly sure how that's supposed to help me.  I'm doing a clean install.  Installing over top = formatting the partition for a clean install.  It hangs before it even touches the partition.
Sorry, I didn't get this! Unfortunately I have no idea how I could help! Sorry.
For a clean install I used to refer to [THIS.]("http://www.psychocats.net/ubuntu/installing") It helped me very well to get through a flawless installation with Edgy and I think the basics are valid for Feisty too.

---

### Post by Ziox on 2007-04-20
Perhaps you should try the alternative disc.  I always find it better and more flexible than the Live Disc.

---

### Post by ydoucare on 2007-04-20
3rd time might be the charm....all I did this round was load system monitor then started the installer so i could monitor memory usage, it's copying files now...

---

### Post by kevoh82 on 2007-04-23
Im having problems on my elg laptop since i installed fiesty fawn, its hanging all the time. it loads up ok but then starts hanging whenever im doing nor not doing anything. Anyone with such a problem or fixed it before tell me what to do..please or where to refer to

---

### Post by use a name on 2007-04-26
> **ydoucare said:**
> Been trying to install Fiesty overtop of a botched Edgy -> Fiesty upgrade.  I can boot into the livecd ok, start the installer, and setup partitions (basically just formatting the current ubuntu partition and installing there)  but when I get to the point where it begins the install, it gets to 15% at "Detecting File Systems..." and just hangs.  I'm not sure the system is totally frozen though, as the CD keeps spinning up and spinning down, almost in a loop or like the system is out of memory or something.  Cursor is frozen, but I did see it move once or twice over the course of 15 min while i sat and waited.

I'm installing on a somewhat old laptop:
Toshiba Satellite 5005 S504
PIII 1.1 GHZ
256 MB mem
40 GB HD
GF 2 Go

Burnt the CD twice, first at Max speed, 2nd at 8x, both do the same thing.

Edgy installed fine with no issues.  Any suggestions?

Exact same problem here. At 15% it hangs. But, I managed to get Feisty installed. :)

I just hit the cancel button, then hit the install button again. Now it skipped the checking of the filesystem and started formatting/installing files. There was no feedback though, so I just waited for the cd and hdd to go quiet again, restarted (ctrl-alt-del still worked, dunno if that's needed, maybe reset does work as well), and Grub was there showing the new kernel.

It's real strange. Also the constant checking of the filesystems after every minor update, even when I was trying to ignore partitions by not assigning a mount-point.

---

### Post by Death_Sargent on 2007-04-26
Perhaps its a crappy install disk?

Did you check integrity before installing?

If you did then are you preserving any old partitions?

Try reformating the drive from the Gparted live cd if all else fails. I find Ubuntu likes to auto preserve many things, one of them could be braking your stuff

---

### Post by geog_eric on 2007-04-27
Same problem with Xubuntu install with same scenario. Botched Ubuntu install (on old laptop with only 2GB harddrive) with hosed GRUB. Tried wiping the harddrive, still hanging at the "Detecting file systems" message.

---

### Post by antagon on 2007-04-29
I've had the same problem as well. Reformatting my partitions to ext3 before the installation solved it for me.

---

### Post by nenduvel on 2007-07-09
I tried several things but what worked for me was: open gnome partition manager and make swap space and a partition for your ubuntu. then select the option "boot" for the ubuntu partition and now try to install. 

I hope it helps.

Note: gnome partition manager may give an error because you didn't unmount a partition you are trying to change.

---

### Post by Pumalite on 2007-07-09
You have to take into account the amount of memory available. 256 MB RAM will require 'Alternate Xubuntu CD' to install and later run well.

---

