---
title: "Ubuntu not starting after update failed"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by djg10 on 2009-12-06
Hiii,
I upgraded from ubuntu 9.04 to 9.10...all went smooth...first update after upgrade was also fine. The second update failed..update manager hanged & I restarted my pc...after that i m not able to start ubuntu...how can i restore to previous stable state?please help...i dual boot ubuntu with win xp..forced to use xp til i get ubuntu running...!
thanks in advance for help...
Jiten

---

### Post by phillw on 2009-12-06
Hi,

When you boot & you get your List of OS's - try the previous version of the ubuntu kernel - see if that boots.

Phill.

---

### Post by djg10 on 2009-12-06
Hi..
Phill i get 6 options - 4 options to boot to ubuntu,1 for memory test & 1 for win xp...i tried all 4 & also memory check...
memory test is fine..

The error message that i am getting when i load any option for ubuntu is :-
"Mount of filesystem failed.
A maintenance shell will now be started.
codec_read  : codec 0 is not valid."

i think the problem is that since the update failed in between, it has corrupted some important files...
Jiten

---

### Post by phillw on 2009-12-06
> **djg10 said:**
> Hi..
Phill i get 6 options - 4 options to boot to ubuntu,1 for memory test & 1 for win xp...i tried all 4 & also memory check...
memory test is fine..

The error message that i am getting when i load any option for ubuntu is :-
"Mount of filesystem failed.
A maintenance shell will now be started.
codec_read  : codec 0 is not valid."

i think the problem is that since the update failed in between, it has corrupted some important files...
Jiten

I'm minded to agree with you - we have no way of knowing how far the install got.

If you cannot get into recovery mode, then things do look a bit grim.

But, the good news ... all your stuff in ~home should be safe - So I'm minded to boot into LiveCD, check your ~home area is okay, get it backed up & do a clean instal.

That's just MHO, others may dis-agree - But I think your installation is pretty messed up.

/edit This may help you -->  [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

Phill.

---

### Post by djg10 on 2009-12-06
i m soo happy i found the solution to my prob...
as i mentioned it was because some files went corrupt because of restart..that left the system in unstable state...
SLOUTION:
i switched on my pc & let it boot till the error message came...
pressed enter & after the ":" typed "fsck" <enter>
it started diagnosing & asking if i wanted to rectify so & so problems...
i kept on pressing 'y' for yes & it ended diagnosing after all the problems were  rectified.
then i restarted by pressing ctl+alt+del....& BINGO..i m back with ubuntu...!

Thanks 
Jiten

---

### Post by phillw on 2009-12-06
> **djg10 said:**
> i m soo happy i found the solution to my prob...
as i mentioned it was because some files went corrupt because of restart..that left the system in unstable state...
SLOUTION:
i switched on my pc & let it boot till the error message came...
pressed enter & after the ":" typed "fsck" <enter>
it started diagnosing & asking if i wanted to rectify so & so problems...
i kept on pressing 'y' for yes & it ended diagnosing after all the problems were  rectified.
then i restarted by pressing ctl+alt+del....& BINGO..i m back with ubuntu...!

Thanks 
Jiten

That's kewl -- I should have remembered that one - I totally messed up mine once & it was fsck that rescued it for me -- NEVER run fsck on a mounted filesystem -- lol

Phill.

---

