---
title: "firefox update menu item greyed out"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by wsx123 on 2007-06-14
I noticed the firefox update menu function is not working.
Is this intentional?  I do not want to be locked into Ubuntu upgrading my browser thank you!b

---

### Post by luvr on 2007-06-14
I believe this is intentional, yes.

Ubuntu installs Firefox from its repositories, so the package manager can keep track of which version of Firefox is installed on your system. Any updates that you install outside of the Ubuntu package management mechanism, cannot be tracked by the package database.

If you want to manage Firefox updates manually, I guess you could uninstall the Ubuntu package of the Firefox product, and install a version that you download from the Firefox site instead. You won't harm your system in this way; the only result will be, that Firefox is no longer registered to the Ubuntu package manager.

I'm not sure about the advantages of manually managing Firefox updates, though--except, perhaps, that you will be able to update directly from the Firefox web site, instead of having to wait one or two days until Ubuntu uploads a new package to its repositories.

---

### Post by bashologist on 2007-06-14
There may be some problems with font rendering when using Firefox from their site, but it's probably safer to use their's since the updates will be quicker.

---

### Post by stchman on 2007-06-14
> **wsx123 said:**
> I noticed the firefox update menu function is not working.
Is this intentional?  I do not want to be locked into Ubuntu upgrading my browser thank you!b

That is exactly what it is.  Ubuntu will upgrade your browser every time a new patch comes out.  That is just the way it is.  They update FF within a few days of Mozilla putting out the update.

---

### Post by wsx123 on 2007-06-15
Thanks, I'm using this on a laptop to try out Ubuntu. I will let things run the course and see how well Ubuntu is at Updating things.
I use a standalone version of Firefox on my desktop and it updates very fast.

---

### Post by stchman on 2007-06-15
> **wsx123 said:**
> Thanks, I'm using this on a laptop to try out Ubuntu. I will let things run the course and see how well Ubuntu is at Updating things.
I use a standalone version of Firefox on my desktop and it updates very fast.

As I said Ubuntu updates FF within a day or so of patch releases.

---

### Post by rodtempleton on 2007-06-15
I noticed this as well when I installed Ubuntu last night.  The current installed version of Firefox is 1.5, but I would imagine that a 2.x build would be available for Linux by now.  Or should I just leave it and let it update in its own time?

Cheers,
Rod

---

