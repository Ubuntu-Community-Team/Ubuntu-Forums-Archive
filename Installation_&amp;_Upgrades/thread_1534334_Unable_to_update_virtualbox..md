---
title: "Unable to update virtualbox."
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by Chris_no on 2010-07-19
Hi.

I have virtualbox installed under ubuntu 8.04 x64.

The kernel got updated and since then I have to reboot the computer
and choose previous kernel to use virtualbox.

The reason is that I can't get a hold of the virtualbox module for 2.6.24-28 generic.

When the kernel has been updated in the past I would just go into
synaptic and select it, but this time it doesn't show and I've waited
a while now...

Tried searching for the package to no avail.

Anybody know what I should do?

---

### Post by Irony on 2010-07-19
> **Chris_no said:**
> Hi.

I have virtualbox installed under ubuntu 8.04 x64.

The kernel got updated and since then I have to reboot the computer
and choose previous kernel to use virtualbox.

The reason is that I can't get a hold of the virtualbox module for 2.6.24-28 generic.

When the kernel has been updated in the past I would just go into
synaptic and select it, but this time it doesn't show and I've waited
a while now...

Tried searching for the package to no avail.

Anybody know what I should do?

Do you have virtualbox-dkms installed, I believe you need that so that virtualbox recompiles itself on a kernel upgrade.

---

### Post by Chris_no on 2010-07-19
That package isn't available to me in synaptic.
So no it isn't installed.
I have always updated it manually in synaptic.

I have version 1.5.6 OSE

So it's a bit old.

I have tried to add proposed packages, but didn't get it anyway.
Maybe the one making the module packages have quit working on my version.

The last version available is module 2.6.24-27 generic.

---

