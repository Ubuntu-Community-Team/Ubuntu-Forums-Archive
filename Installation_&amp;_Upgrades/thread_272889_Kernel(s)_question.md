---
title: "Kernel(s) question"
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by Fingerlakes_Dave on 2006-10-07
Hello all!

  General question.  Which kernel to use?
 i386 works fine.

  i686 and K7 available, however I guess I don't understand why I would want to switch to either. :confused: 

  Athalon Xp 2800+, 1024 RAM

---

### Post by Kateikyoushi on 2006-10-07
If it works why not just leave it so ?
Most likely you wouldn't be able to tell the which one you are actually using, no noticeable benefits.
From the next release of ubuntu the kernel will be avaible only in one flavor.

In case you want to learn about the kernel find guide to learn how to build and compile it and use the one for k7 cpus.

---

### Post by Fingerlakes_Dave on 2006-10-10
> **Kateikyoushi said:**
> If it works why not just leave it so ?
Most likely you wouldn't be able to tell the which one you are actually using, no noticeable benefits.
From the next release of ubuntu the kernel will be avaible only in one flavor.

In case you want to learn about the kernel find guide to learn how to build and compile it and use the one for k7 cpus.

  This does not answer my question.  I'm trying to educate myself on linux
-ubuntu.
  A somewhat more detailed answer (not too tech, still learning), would be more helpful.

  "...no noticable benefits..." then why have kernel "flavors"? :confused:

---

### Post by Kateikyoushi on 2006-10-10
New generations of processors come with new extra [instruction]("http://en.wikipedia.org/wiki/Instruction_(computer_science)") sets.
Your [Athlon]("http://en.wikipedia.org/wiki/Athlon") processor comes with [3DNow!]("http://en.wikipedia.org/wiki/3DNow!") it is a bunch of extra [SIMD instructions]("http://en.wikipedia.org/wiki/SIMD") over the x86 instuctions.

Using the K7 kernel enables the use of these extended instructions, and passes appropriate optimization flags to [GCC]("http://en.wikipedia.org/wiki/GNU_Compiler_Collection").

Those extra instructions won't do much good unless the programs are [Compiled]("http://en.wikipedia.org/wiki/Compiled") to use them.
Ubuntu is not a [source]("http://en.wikipedia.org/wiki/Source-code") based distro, you download precompiled packages, [executable files]("http://en.wikipedia.org/wiki/Executable").
So by default you won't compile with GCC, and if the given software isn't compiled to use those instructions you do not gain much with the K7 kernel.
But if everything comes together you might gain a little extra performance.

Then why did I say not noticeable difference ?
Let's say you use mplayer to play a film now by using 3Dnow it uses only 28% of your cpu time not 30%, would you notice it ?
Of course if you transcode a film it would you gain a few minutes, and you might even compile some of your apps.

I hope it answers some of your questions, there are links in the text if you want to dig deeper.

---

