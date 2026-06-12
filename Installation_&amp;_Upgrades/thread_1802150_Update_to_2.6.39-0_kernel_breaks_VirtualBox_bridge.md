---
title: "Update to 2.6.39-0 kernel breaks VirtualBox bridged networks"
date: 2011-07-11
forum: Installation &amp; Upgrades
---

### Post by rsgrimes on 2011-07-11
Just recently updated 11.04 to kernel 2.6.39-0, and VirtualBox to 4.0.10 (I think in that order) and now my machine doesn't boot.  Here is what happens in the boot screen:

[FONT=Courier New] * Starting KVM                                [fail]
...
 * Starting configure bridges for device       [fail]
...

After the above, one of two things happen:

1. Hangs after the following:

 * Stopping System V runlevel compatibility    [ OK ]
[/FONT] 
2. Repeatedly generates messages like the following:
 
[  370.026890] ata10:exception Emask 0x10 SAct 0x0 SErr 0x4040000 action 0xe frozen
[  370.040750] ata10: irq_stat 0x00000040, connection status changed
[  370.054537] ata10: SError: { DevExch }

If I boot with .38 kernel, it starts, but VirtualBox bridged networks don't work - I think that is because it's driver is specific to .39?

I do need the bridged adapters, so I need to resolve this.

Any ideas?  Any known issues with these version?

Thanks!

---

