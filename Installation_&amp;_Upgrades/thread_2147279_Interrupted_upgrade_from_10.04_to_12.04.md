---
title: "Interrupted upgrade from 10.04 to 12.04"
date: 2013-05-21
forum: Installation &amp; Upgrades
---

### Post by littl3red on 2013-05-21
Last night, I started my upgrade from 10.04 to 11.04, thinking I could let it do all the several-hour-long bits while I was sleeping. But my dad unplugged my computer this morning and my battery died. I booted up my computer and it's still running 10.04, but it says it can't install or remove any programs because some packages are broken (surprise surprise...) and I have to manually fix it before I can continue.

Opening the update manager gives this dialog box:
Software index is broken


It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

So I enter the above line in a terminal and it gives this output:

ashtin@ashtin-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.12) but 2.15-0ubuntu10.4 is installed
         Recommends: libc6-i686
  python-louis: Depends: liblouis0 (>= 1.7.0-2) but it is not installable
  ubuntu-minimal: Depends: libc6-i686
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

So now... I'm pretty much stuck. Any help? I'm fuming because I ordered a brand new custom high-end computer and I really just needed to get this to carry me through to when it shipped. Figures something like this would happen now. ](*,)
[SIZE=3]
EDIT: I meant 12.04. Beware writing forum posts while enraged.[/SIZE]

---

### Post by dino99 on 2013-05-21
boot in recovery mode (hold "shift" key down at bios end process to get the grub menu on a single OS installation) and activate the network from that menu, then select "dpkg" to try repairing it, and finally select "continue" to boot. Otherwise start a fresh install from cd/usb or mini-iso  ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD))

[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

---

