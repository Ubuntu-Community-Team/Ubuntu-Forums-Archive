---
title: "New kernel: 2.6.28-3"
date: 2008-12-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2008-12-16
Not sure what release candidate this is built off of, but the image and header files are now in the repos.

---

### Post by plun on 2008-12-16
> **Starks said:**
> Not sure what release candidate this is built off of, but the image and header files are now in the repos.

Its based on RC8.....

> linux (2.6.28-3.4) jaunty; urgency=low

  [ Tim Gardner ]

  * Build ecryptfs into the kernel
    - LP: #302870
  * Deprecated gnbd

  [ Upstream Kernel Changes ]
[B]
  * Rebased to v2.6.28-rc8[/B]

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001720.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001720.html)




You an also see it in Ubuntus kernel GIT

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=summary)

Seems to work anyway..

---

### Post by IanW on 2008-12-19
Phoronix today reports release of 2.6.28-rc9 & Linus' decision to go "final" for Xmas.

---

### Post by plun on 2008-12-19
> **IanW said:**
> Phoronix today reports release of 2.6.28-rc9 & Linus' decision to go "final" for Xmas.

Yup... Linus wrote

> There really is _nothing_ interesting here. There's just small changes 
mostly to random drivers, with some networking updates. Oh, and some MIPS 
defconfig updates.

The shortlog really tells the whole boring story - if you can get even 
half-way through without falling asleep, you've just proven yourself to be 
sufficiently caffeinated.

In fact, that may be the most exciting part of -rc9: the medical 
revolution it harbors as a caffeine deficiency test.

But please do test it.

And btw, I do think that I'll make 2.6.28 be a Christmas release (or 
Hanukkah, Kwanzaa, Solstice, Insert-Favorite-Holiday, whatever). Because 
quite frankly, this kind of boredom won't help anything and I'll go stir 
crazy if I have to do this for another two weeks.

And I'll make the merge window longer for people who prefer getting drunk 
on glögg to being a useful kernel developer. Although you could do both: 
just prepare your tree to be pulled before christmas, and then you can be 
in a mulled-wine-induced stupor while _also_ feeling like a productive 
member of society during the holidays.

			Linus


[http://lkml.org/lkml/2008/12/18/435](http://lkml.org/lkml/2008/12/18/435)



---

