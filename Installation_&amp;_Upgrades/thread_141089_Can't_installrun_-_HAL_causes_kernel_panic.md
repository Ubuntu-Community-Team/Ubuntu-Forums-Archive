---
title: "Can't install/run - HAL causes kernel panic"
date: 2006-03-07
forum: Installation &amp; Upgrades
---

### Post by mtlinux on 2006-03-07
Hi.  I've got an old spare P3 450 that I've been using to try out various Linux distributions recently.  I don't know a lot about the rest of the hardware, but could find out if necessary (thus far it hasn't been).  I've installed and run Fedora Core, Mepis, and Xandros on the machine without problems.  But unfortunately Ubuntu refuses to work for me.

The first phase of the installation process proceeds without error.  Then I reboot the machine and the installation continues.  When it gets to the point where it starts the Hardware Abstraction Layer, I get a kernel panic.  If I boot in rescue mode and use dpkg to re-try setup of HAL, I get the exact same results.  I also tried running off the Live CD and I get the same thing (though I can't actually see the kernel panic message in the splash startup -- but the machine freezes at "Starting hardware abstraction layer...").

The call trace looks like this:
```
pci_unmap_srb
srb_done
disconnect
dc395x_handle_interrupt
dc395x_interrupt
handle_IRQ_event
__do_IRQ
common_interrupt
default_idle
default_idle
cpu_idle
start_kernel
```

And the kernel panic is:
```
<0> Kernel panic - not syncing: Fatal exception in interrupt
```

After everyting I've heard about Ubuntu I'd really like to try it...but I'm completely stuck at this point.

Any suggestions?  Thanks in advance for any help!

---

### Post by mtlinux on 2006-03-08
Bump.  Still hoping for some help here...

Any HAL experts out there who might have an idea why it would fail so consistently?  If I can't get it to work, I can't run Ubuntu.  :(

---

