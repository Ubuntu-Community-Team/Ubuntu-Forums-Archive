---
title: "How do I do a non-persistent install"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by bigoranges on 2010-02-13
I would like to make all directories except /home non persisent
this way any changes are undone by a reboot. (this will be used by kids)

Where do I start?

I've worked with Linux for years, but never tried this.

---

### Post by QIII on 2010-02-13
You might consider adding them as new users, taking away all but absolutely necessary privileges and keeping them off the sudoers list.

---

### Post by jken146 on 2010-02-13
If you don't give them root access, they won't be able to write to anything outside of /home.

---

### Post by bigoranges on 2010-02-13
> **jken146 said:**
> If you don't give them root access, they won't be able to write to anything outside of /home.

And if I didn't want them making changes in /home either?

Let's say they trash their /home enivironment.

Sure, I can make them a new one, but it would be easier if it just took care of that itself on a reboot.

Ideally, I'd want to be able to decide which users get to have a persistent environment and which not.

I could run a cron job that swaps it out every night also, but just for fun, how do I do this at a filesystem level?  How do I make a directory writable that resets on reboot?

---

### Post by jken146 on 2010-02-13
I think a simple script to delete the user's directory and replace it with a clean one would be your best bet. Running a live CD (even if you copied it to a hard disk) is a bad idea because it gives the user root priviliges.

Does ubuntu still come with a Guest account ??

---

