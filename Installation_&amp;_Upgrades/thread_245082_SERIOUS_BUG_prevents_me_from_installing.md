---
title: "SERIOUS BUG prevents me from installing"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by el3ktro on 2006-08-27
Well at least I think so. I can't install Ubuntu 6.06 on my new Centrino based laptop. It features a Realtek 8139 onboard NIC - and this seems to be the problem.

The Ubuntu Desktop CD and the Alternate CD both don't work - it always hangs when trying to detect (network) hardware. I booted from the Gentoo LiveCD where I experienced the same problem - the system hangs at hardware detection.

I now think that I've found out whats wrong: In Gentoo you can force to boot without hardware detection - and voila - it does boot. Now then I just modprobe the 8139too driver the system hangs. Well I installed Gentoo and now that:

If I compile the 8139too module as normal and boot, the system hangs, but when I compile the module with the "PIO instead of MMIO" option the module loads, Gentoo boots and I have networking!

So the only nasty little thing that prevents me from installing my loved Ubuntu on my new laptop seems to be this damn module, which is not loaded correctly during the install. I BET that if Ubuntu would also use the PIO instead of the MMIO mode to load the module that it would work.

My question now is where do I tell this the Gentoo devs so that this issue is hopefully solved soon (hopefully in Edgy) so that I can install Ubuntu? Is there perhaps any way to prevent the Ubuntu installer from loading this module???

Tom

---

### Post by tkjacobsen on 2006-08-27
you should file a bug report at launchpad [https://launchpad.net/distros/ubuntu/+filebug/+login](https://launchpad.net/distros/ubuntu/+filebug/+login)

---

### Post by pakistansteves on 2006-09-02
I think I have the same problem, installation stops after I continue from step 3 where you enter details about the keyboard. I am a beginner so will need some simple instructions if there is a workaround. If I need to provide configuration details plesas tell me what information is necessary.

---

