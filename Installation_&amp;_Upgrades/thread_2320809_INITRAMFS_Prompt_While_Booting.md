---
title: "INITRAMFS Prompt While Booting"
date: 2016-04-17
forum: Installation &amp; Upgrades
---

### Post by TheZorch on 2016-04-17
Finally, we're getting our server up and working again. We have 4 Mediasonic Probox eSATA drive bays. Two hold 4 drives, the other two hold 8, and we use an SIL eSATA controller card (has the chipset these bays required to work right). Back in Ubuntu 12.04 everything worked fine, though we can't use it on the new server because it doesn't recognize our network card. We're did a fresh install of 14.04 LTS, and while booting the kernel walks through and initializes each drive. However, some of these drives take time to wake up. The entire process looks like it hangs, but if we hit ENTER we get an INITRAMFS prompt. If we type EXIT the whole system continues to boot as if nothing was wrong and boots correctly. So, this looks like a timeout somewhere. All drives are accounted for when it does boot

How do we fix this so it boots normally? Or, should I say how do we make the kernel wait until all of the drives are ready?

After some research we found that Boot Repair might be able to help with this. However, we keep running into a problem, and we can't seem to figure out why it's happening.

We installed it via the instructions on a 14.04 desktop liveCD and tried to run it. It looks like it's working then we get this message...

**Please close all your package managers (Software Center, Update Manager, Synaptic, ...) Then try again**

We found there was a Boot Repair LiveCD. We used Rufus to make a bootable USB drive, and when the tools starts working we get the *exact same error message*.
We tried it with the drive bays turned off and turned on. At this point we don't know what else to do.

---

