---
title: "after 13.04 upgrade /home is empty"
date: 2013-05-17
forum: Installation &amp; Upgrades
---

### Post by scuffedshoes on 2013-05-17
This is something I've never seen before.
I just upgraded from 12.10 to 13.04. Everything seemed to go OK, no error messages at least. But when I tried to login after reboot I kept getting recycled back to the login screen.
I logged in as root, figuring it was a permissions problem, and found that /home is completely empty, or at least ls shows it as empty.
I can log in as a guest, the / tree is fine. But /home, which is on its own partition, shows as empty.
The disk utiltiy shows /home as mounted, and df shows /home as being used to the extent that I recall, but ls and nautilus show it as empty.
That df shows there is something there gives me hope.
I've tried booting in to the older kernel, no joy.
/home is on /dev/sda8 and is formatted ext4.

help.

---

### Post by scuffedshoes on 2013-05-18
I did a clean install from a USB drive and it picked up my original home directory. Just have to reinstall my favorite programs, but my data is safe.

---

### Post by deadflowr on 2013-05-18
When you log in as root (not advisable) you log in as root, so therefore the home folder is actually the root home folder, not your home folder.

Did you dig through the file system to get to the /home directory?

Likewise, the guest session home folder sits in the /tmp directory.


It's been a long while (several years in fact) since I've suffered the loop of death, but as I recall, one method or cure(possibly), was to boot into the recovery mode and remove or simply move the .ICEauthority file from the users home folder.
I've also read about doing that to the .xauthority file in same folder.

---

