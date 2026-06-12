---
title: "all boot options fail"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by mpref on 2010-11-10
Hi,

I had a working KUbuntu 10.04.01 LTS installation on my desktop machine, but since the installation of a lot of packages last week (among them ubuntu-desktop and gnome-desktop-environment) I have big difficulties even booting.  Among the four options GRUB offers me, every one of them fails -- but at different points:

1. Ubuntu, with Linux 2.6.32-25-generic

Freeze at


```
...
Checking battery state...          [ OK]

```

According to some other posts, this certainly has nothing to do with the (non-existing) battery, but may be a driver issue.  I can then Ctrl-Alt-F1 and sudo gdm start to get a login window and start working, but this seems hardly a long-term solution.  In particular, because the error messages of the other boot options (see below) hint at more (related?) issues:

2. Ubuntu, with Linux 2.6.32-25-generic (recovery mode)

Recovery Menu pops up, but is useless, since pressing the cursor keys brings up the kubuntu splash screen instead of navigating between the options (resume, clean, dpkg, failsafeX, etc.).

3. Ubuntu, with Linux 2.6.32-24-generic

```

udevadm trigger is not permitted while udev is unconfigured.
udevadm settle is not permitted while udev is unconfigured.
udevadm settle is not permitted while udev is unconfigured.
udevadm settle is not permitted while udev is unconfigured.
ALERT! /dev/disk/by-uuid/265fd183-3a97-4799-a83b-48da21a46803 does not exist. Dropping to shell!


BusyBox v.1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

```

4. Ubuntu, with Linux 2.6.32-24-generic (recovery mode)

same as 3. Ubuntu, with Linux 2.6.32-24-generic

So, two questions at this point:
- Where do I add boot options, like "nolapic", in the many lines I get after pressing Ctrl-e at a grub entry.  (Some posts referring to the hang at "Checking battery state" suggest a problem with the graphics driver.)
- Why is /dev/disk/by-uuid/ a problem with kernel 2.6.32-24, but not with 2.6.32-25?

Of course, I'm also gratefull for any suggestions.

---

