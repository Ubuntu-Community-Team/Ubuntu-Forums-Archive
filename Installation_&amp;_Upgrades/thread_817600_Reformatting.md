---
title: "Reformatting"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by MarshyTheKid on 2008-06-03
So I tried to upgrade to 8.10 but something went wrong partway through. It has left my computer so that the disk check cannot proceed(vm.mmap_min_addr fails)
I couldn't find a way to skip the disk check so I am running from a live cd to back up all of my files. But the problem(one of the many) is that I don't have permission for all of them. I have about 70 gigs of stuff and I have two backup drives of 40 each. Is there a way for me to access all of the files and put them on the drives?

---

### Post by Pumalite on 2008-06-03
Maybe you can try this:
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by iaculallad on 2008-06-03
> **MarshyTheKid said:**
> So I tried to upgrade to 8.10 but something went wrong partway through. It has left my computer so that the disk check cannot proceed(vm.mmap_min_addr fails)
I couldn't find a way to skip the disk check so I am running from a live cd to back up all of my files. But the problem(one of the many) is that I don't have permission for all of them. I have about 70 gigs of stuff and I have two backup drives of 40 each. Is there a way for me to access all of the files and put them on the drives?

If you can login using the Restore Mode, try to echo 0 (to lower any original value) to your /proc/sys/vm/vdso_enabled file.

Using your terminal:

```
echo 0 > /proc/sys/vm/vdso_enabled
```

Then try restarting again.

---

### Post by MarshyTheKid on 2008-06-04
So it does the check disk with the recover mode, but there is no /proc/sys/vm/vdso_enabled file.

I'm worried that even if I can get back into my system(Which I might be able to now), backing up all of my files won't work(Unless I turn the permissions of everything to everyone?) because although my username will stay the same, it goes by the id number assigned to the username(Or something)

---

