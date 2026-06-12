---
title: "Loss of Ubuntu partition"
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by de_island on 2011-08-11
Hey folks.

Quick summary: Blue Screened, installed Ubuntu on its own partition (let's call it partition B) so I could recover my data, worked with Ubuntu for a few months, reinstalled windows on its original partition (partition A).

At that point I assumed I could dual-boot, but I don't get that option at all at startup. I've tried everything I can, but it seems like installing Vista has completely removed the Ubuntu installation even though it's definitely on a completely different partition.

I can live without Ubuntu if I have to (SHOCK, HORROR) but I want to try and get to the data in B that I can't access, or at least make some use of the space since I wouldn't mind some extra memory.

I have a 250GB hard-drive which is split into 185GB (partition A) and ~65GB which is what I originally allocated to the Ubuntu drive, but that 65GB doesn't display at all in My Computer.

Any help would be appreciated.

---

### Post by Hakunka-Matata on 2011-08-11
By reinstalling windows you overwrote the MBR (Master Boot Record) on your hard drive with windows bootloader.  That wiped out Ubuntus bootloader (Grub) so you cannot boot Ubuntu anymore, if it even exists.  Windows may have formatted the whole drive which of course would wipe out the Ubuntu partition.

what does the partitioning look like on your hard drive  now?

---

### Post by de_island on 2011-08-11
Hmmm... That's annoying.

All I can go by at the moment is what My Computer says (mentioned in my first comment) basically that it isn't detecting the Ubuntu partition or acknowledging the existance of the 65GB in any way. It just thinks that I have a 185GB drive.

I've used other programmes like Speccy and Spacesniffer and none of them can pick up the Ubuntu partition either.

---

### Post by Hakunka-Matata on 2011-08-11
You could use an Ubuntu LiveCD, boot to it and choose the "try Ubuntu without installing" just to get access to the partition editor, GParted.  That would be a great place to start.  Get Ubuntu running and come back here.

---

### Post by Johnb0y on 2011-08-11
google MBR mod'ers to rebuild it... it should find it for you...

[COLOR=Red]*edit: EasyBCD - used it before and it worked when using vista/7 with ubuntu 10.10[/COLOR]. give it a try - 

[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

---

