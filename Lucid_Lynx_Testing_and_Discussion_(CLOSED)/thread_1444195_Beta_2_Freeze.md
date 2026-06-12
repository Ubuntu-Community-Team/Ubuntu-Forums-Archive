---
title: "Beta 2 Freeze"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-04-01
[Beta 2 Freeze]("https://wiki.ubuntu.com/Beta2Freeze") is now in effect. Stand by for ISO testing!

Here's Steve Langasek's [announcement]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2010-April/000697.html") on the [ubuntu-devel-announce mailing list:]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce")

[QUOTE=Steve Langasek]Hello Ubuntu developers,

Two weeks on from 10.04 Beta 1, we are now also 1 week out from 10.04 Beta
2, scheduled for April 8 ([https://wiki.ubuntu.com/LucidReleaseSchedule](https://wiki.ubuntu.com/LucidReleaseSchedule)) -
which means it's time for another beta freeze to start.

During the freeze, all uploads to main must be approved by a member of the
release team [1], so if you have fixes which are important to get in, please
do get in touch as soon as possible.  Uploads to universe require a manual
push through the queue, but are not subject to release management approval.

Issues which are important for the beta release will be tracked by the
release team here:

  [https://bugs.launchpad.net/ubuntu/lucid/+bugs?field.milestone=21447](https://bugs.launchpad.net/ubuntu/lucid/+bugs?field.milestone=21447)

If you have bugs on this list, please fix them at the earliest possible
opportunity, or (in consultation with other developers and the Ubuntu QA
team) un-milestone them if they are not required for beta. If you have
bugs you think should be on this list, talk with the Ubuntu QA team or the
Ubuntu release team about having them milestoned.

Please also do not lose sight of the list of bugs affecting the release as a
whole:

  [https://bugs.launchpad.net/ubuntu/lucid/+bugs](https://bugs.launchpad.net/ubuntu/lucid/+bugs)

Over the next few days, please pay attention to eliminating
inconsistencies in the archive, including:

  [http://people.canonical.com/~ubuntu-archive/testing/lucid_probs.html](http://people.canonical.com/~ubuntu-archive/testing/lucid_probs.html)
    uninstallable packages in main and restricted

  [http://people.canonical.com/~ubuntu-archive/NBS/](http://people.canonical.com/~ubuntu-archive/NBS/)
    obsolete packages which still have reverse-dependencies

Archive administrators should spend time ensuring that any pending
main<->universe component changes have been processed
([http://people.canonical.com/~ubuntu-archive/component-mismatches.txt](http://people.canonical.com/~ubuntu-archive/component-mismatches.txt)).
Developers, if you are waiting for something on this list, please help out
by filing good main inclusion reports.

Thanks,
-- 
Steve Langasek
On behalf of the Ubuntu release team

[1] [https://launchpad.net/~ubuntu-release](https://launchpad.net/~ubuntu-release)
[/QUOTE]

---

### Post by VMC on 2010-04-01
I don't see [**_Bug #530779_**]("https://bugs.launchpad.net/upstart/+bug/530779") listed under *.. do not lose sight of the list of bugs affecting the release as a whole*, and its importance is medium. There several that are listed as either low or undecided.

---

### Post by Irihapeti on 2010-04-01
If one's particular show-stopper bug isn't included (even though it's "high" and "triaged"), what should one conclude from that?

---

### Post by Sslaxx on 2010-04-01
> **Irihapeti said:**
> If one's particular show-stopper bug isn't included (even though it's "high" and "triaged"), what should one conclude from that?
That their priorities are not yours.

---

### Post by jerrylamos on 2010-04-01
Looking at the "High" bugs in the list - there are going to have to be some real breakthroughs before Release.

Two of my four test pc's are unstable with Lucid Beta 1 even with the latest updates.  One has i845 video graphics the other ati Mobility 7500.  I can't reliably use either for work such as downloading a Debian iso without getting sporadic black screen crashes, power off the only way out.  Bryce Harrington says there is some work going on upstream on these bugs.

Oh, well, Karmic is rock solid for me.

Good luck.  Jerry

---

### Post by 23meg on 2010-04-01
> **VMC said:**
> I don't see [**_Bug #530779_**]("https://bugs.launchpad.net/upstart/+bug/530779") listed under *.. do not lose sight of the list of bugs affecting the release as a whole*, and its importance is medium. There several that are listed as either low or undecided.

Since it's an upstream Upstart bug (it has a duplicate in Ubuntu but has no Ubuntu task), it can't be listed among Ubuntu bugs. The upstream one has been filed by Scott himself, so I wouldn't worry about it.

> **Irihapeti said:**
> If one's particular show-stopper bug isn't included (even though it's "high" and "triaged"), what should one conclude from that?

That it's not specifically targeted to be fixed in this milestone; no more or less.

---

### Post by emarkay on 2010-04-01
FWIW, if a user does not have any major issues or has no active bugs, what would be a good way to assist the whole; a location to send them for specific testing - other than ISO and install tests?  It's not practical to attempt to "find bugs to wring out" via a Launchpad search.

There are many of "us" who have had a generally painless Alpha and Beta process, but want to know if can we use our "basically stable" systems to investigate and or test/validate?  (My only issue is the ATI Restricted Hardware, but that's a AMD issue moreso than a Ubuntu issue.)

---

