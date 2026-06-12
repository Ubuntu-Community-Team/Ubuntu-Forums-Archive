---
title: "Upgrade to 14.10 (from 14.04) results in failed boot on VirtualBox"
date: 2014-10-27
forum: Installation &amp; Upgrades
---

### Post by John_Manko on 2014-10-27
I've been running 14.04 on VirtualBox 4.3.16 without problems.  I decided to upgrade Ubuntu to 14.10, but now the system won't boot properly.

Letting the system process the normal boot sequence results in Start/Stop of services, ultimately failing on plymouth, like such:
```
Starting load fallback graphics devices
Stopping load fallback graphics devices
Starting set console font
Stopping set console font
Starting userspace bootsplash
Starting Send an event to indicate plymouth is up
Stopping userspace bootsplash
```

Next, I tried to modify boot (SHIFT, E, CTRL-X at boot) by forcing systemd (as recommended in [this thread]("http://ubuntuforums.org/showthread.php?t=2226708&page=3&p=13036073#post13036073")):
```
init=/lib/systemd/systemd
```

That dumps me into a basic shell, but I'm unable to bring up networking in order to see if there are updated packages that would fix my issue.

I did find [bug 1378423]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1378423") which might be related, but since it was fixed prior to 14.10 final I assume that it was included in the upgrade.

Anyone give me help on this?  I'm completely held up by this.  Upgrades are never smooth with Ubuntu.

---

### Post by John_Manko on 2014-10-27
Upgraded VB to 4.3.18, and now only get black screen.  let the fun begin.  dropping into a root shell, got networking working, not packages to upgrade.  This is where I'm stuck.

---

### Post by John_Manko on 2014-10-27
Apparently some conflicting packages where not removed during the upgrade process.  After killing them, I'm able to boot.  odd.

---

### Post by inkarkat on 2014-11-06
I had the same problem when upgrading 14.04 to 14.10 on VirtualBox 4.3.12 r93733, running on Windows 7/x64.

> **John_Manko said:**
> Apparently some conflicting packages where not removed during the upgrade process.  After killing them, I'm able to boot.  odd.

This did the trick for me, too. To expand on the sparse instructions, here's what I did:       
[LIST=1]
[*]Press Shift key during booting to get Grub's prompt 
[*]Choose Advanced options for Ubuntu from the menu 
[*]Choose Ubuntu, with Linux 3.16.0-24-generic (recovery mode) 
[*]Choose dpkg: Repair broken packages 
[*]Choose resume; the system goes up fine (and this persists for the next reboot, too)! 
[/LIST]

---

