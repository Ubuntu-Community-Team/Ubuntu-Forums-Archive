---
title: "installing 7.0.4"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by brihy1 on 2007-06-04
when i boot with the ubuntu cd and i hit install or start ubuntu i get this error message

/bin/sh/:cant access tty;job control turned off(initramfs)? i cant install or run live cd at all,any ideas?

---

### Post by merlinus on 2007-06-04
Try Safe Mode.

If that does not work, press F6 at the opening menu and add noapic to the bootup default.

Then I would make sure that your cd does not have errors.  You can try burning the .iso at a no more than a 4x speed.

Good luck!

-merlin

---

### Post by brihy1 on 2007-06-04
get same message after trying that,i have a burned cd and bought a ubuntu cd online both checked out ok?

---

### Post by esavato on 2007-06-04
Give the alternate install cd a try. 
Also, another poster with a similar error reported that this worked...

sudo /etc/fstab replaced all the SD* with HD*, saved and rebooted.

Here is the post and reply's
[http://ubuntuforums.org/showthread.php?t=456838](http://ubuntuforums.org/showthread.php?t=456838)

---

### Post by brihy1 on 2007-06-05
i found a ubuntu 6.10 and installed it got all updates and the update manager says 7.04 upgrade,installed it that way,thanks for helpin people

---

