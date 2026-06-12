---
title: "Totally borked upgrade to 10.04"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by sorceror171 on 2010-06-10
Tried to upgrade 9.10 to 10.04, and I'm getting furious at this point.

Finally manage to run the upgrade (CD issues), no obvious errors... and upon reboot, nothin'. Just a blank screen. Left it there all night, never got anything. WTF?

Well, heck, I'll just boot the live CD and reinstall grub, right? I manage to do so, no errors, reboot, and... just a grub prompt. WTF?

Boot into live again, no grub command installed. Oy. Finally manage to jump through the hoops and get the proxy configured, install grub, the commands fail. Oh, try to set root dir and... no /dev/sda* devices in the /dev dir, 'cause everything's dynamic now. Try to use MAKEDEV, that fails. Remove the apparently-invalid device files.

Screw it, I just run a reinstall, don't change my home partition, etc. Finally on reboot I can boot from the hard drive! Then I get... low graphics mode, and the mouse doesn't work! Yay! Get to a console, log in. I'd like to ssh in, but there's no ssh server, of course. I can't authenticate to the net proxy without a graphical browser, so I'll just have to mount the CD...

You're kidding. You're telling me iso9660 is an unrecognized filesystem? Well, maybe I can modprobe the module...

FATAL: Could not load /lib/modules/2.6.32-22-generic/modules.dep: No such file or directory

AAAAAAAAAAAAAAAAAAAAAAAARRRRRRRRRRRRRRRRRRGGGGGGGGGGHHHHHHH!

What the *hell* am I supposed to do now? Wipe the whole damn thing and start from scratch?

---

