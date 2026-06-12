---
title: "On boot initrams shows. On liveCd can't mount filesystem"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by Kognit on 2011-02-16
Hi

I have made a stupid mistake when editing /etc/sudoers with nano. Evenmore, then i started to updating the kernel and something really went wrong. I couldn't used sudo. So, i reboot it to change sudoers but now on boot initrams shows.
So i have tried with livecd to fix the issue and i can mount all partition except the one with filesystem. It says:
Unable to mount location
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

When i write in terminal:sudo fsck /dev/sda4 the terminal output is:
fsck.ext4: Device or resource busy while trying to open /dev/sda4
Filesystem mounted or opened exclusively by another program?


What can i do?

Thx for answers

---

### Post by quixote on 2011-02-17
Is there something missing after this?> but now on boot initrams shows.If not, what do you mean?  

The bad news is, I'm not sure you can recover at this point. Somebody who knows more than I do may have a better suggestion!  

What's on sda4?  If your data is elsewhere, could you just reinstall?

---

### Post by Kognit on 2011-02-17
Hi

I have solved the issue with the different LiveCD (the first was corrupted). I corrected sudoers file and run fsck. Now everything works.

---

### Post by quixote on 2011-02-18
Glad to hear it!  :D

---

