---
title: "i can't even load from the cd!"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by creamcheeze77 on 2007-04-24
i upgraded ubuntu last week from edgy to feisty.  however, the operating system won't load.  i then downloaded the installed from another computer, put it on a cd, and tried to boot it from that cd.  either way, right after the GRUB loads or right after i hit "start or install from CD"  i get the exact same error: " 0.403295] PCI: Failed to allocate mem resource #6: 200000@e0000000 for 0000:04:00.0 ".  It then says " Loading, please wait... " forever.  i *think* pci 0000:04:00.0 is my graphics card, which is a nvidia 7900 gs.  help!

---

### Post by Jussi Kukkonen on 2007-04-24
If you upgraded, you still have the old kernel from Edgy intact. Try booting that.

---

### Post by creamcheeze77 on 2007-04-24
the older kernel loads, but then the graphical interface ( X ) won't run, i think because the kernel has to match the version of X that i'm using, but i'm not sure.

---

### Post by phidia on 2007-04-24
If you had the nvidia driver installed in edgy then maybe the upgrade didn't update your nvidia driver? Try editing /etc/X11/xorg.conf changing "nvidia" to "nv" start x and then re-install the nvidia-glx package.

---

### Post by creamcheeze77 on 2007-04-24
i have nvidia-glx-new installed, the problem is that Ubuntu won't even load in the first place, even booting from a CD.  it doesn't get to the X error, it just hangs.

---

### Post by phidia on 2007-04-24
I saw the failure to boot with cd stuff but just took a shot on a xserver prob.

I see that launchpad has a bug with the same or similar error output

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/54294](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/54294)

---

### Post by creamcheeze77 on 2007-04-24
i actually managed to get rid of the PCI error by unplugging the graphics card.  however, nothing changed, the OS still won't boot up.

---

### Post by jmagsho on 2007-04-24
Did you try loading the old kernel and once you get to a terminal prompt and login, then go ahead and edit the /etc/X11/xorg.conf file to use the standard nvidia driver as phidia suggested?

---

### Post by creamcheeze77 on 2007-04-25
i actually havent tried using "nv" instead of nvidia.  however, this would disable my graphics card.  i'd much rather be able to use the new kernel, but i can't figure out why it won't boot up.  if i let it run for several hours, sometimes it'll reach "configuring network connections" (in ctrl alt f1), but it still wont load.

---

