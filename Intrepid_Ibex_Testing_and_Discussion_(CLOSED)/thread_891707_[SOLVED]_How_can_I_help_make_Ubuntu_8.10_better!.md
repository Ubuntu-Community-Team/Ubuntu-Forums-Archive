---
title: "[SOLVED] How can I help make Ubuntu 8.10 better!"
date: 2008-08-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ptn107 on 2008-08-16
I have no programming experience short from a few basic python exercises (though I am experienced in shell scripting).  What can I do to help eliminate some of the bugs* in Intrepid Ibex?

*[https://bugs.launchpad.net/ubuntu/intrepid/+bugs](https://bugs.launchpad.net/ubuntu/intrepid/+bugs)

---

### Post by tamoneya on 2008-08-16
well if you cant do any serious programming you can at least help confirm bugs.  Basically search for bugs labeled as "new" and see if you can reproduce the bug.  Then post your results.

---

### Post by ptn107 on 2008-08-16
Is it valid enough for me to reproduce them in a VM or should I install it to my spare laptop and go from there.

---

### Post by insane_alien on 2008-08-16
well, if you encounter a bug, post it to launchpad, when a developer asks you for the output of some command you give it to him and generally do everything he asks.

without a bit of programming experience you can't directly fix bugs but by helping developers as much as you possibly can to track down the source of the bug, you can speed up the fixing process.

however, there are other ways to help ubuntu, you can write documentation(even if it is just fixing errors in old documentation). 

you can work on packaging software. although thats more needed post release than anything else. 

every little helps.

If you want to play a more direct role in fixing bugs i suggest you learn python really well, find a program or two written in python on ubuntu and see if you can fix bugs on them. 

Most programs are written in C(or one of its derivatives like ++) so unless you learn one of those theres not much you can do for those programs.

---

### Post by tamoneya on 2008-08-16
> **ptn107 said:**
> Is it valid enough for me to reproduce them in a VM or should I install it to my spare laptop and go from there.

It is best if you can actually install on real hardware.  VMWare should be okay but virtual box has been rather problematic with the new kernel.  It currently gets kernel panics.  This bug is already well documented though as it has been around since pre-alpha.  This bug is also a problem for fedora I think who has a similar release cycle.

---

### Post by ptn107 on 2008-08-16
Good to know.  I'll install intrepid from the x86_64 dvd today and try to start confirming bugs.

---

### Post by UbuWu on 2008-08-16
[https://wiki.ubuntu.com/ContributeToUbuntu](https://wiki.ubuntu.com/ContributeToUbuntu)
[https://wiki.ubuntu.com/HelpingWithBugs](https://wiki.ubuntu.com/HelpingWithBugs)

---

### Post by nanog on 2008-08-16
Actually programming experience is not required for quite a bit of packaging and bug fixing. If you are familiar with the shell and can use stdout and stderr you can almost certainly help:

[https://wiki.ubuntu.com/MOTU/GettingStarted](https://wiki.ubuntu.com/MOTU/GettingStarted)

[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)

[https://wiki.ubuntu.com/PackagingGuide/Recipes](https://wiki.ubuntu.com/PackagingGuide/Recipes)

---

### Post by ubuntu27 on 2008-08-19
[How to Help Ubuntu]("http://www.ubuntu.com/community/participate")

You can also join the [Bug Squad Team]("https://wiki.ubuntu.com/BugSquad")

---

