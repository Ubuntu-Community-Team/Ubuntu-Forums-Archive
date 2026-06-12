---
title: "Looking for package info"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2012-05-01
Is there a URL to access a web site (preferrably an official Ubuntu/Canonical one) where each different package has its own page describing the package, with a search mechanism that searches packages in all aspects?  This would be like a web equivalent to package manager but with a decent UI/UX.

---

### Post by drmrgd on 2012-05-01
Are you looking for something like this?

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Skaperen on 2012-05-02
No.  The descriptions just aren't there on that one.

---

### Post by drmrgd on 2012-05-02
Hmmm...sorry that didn't help.  That's about the best resource I could think of since it not only has specific package information for each release, including all libraries necessary and whatnot, but also has link-outs to homepages for many packages, screenshots, and such.  Maybe someone has a better suggestion of something with more information related to what you're looking for.

---

### Post by Skaperen on 2012-05-02
> **drmrgd said:**
> Hmmm...sorry that didn't help.  That's about the best resource I could think of since it not only has specific package information for each release, including all libraries necessary and whatnot, but also has link-outs to homepages for many packages, screenshots, and such.  Maybe someone has a better suggestion of something with more information related to what you're looking for.
It actually looks like they used to have more info but now they don't.

Compare this page ...
[http://packages.ubuntu.com/lucid/openipmi](http://packages.ubuntu.com/lucid/openipmi)

to this page ...
[http://packages.ubuntu.com/precise/openipmi](http://packages.ubuntu.com/precise/openipmi)

And the search mechanism is goofed up.  Searching for a string in the lucid description, under precise, yields wrong packages that don't have anything like that.

They should hyperlink the package name, not the section name, when going to the package page.

The reason I asked all this was that I was thinking of making a web area like this.  If I did, it would certainly be better than this one.  It would include the descriptions for one thing.

---

### Post by kostkon on 2012-05-02
Something like this? [http://apps.ubuntu.com/]("http://apps.ubuntu.com/")

---

### Post by Skaperen on 2012-05-02
> **kostkon said:**
> Something like this? [http://apps.ubuntu.com/](http://apps.ubuntu.com/)
Big search fail on that one, too.  I did a search for "monitoring and remote management of devices" which should have found just a few packages (mostly IPMI stuff ... but I'm intentionally doing a search as if I didn't know the name IPMI to validate the search engine) ... it finds over 10000 packages.  A few samples have nothing like that string.

Also, going to an app page does not show what section one should have looked in.  This site has fewer sections than the other site.  It's unclear here where to find many kinds of packages.  I suspect the UI here is intended only for desktop apps, though its database is probably the full repository.

There's no "big list" to browse packages.

---

### Post by Skaperen on 2012-05-02
Also, there is an aspect of the user interface on this apps.ubuntu.com site that makes me wonder just what it is that webmasters designing this have in mind.  When you go to a section like "Sound & Video", it starts out by showing a list of apps.  But it chops the list of 396 apps into 20 per page.  The bad aspect here is that this doesn't help.  It only makes it harder.  Either listing all 396 on one page -OR- listing just as many as will fit on the page (Javascript can do this).  Instead, with this messy arrangement, one has to alternate between scrolling and clicking on next to scan through the list by eye.

A quick scan of all those apps sections shows none more than 1000 packages, so a page listing ALL apps is still practical to at least give as an option.

It is cute that they have all these icons.  I wonder where I can get those when (if) I decide to make a better package directory page.

---

