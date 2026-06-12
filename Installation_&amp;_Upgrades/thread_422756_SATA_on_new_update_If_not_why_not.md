---
title: "SATA on new update?? If not why not"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by socngill on 2007-04-25
Hi guys.

Thinking about coming back to Linux after finding that a few decent media Centre options have sprung up since I last left you all.  Only thing is that I itend to replace my current hard drive with a new SATA II one.  I have read that these drives are not supported and that the get around seems some what long winded.

Is this new updated version of Ubuntu able to recoginise and install directly to SATA drives?  I hope so as these have been around for some time know and for an OS to be unable to install on them seems unbelievable to me.  not sure how Linux can be taken seriously in the open market (ie Dells recent decision) if such basic stuff is not supported.

Don't mean to get anybodys back up, just seems strange if it still isn't supported "out of the box".

Thanks all.

---

### Post by jda1701 on 2007-04-25
Yes.  Feisty uses libata for its storage module.  In fact, Feisty now shows all hard drives as /dev/sd* because of libata.  

I have Edgy installed on a SATA I hard drive and Feisty installed on a SATA II hard drive.

Good luck!

---

### Post by socngill on 2007-04-25
Thanks that's great news!  I think I shall be installing Linux onto my Media Centre PC!  Fed up with Windows Media Centre not supporting mpg4 and the Nero one just insn't up to the job.

Linux it is!

---

### Post by psusi on 2007-04-25
SATA drives have been supported at least as far back as breezy, and I think before that.

---

