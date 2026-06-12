---
title: "Copying Dual-Boot Ubuntu/XP Pro to new HDD?"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by becatlibra on 2007-10-30
I have copied (cloned) hdds over a network using dd and netcat but this is a different situation.  It seems it should be SIMPLER.

I have an 80 Gig Partition that is dual-boot (using grub) and I want to copy the whole thing over to a 250 gig drive.  I know I can use gparted to 'grow' the paritions after it's done.  

My problem is how to go about this.  I would like to not have to repartition the new HDD to match but rather simply close from one disc to another.

Would it be as simple as dd if=/dev/hda of=/dev/hdb (from a live cd of course?)

Thanks

Benjamin

---

### Post by logos34 on 2007-10-30
I think you should copy the partitions rather than whole disk since the drive geometry differs.

Or use Partimage (from a utility CD like gparted or parted magic).

[http://www.debianhelp.co.uk/ddcommand.htm](http://www.debianhelp.co.uk/ddcommand.htm)
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)
[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)

---

