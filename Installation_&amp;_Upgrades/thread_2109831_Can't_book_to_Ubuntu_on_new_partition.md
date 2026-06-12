---
title: "Can't book to Ubuntu on new partition"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by ajregester on 2013-01-28
I have been running Ubuntu 11.10 on my computer for awhile now and have managed to do some strange things to it while poking around.  Part of it's strange behavior is that it wouldn't let me run the system update.  I figured I should start from scratch, so I downloaded 12.04.  

Since I have a lot of stuff I need on my old install that I didn't want to lose and don't want to take the time right now to sort everything, I used gparted to re-size my partition to install 12.04 and I figured I could move stuff over as I needed from the other partition.

I now have my old install on sda1, the new 12.04 install on sda2, and swap on sda3.  I cannot figure out how to boot to the new 12.04 install on sda2.  After it installed I restarted and expected to have grub ask me where to go, but it just went back to my old install.  What do I need to do to boot to 12.04?

---

### Post by ronparent on 2013-01-28
1st try a 'sudo grub-uodate' in a terminal. If it finds your new install, fine. Otherwise we go from there.

---

### Post by ajregester on 2013-01-28
Just tried sudo grub-uodate and got

> sudo: grub-uodate: command not found

I also tried grub-update just in case and got the same command not found.

---

### Post by oldfred on 2013-01-28
ronparent had a typo.  try this:

```
sudo update-grub
```

---

### Post by ajregester on 2013-01-31
I ended up installing 12.04 again and selected an option during install to choose the operating system at the time of boot.  I'm not sure what I chose before, but everything's working as I expected as before.

---

