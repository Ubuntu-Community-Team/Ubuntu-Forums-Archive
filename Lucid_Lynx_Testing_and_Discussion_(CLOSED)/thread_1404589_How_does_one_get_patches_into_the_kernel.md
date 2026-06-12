---
title: "How does one get patches into the kernel?"
date: 2010-02-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by AndersAA on 2010-02-11
Specifically this one: [http://bugzilla.kernel.org/show_bug.cgi?id=15064](http://bugzilla.kernel.org/show_bug.cgi?id=15064)

It's fixed in 2.6.33-rc5, a simple enough patch that's very important for some users, and it's a few lines bugfix with a broke acpi implementation.

Whats the procedure to get this patch implemented in the 2.6.32 kernel lucid will ship, and maybe even karmic's kernel?

---

### Post by xebian on 2010-02-11
> **AndersAA said:**
> Specifically this one: [http://bugzilla.kernel.org/show_bug.cgi?id=15064](http://bugzilla.kernel.org/show_bug.cgi?id=15064)

It's fixed in 2.6.33-rc5, a simple enough patch that's very important for some users, and it's a few lines bugfix with a broke acpi implementation.

Whats the procedure to get this patch implemented in the 2.6.32 kernel lucid will ship, and maybe even karmic's kernel?

There is a kernel mainline vanilla version.  33-rc7 is bad though.

---

### Post by jocko on 2010-02-11
You should file a bug report on [launchpad]("https://launchpad.net/ubuntu/+filebug/+login"). Since it is the kernel, I guess you file it against the "linux" package.

---

### Post by benny.kallstrom on 2010-02-12
2.6.33-rc6 works very well on my Hp 6830s laptop. I have had this kernel for about a week and it works perfect.

---

### Post by AndersAA on 2010-02-12
Yeah I've been running a custom built kernel since it was fixed, but the average user won't figure that one out so I'd want it the main tree.

I'll put it on launchpad again though, just wondering if there was a special prodedure to request kernel patches backported.

---

### Post by VMC on 2010-02-12
> **AndersAA said:**
> Specifically this one: [http://bugzilla.kernel.org/show_bug.cgi?id=15064](http://bugzilla.kernel.org/show_bug.cgi?id=15064)

It's fixed in 2.6.33-rc5, a simple enough patch that's very important for some users, and it's a few lines bugfix with a broke acpi implementation.

Whats the procedure to get this patch implemented in the 2.6.32 kernel lucid will ship, and maybe even karmic's kernel?

Did you follow the instructions from [Comment #13]("http://bugzilla.kernel.org/show_bug.cgi?id=15064#c13") ? What were your results?

---

### Post by AndersAA on 2010-02-12
> **VMC said:**
> Did you follow the instructions from [Comment #13]("http://bugzilla.kernel.org/show_bug.cgi?id=15064#c13") ? What were your results?

If you look at the entire bug you'll see that the problem was solved and commited to 2.6.33-rc5.

---

