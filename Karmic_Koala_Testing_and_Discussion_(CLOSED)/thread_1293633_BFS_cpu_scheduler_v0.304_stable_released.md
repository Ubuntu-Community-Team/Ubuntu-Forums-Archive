---
title: "BFS cpu scheduler v0.304 stable released"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by froggyswamp on 2009-10-17
[http://lkml.org/lkml/2009/10/16/96](http://lkml.org/lkml/2009/10/16/96)

Folks what du think about these questions:
1) Are the Ubuntu devs (at least for fun) gonna provide a PPA with this scheduler?
2) My desktop (karmic x64) still becomes significantly less responsible when copying/moving files for longer than a few tens of seconds (not everyone experiences this issue, but those who do find it a disappointing experience). Did anyone check if the BFS fixes this issue?

---

### Post by 23meg on 2009-10-17
> **froggyswamp said:**
> [http://lkml.org/lkml/2009/10/16/96](http://lkml.org/lkml/2009/10/16/96)

Folks what du think about these questions:
1) Are the Ubuntu devs (at least for fun) gonna provide a PPA with this scheduler?

Unlikely, but that's a moot point, since anyone can do that.

> **froggyswamp said:**
> 2) My desktop (karmic x64) still becomes significantly less responsible when copying/moving files for longer than a few tens of seconds (not everyone experiences this issue, but those who do find it a disappointing experience). Did anyone check if the BFS fixes this issue?

Unlikely, since BFS is a task scheduler, not an I/O scheduler. Still, the only way to know is to try it on your configuration, since different people experiencing the same symptom may be having different underlying problems.

---

### Post by froggyswamp on 2009-10-17
"since anyone can do that" - unless you mean kernel developers and alike, but simple people like me who only know Java have to learn a lot and wouldn't go that far, I'd rather wait for a PPA.

---

### Post by 23meg on 2009-10-17
> **froggyswamp said:**
> "since anyone can do that" - unless you mean kernel developers and alike, but simple people like me who only know Java have to learn a lot and wouldn't go that far, I'd rather wait for a PPA.

No, anyone who knows or can learn how to do packaging or modify existing packages and apply some patches can do it. It's a packaging job, not a development job.

---

### Post by froggyswamp on 2009-10-17
Which is what I'm basically saying, everyone who <...> wants to test it that much that is willing to learn packaging, applying patches etc.
What I'm saying is that suggesting to simple people do it by hand is overkill for most of them, such people are much more likely to try out a PPA than build it themselves.

---

### Post by 23meg on 2009-10-17
What I meant with "anyone" was "not necessarily Ubuntu developers". Sorry, should have been clearer.

---

### Post by psyke83 on 2009-10-17
> **froggyswamp said:**
> Which is what I'm basically saying, everyone who <...> wants to test it that much that is willing to learn packaging, applying patches etc.
What I'm saying is that suggesting to simple people do it by hand is overkill for most of them, such people are much more likely to try out a PPA than build it themselves.

So you're willing to test a development kernel task scheduler, but unwilling to learn how to build a kernel package (which also implies to learn how to apply a patch and build a kernel)?

I see a flaw in your reasoning. How are you going to test properly - if you file a bug and are asked to test a modification to the scheduler, how are you going to do so? Wait for someone else to rebuild a package for you?

---

### Post by hexsel on 2009-10-17
> **psyke83 said:**
> So you're willing to test a development kernel task scheduler, but unwilling to learn how to build a kernel package (which also implies to learn how to apply a patch and build a kernel)?

I see a flaw in your reasoning. How are you going to test properly - if you file a bug and are asked to test a modification to the scheduler, how are you going to do so? Wait for someone else to rebuild a package for you?

There's a bug and brave user that did that.  I've been using it daily and it works fine.  I've had one issue with a memory-heavy program, but I think it was java, not BFS/BFQ.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/424927](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/424927)

[https://launchpad.net/~darxus/+archive/bfsbfq/](https://launchpad.net/~darxus/+archive/bfsbfq/)

PS.: I don't know or endorse Darxus

---

### Post by Keyper7 on 2009-10-17
Wow, Con is actually posting in LKML again?

I was surprised enough by BFS, but never thought this would happen.

---

