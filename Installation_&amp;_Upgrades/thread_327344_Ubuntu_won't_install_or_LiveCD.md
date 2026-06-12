---
title: "Ubuntu won't install or LiveCD"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by DarkestOfAll on 2006-12-29
Whenever I try to install Ubuntu (Both 6.10 x86 and 6.06 x86), after I click the "Install or Start Ubuntu" button, it hangs on "mounting root fs" and after about 5 minutes, it exits back to a black screen. About every minute 8 errors come up. "error on device hdc, logical block 0 to 7 and then 0 again." After some research, I've found that device hdc is the cd-rom drive. I've checked the isos, burned all the discs at 2x, and checked the discs for defects (which came up as no defects). ](*,) :confused: :mad: ! Help would be greatly appreciated :) .

---

### Post by Soarer on 2006-12-29
It sounds like the CD-ROM may not have a driver. Could you tell us what machine you are attempting to install on, please?

Also, are you using the 'desktop' CD or the 'Alternative' CD. I find the latter works when the former sometimes doesn't.

---

### Post by DarkestOfAll on 2006-12-29
I'm using a DELL Dimension 4600C with an NEC ND-5100 ATAPI drive. I'm burning the Alt CD as I type so I'll see how that works out.

---

### Post by DarkestOfAll on 2006-12-29
Should I use OEM or text mode?

P.S. I'm trying to install tonight so if I don't get a reply by like, 8:30, I'll just use the text mode.
:D

---

### Post by raul_ on 2006-12-29
Try pressing F6 once the ubuntu logo appears...that should give you a command line - that's the boot command. Try adding "noapic nolapic" to the end of that line, and press enter

---

### Post by raul_ on 2006-12-29
i also found this:

> **xavier_m said:**
> I had the same problem with disks I burnt, and not only with ubuntu, also with other distributions. I replaced de cd-writer, the hard disk,  a spent maybe 10 hours testing what was going wrong. 

Finally I discovered that in my case the problem was the way I burnt the cds (from xp!),... windows....

To solve it I followed the instructions in [BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto") and used InfraRecorder. The most important detail is to choose raw96r as method for burning the iso image (and it isn't explained in the help page). You can also compare the hash with hashtab.

Probably the problem is only the way you burn your cds, too!! (nero shows track-at-once by default...)  grrrrrrr.

Hope it helps, regards,
Xavier

---

### Post by DarkestOfAll on 2006-12-30
The CD was burnt in Linux so I had no problem :). Thanks all of you for all your advice, every piece helps. I'm typing this from my newly installed Edgy system :-D . Once I used the Alt CD, everything went as smooth as it ever could.
Thanks again!

---

