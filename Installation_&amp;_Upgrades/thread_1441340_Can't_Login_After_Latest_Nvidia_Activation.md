---
title: "Can't Login After Latest Nvidia Activation"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by rgutierrez on 2010-03-28
Running HP DV9000 with Nvidia 8600 card. Just installed Lucid Beta 1. Live CD boots fine. Can't remember, but I believe initial install had login problems. So, I edited xorg.conf to use "nv" driver. Then, login screen worked fine. Activated latest Nvidia driver (v195.36.15) and now login screen is garbled, possibly frozen. I can't CTRL+ALT+F1. No mouse, no keyboard as far as I can tell. Have to hold power button to shutdown.

What steps should I take from here to troubleshoot?

---

### Post by rgutierrez on 2010-03-28
Tried "nomodeset" and tried specifying known good resolutions in xorg.conf. No change.

---

### Post by rgutierrez on 2010-03-28
My xorg has an EQ overflow error. The following link references this error and notes it's a GPU problem.

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Problem:%20%20Log%20shows%20%22[mi]%20EQ%20overflowing%22%20and%20X%20freezes](https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Problem:%20%20Log%20shows%20%22[mi]%20EQ%20overflowing%22%20and%20X%20freezes)

---

### Post by rgutierrez on 2010-03-28
Activated Nvidia driver version 173. After reboot, login screen appeared. Logged in, and gdm was scrambled or something. Did CTRL+ALT+F1 and got to text login. Then, did CTRL+ALT+F7 to get back and system eventually froze. Did hard shutdown. Then, I booted up and everything seemed to work. Again, this was after reverting to Nvidia driver version 173. 

Opened NVIDIA X server settings and tried to view X Server Display Configuration tab. Error appears on right side pane where details normally display:

```
Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0.
```

So, this is progress (sort of). Obviously, I'm still having some sort of Nvidia-related issue.

---

### Post by rgutierrez on 2010-03-29
Found bug related to this. Not exactly the same driver/kernel/nvidia-settings versions. But, it's obviously the same problem.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/528126](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/528126)

nvidia-settings v195.36.08 is querying the NoScanout attribute, which doesn't exist in the 173.14.22 version of the driver.

---

