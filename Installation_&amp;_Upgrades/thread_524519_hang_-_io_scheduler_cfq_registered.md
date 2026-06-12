---
title: "hang - io scheduler cfq registered"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by Roswellgrey on 2007-08-13
Greetings :)

Installed Fiesty on a couple of other PCs ; had a few fun and games, but a search of this site soon sorted them out  ...

However, my desktop is proving a pain ...

Mobo : P4S5A ( Sis 645 chipset), P4 1.8G, 512M RAM, ATI AIW Radeon 9600, Audigy2

X server seemed to not start from the Fiesty Live CD, but the addition of "noapic" and waiting for a 2 minute pause at "io scheduler cfq registered " allowed it to continue and run .... 

So, with the  LiveCD booted up, did an install 

Upon reboot , Grub boots OK, 
I select Fiesty ,
it boots as far as "io scheduler cfq registered ( default)" 

and then hangs for anywhere between 3 and 10 minutes...

This happens regardless of normal boot or rescue mode.

Adding the following boot params ( in various combinations) doesn't resolve this 
noapic
nolapic
acpi=off
elevator=deadline
 
Neither does disabling ACPI in BIOS or enabling  / disabling "Plug and Play OS" in BIOS

Research finds  that this does seem to happen on certain HW combinations with the latest kernel

But the standard "fixes" don't work for me ....

Anyone have any other ideas ? - I am at a loss what to try next ....

---

### Post by kerry_s on 2007-08-13
does /var/log/dmesg have any clues what it's getting stuck on

---

### Post by Roswellgrey on 2007-08-13
Thanks for the reply :)

Unfortunately, all it shows is the large pause timewise between the scheduler load and the next step  i.e the PNP scan.

[   33.606880] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   33.607108] io scheduler noop registered
[   33.607209] io scheduler anticipatory registered
[   33.607307] io scheduler deadline registered
[   33.607420] io scheduler cfq registered (default)
[  552.144223] isapnp: Scanning for PnP cards...
[  552.498550] isapnp: No Plug & Play device found
[  552.550961] Real Time Clock Driver v1.12ac

The rest of the boot process is lovely and clean .... ( and quick !)

---

### Post by Roswellgrey on 2007-08-14
Ooops - the old ones are always the best ....

Whilst searching for more info on this, I happened across an old post regarding USB keyboards; whereas having a USB keyboard can cause this hang.

One USB-> PS2 adapter later .....  Problem resolved .

What threw me was the fact that Suse 9.3 worked fine on this box, and I didn't consider that a USB keyboard and the later kernels could cause this - Oh well, lesson learned :)

---

