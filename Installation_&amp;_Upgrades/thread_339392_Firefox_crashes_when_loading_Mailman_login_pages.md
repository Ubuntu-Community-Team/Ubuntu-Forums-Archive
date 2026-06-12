---
title: "Firefox crashes when loading Mailman login pages"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by amanda on 2007-01-15
This is a bug that seems to be duplicated all over the place.

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/77859](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/77859)
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/77998](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/77998)
[http://www.ubuntuforums.org/showpost.php?p=1968450](http://www.ubuntuforums.org/showpost.php?p=1968450) <-- This actually describes a different issue, but the comments all talk about the mailman problem.
[https://bugzilla.mozilla.org/show_bug.cgi?id=235336](https://bugzilla.mozilla.org/show_bug.cgi?id=235336)
[https://bugzilla.mozilla.org/show_bug.cgi?id=366110](https://bugzilla.mozilla.org/show_bug.cgi?id=366110) <-- This is the open bug at Mozilla.
[https://bugzilla.mozilla.org/show_bug.cgi?id=290820](https://bugzilla.mozilla.org/show_bug.cgi?id=290820)

Basically after a recent update, Firefox and Galeon both crash completely (close down) when you try to access any mailman admin page.  Possibly when you try to access any page that has a stored password without an accompanying username. The advice on mozilla's bugzilla install is to "please try a mozilla.org build" -- helpful, and yet, not so helpful. I don't know off the top of my head how to install a build that isn't in my synaptic package list. I'm not really sure that I should be doing that, especially since there is no indication in the thread that the source of this advice even understands the issue. We're saying that a security update has broken Mozilla browsers. That is a big deal, and I don't think the solution is for everyone who wants to admin a mailman list to install a non-stable browser. 

I don't know what the solution is. I'm pretty sure that huffing about how this makes me have real doubts about whether Ubuntu is *really* usable is not the solution, either, though.

The short term solution is to rollback your firefox version: 

<code>sudo aptitude install firefox/dapper</code>

Long term, I don't know yet what the solution is.

---

### Post by amanda on 2007-03-07
Update: a fix was released in a recent mailman version.

---

