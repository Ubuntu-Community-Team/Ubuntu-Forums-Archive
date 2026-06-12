---
title: "Breezy gcc problems"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by chaok on 2005-10-18
I installed breezy the other day and found that I have all kinds of problem when I had to compile against my Kernel.  I was able to fix some of them by changing my default compiler.  But some programs still yell about it.

Are you guys having the same problems, and would a possible solution be to recompile the Kernel with the gcc4 compiler?  And why would you even release an os that was compiled with a different compiler than the default, just seems silly.

---

### Post by tseliot on 2005-10-18
[QUOTE=chaok]I installed breezy the other day and found that I have all kinds of problem when I had to compile against my Kernel.  I was able to fix some of them by changing my default compiler.  But some programs still yell about it.

Are you guys having the same problems, and would a possible solution be to recompile the Kernel with the gcc4 compiler?  And why would you even release an os that was compiled with a different compiler than the default, just seems silly.[/QUOTE]
Kernels 2.6.12-xx are compiled using gcc-3.4. 2.6.13-xx use gcc-4.0. I don't know why.

---

### Post by chaok on 2005-10-18
which one goes with each version?  is the 2.6.12 ubuntu 5.02 and the 2.6.13 breezy?  Or can both be used for breezy?

---

### Post by mlomker on 2005-10-18
> And why would you even release an os that was compiled with a different compiler than the default, just seems silly.

I'm forced to assume that other parts of the operating system are in 4.0, but the kernel is definitely 3.4.

```

sudo apt-get install gcc-3.4
sudo nano /etc/bash.bashrc

```

Add at the bottom:
```

export CC=/usr/bin/gcc-3.4

```

Ctrl-X, Y, Enter to save.

---

### Post by tseliot on 2005-10-18
[QUOTE=chaok]which one goes with each version?  is the 2.6.12 ubuntu 5.02 and the 2.6.13 breezy?  Or can both be used for breezy?[/QUOTE]
2.6.12 ubuntu breezy. I have compiled a vanilla kernel 2.6.13 in Hoary and it required gcc-4.0. Kernel 2.6.13 is not available for Ubuntu yet (but you can compile it from vanilla sources). On the other hand OpenSuse 10 comes with 2.6.13

---

### Post by malv on 2005-10-19
[QUOTE=tseliot]Kernels 2.6.12-xx are compiled using gcc-3.4. 2.6.13-xx use gcc-4.0. I don't know why.[/QUOTE]
Anything that uses gcc-4.x compilers is in a big mess, this due to more severe checking built into the new c-compiler. This requires modifying source code in many nooks and crannies.
The same applies also to SuSE 10.0. They compiled their kernel with gcc4 but you quickly find out that things don't really square yet when you try compiling kernel-modules.

The user's problem-mess with both Ubuntu & SuSE is that NO KERNEL should ever be released without its 100+ percent FOOLPROOF compiler/kernel pair. Users are victims of a crazy race against time. Don't believe me? Scan backwards through the postings of the last weeks.

---

