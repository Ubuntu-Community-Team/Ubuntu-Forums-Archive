---
title: "OpenOffice and QuickStarter Both Screwed Up"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2011-02-05
Update Manager tells me it has updates.  So I close what I am doing with VirtualBox and a Windows Client and I tell the Update Manager to go ahead.  But it stops, says I've got OpenOffice and QuickStarter both
running.  Not so, at last not to my knowledge.  I try again, and it tells me I have a broken package, and to use the 'Broken' filter to find it.  Where is the 'Broken' filter?  And even if I work that out, what should I do about a "broken" package?  Fix it with glue, or will nails hold?

So I look online.  Only references to "Broken" packages are with respect to Windows.  Windows is a shut down client, and VirtualBox has been shut down.  Now what?  So I try the recovery mode on a reboot.  This reports I have 15 broken packages, all to do with OpenOffice.  I select Fix Broken Packages, and it keep stopping to tell me that OpenOffice and QuickStarter are both running, and I need to deal with that.  How? A restart and effort to fix broken packages did no good.

I look online again, and this time I run down where someone writes you can follow a link, and what you get there will do the trick.  Only the link goes nowhere, so it has been moved or deleted.

Alright, at this point I have to admit I need help.  Can't bother with a trouble ticket, none of them have done a thing for me.  Why wait six months for an email where someone wants more details when there is a better chance of a response on the forums?  And in a lot less time as well.

---

### Post by mörgæs on 2011-02-05
What happens if you reboot the system and run the following commands?

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by oldefoxx on 2011-02-10
I got the problem resolved, somehow.  What I mean is I kept tinkering, trying to uninstall the packages, reinstall then packaged, reboot, and each time I had a go at it, I seemed to knock another package free from its broken state.  Sounds easy, but there wasn't any real rhyme to it.  A Day later I followed some manual instructions to upgrade 9.10 to OpenOffice 3.2.
which seemed to work, but I got 3.0 instead.  So I ran them again and I was up to3.1.  A third try and I was up to 3.2.

The problem seemed to deal with registration and the fact that Linux had OpenOffice and QuickStarted both flagged as being open and active.  The install and uninstall processes were both blocked by this, and reboots did not change these states.  Maybe only a small problem, but sure got in my way.

---

