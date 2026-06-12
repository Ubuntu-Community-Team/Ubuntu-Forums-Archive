---
title: "installed new over older..."
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by WebJoel on 2008-04-14
A few weeks ago I was having boot-problems with my dual-boot system. I could only boot into Linux (the default start-up on the slave drive). Attempting to boot XP on primary would fail, so I changed BIOS to boot the Secondary HDD before the Primary (to prevent multi-user problems that might occur in my household).
Turned out that the Windoze bootloader was messed-up, and using the OEM 'Rescue disk', I corrected it.
I then changed BIOS back to allow the choice of "Ubuntu Linux" or "Windows XP". Great.
Then, I couldn't get into Ubuntu now... so I downloaded to the XP drive, the current stable version of Ubuntu. It is a slightly newer version that what I was using, -this one is 7.10 I think. Burned the ISO to CD, ran the LiveCD and re-installed to my slave drive as~per usual.

I can now dual-boot to either Linux, or XP. But the Ubuntu load takes WAAAAY longer than it used to, and I see text messages of things being 'ran', including a series of lines something to the effect of this:
Quote:
USB 3-1: device descriptor read/64, error -110
I have six USB ports, and it seems as if all of these are being examined for use, and are failed.

Further messages on the GRUB bootloader for testing include things like:
Quote:
[ 151.973956 ] device not accepting address 5, error -100
[ 167.288519 ] "
[ 182.491176 ] "
.... (and etc)

Now, since this is a 'new install over an old install', I expect to have little to nothing in there worth keeping, so if a re-format and re-install is best, I can do that easily, I suppose. I'd almost rather format the slave-drive and start over, -but is there a 'corrective action' that can be taken first to try to remedy this situation?
I don't so much mind that the USB aren't being recognized and thus non-functioning, but it's the WAIT to boot that is most annoying. It takes like 5-minutes (or a bit less) to load Ubuntu. I should and always has, loaded faster than XP on the primary...

---

