---
title: "Triple boot loading with Ubuntu 10.04"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by thelugnut on 2010-12-21
I want to install a triple boot load consisting of Windows 7, Ubuntu 10.04, and  Fedora.

My question is, if I install Windows 7, followed by another distro, like Fedora, and then install Ubuntu 10.04, will the Ubuntu GRUB 2 menu display all three options?

I know if I install Ubuntu and then install Fedora, I have to go through some heavy gyrations to get everything to show in the load menu, so it seems easier to install Ubuntu last.

What say ye? Will it work?

---

### Post by oldfred on 2010-12-21
I believe Fedora still uses grub legacy, so it will not find Ubuntu easily. It is much better to install Ubuntu last and lets its osprober find the other installs.

You may be able to install the grub legacy to Fedora's boot partition. It also likes to have a separate boot partition and create LVM logical volume management for its partition(s).

May not be the most current version but show some of the issues.
[http://ubuntuforums.org/showthread.php?t=1415879](http://ubuntuforums.org/showthread.php?t=1415879)
 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)
See posts 26 & 27
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)

---

### Post by thelugnut on 2010-12-21
Thanks oldfred, for the reply
That is what I had supposed was the best direction to take. That is, install Ubuntu last. 
So, that's what I will do.:D
Again, thanks.

---

