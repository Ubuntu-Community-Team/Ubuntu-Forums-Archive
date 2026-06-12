---
title: "Single user mode: Can't mount root as read-only"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by mfanou on 2012-02-12
I am running Ubuntu 10.10 in an asus netbook.

I want to grab a dd image of the root filesystem, in order to save it for later restoration, in case the system gets bloated. I used to do this in debian once in a while, to have "working" instances of my system.

But in Ubuntu 10.10, I see that in the root shell prompt of the single user mode, all services are running. It's not possible to mount the root filesystem as read only, because it's being used.

I was looking in the grub settings in the recovery mode boot option. "ro single" is there, but despite that, Ubuntu starts all services.

I don't want to stop all services by hand, this is definitely not the easiest way to do it.

Of course there is the option of starting with a bootable usb flash and running a live operating system. But I don't like this idea. Plus, it harder get it automated through scripts.

Any idea?


Thanks in advance

---

### Post by mfanou on 2012-02-14
> **mfanou said:**
> I am running Ubuntu 10.10 in an asus netbook.

I want to grab a dd image of the root filesystem, in order to save it for later restoration, in case the system gets bloated. I used to do this in debian once in a while, to have "working" instances of my system.

But in Ubuntu 10.10, I see that in the root shell prompt of the single user mode, all services are running. It's not possible to mount the root filesystem as read only, because it's being used.

I was looking in the grub settings in the recovery mode boot option. "ro single" is there, but despite that, Ubuntu starts all services.

I don't want to stop all services by hand, this is definitely not the easiest way to do it.

Of course there is the option of starting with a bootable usb flash and running a live operating system. But I don't like this idea. Plus, it harder get it automated through scripts.

Any idea?


Thanks in advance

Bump...

---

