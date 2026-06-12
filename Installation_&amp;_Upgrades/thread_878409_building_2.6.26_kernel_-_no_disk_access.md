---
title: "building 2.6.26 kernel - no disk access"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by chiefchimp on 2008-08-02
I'm trying to build a custom 2.6.26 kernel on kubuntu but I'm getting blocked by disk access when booting it.

The existing ubuntu kernel (2.6.24-19) uses kludging to access the drives as SCSI drives but I can't find a xconfig setting to reproduce this effect in the 2.6.26 kernel and end up with the drives using the IDE drivers and therefore panicing when it tries to mount the partitions.

I can change /etc/fstab to use /dev/hda... but this prevents the 2.6.24-19 kernel from booting.

Hardware
IBM ThinkPad R32, 512MB RAM, 40GB Hdd, noname Realtek 8185 CardBus wifi card.

Mick

---

### Post by zvacet on 2008-08-03
I don´t know if this is the answer to your question,but you can read [this.]("http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html")

---

### Post by coffeecat on 2008-08-03
> **chiefchimp said:**
> The existing ubuntu kernel (2.6.24-19) uses kludging to access the drives as SCSI drives

If I have correctly understood what you are referring to, that is no kludge. That is a deliberate strategic decision by the kernel developers and not limited to Ubuntu. The old pata drivers have been deprecated in favour of the newer libata drivers with the result that ide drives now appear (on most systems) as sda/b rather than hda/b.

[This link]("http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce") is pretty old now, but explains the background.

If this is your problem, you need to remove all the older ATA drivers when you do make menuconfig (or whichever config utility you use * ) and include the appropriate libata ones.

* **Edit**: oops! Missed your mention of xconfig. Much nicer than menuconfig. But if you were running gnome, you could use gconfig - even better. :wink:

---

### Post by chiefchimp on 2008-08-03
> **coffeecat said:**
> If I have correctly understood what you are referring to, that is no kludge. That is a deliberate strategic decision by the kernel developers and not limited to Ubuntu. The old pata drivers have been deprecated in favour of the newer libata drivers with the result that ide drives now appear (on most systems) as sda/b rather than hda/b.

I have no issues with a change to a better paradigm, just that there was no clear indication of choose A or B to get this effect.

I had been required to build custom kernels since I started using Red Hat 5.2 back in the stone age and this continued through my debian days.

Since I started using ubuntu at v6.06 until now I was able to use the distro kernels until I got a TV capture card for my desktop and a wifi card for my laptop. The desktop was a pain with so many config options changed/renamed but I got past that.

> **coffeecat said:**
> If this is your problem, you need to remove all the older ATA drivers when you do make menuconfig (or whichever config utility you use * ) and include the appropriate libata ones.

If I could just recognise the right kernel config options to do that, guess I got another day of tickling xconfig.
 
> **coffeecat said:**
> * **Edit**: oops! Missed your mention of xconfig. Much nicer than menuconfig. But if you were running gnome, you could use gconfig - even better. :wink:

gnomes are hideous concrete creatures that sit in the garden scaring young children and old ladies :wink:

Thanks for your help
mick

---

