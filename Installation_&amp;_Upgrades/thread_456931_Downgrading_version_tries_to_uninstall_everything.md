---
title: "Downgrading version tries to uninstall everything"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by hpalma on 2007-05-28
I'm trying to downgrade the libc6 package to the default one that comes with feisty. When i use synaptic to force the version it shows a list of about 100 other package that it says he's going to remove. I'm guessing those are all the package dependencies, but i don't want to remove the package, just downgrade the version. Why is he behaving like i want to remove the package ? How do i downgrade the package then ?

Thanks..

---

### Post by Jussi Kukkonen on 2007-05-28
First, I hope you know what you are doing -- libc is an essential and fragile piece of the base system.

The hundred packages you see are probably not all packages depending on libc6: there are over 10 000 such packages in the repositories...

---

### Post by hpalma on 2007-05-28
> **Jussi Kukkonen said:**
> First, I hope you know what you are doing -- libc is an essential and fragile piece of the base system.

The hundred packages you see are probably not all packages depending on libc6: there are over 10 000 such packages in the repositories...

I hope so too. The problem is that i installed a new libc6 from the gutsy repo by mistake and now i want to downgrade it to the feisty version.

Any idea how i can do that ?

---

### Post by hpalma on 2007-05-28
It seems that dpkg -i --force-downgrade should do the trick. But i can't find the libc6 dev anywhere. Not even in the feisty iso. Any idea where i can find it ?

---

### Post by hpalma on 2007-05-28
Found the debs and dpkg -i --force-downgrade worked great...

Problem solved...phew

---

