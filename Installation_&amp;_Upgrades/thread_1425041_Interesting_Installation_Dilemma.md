---
title: "Interesting Installation Dilemma"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by briansrapier on 2010-03-08
**[SOLVED]** So I have this Dell Latitude LM laptop that is in perfect condition except for the fact that it has W2K installed with a corrupted iexplore.exe which causes the screen to go blank and the system to lock up about 10 seconds after login. I'd like to install something else rather than try to fix windows.

Here's the dilemma: the BIOS only supports boot off the hard drive or floppy, but it only has a CDROM - no floppy. It also lacks and network, modem, or USB ports.

I thought about a Wubi install, but the Wubi system requirements call for 5GB of free space and I have less than 1/2 that available.

Any one have other ideas on how I might be able to tackle this issue? I'd hate to throw it back in the closet...

Thanks.

---

### Post by snowpine on 2010-03-08
Does the computer even meet the Ubuntu system requirements?

> Recommended minimum requirements

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution
    * Sound card
    * A network or Internet connection

It might be time to retire that old computer and get something new (or new to you). Where I live (New York) you can find an old Pentium 4 on Craigslist for under $100 that will easily run Ubuntu.

---

### Post by briansrapier on 2010-03-08
I'm trying it because I rather love a challenge. Also, there are other Linux variants that I've used (Puppy, Knoppix, Wolvix, etc) that actually run very well on old hardware.

Ah, well. I guess I'll keep looking.

---

### Post by briansrapier on 2010-03-10
After doing some digging, I found a number of alternate bootloaders that I could install. I tried "Smart Boot Loader", but didn't have any success. However, with PLoP, I was able to boot up and select CDROM from the PLoP menu. 

It took a couple of tries, but I was able to boot into the Puppy installer. (I realize this isn't much relevance to Ubuntu, but I'm adding my experience for reference by others.)

It took some playing to get it to work properly and one of the issues I encountered is documented in the [PLoP forums]("http://forum.plop.at/index.php/topic,174.msg1486.html#msg1486").

---

