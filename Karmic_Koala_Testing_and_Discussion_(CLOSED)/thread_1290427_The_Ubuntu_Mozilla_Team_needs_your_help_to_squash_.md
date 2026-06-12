---
title: "The Ubuntu Mozilla Team needs your help to squash a nasty Firefox autocomplete bug."
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-10-13
Is anyone here experiencing this bug?
[https://bugs.edge.launchpad.net/ubuntu/+source/firefox-3.5/+bug/438868](https://bugs.edge.launchpad.net/ubuntu/+source/firefox-3.5/+bug/438868)

---

### Post by reborg on 2009-10-13
> **Starks said:**
> Is anyone here experiencing this bug?
[https://bugs.edge.launchpad.net/ubuntu/+source/firefox-3.5/+bug/438868](https://bugs.edge.launchpad.net/ubuntu/+source/firefox-3.5/+bug/438868)

Yes, I have noticed this one.

---

### Post by slakkie on 2009-10-13
I see in the report that some people experience it when they have suspended their PC before it triggers the bug. Do you also use suspend?

I haven't noticed this bug in FF and I use it daily on this box (I run Karmic on my work laptop). I don't use suspend or hibernation, maybe that explains?

If you have more details on how to reproduce the bug I might help to reproduce it...

---

### Post by Longinus00 on 2009-10-13
Hmm, I've had this bug but never really paid any attention to it...

---

### Post by reborg on 2009-10-13
No. I don't suspend.

I tried it once but ran into the pulseaudio resume problems so I haven't used suspend since then.

I'm keeping track of what I am doing now so that if it happens again I might have steps to reproduce.

I haven't searched yet, but highlight->right click->search is also intermittent. Sometimes it works sometimes not.

---

### Post by reborg on 2009-10-13
> **Longinus00 said:**
> Hmm, I've had this bug but never really paid any attention to it...

To be honest I was the same.

---

### Post by emarkay on 2009-10-13
FWIW, I don't use those "Dog-and-Pony show" features, sorry.

---

### Post by Starks on 2009-10-13
> **emarkay said:**
> FWIW, I don't use those "Dog-and-Pony show" features, sorry.
It's a core feature that prevents you from needlessly typing out an entire URL for a site or pages within a site that you've already visited.

---

### Post by reborg on 2009-10-13
Ok two updates:

I let my machine go to sleep and it appeared after that.

Double-clicking favicon makes the feature work again. It seems as if an event is initially not firing/being processed after sleep.

---

### Post by emarkay on 2009-10-13
> **Starks said:**
> It's a core feature that prevents you from needlessly typing out an entire URL for a site or pages within a site that you've already visited.

Hmm, that's what bookmmarks and history are for.  Been that way since Netscape was on floppies...  Plus, I don't keep any history between sessions.  FWIW.

---

### Post by adrianx on 2009-10-13
> **emarkay said:**
> Plus, I don't keep any history between sessions.  FWIW.
Porn mode, eh? :D Just joking.

I've noticed the problem too. It happens whenever my mouse cursor leaves the Firefox window. It also  affects input fields in html forms. 

As soon as I hover the cursor over the address bar or form fields, they regain focus and I'm able to type again.

I haven't really tried testing it with desktop effects disabled...

**Edit:** I'm only now noticing that this is a Karmic Koala thread. What I'm talking about has been happening to me in Jaunty from day one.

---

### Post by null_pointer_us on 2009-10-13
I had problems with the autocomplete address bar in Ubuntu 9.04 64-bit w/ stock Firefox (3.1?) for that distro. After a while, it would just stop working. Eventually, I realized that this problem only occurred when compiz (desktop compositing) was enabled. Suspend/resume could have had something to do with it, but I can't confirm.

---

### Post by Starks on 2009-10-17
Bumping.

---

