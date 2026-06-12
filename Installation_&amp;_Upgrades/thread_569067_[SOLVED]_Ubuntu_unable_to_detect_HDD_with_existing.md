---
title: "[SOLVED] Ubuntu unable to detect HDD with existing Vista install"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by Salamander_MN on 2007-10-06
I apologize if this is already answered somewhere else, but I can't find one that works for me.

I just built a brand-new machine and have Windows Vista Utimate installed on it currently.  I want to install Ubuntu onto the free space since the since hard drive is large enough.  Here is what I have done already and the problem I am encountering:

I used the Windows Disk Partition manager to shrink the drive down.  I have a 222GB partition for Vista and am left with 178GB of free space that is unpartitioned.  I downloaded and burned a CD image of Ubuntu 6.06.1 (since that one has the extended support) and am able to launch the LiveCD.  I get to the desktop and click on Install to kick it off.  Everything goes as planned until I get to the partitioning ... it just hangs at the "Select a disk" screen.  No drives show up at all and it just clocks.  I am able to click Cancel and exit the installer.

I found in another post to check GParted, but that also comes back with "No devices detected".  Found yet another post that said on the initial bootup screen, you press F6 and add 'acpi=force irqpoll', but that didn't seem to help either.  (I didn't know if the quotes should be there or not, but I tried it both ways and to no avail)

So at this point, it appears that Ubuntu doesn't recognize my HDD at all.  I'm wondering if there's something I'm missing, or if possibly I need to try a newer version of Ubuntu instead since this is a brand new machine.  (SATA 3.0GB/sec HDD)  I noticed in the System Device Manager that it didn't recognize a lot of the devices either ...

I was able to successfully install Mandriva on this system and didn't have an issue with partitioning, but I did have a problem with Video drivers which made X not work correctly.  I eventually gave up and wanted to try Ubuntu instead since I'd read some good reviews about it.

Anyone have any thoughts or additional things to try, I'm at a loss .....

Thanks in advance!!
--------
Jeremy
[email]Salamander_MN@yahoo.com[/email]

---

### Post by Salamander_MN on 2007-10-06
Correction ... the CD image I downloaded was v6.06.1.... not v6.04.1 ....

---

### Post by Salamander_MN on 2007-10-06
In case someone comes across this thread, I wanted to post the solution.  I downloaded and attempted v7.04 and it installed flawlessly.  Evidently v6.06.1 didn't recognize my HDD controller due the brand-new equipment.  The only thing that's still iffy is the Vid card ... I tell it to use the ATI driver and it wigs out ... guess I may have to boot into Windows to game.

So I am happily posting this reply within Ubuntu!  w00t!

---

