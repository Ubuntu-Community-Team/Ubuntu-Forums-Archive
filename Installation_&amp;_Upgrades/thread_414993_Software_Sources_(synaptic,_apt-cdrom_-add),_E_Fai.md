---
title: "Software Sources (synaptic, apt-cdrom -add), E: Failed to mount the cdrom"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by midia on 2007-04-20
I installed Feisty.
I needed to get something off the Ubuntu 7.04 cdrom after the install. 
Synaptic software sources (System>Software sources), and command line command "apt-cdrom -add" both gave me an error when I wanted to add my Feisty cd as a source:
"E: Failed to mount the cdrom"

Strangely, the cdrom was mounted and sitting as an icon on my desktop "Ubuntu 7.04 i386", and I was even able to surf the cdrom, indicating that it was mounted and recognized by the system, just not synaptic.  I have a cdrw drive and a dvd drive in my system.

To add the Feisty cdrom as a source, I popped the cd into my dvd drive and at a command line I typed the following commands:

sudo umount /media/cdrom  <enter>                note: this un-mounted the cdrom
sudo mount /dev/dvd /media/cdrom <enter>  note: this mounted the cdrom at /media/cdrom

A dialog box popped up recognizing that the cdrom was one with a package list on it, asking me if I wanted to add it to the sources list.  I agreed and the Feisty cdrom then worked as a source.

Note:  If I popped the cd into the cdrw drive, the same Failure message would occur.  I think would have to change my second command above to 
sudo mount /dev/cdrw /media/cdrom  
but I didn't try it.

Using my cd as a source added this line to sources.list in /etc/apt/sources.list:

"deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted"

I think a bug report on this was closed after they thought they found an answer.  Anyway, I hope it gets corrected and maybe this procedure can help somebody else.

Good luck and have fun.
Midia

---

