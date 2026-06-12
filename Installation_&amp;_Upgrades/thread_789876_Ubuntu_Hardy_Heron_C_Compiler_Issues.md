---
title: "Ubuntu Hardy Heron C Compiler Issues?"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by jmg498 on 2008-05-10
Hello all,

I am having difficulty compiling anything from source in Hardy Heron.  I just upgraded from Feisty Fawn.  I consistently am getting a list of warnings and errors, followed by "error 1" and the programs do not build.

I tried reinstalling gcc from the package manager but no luck.

Before I copy and paste a bunch of stuff to this forum, is there maybe a way to just reinstall all the C compiler packages and give that a go first?  Or any other suggestions?

Thanks much!

---

### Post by Rocket2DMn on 2008-05-10
The correct package to install is
```
sudo apt-get install build-essential
```
That metapackage has all sorts of compilers in it + libraries.
Does that fix you up?  Otherwise post more output, please.

---

### Post by jmg498 on 2008-05-11
Yep, all's good now.  I figured there was some libraries missing but didn't know which package to install.  Is there no "marked as solved" option on here anymore?  I edited the title to try to reflect that but it'd be best to actually mark it as solved.

Thanks so much!

--Josh G.

> **jmg498 said:**
> Hello all,

I am having difficulty compiling anything from source in Hardy Heron.  I just upgraded from Feisty Fawn.  I consistently am getting a list of warnings and errors, followed by "error 1" and the programs do not build.

I tried reinstalling gcc from the package manager but no luck.

Before I copy and paste a bunch of stuff to this forum, is there maybe a way to just reinstall all the C compiler packages and give that a go first?  Or any other suggestions?

Thanks much!

---

