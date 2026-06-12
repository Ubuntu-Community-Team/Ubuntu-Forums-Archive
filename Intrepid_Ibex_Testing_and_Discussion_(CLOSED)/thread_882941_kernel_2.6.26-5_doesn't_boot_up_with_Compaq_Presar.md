---
title: "kernel 2.6.26-5 doesn't boot up with Compaq Presario A900"
date: 2008-08-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by hexion on 2008-08-07
I tried first with the live CD for Alpha 3, won't boot up.

Then I upgraded from Hardy (testing partition of course), same results.

The splash shows up but then it just goes blank and that's it. Ctrl-alt-delete closes some processes and reboots so the kernel is not frozen.

With Hardy's kernel, Intrepid boots perfectly.

Any tips? Someone with the same problem? Any related bug-report someone knows about?

---

### Post by gjoellee on 2008-08-07
you should report this to [www.launchpad.net](www.launchpad.net)

remember to include facts about your computer  ex: 
I am running on
AMD 3000+
Nvidia GeForceFX 5200
512 mb RAM

---

### Post by hexion on 2008-08-07
> **gjoellee said:**
> you should report this to [www.launchpad.net]("http://www.launchpad.net")

remember to include facts about your computer  ex: 
I am running on
AMD 3000+
Nvidia GeForceFX 5200
512 mb RAM
I know I know ;)

But first I want to discuss it in case it's a known issue or else someone knows about a related bug (already searched at launchpad myself)

---

### Post by klange on 2008-08-07
Boot with the splash disabled, see if anything fails.
(Note: usplash has been messed up for a while due to the switch to uvesafb)

---

### Post by hexion on 2008-08-09
Booted up without splash, no image at all.
Nothing wrong apparently but the image is blank. I can hear the gnome starting sound though.

Booting up with Hardy's kernel and everything is ok.
Time to open a bug report?

---

### Post by meborc on 2008-08-09
try the search function in launchpad first...

---

### Post by hexion on 2008-08-09
> **meborc said:**
> try the search function in launchpad first...

> **hexion said:**
> 

But first I want to discuss it in case it's a known issue or else someone knows about a related bug (**already searched at launchpad myself**)
 
Opening one..

**Edited**: [https://bugs.launchpad.net/ubuntu/+bug/256389](https://bugs.launchpad.net/ubuntu/+bug/256389)

---

