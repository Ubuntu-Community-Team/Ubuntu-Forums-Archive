---
title: "Hardy upgrade failed and borked everything. Possible to recover?"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by chetan.s on 2008-07-08
My Gutsy -> Hardy upgrade failed pretty miserably -- started spitting out of memory errors all over the console before it finally died. 

Is there any way to recover the installation using the CD and the rescue console? I haven't been able to find any instructions for doing this. debootstrap so far hasn't been any help as after I chroot into my root partition, everything segfaults on me.

---

### Post by SkonesMickLoud on 2008-07-08
Do you have a separate /home partition?

---

### Post by chetan.s on 2008-07-08
Nope, just a single root partition.

---

### Post by SkonesMickLoud on 2008-07-10
Sorry I didn't get back to you sooner.

If you have the space, and are able to boot into the LiveCD, try making a separate /home with this:

[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

Once that's done and all of your stuff is moved, you can wipe your / and reinstall Ubuntu.  When you boot into it again, most of your settings will still be there.

---

