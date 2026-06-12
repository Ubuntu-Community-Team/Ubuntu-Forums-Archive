---
title: "What happened?"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by snakedog on 2006-06-13
I did a clean install from the Ubuntu 6.06 Alternate disk, used my previous partitions for Ubuntu 5.10, formatting those.  I left the Windows partitions intact.  

The install started and seemed to be going ok, then the laptop, a Toshiba A45-S120, slipped into what I thought was some kind of power saving mode.  But I still had a busy hdd indicator light.  Left it alone figuring the install would come out the other side ok.  

Well, it didn't.  After letting it set for a while, the hdd indicator went out, but I still had a blank screen.  No key combo made a difference, so I eventually coldbooted the unit.  

When I rebooted, I got the message "Error loading operating system".

Booted to an XP cd and brought up a command prompt.  Ran "fixmbr" to no avail".

Rebooted to the same XP cd and ran "fixboot".  Got the message it would repair the F: drive.  F:?  There's no such thing.  Had a C: and an E: on my Windows install (cd was D:).

My Windows partitions are still there, as is the data.

What happened?  Any idea of how to get back the original Windows install?  Ubuntu 5.10 ran fine on this thing, but 6.06 brings it down like a house of cards.

p.s. -- how do I turn off the stupid smiley face?  That's ridiculous!

---

### Post by snakedog on 2006-06-13
Got my fingers crossed...went back thru step-by-step everything I did running the install.  Then I recall in manually editing the partition table that I'd toggled the bootable flag (don't ask me why).  Re-edited the partition table and tried another install from the alternative disk.

Ugh, the second install failed, but I've got Windows back.  Looks like the install hung up about the same place...somewhere around 60%, just after OpenOffice.

I'm trying it off the live cd now.

Wish me luck.

---

### Post by snakedog on 2006-06-13
Strange...install went off w/o a hitch from the live cd.  The alternative cd...remains that.  VERY alternative.

We're good here.  Feeling kinda lonesome though.

---

### Post by Herman on 2006-06-14
Hello, snakedog, I'm glad everything turned out okay for you in the end. 
About your 'Alternate' Install CD, I was wondering if you ran an MD5sum check on the downloaded .iso before you burned it?  And also did you use the 'Check CD For Defects' option before you began your install?
A laptop shouldn't be affected by any fluctuations in your electrical suppy since they have a battery, but I still use UPS units all the time for desktops and my laptop both for installing and regular use. We do get some bad electrical disturbances where I live, and reasonably often too, even when there are no lightning storms around.
I don't think it makes any difference whether we toggle the boot flags or not. I used to think they were important, but now I just ignore them.  Has anyone got some information about them, or an opinion?
I think the new LiveCD installer is great, but the 'Alternate CD' I have has proven reliable for me. 
I hope you won't feel alone now, Regards, Herman :D

---

