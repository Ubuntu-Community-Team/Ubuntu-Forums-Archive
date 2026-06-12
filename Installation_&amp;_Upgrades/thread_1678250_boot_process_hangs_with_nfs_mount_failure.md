---
title: "boot process hangs with nfs mount failure"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by fbusse on 2011-01-30
I have an nfs mount def'ed in fstab like the following:

192.168.120.230:/source /mountpoint nfs nouser,nfsvers=3,nolock,async,atime,auto,rw,nodev,exec,suid 0 0

If I remember correctly, until some weeks ago, failure to mount simply resulted in an error message and the option to proceed without the mount (which was exactly what I wanted to happen).

Now, the boot process hangs in KDE's graphical "running points" screen, on ESC, the mount failure message is shown.

Is there any way to get back to the previous system behaviour?

My system is 10.04 with all regular updates applied.

Canonical support suggests booting in recovery mode and setting the mount to "noauto". But even in "recovery mode", the system hangs with the above error. The messages reads as follows:

mount.nfs: DNS resolution failed for 192.168.x.x: Name or service not known
mount.nfs: mount system call failed
mountall: mount /mountpoint (623) brach mit dem Status 32 ab

The related device with the given ID in fact is not down, but some network services, obviously including nfs are broken. (I'm in contact with the device support for more details, but received no answer, yet.)

The German message "mount brach mit dem Status 32 ab" translates to English "mount cancelled with status 32". Mount fails for other mountpoints on the same device, showing mountpoint numbers 635, 643, 659 and 666.

What struck me is the fact that with the current settings, I previously was given the option to proceed boot without the mounts (selecting "m" for "check manually") after mount failure.

---

