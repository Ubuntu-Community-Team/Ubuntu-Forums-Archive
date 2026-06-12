---
title: "Should we file bugs against apps not following XDG specification?"
date: 2008-05-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bou on 2008-05-21
Hi,

I've noticed that some apps have started moving their data and configuration files to ~/.local/share and ~/.config.

Is that a new standard? What's its importance? Should we file bugs against apps that are not following it, e.g. rhythmbox? If so, what would the rational be?

I for one would love to get rid of all those .configuration folders in my /home.

---

### Post by 23meg on 2008-05-21
That's the [XDG Base Directory specification]("http://standards.freedesktop.org/basedir-spec/basedir-spec-0.6.html"). I suggest you either file bugs in upstream bug trackers, or contact upstreams in their preferred way (usually posting to their development mailing lists) about it.

---

### Post by Bou on 2008-05-21
But what's the relevance of following it? I'd rather have a solid argument before contacting them, instead of just personal preference.

---

### Post by 23meg on 2008-05-21
The rationale of the specification is having a unified, predictable behavior across all free software applications, rather than having thousands of applications each of which go about things their own way. Still, like all other fd.o specifications, it's essentially non-binding; there's no "fd.o compliance" stamp, other than the LSB, which is a much wider set of specifications that include some fd.o ones.

---

### Post by Lieter on 2008-05-26
> **23meg said:**
> That's the [XDG Base Directory specification]("http://standards.freedesktop.org/basedir-spec/basedir-spec-0.6.html"). I suggest you either file bugs in upstream bug trackers, or contact upstreams in their preferred way (usually posting to their development mailing lists) about it.
isn't this behaviour gonna break upgrades... since all personal data is in .[program name]?

Or will update-manager refractor(that's i think te right word) all the users' homedirs?

---

### Post by 23meg on 2008-05-26
That would be fixed per application in the packaging by the maintainer.

---

### Post by meastp on 2008-05-28
Rhythmbox already has this bug. Search for gnome-love bugs on Rhythmbox to find it.

---

### Post by talkingwires on 2008-05-29
> **23meg said:**
> That would be fixed per application in the packaging by the maintainer.Just to clarify, do we report bugs to the application's maintainers or to Launchpad?

I think having a consistent directory for configuration files is a long overdue idea. Will /etc, /var, and /usr/share be next?

---

### Post by Druke on 2008-05-29
it was suggested to report it upstream in their preferred method

---

### Post by talkingwires on 2008-05-29
> **Druke said:**
> it was suggested to report it upstream in their preferred methodGotcha.

I guess after the beta lands and upstream still hasn't fixed their package, we report to Launchpad, right?

---

### Post by aamukahvi on 2008-05-29
> **talkingwires said:**
> I think having a consistent directory for configuration files is a long overdue idea. Will /etc, /var, and /usr/share be next?
What's wrong with those directories?

---

### Post by Amaranth on 2008-06-03
This is not something we would be doing in Ubuntu as it doesn't matter either way and would be a gigantic amount of work. Please do not ever file bugs in Launchpad about this, we are not going to work on it.

---

### Post by Quikee on 2008-06-03
> **Amaranth said:**
> This is not something we would be doing in Ubuntu as it doesn't matter either way and would be a gigantic amount of work. Please do not ever file bugs in Launchpad about this, we are not going to work on it.

There is no easy "to upstream" delegation system in Launchpad? I always thought there is such a thing in place - bad :(

---

### Post by 23meg on 2008-06-03
> **Quikee said:**
> There is no easy "to upstream" delegation system in Launchpad? I always thought there is such a thing in place - bad :(

Bugs can be forwarded upstream once filed in Launchpad, but someone (a triager) still needs to decide what is an upstream bug and what is not. With issues like this, if people file bug reports in the upstream bug trackers directly, that saves the triage work on the Ubuntu side.

---

### Post by Amaranth on 2008-06-03
Someone has to actually file the bug upstream then tell launchpad it exists. There is no automated system.

An automated system would likely be abused as people would not stop to check if this bug is Ubuntu-specific or something that affects upstream as well.

---

### Post by meastp on 2008-06-03
> **Amaranth said:**
> Someone has to actually file the bug upstream then tell launchpad it exists. There is no automated system.

An automated system would likely be abused as people would not stop to check if this bug is Ubuntu-specific or something that affects upstream as well.

I read a blog post on this, and I think the author filed bugs against most of the gnome applications, so I'm sure a search on XDG in Gnome bugzilla will yield results.

---

