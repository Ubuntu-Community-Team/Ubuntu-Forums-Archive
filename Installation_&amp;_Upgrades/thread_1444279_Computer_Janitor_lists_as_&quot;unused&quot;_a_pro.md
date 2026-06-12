---
title: "Computer Janitor lists as &quot;unused&quot; a program that I'm pretty sure gets used often"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by SnickerSnack on 2010-04-01
Hi all,

I ran the Computer Janitor to clean things up a bit, and found that the list of "unused" items is pretty long, ~141.

Among the items listed, I found Maxima, Pari-GP and Gnuplot, which are used by Sage, which I use all the time.  Is this possibly a mistake?  I'm currently using a binary form of Sage, rather than the one available via apt, so maybe these aren't currently being used?

Also listed were cpython, ipython and a lot of python-*; does that seem right?

I don't want to follow the recommendations and then have to reinstall things.

Advice?

If it matters: Ubuntu 9.10, Sage 4.3.3 binary

---

### Post by SnickerSnack on 2010-04-02
Bumping.  ~24 hours old and from the 6th page.  I apologize if this breaks any forum rules.  I'll bump again in 24 to 48 hours.

---

### Post by SnickerSnack on 2010-04-19
> **SnickerSnack said:**
> Bumping.  ~24 hours old and from the 6th page.  I apologize if this breaks any forum rules.  I'll bump again in 24 to 48 hours.

Or in two weeks.

bump

---

### Post by bumanie on 2010-04-19
Just uninstall the ones you are sure about. Doing > sudo apt-get autoclean will clean most stuff that is not needed.

---

### Post by oldos2er on 2010-04-19
I've read that Computer Janitor is geared toward newbies who may not know how to fully remove packages or other installed software, but it seems to me that you need some experience to understand what software can be safely removed, and what software can't.

I personally just stick to **sudo apt-get autoremove**, etc.

---

### Post by SnickerSnack on 2010-04-24
> **bumanie said:**
> Just uninstall the ones you are sure about. Doing  will clean most stuff that is not needed.

> **oldos2er said:**
> I've read that Computer Janitor is geared toward newbies who may not know how to fully remove packages or other installed software, but it seems to me that you need some experience to understand what software can be safely removed, and what software can't.

I personally just stick to **sudo apt-get autoremove**, etc.

Thanks for your replies.

I decided a few days ago to go ahead and do autoclean.  Then, I realized that the 'janitor' and apt list those packages as unused not necessarily because they actually aren't, but maybe only because I removed sage through apt, and therefore those packages are marked as "installed because something needed them, but now nothing does".  Well, if I find that some parts of sage are now broken, I'll just reinstall those things that I need...

---

