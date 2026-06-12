---
title: "HP dx5150 clean forces VGA but installer dialogues are too big!"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by Frank-Hamersley on 2006-06-04
Help!

Am looking to move to Dapper after install troubles on Breezy with a HP dx5150 (ATI X200 video integrated) - but seem to be going from the frying pan to the fire!

Although the installer accepts 800x600 (or 1024x768) as video modes at boot time, by the time that the installer is running the screen is locked to VGA only.

This should be no problem except that the installer seems to be configured to assume 800x600 pels are available and therefore I can't see the whole dialogue box - and most importantly the "proceed" etc buttons are out of sight.  Even worse it doesn't provide scroll bars to help out!

So - how can I either force it by boot strings to use VGA sized dialogue boxes or a generic SVGA driver or a character mode install?

Should I look to perform non X install (server?) and then migrate once booted to a workstation config?  Or is running the Breezy and using dist-upgrade a better option (I was hoping to do a clean install if possible)?

No pressure - I just need a solution before Germany 06 kicks off!!!!

Cheers, Frank.

---

### Post by llamakc on 2006-06-04
hit escape and do an old-fashioned text install.

---

### Post by Frank-Hamersley on 2006-06-04
[QUOTE=llamakc]hit escape and do an old-fashioned text install.[/QUOTE]

Yes - I noticed when pressing <ESC> it suggested it would drop back to a text based install - but I tried a couple of times and it didn't make any difference (it was 2:00 AM after a big night previously).

Is there a boot time option that forces a text mode UI from the start?

Cheers, Frank.

---

### Post by llamakc on 2006-06-04
I think the alternate install cd is all text based and doesn't do the LiveCD thing.

---

### Post by Frank-Hamersley on 2006-06-04
Thanks - will try it out later today and report back!

Cheers, Frank.

---

### Post by Frank-Hamersley on 2006-06-05
Yup - all good - Dapper Alternate went like mercury through a ... duck!  Didn't need to spec any boot strings at all.

Still having X problems (with fglrx) but will be elsewhere about them.

Thanks, Frank.

---

