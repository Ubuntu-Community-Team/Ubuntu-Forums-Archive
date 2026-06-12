---
title: "Synaptic, Installed (manual)"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by exploder on 2009-09-04
After installing updates today, I now have Installed (manual) in Synaptic and it is loaded with entries. Is anyone else seeing this?

Edit: The "Installed" and "Installed (manual)" sections are identical. What's going on with Synaptic?

---

### Post by exploder on 2009-09-04
Anyone?

---

### Post by qamelian on 2009-09-04
I have 1391 packages in Installed (manual). I have over 1600 in Installed.

---

### Post by VMC on 2009-09-04
> **exploder said:**
> After installing updates today, I now have Installed (manual) in Synaptic and it is loaded with entries. Is anyone else seeing this?

Edit: The "Installed" and "Installed (manual)" sections are identical. What's going on with Synaptic?

Yes, I'm seeing it, but I'm not sure if I'm not suppose to see it. I don't see the problem.

---

### Post by taavikko on 2009-09-05
> **exploder said:**
> After installing updates today, I now have Installed (manual) in Synaptic and it is loaded with entries. Is anyone else seeing this?

Edit: The "Installed" and "Installed (manual)" sections are identical. What's going on with Synaptic?

It's always good idea to check the changelogs...
```
synaptic (0.62.7ubuntu3) karmic; urgency=low

  * common/rpackagelister.cc:
    - add prefixes for "name" and "section" in the quick search
      This allows "name:apt" or "section:devel" searches
  * debian/control:
    - recommends gksu|kdebase-bin (kdsu is fine too)
      closes: #442421
  * add filter for manual installed packages (LP: #122047)
  * fix typo (thanks to Florentin Duneau), closes: #542122
  * po/pt_BR.po:
    - updated translation, thanks to Sergio Cipolla
      (closes: #532473)
  * common/rpackage.{cc,h}:
    - fix potential segfault

```

Specially the section: **add filter for manual installed packages**

---

### Post by exploder on 2009-09-05
Thanks for all of the responses on this!

---

### Post by Schrotthaufen on 2009-09-05
Not only manually installed but also recently upgraded packages are marked as "Installed (manual)"

---

### Post by forumache on 2009-09-08
> **VMC said:**
> Yes, I'm seeing it, but I'm not sure if I'm not suppose to see it. I don't see the problem.

The problem is, in my opinion, that those packages are displayed as "Installed (manual)". I did not manually install those.

Of course, maybe due to my bad command of English language, "manual" means something different than what I think it means. In this case, anybody, please explain the other sense ... Thanks in advance.

---

### Post by zanglang on 2009-09-11
> **forumache said:**
> The problem is, in my opinion, that those packages are displayed as "Installed (manual)". I did not manually install those.

Of course, maybe due to my bad command of English language, "manual" means something different than what I think it means. In this case, anybody, please explain the other sense ... Thanks in advance.

Just noticed this as well, with core packages like 'cron' and 'synaptic' in the manual installed list. My system has gone through quite a few manual 'aptitude dist-upgrade's though, so it's possible that the auto flag got set that time.

When I get time I'll probably go through the list and do 'aptitude markauto' on the packages I can identify.

Edit: Noticed that under the Package menu was an 'Automatically Installed' checkbox option, so I just marked all 1200+ 'manual' packages, and progressively checked off about ~100 of them as manual again, then uninstalled the rest of the stuff. In the end took about 15 minutes, but freed up about 400mb, so i'm glad. :)

---

### Post by TheForkOfJustice on 2009-09-21
Trying to change the status of the following packages: 

ubuntu-desktop
ubuntu-standard
ubuntu-minimal

to 'Automatically Installed' just prompts to remove your whole damn system.

Something aint right here.

---

### Post by TheForkOfJustice on 2009-09-21
Suspicion confirmed.  Tried removing everything that was 'auto removeable' in Synaptic and it uninstalled the whole system. Useless now.

Going to check if Alpha 6 has this issue as I was using an up-to-date Alpha 5 on that occasion.

---

### Post by VMC on 2009-09-21
> **TheForkOfJustice said:**
> Suspicion confirmed.  Tried removing everything that was 'auto removeable' in Synaptic and it uninstalled the whole system. Useless now.

Going to check if Alpha 6 has this issue as I was using an up-to-date Alpha 5 on that occasion.

We live and learn don't we. I did that once, but not related to this subject. I thought at the time it was an innocent removal. I'm not even sure at the time if I was even warned of the consequences.

---

### Post by TheForkOfJustice on 2009-09-21
> **VMC said:**
> We live and learn don't we. I did that once, but not related to this subject. I thought at the time it was an innocent removal. I'm not even sure at the time if I was even warned of the consequences.

Well I was pretty sure it would happen.  It's an alpha it's supposed to be crushed :P

Anyway, using Alpha 6 now and the problem persists.  Guess I'll look at it some more tomorrow.

---

### Post by TheForkOfJustice on 2009-09-21
Okay, last bit before bed: a revised list of packages that will cause necessary system packages to become autoremoveable in Synaptic.  

couchdb
language-pack-en
language-pack-en-base
language-pack-gnome-en
language-pack-gnome-en-base
language-support-en
language-support-writing-en
linux-generic
openoffice.org-hyphenation
openoffice.org-hyphenation-en-us
openoffice.org-thesaurus-en-au
openoffice.org-thesaurus-en-us
ubuntu-desktop
ubuntu-minimal
ubuntu-standard

My methods:

I used the 'Package'>'Automatically Installed' function on each package.  If they appeared as 'autoremoveable' afterwards, I undid what I did which sent them back to the 'manual' section.

The ubuntu-standard, desktop and minimal packages suggested the most system packages be autoremoved likely because they are very complex metapackages with lots of depends. The other packages usually just offered themselves and nothing else.

---

