---
title: "Installing Ubuntu problems"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by gammarik on 2012-06-03
Hi all

I am currently trying to install Ubuntu 12.04 on my old Windows XP machine, but when i reach the Ubuntu Menu on the disk and choose "Install Ubuntu" it freezes. It is an old IBM Thinkpad T40 with a 1.6-GHz Pentium M CPU, 1.5 GB of RAM, an 50 GB HDD and an ATI Radeon 9000 32MB GPU. 

[IMG]http://i.imgur.com/pMxNM.jpg[/IMG]

I hope someone can help me
Thanks in advance

/gammarik

---

### Post by Lorin Ricker on 2012-06-03
I'm going to bet that your freeze is an unexpected behavior of the 12.04 distro in response to finding itself on a non-PAE equipped hardware, which might (likely) include your ThinkPad's version of the Pentium M CPU. Usually, the distro CDROM generates a "helpful" error message when it encounters/boots-on "deficient" hardware, but your mileage may be varying...

"[Physical Address Extension (PAE)]("http://en.wikipedia.org/wiki/Physical_Address_Extension") is a [hardware] feature to allow (32-bit) x86 processors to access a physical address space (including random access memory and memory mapped devices) larger than 4 gigabytes."

Back in November 2011, a developer at Canonical made the rather unilateral decision to "no longer support older non-PAE systems", reasoning that "there can't be many of those old systems left anymore" (!!!???... Wrong!).  There seems to be some low-visibility activities which counter, if not completely rescind, this (dumb) decision.

Presuming that this is actually your problem, check these resources out:

[http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html)

[http://askubuntu.com/questions/103280/is-there-any-version-of-ubuntu-that-does-not-require-pae](http://askubuntu.com/questions/103280/is-there-any-version-of-ubuntu-that-does-not-require-pae)

Since your boot process is just freezing, it's hard to tell if non-PAE is exactly your issue, but hopefully the above, plus any more Googling on these keywords as needed, will help.

Try the "non-PAE mini ISO" from the first URL above, and let us know if that solves this problem.

Good luck! -- Lorin

---

### Post by traditionalist on 2012-06-03
> **gammarik said:**
> Hi all

I am currently trying to install Ubuntu 12.04 on my old Windows XP machine, but when i reach the Ubuntu Menu on the disk and choose "Install Ubuntu" it freezes. It is an old IBM Thinkpad T40 with a 1.6-GHz Pentium M CPU, 1.5 GB of RAM, an 50 GB HDD and an ATI Radeon 9000 32MB GPU. 
I hope someone can help me
Thanks in advance

/gammarik

Have you tried it without installing?  Does the live disk run?

---

### Post by gammarik on 2012-06-03
> **Lorin Ricker said:**
> I'm going to bet that your freeze is an unexpected behavior of the 12.04 distro in response to finding itself on a non-PAE equipped hardware, which might (likely) include your ThinkPad's version of the Pentium M CPU. Usually, the distro CDROM generates a "helpful" error message when it encounters/boots-on "deficient" hardware, but your mileage may be varying...

"[Physical Address Extension (PAE)]("http://en.wikipedia.org/wiki/Physical_Address_Extension") is a [hardware] feature to allow (32-bit) x86 processors to access a physical address space (including random access memory and memory mapped devices) larger than 4 gigabytes."

Back in November 2011, a developer at Canonical made the rather unilateral decision to "no longer support older non-PAE systems", reasoning that "there can't be many of those old systems left anymore" (!!!???... Wrong!).  There seems to be some low-visibility activities which counter, if not completely rescind, this (dumb) decision.

Presuming that this is actually your problem, check these resources out:

[http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html)

[http://askubuntu.com/questions/103280/is-there-any-version-of-ubuntu-that-does-not-require-pae](http://askubuntu.com/questions/103280/is-there-any-version-of-ubuntu-that-does-not-require-pae)

Since your boot process is just freezing, it's hard to tell if non-PAE is exactly your issue, but hopefully the above, plus any more Googling on these keywords as needed, will help.

Try the "non-PAE mini ISO" from the first URL above, and let us know if that solves this problem.

Good luck! -- Lorin

Hi again

Thanks for the help! I got through the setup and it is installing at the moment! Thank you again! Have a nice day :)

/gammarik

---

### Post by Lorin Ricker on 2012-06-03
Hey, gammarik! Glad your install is working now. ;-) Just for the record, while the guess of non-PAE might have been accurate, it's also possible that, just by using a smaller, simpler non-GUI install disk, you've solve a different problem.  Same happy result!

When working with older systems & laptops, it seems that the ubuntu-...-alternate distros often work better, again, just because they don't have to start up all that GUI support, just work from a much simpler, less demanding terminal interface.  Not as "sexy", but actually works and gets to the same desired end-point -- an installed Ubuntu/Linux.

Happy Tuxing! -- Lorin

---

