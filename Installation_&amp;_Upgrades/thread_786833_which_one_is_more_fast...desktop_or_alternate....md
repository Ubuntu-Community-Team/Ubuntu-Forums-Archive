---
title: "which one is more fast...desktop or alternate..."
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by luckyyyyyy on 2008-05-08
can anybody explain which is more fast ubuntu desktop version(8.04 hardy) or ubuntu alternate version(8.04 hardy)..????...which one is more suitable...

because when we try to install ubuntu desktop version using wubi...wubi tells that if you choose this command(install in windows) then operating is slow...and also hibernate is disable... 

plzz explain...?

---

### Post by gforster on 2008-05-08
Do you mean which has a faster install process or which one is faster to use once installed?

If you are looking for a faster install process, it depends on your computers specs - e.g. to install on my laptop (HP dv6607nr - AMD processor, I need to use the alternate version and the live cd will not work, so it is faster in a sense. 

but, on my desktop, the live cd version is "easier" in that there are only a few clicks and it installs itself, so i choose to use that one.

If are looking at which will run faster once installed on your system - it doesn't matter. the alternate and the regular installer both install the same ubuntu on your system. The reason the wubi is slow is because it is installed "inside" of windows.

---

### Post by kostkon on 2008-05-08
> **luckyyyyyy said:**
> can anybody explain which is more fast ubuntu desktop version(8.04 hardy) or ubuntu alternate version(8.04 hardy)..????...which one is more suitable...

because when we try to install ubuntu desktop version using wubi...wubi tells that if you choose this command(install in windows) then operating is slow...and also hibernate is disable... 

plzz explain...?
There is not an *Ubuntu* alternate version. The *Alternate Install CD* is just a different way to install it.

Actually there are three ways to install *Ubuntu*:

The *Live CD* installation where you have to install *Ubuntu* in its own partitions, using *Wubi* where you install it as a *Windows* file (but it runs a little slower, as you have already said) and using the *Alternate Install CD* where a text based installer is being used.

The *Alternate Install CD* is used in cases when the *Live CD* does not work or for OEM installations.

If you want *Ubuntu* to run as speedier as possible then you have to install it in its own partitions using the *Live CD* (or the alternate CD, if needed).

Nevertheless, if you want a lighter version of *Ubuntu*, you can check [*Xubuntu*]("http://www.xubuntu.com/").

---

### Post by luckyyyyyy on 2008-05-08
thanks....i understand now...

u means if i install only ubuntu in c derive...and no any other operating system in c...then it will more speedy than with windows install....


and one more can i increase ubuntu partition size...because when i install i gave it to 8GB,,,.now i want 20 GB..can i increase...?

---

### Post by gforster on 2008-05-17
> **luckyyyyyy said:**
> u means if i install only ubuntu in c derive...and no any other operating system in c...then it will more speedy than with windows install....

You have the same struggles I did when I first began using ubuntu. In linux, there is no "C Drive."  Everything is either a file or a folder.  It took me a little bit to wrap my head around that. I used windows for way too long. 

but to answer your question - yes, if you install ubuntu on its own partition, it will be speedier than the wubi install. It is by far easiest to do this using the Live CD as mentioned above.

> and one more can i increase ubuntu partition size...because when i install i gave it to 8GB,,,.now i want 20 GB..can i increase...?

That kind of depends on how you set it up.  What does your parition scheme look like?  If you use the Live CD, look at the partition editor located under System > Administration.  That will allow you to change the partition size if it is possible.

---

### Post by Sef on 2008-05-17
> The Alternate Install CD is used in cases when the Live CD does not work or for OEM installations.

Or one prefers it.  The only hard part with using the alternate cd is if you have to manually partition, but once you learn how to manually partition it is easy.

---

