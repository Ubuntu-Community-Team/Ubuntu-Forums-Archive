---
title: "Swapping home directory between Precise and Lucid"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by henrylaw on 2012-06-06
Currently running Lucid and plan to upgrade to Precise.  I'll do a fresh install on a separate partition; I'll leave Lucid as the default while I'm working on the upgrade as I can see it will take some time, and flip GRUB when everything's ready.  /home is a separate partition already so I'll mount it on both versions of the OS.

What worries me is that while I'm working in Precise some of the programs I run will update their .whatever files to the latest release of whatever-it-is (OOO to Libre is just one example; others might be GIMP, Firefox, abcde etc); I foresee problems when I boot back into Lucid because the stored information will be from later levels.

Is this a realistic fear?  Is there anything I can do to minimise it?  Interrupting the user (my wife, rightly intolerant of technical annoyances) is something I'd like to avoid ;)

---

### Post by darkod on 2012-06-06
Sharing /home like that between different versions is not recommended. You said it yourself, the two OSs will have programs with different version numbers, etc. You can't expect them to share the same location for the settings/configuration and work fine.

---

### Post by henrylaw on 2012-06-06
Yes, well I feared that but wondered if someone who knows more than I do could confirm it.

So let's say I take a copy of /home (or at least some of it) and work on the new Precise system for a bit, the problem is that during the periods in which I boot back to Lucid (for normal work) -- which might be over several days -- the "active" /home will get out of step with the one I'm working on.  Sounds difficult to get round.  Hmmm. :confused:

Would it work if, at the final cut-over, I copied across everything that wasn't in, or under, a hidden directory?  That assumes that all the sensitive configuration-type stuff is under such a directory.

---

