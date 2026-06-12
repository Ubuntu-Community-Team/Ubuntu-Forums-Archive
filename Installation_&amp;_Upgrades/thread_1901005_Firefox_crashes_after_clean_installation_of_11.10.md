---
title: "Firefox crashes after clean installation of 11.10"
date: 2011-12-27
forum: Installation &amp; Upgrades
---

### Post by helmarfernandes on 2011-12-27
Ok guys.

Everything´s working fine, but... Firefox that is crashing when I try to browse any website.

Everything says that this is a common error for new Oneiric Ocelot installations...

I think that is this one:
[http://support.mozilla.com/en-US/questions/899653](http://support.mozilla.com/en-US/questions/899653)

Does anyone report some solution for this problem?

---

### Post by darkod on 2011-12-27
I have a clean install and it works fine without touching anything. Maybe it helps that I have separate /home partition and the FF profile is of course inside.

The link you posted looks like only the question unfortunately, no answers yet.

---

### Post by darkod on 2011-12-27
Does it happen all the time or only on some pages? Do you have any home page set that should open by default when starting FF? If yes, which page is it?

It might be related to some plugin like flash, etc.

---

### Post by GhostOfTomJoad on 2011-12-27
I had the same problem.  

$ sudo apt-get update
$ sudo apt-get install firefox

Worked to resolve my issues.  I'm assuming you already tried this but, just in case, it fixed it for me.

---

