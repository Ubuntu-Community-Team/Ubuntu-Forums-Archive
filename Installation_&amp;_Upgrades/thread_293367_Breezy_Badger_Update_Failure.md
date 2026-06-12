---
title: "Breezy Badger Update Failure"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by Jonas54 on 2006-11-05
I'll start off with admitting I'm not a Linux expert and some of my problems are probably my fault.

Anyway, I was running Breezy Badger and ran the update manager (just for package updates, not a distro upgrade). At the time I had a few programs open in the background, not sure if that would cause any problems. Part way through updating the update manager failed to update one of the packages (some obscure library). The error was that it couldn't access the directory it needed due to it being read-only. I hit OK, closed the update manager, and then went to restart it to retry the update again. However, the update manager failed to start. I figured I'd reboot the system (usually works with Windows). After I told the system to reboot it froze. I could alt-tab to switch windows and could move the mouse, but I couldn't click on anything and no keyboard input would work at a console window or anything like that. I then did a hard reboot.

So then the system is in the middle of rebooting.. and it fails. It attempts to automatically run fsck, but that fails as well. It also mentions that the root filesystem is read-only, and that it could be made writable by remounting it (and gave me the command to do so). I then remounted it and ran fsck. fsck then complained about how running it on a mounted filesystem was a bad idea. I guess I don't fully understand the mount stuff. Okay, well, I have no idea how to unmount or whatever. So I then decide to reboot and try again. I type "shutdown -r now," and guess what? That fails. I then tried a few random commands to see if they'd work, but bash complained about them not existing. Then I ended up doing a hard reboot, again.

Okay, so now it's rebooting and I go into recovery mode. Automatic fsck fails again, but this time I didn't remount the filesystem and the manual fsck worked. fsck then found a ton of errors and seemed to fix them. After fsck finsihed it said I needed to reboot. However, "shutdown -r now" failed again, so I did a hard reboot once again.

Now this is the point where I'm currently at. GRUB now fails to load with "error 18". I'm clueless as to what to do now, besides a fresh install. I won't be too upset if I can't recover the system, it was just a learning machine after all, but it would be nice if I could. At the lest I'd like to learn how I could avoid or properly handle this situation in the future. So, what can I do?

Thanks for any help.

---

