---
title: "Lucid Lynx boot failure after upgrade"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by Alexis Phoenix on 2010-07-27
After upgrading to 10.04, my laptop refused to boot - not even into single user mode.  It looked to be failing at the point where the filesystems are mounted, however I couldn't see anything wrong with my fstab.  Plymouth (which I hate already) wasn't giving me any messages and there was nothing useful on the console.  Plymouth steals the console output, btw, so if it then doesn't show it, you're stuffed.  Canonical, if you're reading this, please please please make it possible to uninstall Plymouth without removing everything else!

I used a rescue cd, "Syslinux Rescue CD" - Gentoo based - to chroot into the broken installation - thanks to a tutorial on these forums which I now can't find. As I ended up doing this quite a lot over the last week or so, I wrote a little script to do it:```
#!/bin/bash

MOUNTPOINT=/mnt/custom
DRIVE=/dev/sda5

# assume the drive is already mounted to access this script!
# mount $DRIVE $MOUNTPOINT

echo "starting chrooted environment"
mount --bind /dev $MOUNTPOINT/dev
mount --bind /proc $MOUNTPOINT/proc
mount --bind /sys $MOUNTPOINT/sys
mount --bind /dev/pts $MOUNTPOINT/dev/pts
chroot $MOUNTPOINT /bin/bash

```I'm endlessly grateful for that tutorial.

I used ```
xhost +
```to enable programs from the broken installation to run in the rescue disk's gui, and started synaptic.  I installed grub 2 (grub-pc) and rebooted.

Plymouth showed me a message about not being able to mount my windows partition, and let me drop to a shell to fix this, and eventually brought up gdm. Seems to me boot time is a lot worse though!

So what I now wonder is, why did Plymouth need grub 2 to be able to show the message it was waiting for me to respond to - and which I never previously saw?

---

