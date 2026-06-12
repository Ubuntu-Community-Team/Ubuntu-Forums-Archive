---
title: "Where can I manually download the -9 kernel?"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Jim March on 2009-09-01
I'm stuck hard on kernel -6 (64bit) - yes, I've tried doing command-line updates, doesn't matter.  I have the -7 kernel but it hard-locks on LVMs so I have to manually revert to -6, and I'm blocked from updating to -8 or -9.

Somebody in another thread said basically "download it from the site" but neglected to cough up a URL...

---

### Post by jpeddicord on 2009-09-01
[http://packages.ubuntu.com/karmic/linux-image-2.6.31-9-generic](http://packages.ubuntu.com/karmic/linux-image-2.6.31-9-generic)

though a dist-upgrade should be pulling it in...

---

### Post by plun on 2009-09-01
headers and image from here

[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/)


--

---

### Post by jocko on 2009-09-01
> **Jim March said:**
> I'm stuck hard on kernel -6 (64bit) - yes, I've tried doing command-line updates, doesn't matter.  I have the -7 kernel but it hard-locks on LVMs so I have to manually revert to -6, and I'm blocked from updating to -8 or -9.

Somebody in another thread said basically "download it from the site" but neglected to cough up a URL...
What do you mean with "blocked from updating to -8 or -9". Just mark them from installation in synaptic. If synaptic cant install them for you, you won't be able to install them manually either...

But to answer your question: Either find the packages on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) or browse through the repos at [http://archive.ubuntu.com](http://archive.ubuntu.com) (or whatever local mirror is closest to you)...

---

### Post by Jim March on 2009-09-01
Huh.  Yeah, dist-upgrade DOES seem to work.

> sudo apt-get update && sudo apt-get upgrade didn't.

What I meant by "blocked" was, in the update screens the majority of potential updates were "grayed-out" uncheckable.

---

### Post by Jim March on 2009-09-01
Yeah, that did it.  Huh.  And update manager shows no more blocked items.

---

