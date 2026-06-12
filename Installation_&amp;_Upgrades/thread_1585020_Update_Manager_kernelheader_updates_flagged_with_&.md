---
title: "Update Manager kernel/header updates flagged with &quot;New install&quot;"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by kevintap on 2010-09-29
Update Manager popped up today and has a few Recommended updates for my machine.  Included in the Recommended updates is a new kernel (2.6.32-25).  Next to several of the kernel/header updates is the text "(New install)".  What does the "New install" text mean here?  Will installing the kernel/header updates do anything destructive to the system?

Thanks!

---

### Post by tommcd on 2010-09-30
Well, the kernel updates are "new" in that they are not yet currently installed. The kernel updates are provided for bug fixes and or security updates, so the should be installed.
Please run in the terminal: ```
sudo apt-get update
```
And then post the output of: ```
sudo apt-get dist-upgrade
```
I have not used update manager in years. I manage all updates and package installs from the terminal. It is faster and simpler that way you know.
In all likelihood this is a harmless update.

And welcome to the Ubuntu forums!

---

### Post by Elfy on 2010-09-30
It is - I got it yesterday I think.

If update-manager is offering them I'd use that - the only time I don't use update manager is when I'm using an unreleased version.

---

### Post by kevintap on 2010-09-30
Thanks guys, the kernel updates installed just fine.  I had just never seen the "New install" text next to an updated package before.

---

### Post by Elfy on 2010-09-30
It wasn't updated - it was new :)

When that kernel get's updates it'll not say new 

That at least is what I understood it to mean when I first saw the same thing.

If you're happy can you mark the thread solved - in Thread Tools at the top.

---

