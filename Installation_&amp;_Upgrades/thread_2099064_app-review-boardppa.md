---
title: "app-review-board/ppa"
date: 2012-12-28
forum: Installation &amp; Upgrades
---

### Post by den_ on 2012-12-28
My system tries to upgrade lintian package and according to Software Updater the update comes from app-review-board/ppa.

Actually Software Updater lists the package under "Other updates (LP-PPA-app-review-board). Does this means it comes from the above mentioned repository?

If yes that looks strange to me, because I do not have that repository installed/added.

Could someone please explain what is happening here?

Many thanks in advance

---

### Post by den_ on 2012-12-28
Ok, aptitude download shows that package is downloaded from [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/), and I have that (extras) repo enabled. This is a little confusing, since there is an app-review-board repository, and software updater mentiones that name as a source or whatever.

---

### Post by vasa1 on 2012-12-28
Someone else asked a similar question today, IIRC. I'll try to find it.

---

### Post by meow9th on 2012-12-28
I think that update screwed up my update manager settings.

Out of reflex, I hit 'update' and only after doing so did I realize that that 'other updates' from a PPA was highly suspicious, as I never added any PPAs to my software sources. After the update was complete (and two new packages, libtext-levenshtein-perl and t1utils, were installed because, I assume, they were dependencies for lintian), I tried to check my software sources, and that's when I realized that I couldn't open the settings dialog for update manager. I tried re-installing (apt-get install -reinstall) all packages that had to do with update manager or software center, but no dice. Working on a clean install now.

EDIT
I tried to access the settings menu again just now (on the old install) and it works. Go figure.

---

### Post by vasa1 on 2012-12-29
Just FYI, this is where I saw it: [Strange update in Lubuntu 12.10 32-bit]("https://lists.ubuntu.com/archives/lubuntu-users/2012-December/003267.html")

---

### Post by den_ on 2012-12-30
> **vasa1 said:**
> Just FYI, this is where I saw it: [Strange update in Lubuntu 12.10 32-bit]("https://lists.ubuntu.com/archives/lubuntu-users/2012-December/003267.html")

Thanks, strange that no one responded to it. It looks like some packages from extras repo are actually from app-review-board.

---

