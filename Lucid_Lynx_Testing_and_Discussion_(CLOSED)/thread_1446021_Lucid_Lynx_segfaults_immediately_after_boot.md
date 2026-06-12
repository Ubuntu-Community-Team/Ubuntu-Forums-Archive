---
title: "Lucid Lynx segfaults immediately after boot"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by JacaByte on 2010-04-03
So I wanted to see what all the buzz was about 10.04, and decided to give it a whirl.

I stuck an old 40 GB HDD in my [Mirror Door Drive 1.25 GHz G4]("http://lowendmac.com/ppc/mdd-power-mac-g4-dual.html"), a new-world PowerPC, and clean installed Ubuntu 8.04 LTS on it. The installation worked like a champ and I had a linux system with 100% functionality.

I opened a console and typed "update-manager -d" and used the update manager to upgrade to 10.04.

I did things this way because the 10.04 cd image for PPC is oversize (708 MB instead of 700 MB) so I'd have to burn a DVD in order to do that, but the primary optical drive in my machine can't read or write DVDs anymore.

After I let the update manager do its thing and restarting the machine, I get the following;

```
mount: mouting none on /dev failed: no such device

error initializing netlink socket
udevd[828]: error initializing netlink socket

libudev: udev_monitor_new_from_netlink: error getting socket: invalid argument
segmentation fault

/dev/hdc does not exist. Dropping to a shell!

(initramfs)
```

Or something along the lines of that. It can't find the root partition, fails to boot and drops me into a busybox from (initramfs). The Catch 22 is that the (Apple USB) keyboard does not work and I have to restart the computer via the power button. There is a cursor blinking at the busybox prompt, so I must assume that it's not frozen, just unresponsive.

Does anybody have any suggestions as to what I can do to salvage the installation? I'd rather not have to start from scratch, but will if I must.

---

