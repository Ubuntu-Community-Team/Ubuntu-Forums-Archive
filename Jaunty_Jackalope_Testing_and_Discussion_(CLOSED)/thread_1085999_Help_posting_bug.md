---
title: "Help posting bug"
date: 2009-03-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ace214 on 2009-03-03
So, I've encountered some strange behavior with the routine drive check on Jaunty, but I think it may be hardware dependent because I have only seen it on my laptop that is running Jaunty, not on my Desktop.

It seems that if I skip the drive check, it apparently registers as an error and mounts the system read-only, which prevents X from starting, internet connecting, and basically from doing anything. If I reboot and let it run, it boots fine.

How can I diagnose this and make a bug report? I haven't been able to find any existing ones on Launchpad or in this forum...

---

### Post by nyarnon on 2009-03-03
When your drive is checked is is unmounted first so it is expected behaviour if you break into this process that you cannot continue untill the drive is mounted. After you let it runout it mounts the drive and everything starts as usually also expected behaviour. What I didn't understand is id this happens every time you boot?

---

### Post by ace214 on 2009-03-03
No, this only happens when it does the drive check that happens every 30 times you boot or whatever the number is, that takes place on the usplash screen. If I skip it as the dialog prompts is possible by pressing escape, my system the goofy things as described in my first post. If I let it run, then my system boots fine.

---

### Post by nyarnon on 2009-03-03
Well my advice is to let the check run it's there for a purpose. If you boot a lot you can consider to raise the threshold.

---

### Post by ace214 on 2009-03-03
Right, but that's not the point. It's a regression. Previously, if you skipped the check and nothing was fatally wrong, the system would still boot normally.

---

### Post by Nullack on 2009-03-04
If your sure its a regression you can consider tagging your bug with regression-potential to help the QA team identify and manage it

---

### Post by lisati on 2009-03-04
This is my paraphrase of what I think is happening: There is a combination of circumstances where ESCaping out of the disk check is being mis-interpreted as a disk error.

---

### Post by ace214 on 2009-03-04
> **lisati said:**
> This is my paraphrase of what I think is happening: There is a combination of circumstances where ESCaping out of the disk check is being mis-interpreted as a disk error.
That's what I am thinking.

---

### Post by lisati on 2009-03-04
> **ace214 said:**
> That's what I am thinking.

I'm not particularly clued up on the "behind the scenes" stuff that Jaunty uses in its boot-up process, so I'm not even sure what to suggest. Anyone else?

---

### Post by nyarnon on 2009-03-04
I wiçç wait till my next check and see what happens if I can confirm I will enter a bug report.

---

