---
title: "Hardy Proposed Testing - Log Items"
date: 2008-06-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-06-20
Hi folks, please help me understand some log items that have come up with my testing of hardy proposed on AMD64. Basically I have been trawling through my logs and see some items:

KERNEL STUFF:

```
Jun 20 15:42:38 ppp kernel: [   28.432094] Failure registering capabilities with primary security module.
```

Ack! :) Thinking about it, I figured it just informing me its not using SELinux and using AppArmour instead but Im guessing here?

```
Jun 20 15:42:38 ppp kernel: [   28.915005] PCI: Cannot allocate resource region 8 of bridge 0000:00:03.0
Jun 20 15:42:38 ppp kernel: [   28.915012] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
```

Got a few of these - I dont know what this means in practice?

```
Jun 20 15:42:38 ppp kernel: [   28.942993] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
```

And now various things about not being able to reserve certain areas?

```
Jun 20 15:42:38 ppp kernel: [   29.807116]   Magic number: 12:776:740
```

Right, can I use that in lotto? :)

```
Jun 20 15:42:38 ppp kernel: [   29.807223] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
```

Hmmmmm

```
Jun 20 15:42:38 ppp kernel: [   33.152793] Driver 'sd' needs updating - please use bus_type methods
Jun 20 15:42:38 ppp kernel: [   33.153004]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
```

Hmmmmm

```
Jun 20 15:42:38 ppp kernel: [   33.733715] Attempting manual resume
Jun 20 15:42:38 ppp kernel: [   33.733719] swsusp: Resume From Partition 8:19
Jun 20 15:42:38 ppp kernel: [   33.733721] PM: Checking swsusp image.
Jun 20 15:42:38 ppp kernel: [   33.734083] PM: Resume from disk failed.
```

This sequence puzzled me because I do not resume or enable sleep. It was a normal re-boot?

```

Jun 20 15:42:38 ppp kernel: [   47.307463] lo: Disabled Privacy Extensions
```

Why?

```
Jun 20 15:42:38 ppp kernel: [   54.332877] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
```

I have the latest BIOS from ASUS so hmmmm

XORG Stuff

```
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
```

Why is this font not in Ubuntu?

---

### Post by RAOF on 2008-06-20
> **Nullack said:**
> ...

```
Jun 20 15:42:38 ppp kernel: [   28.915005] PCI: Cannot allocate resource region 8 of bridge 0000:00:03.0
Jun 20 15:42:38 ppp kernel: [   28.915012] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
```

Got a few of these - I dont know what this means in practice?

Nothing, generally.

> **Nullack said:**
> 
```
Jun 20 15:42:38 ppp kernel: [   28.942993] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
```

And now various things about not being able to reserve certain areas?

Again, nothing much.  The kernel is quite verbose about what it's doing, and the degree of variation between different motherboads/bioses/whatever means that you'll almost certainly get some messages like these.

> **Nullack said:**
> 
```
Jun 20 15:42:38 ppp kernel: [   29.807116]   Magic number: 12:776:740
```

Right, can I use that in lotto? :)

Yes :).

> **Nullack said:**
> 
...
```
Jun 20 15:42:38 ppp kernel: [   33.152793] Driver 'sd' needs updating - please use bus_type methods
Jun 20 15:42:38 ppp kernel: [   33.153004]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
```

Hmmmmm

Upstream driver issue; that's basically saying "Yo!  Driver writer!  Update for the new hotness, kthxbye".  You don't need to care.

> **Nullack said:**
> 
```
Jun 20 15:42:38 ppp kernel: [   33.733715] Attempting manual resume
Jun 20 15:42:38 ppp kernel: [   33.733719] swsusp: Resume From Partition 8:19
Jun 20 15:42:38 ppp kernel: [   33.733721] PM: Checking swsusp image.
Jun 20 15:42:38 ppp kernel: [   33.734083] PM: Resume from disk failed.
```

This sequence puzzled me because I do not resume or enable sleep. It was a normal re-boot?

How do you think resume from hibernate works?  Because the system is totally powered off, the only way it can work is by the kernel checking at the start of every boot whether it should be resuming from hibernate; that's this check here.

> **Nullack said:**
> 
```
Jun 20 15:42:38 ppp kernel: [   54.332877] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
```

I have the latest BIOS from ASUS so hmmmm

Heh.  Having the latest BIOS doesn't really correlate with your BIOS implementing ACPI correctly :).

> **Nullack said:**
> 
XORG Stuff

```
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
```

Why is this font not in Ubuntu?

Because no one wants to use X fonts anymore?

In general: all sorts of subsystems are very verbose.  This makes it easier to find out when something's wrong, but also means that they'll spew out information even when everything's working as planned.  As such, log trawling is only really useful[1] when something's going wrong, and you want to find out why.

[1] With the obvious exception of audit logs.

---

### Post by Nullack on 2008-06-20
Thanks very much RAOF. Apparently magic numbers are some sort of validation like hash that can be used.

Im investigating the K8 power issue further.

The security issue is reported under bug [https://bugs.launchpad.net/ubuntu/+bug/163616](https://bugs.launchpad.net/ubuntu/+bug/163616)   ---- the root cause appears to be yet explained on this as it occurs in vanilla hardy and proposed hardy.

---

