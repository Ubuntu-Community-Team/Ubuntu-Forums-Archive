---
title: "Can't load vmnet module"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by dcroxton on 2008-03-19
I have the VMWare server from the Ubuntu repositories installed.  I have used it with no trouble in the past (a few months ago), but today when I tried to start it I got the following:

```
dcroxton@Avaux:/usr/bin$ sudo /etc/init.d/vmware-server start
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.
```

Okay, so then I tried to load the vmnet module, but:

```
dcroxton@Avaux:/usr/bin$ sudo modprobe vmnet
FATAL: Module vmnet not found.

```

So what do I do?  I tried re-installing all of the vmware packages.  All of the information I can find online says, "run vmware-config.pl," but that only exists if you download vmware from their site, not if you use the Ubuntu packages.  (In any case, I don't have it on my machine.)  I could go that route, which I have done in the past and it has worked, but I'd much rather use the repositories if I can.

Sincerely,
Derek

---

### Post by dcroxton on 2008-03-19
Thankfully, I managed to stumble onto the solution to this on my own.

One of the Ubuntu updates must have changed the default kernel in GRUB to a real-time kernel (linux-2.6.22-*-rt).  The vmmon module was for the generic kernel.  I never noticed the change in GRUB because I have my computer boot up automatically every day at 7, so I never see the GRUB menu.

Sincerely,
Derek

---

### Post by YorYor on 2008-04-03
Thanks, had the same problem as you after I upgraded to Gutsy last night.
Much appreciated.

---

