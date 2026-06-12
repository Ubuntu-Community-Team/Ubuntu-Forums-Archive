---
title: "Server install not working"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by Katana24 on 2011-04-11
Hi - Im trying to install the 32bit Ubuntu Server OS on a computer I recently received. I burned an installation disc from the website and fired it in and set the BIOS to boot from the CD first. All is well until what seems to be the last step when it tells me that the HD will be partitioned. It just seems to stick at a blue-screen and won't go any further.

I left it in this state for a couple of hours and it didn't move from it which seems to me like there's absolutely to progress. I have two questions: does the computer have to be connected to the network via an ethernet cable? Or does it matter that it isn't connected to any computer at all because the installation should occur regardless of connection or not. 

Cheers

---

### Post by mörgæs on 2011-04-11
It is highly recommended to have a wired connection while installing, but in this case I doubt that it will solve the problem.

You could try to erase the hard drive(s) with Killdisk before trying again.

[www.killdisk.com](www.killdisk.com)

---

### Post by Katana24 on 2011-04-12
I tried to connect it to the ethernet cable and yes it did fail. I didn't really expect it to succeed but it was worth a shot.
Well morgaes the actual hard drive in the computer is completely clean. It was wiped before I installed it into the computer. 
Any ideas?

---

### Post by mörgæs on 2011-04-12
We need some more observations here.

Can you install a desktop 10.04.2 and / or 10.10? 
Does the alternate install work? 
Does the mini.iso? 
and so on.

---

### Post by Katana24 on 2011-04-12
I tried using the 64 bit edition but it wasnt the correct kernel. I want the computer to function as a server but if a desktop edition would help solve the problem then I'll try it - should i install a desktop edition for diagnostic reasons?

---

### Post by mörgæs on 2011-04-12
yes.

---

### Post by Katana24 on 2011-04-13
Tried installing the 32bit Desktop edition of Ubuntu. It failed to - it got to the screen for inputting your username & password and froze - I tried this several times and it failed each time. 

This either means that all the versions of Ubuntu that I have downloaded have some fault hidden within in them that only I seem to be getting, unlikely, or it could be a hardware issue. 

Correct me if you think Im wrong - the hard-drive that I used appears to be working correctly as does the other hard-drive that I tried - both are completely wiped and clean - as they were de-banned to American Ministry of Defence Standard; i.e. this isn't a HD problem?

What other components can effect the installation of an OS? Am I wrong?

---

### Post by mörgæs on 2011-04-13
A system freezing can have several reasons. You could try

- selecting the self-test from the menu when booting the CD
- selecting the memory test from the same menu (might take long)

Have you also tried the alternate install?

---

