---
title: "GDM on Lucid is not generating necessary MIT-MAGIC-COOKIE"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by aajax on 2010-10-08
This thread is a follow-on to another which can be found [here]("http://ubuntuforums.org/showthread.php?t=1586702").

On my prior Ubuntu Desktop system (Hardy) GDM is generating MIT_MAGIC_COOKIEs (MMC) for display names that can be used by remote X clients to display on my desktop.  For example, on Hardy this includes an MMC with a display name in the format of "hostname.domain_name:0".  However, on Lucid it seems there is no such MMC.  In fact there is no MMC that could possibly be used by a remote system accessing via TCP.

I've been using X11 with various display managers since long before Ubuntu ever existed.  From what I understand generating MMCs is a fundamantal function performed by a display manager at logon.  A rather surprising change that appears on Lucid is that the display manager (GDM) is actually generating a new XAUTHORITY file on every logon.  I have no idea why but significant usability issues result.  Traditionally users could use the xauth command to generate their own MMCs.  However, the new placement of the XAUTHORITY file creates the need to assign permissions that prevent the user from updating it.  Therefore, Lucid also prevents the user from doing their own solution.  From my vantage point this is a very poor design.  Possibly there are other changes which I haven't been able to discover that correct this deficiency.  However, I've spent considerable effort trying to find such without any luck.

However, I have also discovered that the so called GDM manual found [here]("http://manpages.ubuntu.com/manpages/lucid/en/man1/gdm.1.html") also contains gross inaccuracies and provides a very misleading description when compared to what is actually on my system.  If this documentation accurately describes some version of GDM then it ought to be relabeled accordingly but users of Lucid ought not be referred to it.

In its' present state I cannot use Lucid.

---

