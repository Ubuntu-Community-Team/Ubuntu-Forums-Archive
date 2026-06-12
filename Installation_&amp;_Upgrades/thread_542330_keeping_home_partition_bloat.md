---
title: "keeping /home partition bloat?"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by stryderjzw on 2007-09-03
Hi,

I have used Ubuntu since Hoary.  I installed the /home directory to a separate partition, so every upgrade I can keep the same settings, etc.

I am wondering if there's any downsides to this.  Does it get bloated like Windows registry?  How do you keep your home folder clean?

Thanks in advance,
Justin

---

### Post by MacJay on 2007-09-03
You did it right. Putting the home on the same partition can cost a lot more headaches. We always put the /home on a different drive. It's practicle as we have many users. I personally follow the same rule.
UNIX will never "bloat" like MS windows.
Good luck!

---

### Post by merlinus on 2007-09-03
You might delete any folders which names begin with a dot (.) that are leftover after uninstalling applications.

If you activate Show Hidden Files, you will see lots of them in /home/username.

-merlin

---

