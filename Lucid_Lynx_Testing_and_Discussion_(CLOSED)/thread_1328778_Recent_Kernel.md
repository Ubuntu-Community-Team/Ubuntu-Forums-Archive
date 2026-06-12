---
title: "Recent Kernel?"
date: 2009-11-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-11-16
I seem to have 4 installed.  2.6.32-3.4, 2-6.31-14.48, 2.6.32-2.2 and 2.6.32-24.  Which is the most recent so I can delete one or 2? And is this wise since I have 4?

---

### Post by xebian on 2009-11-16
> **sox fan Matt said:**
> I seem to have 4 installed.  2.6.32-3.4, 2-6.31-14.48, 2.6.32-2.2 and 2.6.32-24.  Which is the most recent so I can delete one or 2? And is this wise since I have 4?

Have you looked at the timestamp? Or tried sorting it out?

From your list, I can see

Oldest  ----------------------------------Newest

2.6.31-14.48 < 2.6.32-2.2 < 2.6.32-3.4 < 2.6.32-24

---

### Post by sports fan Matt on 2009-11-16
That was the way they showed up in Symnaptic, but are the kernels in order?

---

### Post by sgosnell on 2009-11-16
That's the order.  The higher the numbers, the later the kernel.  I keep multiple kernels for awhile until I know for sure that a later kernel works without problems, and this can take some time.  Four is probably more than necessary, and you can delete those you want to get rid of through Synaptic.

---

### Post by wnelson on 2009-11-16
I have use the computer janitor with some really good success. You are able to choose what you want not removed and removed.

---

### Post by slakkie on 2009-11-17
If you want to figure out the what the latest kernel is:

```

apt-cache policy linux-image-generic
linux-image-generic:
  Installed: 2.6.32.4.4
  Candidate: 2.6.32.4.4

```

Then you will see which kernel is required by the latest kernel meta-package.

Use one of the following meta packages:

linux-image-386
linux-image-ec2
linux-image-generic
linux-image-generic-pae
linux-image-rt
linux-image-server
linux-image-virtual

---

### Post by philinux on 2009-11-17
> **wnelson said:**
> I have use the computer janitor with some really good success. You are able to choose what you want not removed and removed.

Computer janitor no longer offers to remove old kernels. This is deliberate at the moment.

---

### Post by Kevbert on 2009-11-17
You can remove old kernels with Synaptic. Just search for linux-image and then completely remove the generic ones that you no longer require (e.g. linux-image-2.6.32-3-generic). This will also remove the grub2 entry.

---

### Post by seeker5528 on 2009-11-18
In Synaptic old kernels should show in the status view when 'installed: (local or obsolete)' is selected.

Later, Seeker

---

### Post by ronacc on 2009-11-18
if you have enough space it doesn't hurt to keep the old kernels . During a dev cycle I keep all old kernels and also set synaptic  to keep all old files in the cache . It does cause clutter but it also saves your butt when the current version of something barfs and the previous version is gone from the repos .

---

