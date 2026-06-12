---
title: "Install hangs at hardware drivers"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by YtseWolf on 2007-01-24
Hey all,

    I'm trying to install Ubuntu on my i386 machine (Intel P4 3.06 GHz), and (generally) when it gets to the installing hardware drivers part, it hangs, although I've seen it hang at other stages of the liveCD bootup process.  I'm not sure what's wrong, because there's no output before it hangs.  I can tell it's hung because the keyboard stops responding (caps/num/scroll lock do not toggle LEDs, and ctrl-alt-del does nothing),  and the CD eventually spins down with no further disk access.  I was able to install Debian, so I think my hardware is OK (no CPU overheating, bad RAM, etc).  I've taken out extraneous hardware, and combed through my BIOS, and I can't find anything that looks out of place.  Any ideas?  Thanks!

-Ytse

---

### Post by taurus on 2007-01-24
1.  Did you check the integrity of the ISO image before you burned it?

2.  Did you burn it at a slow speed like 4x?

3.  Did you scan the CD first before you picked the first option to run/install on the menu when you first booted the LiveCD?

---

### Post by YtseWolf on 2007-01-24
I did scan the CD from the install menu before attempting the install, and it reported no problems.  I will re-burn the image at a lower speed even though my drive and media will work up to 16x and I burned at 12x.  My ISO burning software (NTI CD-Maker) does not appear to have an option to check the integrity of the ISO, but I have used my 6.06 CD on  another machine and it worked fine.  I see the same behavior with both 6.06 and 6.10.  I also have two CD drives in the target machine and I get the same result in each drive.  Is there a utility you can recommend to check the ISO?  Thanks.

-Ytse

---

### Post by taurus on 2007-01-24
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by YtseWolf on 2007-01-24
After ripping even more hardware out of my machine and shutting devices down in the BIOS while waiting for the verified ISO to burn at 4x, I have it narrowed down to a NIC or the sound device.  Thanks for your assistance.

---

