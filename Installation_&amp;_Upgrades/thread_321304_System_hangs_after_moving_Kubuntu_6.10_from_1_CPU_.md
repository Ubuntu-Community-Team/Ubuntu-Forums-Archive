---
title: "System hangs after moving Kubuntu 6.10 from 1 CPU to 2 CPU machine"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by user2037 on 2006-12-18
Previous machine was a P4 1.3GHz with 600MB SD-RAM and Kubuntu 6.10. New machine is a dual P3 1.4GHz with 1GB SD-RAM. After moving the HDD I booted into recovery mode and installed the SMP kernel:

sudo apt-get install linux-686-smp

Then updated GRUB to use the new "generic" option. Typing "cat /proc/cpuinfo" displays two processors but the machine slows down and locks up after a few minutes use. No obvious cause.

---

### Post by eXisor on 2006-12-18
For edgy the i686 kernel is part of the generic kernel. linux-generic

---

### Post by user2037 on 2006-12-21
Yeah, I installed that from Apt and the generic option appeared in Grub but the same issue recurred with the generic kernel.

After backing up and starting with a fresh, vanilla installation of Ubuntu 5.10 and upgrading to 6.06, then 6.10, the issue has come up again. I updated Grub to use the generic kernel but it still hangs after a while. Tried using the non-generic kernel so only one CPU is used but it hangs again.

When the problem comes up the mouse can still move for a while. And toggling caps or num-lock on the keyboard will change the lights. But clicking has no effect. Then, after a moment, it locks completely.

At times it will run for an hour before the issue occurs. Other times it comes up after only a few minutes.

My previous Kubuntu installation did have Gnome installed as well.

---

