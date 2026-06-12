---
title: "(Sony Vaio PCG-5312) /bin/sh: can't access tty; job control turned off"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by loopiv on 2007-01-26
Trying to install dapper (or even edgy) on a Sony Vaio PCG-5312. [B]<--- Correction, it's a PCG-Z505LSK
[/B]
Got past the error in the subject by hitting F6 (boot options) and putting this before the "--":

ide2=0x180 nopcmcia

Got this from the Knoppix cheat codes.  However, no the install is stuck at:

* Starting kernel event manager...

Any ideas?

---

### Post by loopiv on 2007-01-26
So I removed quiet and splash, and it seems to be stuck on the cdrom drive.  For some reason, it shows up as busy and times out.  I've tried both Edgy and Dapper.

The odd thing is that the install starts pcmcia even though I have the nopcmcia option in place.  I get

hde: status timeout: status=0xff { Busy }

and then a bunch of timed-out and failed opcode messages.

CentOS seems to install just fine with the "ide2=0x180,0x386 nopcmcia" options.

Vip

---

