---
title: "X freeze during Karmic upgrade left OS unbootable"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by SteveWh on 2010-04-19
After about 2 weeks of spare-time downloading of the 1.7GB upgrade files on dialup, sudo apt-get dist-upgrade got to the point of applying the upgrade.

After only a few hundred lines of status reports, there was an unfortunately timed hangup that I've occasionally experienced and fits the description of an X freeze: frozen screen, no keyboard, no mouse, but Alt+Shift+PrtSc+REISUB does work to restart, so that's what I had to do to get control back. After that, Ubuntu is unbootable.

I believe the last line on the screen before the freeze said something about restarting hald.

When booting now, the last 2 lines shown before activity stops are:

sd 4 :0 :0 :3: [sdf] Attached scsi removable disk
sd 4 :0 :0 :3: Attached scsi generic sg7 type 0

I have only two HD, both SATA.

When using my USB keyboard during boot, it was unusable, but when I attached a PS/2 keyboard, at this point REISUB works to reboot, but that's the only thing I can do. 

Tried both a normal boot and the other option (repair/recovery  boot), but they both hang at the same place.

I can browse my /home partition files using a Jaunty LiveCD. Hardly anything seems changed. The upgrade didn't get very far. My old fstab is intact. GRUB's menu.lst is the same as before, and points to the old kernel version, and  the vmlinuz file itself is still the old Jaunty version.

The symptoms seem to point to a USB problem (disk drives and keyboard), and I found reports of similar problems that seemed to implicate USB. If I recall correctly, some of them mentioned udev. Does that sound right?

It seems like a crash mid-upgrade is nearly the worst thing that could have happened, so my basic question is how hard it's worth trying to attempt repairs.

If it's worth a try, does anyone have a suggestion about places to look? I'm not looking for a step-by-step, just suggestions about a broad approach.

My current plan is to get a complete listing of files that were modified just before the crash and examine any of the text config files for boot-related configuration commands and USB-related entries, and try to edit them. Last resort would be to try to manually overwrite those files with fresh ones from the old Jaunty LiveCD. 

If I can just get it to boot, I can retry the upgrade, but failing that, will need to do a fresh install. 

Although my video card is an ATI, I use the free driver and have not previously had issues that implicated the driver.

I've been using Ubuntu and Linux since last September, not enough experience to be able to judge whether the above plan is any good or if there's a better approach. Thank you.

---

