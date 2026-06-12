---
title: "menu.lst"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by Howard Kaikow on 2007-06-24
Why does menu.lst contain entries for two different versions of the kernel, etc?
What's the difference between the entries for 2.6.20-16 and 2.6.20-15?
Why are both included?

```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd3,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ea9c0990-5c47-4031-bce3-deadc541752f ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd3,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ea9c0990-5c47-4031-bce3-deadc541752f ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd3,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ea9c0990-5c47-4031-bce3-deadc541752f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd3,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ea9c0990-5c47-4031-bce3-deadc541752f ro single
```

---

### Post by mikewhatever on 2007-06-24
2.6.20-16 is an upgrade of 2.6.20-15. The older version is not removed in case the new one should not work. In case you do not want to see the 2.6.20-15 entries, put hash marks before each, for example, the following will not show during boot time
> 
#title		Ubuntu, kernel 2.6.20-15-generic
#root		(hd3,4)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ea9c0990-5c47-4031-bce3-deadc541752f ro quiet splash
#initrd		/boot/initrd.img-2.6.20-15-generic
#quiet
#savedefault

It is also possible to uninstall the old kernel from Synaptic and delete its entries altogether.

---

### Post by Howard Kaikow on 2007-06-24
> **mikewhatever said:**
> 2.6.20-16 is an upgrade of 2.6.20-15. The older version is not removed in case the new one should not work. In case you do not want to see the 2.6.20-15 entries, put hash marks before each, for example, the following will not show during boot time


It is also possible to uninstall the old kernel from Synaptic and delete its entries altogether.

Thanx.

How many old versions are retained?

---

### Post by mikewhatever on 2007-06-24
> **Howard Kaikow said:**
> Thanx.

How many old versions are retained?

All of them. Feisty's original kernel had one update, so there is one so far. It is up to the user to remove the old ones.

---

### Post by Howard Kaikow on 2007-06-24
> **mikewhatever said:**
> All of them. Feisty's original kernel had one update, so there is one so far. It is up to the user to remove the old ones.

Does the synaptic manager explicitly list the versions, so we can know what to delete?

And, once deleted, do we then have to manually edit menu.lst?

---

### Post by merlinus on 2007-06-24
q1. Yes.  Search for linux-header and linux-image.  But be sure to only remove the outdated ones.  /boot/grub/menu.lst will have the info.

q2. Maybe.  Try it and let us know.

-merlin

---

### Post by syko21 on 2007-06-24
Better way to do it is search in synaptic by name only, not name and description, with the string "2.6.20-15" then sort by installed/not installed (click the table header button thats all the way to the left). It should have 3-4 entries listed, linux-image* linux-restricted* linux-headers* and one other that i cannot remember. As long as your 2.6.20-16 kernel is working fine it is safe to remove these packages (I've done so many times without problem).

---

### Post by merlinus on 2007-06-24
Good idea for the search!

I find, however, that it is best to keep one older kernel.  I never know when I will run into a problem that had not yet arisen, and being able to boot up with the previous version is a fail-safe.

ymmv.....

-merlin

---

### Post by Howard Kaikow on 2007-06-24
Thanx fer the responses.

I would expect that each time there is a major release such as moving from Feisty to whatever will be its successor, at that time, I would remove all but the most recent release of Feisty.

Seems that this is more easily controlled than the great space waste when windows updates are run, i.e., 100-200+ MB each time.

---

### Post by merlinus on 2007-06-24
I thought we were talking about older linux kernels, not os releases.

When you upgrade to the new version of ubuntu (or do a fresh install), the previous version will be gone.

gutsy gibbon (7.10) is next, due sometime in October.

-merlin

---

### Post by Howard Kaikow on 2007-06-24
> **merlinus said:**
> I thought we were talking about older linux kernels, not os releases.

When you upgrade to the new version of ubuntu (or do a fresh install), the previous version will be gone.

gutsy gibbon (7.10) is next, due sometime in October.

-merlin

Yes, but I do not want too many kernel releases to accummulate.

---

### Post by merlinus on 2007-06-24
As stated previously, upgrading or doing a fresh install of gutsy, when it becomes available, will completely overwrite everything in /.

At the moment you have two kernels,  You can get rid of the old one at any time using Synaptic and doing a search for it.

-merlin

---

### Post by Howard Kaikow on 2007-06-24
I dood the deed.
Removed 2.6.20-15, and menu.lst was automatically changed.

But there are still, as I recall, 28 packages listed with "2.6.20-15" in their name.
How does one remove "not installed" packages?

---

### Post by merlinus on 2007-06-24
I assume the "not installed" packages were listed in Synaptic?

If so, fuggedaboutit.  They are not installed on your hard drive!

-merlin

---

### Post by Howard Kaikow on 2007-06-24
> **merlinus said:**
> I assume the "not installed" packages were listed in Synaptic?

If so, fuggedaboutit.  They are not installed on your hard drive!

-merlin

What about

sudo apt-get clean

Since linux always tries to download packages, is there a need to keep them around?

---

### Post by merlinus on 2007-06-24
I would run these:
```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

```If you want to get rid of applications that you do not use, do it either via Synaptic or Applications/Add Remove, and the "installed" filter.

But be careful that you do not uninstall basic apps, etc. needed by the system.

BTW, how much unused space is on your hard drive?

-merlin

---

### Post by Howard Kaikow on 2007-06-25
> **merlinus said:**
> I would run these:
```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

```If you want to get rid of applications that you do not use, do it either via Synaptic or Applications/Add Remove, and the "installed" filter.

But be careful that you do not uninstall basic apps, etc. needed by the system.

BTW, how much unused space is on your hard drive?

-merlin

I have oodles of unused space, but I'm just starting to (ab)use Linux and I want to know how do things as necessary.

I see no reason to save packages from earlier versions of software that I will never use.

---

### Post by syko21 on 2007-06-25
> **merlinus said:**
> I would run these:
```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

```If you want to get rid of applications that you do not use, do it either via Synaptic or Applications/Add Remove, and the "installed" filter.

But be careful that you do not uninstall basic apps, etc. needed by the system.

BTW, how much unused space is on your hard drive?

-merlin
Those commands don't remove all unused packages. For example I built pidgin from source and used the command sudo apt-get build-dep gaim so I could get all dependencies in one shot. Then after it was installed those commands did not clean the dev packages from my system. Any way to get rid of them other than manually?

---

