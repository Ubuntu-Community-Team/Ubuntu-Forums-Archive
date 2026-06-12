---
title: "No GCC in ubuntu 5.10 by default"
date: 2005-11-03
forum: Installation &amp; Upgrades
---

### Post by Vertical on 2005-11-03
Hello

I was a bit confused, when found out that Ubuntu isn't shipped with gcc and make by default!

But, when I installed gcc4 and make from synaptic, my system gives such error after ./configure:

**checking for C compiler default output... configure: error: C compiler cannot create executables**


What is wrong?

---

### Post by mcduck on 2005-11-03
[QUOTE=Vertical]Hello

I was a bit confused, when found out that Ubuntu isn't shipped with gcc and make by default!

But, when I installed gcc4 and make from synaptic, my system gives such error after ./configure:

**checking for C compiler default output... configure: error: C compiler cannot create executables**


What is wrong?[/QUOTE]try to install build-essentials with synaptic. That should install everything needed to compile programs.

---

### Post by Dracontopes on 2005-11-03
And install gcc-3.4 also because some programs need this to compile.

---

### Post by az on 2005-11-03
[QUOTE=Dracontopes]And install gcc-3.4 also because some programs need this to compile.[/QUOTE]
Only kernel modules need this.  Gcc-3.4 is not on the cd, but everything else is.....  I asked why that was:

"That will never happen again!" - Matt Zimmerman

---

### Post by taurus on 2005-11-03
I know you can install everything to compile a program with build-essentials but I don't see a logic in not including gcc compile as a default!!!  It seems a little odd to me...  :rolleyes:

---

### Post by mcduck on 2005-11-03
why should it be in default install? Everybody doesn't need it, and those who do can get it with a single command..

---

### Post by Vertical on 2005-11-05
[QUOTE=mcduck]why should it be in default install? Everybody doesn't need it, and those who do can get it with a single command..[/QUOTE]

If I can get it with a single command there will be no reason for this thread.
And sometimes users install software not only with apt-get.

---

### Post by Biased turkey on 2005-11-05
[QUOTE=Vertical]If I can get it with a single command there will be no reason for this thread.
And sometimes users install software not only with apt-get.[/QUOTE]
I kind of agree, all the other "popular distros"  : Fedora, debian, gentoo ( of course ) install the gcc compiler by default.
but hey, 
[https://wiki.ubuntu.com/InstallingCompilers]("https://wiki.ubuntu.com/InstallingCompilers")
is just a few keystrokes away :)

---

### Post by az on 2005-11-05
Just because most other distributions do it does not mean it is a good thing.  

Anyway, it is not like it doesn't come on the cd.  There is only one way to install ubuntu and that is with the installer cd.  "build-essential" and its' dependancies are on it, so everyone who has Ubuntu has it.

---

### Post by riggsd on 2005-11-05
[QUOTE=Vertical]If I can get it with a single command there will be no reason for this thread.
And sometimes users install software not only with apt-get.[/QUOTE]

If you'd read the docs then there'd be no reason for this thread.

```
sudo apt-get install build-essential
```

FYI, it's considered dangerous by some to have a compiler installed on a production server as it could allow a user-level exploit to become a root-level one. Not to mention that I could list off a dozen other applications that are "essential" for *everyone* to have installed by default.

---

### Post by az on 2005-11-06
[QUOTE=riggsd]If you'd read the docs then there'd be no reason for this thread.

[/QUOTE]

I think the real problem is that people are willing to read the docs, but something like this is not straightforwardly documented.

Quote:
"The doc team needs warm bodies."
-Corey Burger

---

### Post by mechanic on 2005-11-06
If no-one asked questions here, how would we all learn?

Reading the docs is asking for problems in linux generally, as they are never up to date, and often contradictory.

m.

---

### Post by riggsd on 2005-11-06
[QUOTE=mechanic]Reading the docs is asking for problems in linux generally, as they are never up to date, and often contradictory.[/QUOTE]

I'm sorry, but if someone has this attitude, then no amount of questions will be enough to *ever* get them to a competant level. The Ubuntu team does an incredible amount of work preparing documentation and making it up to date, both on the web, and "off the CD".

Have you actually clicked the "liferaft" Help docs icon and read them? System -> Help. The intro talks about how to use synaptic, how to add repositories, etc. Under Applications -> System Utilities you can read the answer to "How do I install basic compilers?"

I'm very glad to help out new users and people without the experience to troubleshoot Linux problems, that's where every one of us started out. Taking the attitude that "reading the docs is asking for problems" makes you sound like a flat-out idiot. It takes time away from the people helping and it takes time away from the people who have actually tried to figure out the issue or (gasp) [searched google]("http://www.google.com/search?q=ubuntu+install+compilers") first.

---

