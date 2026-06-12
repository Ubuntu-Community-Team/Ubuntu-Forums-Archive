---
title: "Latest Update"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by bingobingo on 2010-03-13
What the hell is the point of the updates if it is constantly making your computer run like crap! I am soooo getting tired of this. Is it not suppose to make things run better? Once again I just updated to the latest kernel and again I got memory leeks, constant running hard-drive, and overworking cpu. Why is Ubuntu not running this update on a older generation computer and testing it before posting for all to do the same?

My computer was doing just fine after that last major screw up, now I am back where I stated, a shitty computer. This sucks.

---

### Post by akand074 on 2010-03-13
I don't know why its doing that, didn't for me. But just boot into the old kernel. Or if you removed it, reinstall it using apt-get or through the package manager and then restart and boot into it.

---

### Post by snowpine on 2010-03-13
'apt-get dist-upgrade' will give you a new kernel (if available). 'apt-get upgrade' won't, so it is safer.

But guess what, you can just boot into your old kernel from the GRUB menu. No problem! :)

---

### Post by Sef on 2010-03-13
> 'apt-get dist-upgrade'

That code is not recommended.

---

### Post by snowpine on 2010-03-13
> **Sef said:**
> That code is not recommended.

Why not... can you explain? How do you get new kernel versions without it?

---

### Post by jocko on 2010-03-13
> **snowpine said:**
> Why not... can you explain? How do you get new kernel versions without it?
'apt-get dist-upgrade' tries a little bit too hard to solve dependencies and can sometimes (= very often during development, less often in a stable release) lead to unintentional removal or breakage of packages due to unsolvable dependency issues.

If an update is held back by 'apt-get upgrade', it is a lot safer to try to install the update manually by 'apt-get install *package*' (or use synaptic to update just the held back packages) and solve the dependency issues yourself (or wait until the issue is solved in the repos).

So when you see that an update to the linux meta packages is being held back, just update them manually:
```
sudo apt-get install linux-generic linux-header-generic
```If the actual kernel packages are not ready yet, apt-get will tell you so and exit without doing anything instead of uninstalling the meta packages due to their unsolved dependencies (which is what 'dist-upgrade' would do).

---

### Post by snowpine on 2010-03-13
Interesting info :) but I'll repeat the question: What is the "recommended" terminal command for a full upgrade, including a new kernel version (if available)?

I'll repeat my recommendation to the OP to use 'apt-get upgrade' next time as a safer option, to prevent unwanted kernel upgrades.

---

