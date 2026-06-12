---
title: "[SOLVED] Trouble Installing"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by wtfnomorenames on 2008-07-08
Right now, I have Windows XP installed on my laptop and I was hoping to wipe that off and install Ubuntu on it instead.

I have a Dell Latitude D820 with the following specs:
Intel Centrino Duo (~2.0 GHz)
2GB RAM
80GB Hard drive

I've downloaded Hardy 8.04.1 (md5 checksum: c69e34e92d5402d1b87e6babc739f774). I also checked the CD's checksum and it matches up.

It boots up to the Ubuntu boot menu, and if I try to Install, it gives me the following message:

kernel panic - not syncing: VFS: unable to mount root fs on unknown-block (104,1)

Any ideas or solutions would be greatly appreciated.

Thanks, guys.

---

### Post by Pumalite on 2008-07-08
Get Gparted Live CD and delete everything in your hard drive. Format it ext3. Then try again. Graphics?

---

### Post by wtfnomorenames on 2008-07-09
I wiped everything off the drive and formatted it to ext3. Still getting the same message.

The dialog pops up that says "Loading kernel..." goes all the way to 100%, stays that way for about 1-2 minutes, and then the screen refreshes and the error message is shown.

For graphics, I have an nVidia Quadro NVS (mobile?).

I'm downloading the alternate CD image to see if that will help at all.

---

### Post by wtfnomorenames on 2008-07-09
UPDATE: I ran the alternate text-based installer, and it started up with no problem.

The installer partitioned the drive with no problems, however, sometime right after that step I got this error message:

"An error was returned while trying to install the kernel into the target system.

kernel package: 'linux-generic'"

A "cat /var/log/syslog | tail" revealed:

in-target: E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
base-installer: error: exiting on error base-installer/kernel/failed-install

The installer allowed me to go back a step, so first, I retried the step that failed, but it didn't work (didn't really expect it to, anyways). I went back one step and re-partitioned the drive, and then crossed my fingers and attempted to move onward!

It seemed to move forward just fine this time, and then prompted me to select which kernel to install, giving me these three choices:

linux-generic
linux-image-generic
linux-image-2.6.24-19-generic

I chose the last option (if anybody can explain the differences between these three, I would greatly appreciate it), and it seemed to accept that just fine.

Currently, it's installing packages so hopefully the rest of the installation will go without problem.

---

### Post by wtfnomorenames on 2008-07-09
The alternate text-based installer completed without any more problems! Case closed.

---

