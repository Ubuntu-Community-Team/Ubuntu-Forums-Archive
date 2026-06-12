---
title: "Upgrade tool crashed, system broken"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by CJNyfalt on 2007-03-13
Adept wanted to upgrade to Feisty this morning but the upgrade tool crashed in the middle of the process. Trying to restart adept it complained about locks, so I rebooted to reset those. Well, after rebooting, X11 won't start.
So now I stuck without any idea how to restart the upgrade process.
HELP!

---

### Post by Kateikyoushi on 2007-03-13
Boot into recovery mode and check your sources.list whether it is updated to feisty or not, I assume it is but better to check.

```
cat /etc/apt/sources.list
```

---

### Post by CJNyfalt on 2007-03-13
Yes, the list is upgraded to feisty.

---

### Post by Kateikyoushi on 2007-03-13
Then try to continue the update reboot to recovery mode and type this to the terminal.

```
aptitude dist-upgrade
```

---

### Post by CJNyfalt on 2007-03-13
I managed to finish the upgrade, but X11 is still broken.
I get:
FATAL: Error running install command for nvidia
Failed to load the NVIDIA kernel module

I have a NVidia 2, so I need the legacy module.

What should I do?
Is there some way to use X11 without acceleration?

---

### Post by princemackenzie on 2007-03-13
crack open your x.org conf file with

> sudo nano /etc/X11/xorg.conf

find the "device" section where the driver is listed.  change it from "nvidia" to simply "nv", the open-source non-accelerated driver.  Save and quit.

Then you'll have X back.

---

### Post by macdhuibh on 2007-03-13
> **Kateikyoushi said:**
> Boot into recovery mode and check your sources.list whether it is updated to feisty or not, I assume it is but better to check.

```
cat /etc/apt/sources.list
```

What is the next step if its is not showing feisty?

---

### Post by FrozenFOXX on 2007-03-13
If nv doesn't work just use "vesa" to get the desktop up.  From there you can worry about how to proceed with the legacy driver installation as normal.

---

### Post by CJNyfalt on 2007-03-13
Ah, yes I should have remembered that.
Thank you both!
My system works again, except for 3d acceleration.

---

