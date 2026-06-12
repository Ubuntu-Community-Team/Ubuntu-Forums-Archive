---
title: "Custom boot loader setup"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by aksdb on 2006-06-03
How can I get the live cd installer to *not* install grub or offer me the choice where to install it? I don't want it to even touch my MBR or primary partition (so the best thing would be it wouldn't try to install and let me do this manually).

---

### Post by Marrea on 2006-06-03
I too, would _very_ much like to know the answer to this.  I have a multiboot computer and I use the NTLDR to boot into all my various Linux distros.  I therefore wanted to locate Ubuntu's bootloader on its root partition.  I was absolutely flabbergasted to see it plonk Grub on the MBR without even asking where I wanted it put.  BAD, BAD, BAD, BAD, BAD move, Mr Shuttleworth.

I am now going to do a fixmbr and I'm afraid Ubuntu 6.06 is coming off my computer until someone explains to me how I can reinstall it and place Grub where I want it, not where Ubuntu wants it.

:evil: :evil: :evil: :evil: :evil: :evil: :evil: :evil:

---

### Post by llamakc on 2006-06-03
Does doing an "expert" install offer that granularity? It sure better.

---

### Post by llamakc on 2006-06-03
[http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)

Look at the Alternate Install CD:

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:
  [LIST]
[*]creating pre-configured OEM systems;
[*]setting up automated deployments;
[*]upgrading from older installations without network access;
[*]LVM and/or RAID partitioning;
[*]installing GRUB to a location other than the Master Boot Record;
[*]installs on systems with less than about 192MB of RAM.[/LIST]  There are three images available, each for a different type of computer:

---

### Post by aksdb on 2006-06-03
Good point, but I had hoped that I can somehow configure the live cd installer to change its behaviour. Except that boot loader thing, it mostly suits my install-needs :D

---

### Post by Marrea on 2006-06-03
[QUOTE=llamakc][http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)

Look at the Alternate Install CD:[/QUOTE]

Many thanks for this.  Unfortunately I had completely missed this when I first went to the site.  I have now repaired my MBR, downloaded and installed the "Alternate" and am up and running.

I still think it would have made more sense to have a Live CD and a completely separate single install CD containing all the options people are likely to want.  Surely it is quite normal for people to want a choice of where (if at all) to locate Grub?

---

### Post by chisler on 2006-06-03
[QUOTE=Marrea]Many thanks for this.  Unfortunately I had completely missed this when I first went to the site.  I have now repaired my MBR, downloaded and installed the "Alternate" and am up and running.
[/QUOTE]

Could you please post the steps needed to manually set the grub location and also how to change boot.ini to boot from the linux HD/Partition?

Thanks
Chisler

---

### Post by llamakc on 2006-06-03
The alternate cd (as mentioned above) lets you define where to install GRUB. As for boot.ini I guess that's a Windows thing? No idea.

The suggestion I gave was to download and burn and install via the alternate install cd image instead of using the LiveCD or regular install iso.

---

