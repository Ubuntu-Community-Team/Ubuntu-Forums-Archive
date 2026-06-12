---
title: "Flaky NVIDIA Hybrid system after update 21.10 to 22.04"
date: 2022-05-13
forum: Installation &amp; Upgrades
---

### Post by phil_hood on 2022-05-13
I upgraded from 21.10 to 22.04 on my MSI GL73 9RCX a couple of weeks ago.  This has a hybrid NVIDIA/Intel video system. There is a 4K Acer Monitor attached via Displayport cable.  This setup was working very well before the upgrade.  After the upgrade the Acer Monitor would go completely blank for a few seconds at a time, at random intervals. This persists in MATE, in GNOME, with and without Wayland.  It persists when I lower the frequency for the monitor, and also persists when I change the resolution.  There may be some difference in the frequency for all these different settings, but the basic problem continues at some frequency. I tried replacing the cable with a brand new certified 8K cable.  There was no difference.  This happens when whenever I am in in PRIME performance mode, it stops if I change to PRIME on-demand, or Intel mode. I have tried every version of the NVIDIA driver listed on the Custom driver page with no noticeable difference.
Any clue what might have caused this during the upgrade?

---

### Post by phil_hood on 2022-05-16
Thanks to Ernst P for feedback.  He suggested I look at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1958191](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1958191).  Which suggests that I set  intel_idle.max_cstate=4 in my /etc/default/grub file,  GRUB_CMDLINE_LINUX_DEFAULT parameter.  I made this change and so far my second monitor is stable.  So that looks like the solution.

---

