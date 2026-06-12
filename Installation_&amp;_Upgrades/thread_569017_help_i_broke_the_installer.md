---
title: "help i broke the installer"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by FreeThePenguin on 2007-10-06
ok, im trying to install ubuntu 7.10 on my new pc.  I've installed windows XP fisrt, then ran ubuntu intaller went to manual partition created a new partition mounted to / and read that i was supposed to defrag windows partition first, dont know why, maybe ubuntu installer runs from windows?  any i canceled the install booted into windows, defraged (which was pointless as its a fresh install) and through the cd back in.  The boot screen comes up...  i select run/install...  and the screen goes blank... the hdd lite flickers a bit and then... nothing!    I've tried safe graphics mode as well, same thing.   BTW the partition did not show up in windows either, it was just part of the unpartitioned space.   So whats wrong? how do i get ny installer working again?

---

### Post by Pumalite on 2007-10-06
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by FreeThePenguin on 2007-10-06
um yeah, hows that going to make my installer work again?  that tutorial is for a working installer, besides i already read that.

---

### Post by Pumalite on 2007-10-06
Well. if I were you I'd start installing XP in the whole drive formatted ntfs. Defrag several times, erase all temp files. Then use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
(the stand alone, burn to CD, boot from, program)
Boot from it and right click on XP and in the menu choose 'resize partition'
Then install Ubuntu in the new partition.

---

### Post by FreeThePenguin on 2007-10-06
why would i create a large partition then take a chance and try to resize it?   better off make the partition the size you want it.

Anyway I've figured it out, if this happens to anyone else... just press F6 and type: *linux vga=771*

I found that at [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/")

---

### Post by dinub1 on 2007-10-06
> **FreeThePenguin said:**
> ok, im trying to install ubuntu 7.10 on my new pc.  I've installed windows XP fisrt, then ran ubuntu intaller went to manual partition created a new partition mounted to / and read that i was supposed to defrag windows partition first, dont know why, maybe ubuntu installer runs from windows?  any i canceled the install booted into windows, defraged (which was pointless as its a fresh install) and through the cd back in.  The boot screen comes up...  i select run/install...  and the screen goes blank... the hdd lite flickers a bit and then... nothing!    I've tried safe graphics mode as well, same thing.   BTW the partition did not show up in windows either, it was just part of the unpartitioned space.   So whats wrong? how do i get ny installer working again?

Why did you break it? Is that nice :) ?

---

### Post by FreeThePenguin on 2007-10-06
> **dinub1 said:**
> Why did you break it? Is that nice :) ?

nooo :(

---

### Post by dinub1 on 2007-10-06
Anyway... :)

How can I help you?

---

### Post by dinub1 on 2007-10-06
*[COLOR="Blue"]ok, im trying to install ubuntu 7.10 on my new pc. I've installed windows XP fisrt, then ran ubuntu intaller went to manual partition created a new partition mounted to / and read that i was supposed to defrag windows partition first, dont know why,[/COLOR]*

No. 1st why do manual partitionning? Do you know how that works? The best thing would be to do guided partitionning. Let Ubuntu shrink the existing Windows XP partition and then install into the free space. Or you should have gone into Windows XP and with a program like Partition Magic make free space for the Ubuntu partitions. If you pick up manual parititonning you need to make sure you know what you are doing (no offense please). After making space free space on the HDD, you go to Ubuntu install and pick "guided, use free space"

[I][COLOR="Blue"]maybe ubuntu installer runs from windows? 
[/COLOR][/I]

No, it does not. Ubnutu installer either works within Ubuntu Live CD (Adter loading) or via Ubuntu alternative installation CD. Not under Windows :)

*[COLOR="Blue"]any i canceled the install booted into windows, defraged (which was pointless as its a fresh install) and through the cd back in. The boot screen comes up... i select run/install... and the screen goes blank... the hdd lite flickers a bit and then... nothing! I've tried safe graphics mode as well, same thing. BTW the partition did not show up in windows either, it was just part of the unpartitioned space. So whats wrong? how do i get ny installer working again?[/COLOR]*

It got stuck. Try different options like acpi=off. Sometimes the straight loading does not go thru. It depends on your PC hardware. You may need to experiement with different options. I suggest, go to acpi=off then pick up the "e" option for edit. Remove the "splash" option and boot. See if there is any "Kernel panik" which may indicate a hardware incompatiblilty. Otherwise you are lost.

---

