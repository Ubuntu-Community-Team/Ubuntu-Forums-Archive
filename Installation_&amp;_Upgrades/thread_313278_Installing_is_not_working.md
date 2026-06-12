---
title: "Installing is not working"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by Shadic on 2006-12-05
I've burned the ISO onto two different brands of CDs, and at different speeds. (32x and 16x)

The CDs are both 700MB, and I currently have FreeBSD on the system right now.

Some errors:

Recursive die() failure, output suppressed
Kernel panic - not syncing: Fatal Exception in interrupt
BUG: unable to handle kernel paging request at virtual add resss ffffd370

---

### Post by wpshooter on 2006-12-05
TOO FAST. 

Make sure you burn the Ubuntu ISO image at 4x or less.

Then make sure you check the integrity of the Ubuntu ISO image by running the verfication test found on the initial Ubuntu boot screen menu.

Good luck.

---

### Post by Shadic on 2006-12-05
Ran the test, and I burned it at 2X.

Still problems.

EDIT: Incase I was not clear, I burned a new CD at 2X, and then ran the test for errors on the CD. No errors occured, and then I attempted to install Ubuntu.

It errored again, although with a slightly different bit of errors.

They're all addresses of some sort, I'll type up a line or two:

apic_timer_interrupt+x0x1c/0x30 <e01cb87e> intel_i 830_configure+0xfe/ox110 [intel_agp]

---

### Post by wpshooter on 2006-12-05
What are your hardware specs ?

Are you burning DESKTOP or ALTERNATE CD image ?

---

### Post by Shadic on 2006-12-05
Downloading the Desktop version, 6.10.

Not too good at hardware-things, but I can say the following..

I have 512MB DDR SDRAM
BIOS = Phoenix 3.02
Intel Celeron CPU
CPU Speed = 2.93GHz/533MHz
CPU Cache RAM 256KB

Yay for reading things straight from the BIOS.

It is also a Compaq, had XP installed on it, which broke. Now I've got FreeBSD, with KDE on it. I just wanted to make the switch into Ubuntu, because it appears to be a better choice for a Unix-based operating system.

---

### Post by wpshooter on 2006-12-05
Are you going to be using Ubuntu ONLY or are you going to keep any other O/S on the machine ?

---

### Post by Shadic on 2006-12-05
As of now, I only plan to be using Ubuntu.

---

### Post by wpshooter on 2006-12-05
Then I would do this.

Get the **KILLDISK** program and **WIPE** your drive completely clean.

[http://www.killdisk.com/](http://www.killdisk.com/)

Then you may want to give the DESKTOP CD another try and if that still does not work (and it may not) download and burn the ALTERNATE version of Ubuntu and then WIPE your drive again and try installing the the ALTERNATE.  Again make sure you test CD integrity.

Good luck.

---

### Post by Shadic on 2006-12-06
I have done all of that, and when I'm installing it, I get a whole bunch of code zipping by.

It has been doing that for at least half an hour, is this normal, or do I have another problem?

EDIT: I seem to have a different error/problem every time I try and install it. I ran the killdisk thing, as well.

Anyways, I got a good amount of errors this time around, here's what it says:

"unable to handle kernel paging request at virtual address e856026a"

---

