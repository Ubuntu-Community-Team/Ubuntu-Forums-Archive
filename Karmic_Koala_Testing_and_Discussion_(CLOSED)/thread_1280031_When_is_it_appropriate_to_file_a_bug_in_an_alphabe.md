---
title: "When is it appropriate to file a bug in an alpha/beta release"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2009-10-01
Hi

What comes to mind is,since an alpha is a work in progress,many of the minor things we see will be probably fixed in forthcoming updates ,some of them coming up in a couple of days.

For example i filed a bug where boot would not go forward without a network connection,but it got fixed same day with an update.But i ended up cluttering launchpad with a bug report.

Iam looking for advice on when and why not to file bugs.


thanks.

---

### Post by SuperSonic4 on 2009-10-01
I would go with reporting any bug that is not fixed or is not said to be fixed within 24 hours of you noticing it

---

### Post by 23meg on 2009-10-01
It's *always* appropriate to file a bug in the development branch, at any point, as long as the issue you're encountering is reproducible. It's not a good idea to assume it's already known.

Your not wanting to clutter the bug tracker with duplicates is of course appreciated; if you strongly suspect that the issue you're about to report has already been reported, it's a good idea to do a search for existing bugs before reporting, even though Launchpad will show you possible duplicates after you submit your title. You may also want to start a thread here, and do a forum search, to learn if others are encountering it.

---

### Post by diesch on 2009-10-01
Always report bugs you find. If they get fixed by an update later you can add a comment saying which package version fixed it.

---

### Post by Seventh Reign on 2009-10-01
Linux isnt like Windows where there is a huge trillion dollar company producing the system.  Canonical may produce Ubuntu, but essentially it is built and maintained by you and me and everyone here.

Filing bugs is how the developers know they are there.  If you dont file the bug, they wont know about them, therefore they wont be fixed.  Alot of people might think "Well someone else probably already reported it so there's no point in me doing it too".  Those people are the reason there are still bugs in the final releases.

So search Launchpad and if your bug isnt already listed, file every one you find, no matter how trivial they may seem.

---

### Post by Longinus00 on 2009-10-01
You can always change the status of the bug to "invalid" if it gets fixed from an update.

---

### Post by 23meg on 2009-10-01
> **Longinus00 said:**
> You can always change the status of the bug to "invalid" if it gets fixed from an update.

Or "Fix Released", if you can ascertain (by looking at changelogs, corresponding with developers etc.) that it *was* a legitimate issue and got fixed. Either way, it will no longer appear in searches and index views by default.

It's always a good idea to keep an eye on the bugs you've filed and update their status when appropriate (just don't confirm your own bugs!).

---

### Post by rajeev1204 on 2009-10-01
> **23meg said:**
> Or "Fix Released", if you can ascertain (by looking at changelogs, corresponding with developers etc.) that it *was* a legitimate issue and got fixed. Either way, it will no longer appear in searches and index views by default.

It's always a good idea to keep an eye on the bugs you've filed and update their status when appropriate (just don't confirm your own bugs!).

Thank you for your replies.I appreciate it.I plan to be more active triaging with bugs,so this will help.Just started this a month ago but did make some mistakes while triaging.

Also,how does one correspond with the developers?

rajeev.

---

### Post by hanzomon4 on 2009-10-01
File whatever bug you want... whenever you want. If it's a duplicate you'll know before you actually finish reporting it because lauchpad automatically searches for bugs similar to yours and asks if "this" is the bug you're trying to report. Never assume that someone knows about a bug if you haven't reported it.

---

### Post by 23meg on 2009-10-02
> **rajeev1204 said:**
> Thank you for your replies.I appreciate it.I plan to be more active triaging with bugs,so this will help.Just started this a month ago but did make some mistakes while triaging.

You're welcome; let me know, and/or stop by in #ubuntu-bugs in Freenode (IRC) if you need any help.

> **rajeev1204 said:**
> Also,how does one correspond with the developers?

Through bug comments, on [IRC]("https://help.ubuntu.com/community/InternetRelayChat"), via [the mailing lists]("http://lists.ubuntu.com/").. depends on the purpose and context.

---

