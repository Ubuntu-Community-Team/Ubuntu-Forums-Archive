---
title: "Does enabling multiverse of Groovy in Ubuntu 20.04 break the system while updating?"
date: 2020-09-18
forum: Installation &amp; Upgrades
---

### Post by drpjkurian on 2020-09-18
Hello friends
I'm trying to install the software GNU PSPP from the source in my machine that is running on Ubuntu 20.04. There is no official package for this software in the repositories due to various reasons. I realized that a dependency package named 'spread-sheet-widget 0.6' is a prerequisite to installing the GNU PSPP. Unfortunately, this version of the package is available only in the multiverse repository of the Groovy. Hence my question is, does enablement of the multiverse repositories of Groovy break my system while updating?

---

### Post by CelticWarrior on 2020-09-18
Yes, it will.

That said you're to try. Maybe safer to enable the repo, install what you need then immediately undo that change.

---

### Post by tea for one on 2020-09-18
> **drpjkurian said:**
>  Unfortunately, this version of the package is available only in the multiverse repository of the Groovy. Hence my question is, does enablement of the multiverse repositories of Groovy break my system while updating?

If you enable the Groovy repository, locate the [COLOR="#0000CD"]specific[/COLOR] package you need and install it, you will probably be OK.

Then, I would advise (as mentioned by **CelticWarrior**), that you immediately remove the repo to prevent other Groovy packages breaking your system in the future.

In the past, I have done this with Shotwell (to correct a known bug with the slideshow) and no harm was done.

Again, proceed cautiously and, in the event of a problem, it will be easy to identify and remove the single package if it corrupts anything else unwittingly.

---

### Post by QIII on 2020-09-18
Let's remember that things are in the Universe repository because they are not elsewhere in the Ubuntu repos.

Everything in Universe is packaged and tested by what Canonical calls a MOTU -- Master of the Universe.  These are volunteers who test packages against Ubuntu and include them in Universe when they are as ready as they can be.  It may take time to test them against a new release, so that is the primary risk.  But they won't likely conflict with anything in the other repos since the application won't be living there.  But you will want to stay away from anything labeled "ugly".

As far as whether or not it will break your system:  There is a far smaller chance of that than in making an error in building it from source -- or the provider of the source package not having tested it against a specific release of a specific distro.

---

### Post by drpjkurian on 2020-09-18
I extend my gratitude to everyone who advised me. I appreciate it. I solved the dependencies issue by scaling down the version of GNU PSPP. Hence it does not require any dependency package from Groovy. I installed the software from the source without any issues.

---

