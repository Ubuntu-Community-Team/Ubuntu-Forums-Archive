---
title: "Recompile kernel after install?"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by hannav85 on 2006-10-10
Hi,

I was told by someone else that i should recompile the linux kernel after installation since the one i downloaded is just a standard kernel (i386) and that by customising it to suit my system ubuntu will run faster.

Is there any point in doing this and if so can someone recommend a good place to find info on recompiling the kernel manually (i dont have a clue and google hasnt helped much!)

thanks

---

### Post by taurus on 2006-10-10
Not that much faster!!!  The only reason I see you need to build a new kernel is you need something for your harddrive that doesn't support with the default kernel.  If you have P3 or above, install i686 kernel either with synaptic or aptitude/apt-get and it's all good...  But if you still insist on building a new kernel, then check out [http://www.kernel.org/](http://www.kernel.org/).

---

### Post by srt4play on 2006-10-10
The only sensible reason to do it would be if you had obscure hardware that there were no kernel module for, but built-in support was there and just not compiled in. 

You will not see a dramatic difference in speed.

---

