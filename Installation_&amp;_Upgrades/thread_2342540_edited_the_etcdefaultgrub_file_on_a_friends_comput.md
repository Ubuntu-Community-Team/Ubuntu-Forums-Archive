---
title: "edited the etc/default/grub file on a friends computer ... will it survive updates?"
date: 2016-11-07
forum: Installation &amp; Upgrades
---

### Post by SuperFreak on 2016-11-07
I edited the etc/default/grub file on a friends computer to solve issues with freezing. Do I need to to do anything else or will this survive future updates such as Kernel changes?
Change was:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
to

```

GRUB_CMDLINE_LINUX_DEFAULT= "intel_idle.max_cstate=1"
```

---

### Post by alexjpowell on 2016-11-08
Backup the previous file,
make sure you run sudo update-grub after

Reboot to test
Upgrade the kernel yourself, it's pretty easy
Then reboot again and you'll find out

---

### Post by Impavidus on 2016-11-08
It should survive upgrades. During kernel upgrades grub is upgraded using settings in /etc/default/grub. Having settings survive upgrades is the entire reason /etc/default/grub exists.

---

### Post by oldfred on 2016-11-08
Sometimes we suggest a full total reinstall of grub2. That then overwrites all settings and restores everything to defaults.
So backup is important, but should only be required if system gets so corrupted that a full reinstall of grub is required.

I only edit a few files in /etc. I either know those settings, have them scripted to update on a new install and/or copy them into /home so my normal backup includes them. Most suggest backing up all of /etc as part of your standard backups.

---

### Post by SuperFreak on 2016-11-08
> **Impavidus said:**
> It should survive upgrades. During kernel upgrades grub is upgraded using settings in /etc/default/grub. Having settings survive upgrades is the entire reason /etc/default/grub exists.

Great that is what I needed to know. Thanks

---

