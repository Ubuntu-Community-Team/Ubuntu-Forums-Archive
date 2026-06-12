---
title: "Is it Impossible to remove or install a kernel???"
date: 2005-07-26
forum: Installation &amp; Upgrades
---

### Post by tseliot on 2005-07-26
Hi, there was an error and I restarted my computer. Then there was a ext3 check and there were some problems with the blocks. I had to use fsck to solve the problems. I rebooted but the bootstrap hanged so I had to use my previous kernel Now I've lost a kernel (it doesn't appear in synaptic) (however I have 2 other kernels) and I can't remove it.

alberto@ubuntu:/usr/src$ sudo dpkg -r kernel-image-2.6.12-alberto
(Reading database ... dpkg: error processing kernel-image-2.6.12-alberto (--remove):
 files list file for package `gnome-pilot' is missing final newline
Errors were encountered while processing:
 kernel-image-2.6.12-alberto
Processing was halted because there were too many errors.

And if I try to install a new kernel (compiled by me):

alberto@ubuntu:/usr/src$ sudo dpkg -i kernel-image-2.6.12-history_10.00.Custom_amd64.deb
(Reading database ... dpkg: error processing kernel-image-2.6.12-history_10.00.Custom_amd64.deb (--install):
 files list file for package `gnome-pilot' is missing final newline
Errors were encountered while processing:
 kernel-image-2.6.12-history_10.00.Custom_amd64.deb
Processing was halted because there were too many errors.

Same error.

Can I solve the problem by reinstalling something or shall I reinstall Ubuntu again?

(I hope the latter is not the only chance)

Any ideas?

---

### Post by az on 2005-07-26
The problem has nothing to do with the kernel. Another package has currupted the database.

sudo dpkg --clear-avail

should fix your package database.



Stay away from nasty packages!

---

### Post by tseliot on 2005-07-26
This didn't solve the problem. The new kernel I'm trying to install has the same settings as the previous kernel (that is it will work well). It isn't a nasty package.


alberto@ubuntu:/usr/src$ sudo dpkg --clear-avail
alberto@ubuntu:/usr/src$ sudo dpkg -i kernel-image-2.6.12-history_10.00.Custom_amd64.deb
(Reading database ... dpkg: error processing kernel-image-2.6.12-history_10.00.Custom_amd64.deb (--install):
 files list file for package `gnome-pilot' is missing final newline
Errors were encountered while processing:
 kernel-image-2.6.12-history_10.00.Custom_amd64.deb
Processing was halted because there were too many errors.

---

### Post by heimo on 2005-07-26
Try moving /var/lib/dpkg/info/gnome-pilot* files away or removing them, and try again. Some of those files is probably corrupted. That's my best guess.

---

### Post by tseliot on 2005-07-26
Can't I just uninstall gnome-pilot?

It doesn't work. I'll try as you said

---

### Post by tseliot on 2005-07-26
I can't move them, even by opening konqueror with sudo

---

### Post by tseliot on 2005-07-26
I'm almost getting used to screw Ubuntu64 up every 2 days...

Shall I proceed with a fresh installation? 

(Fortunately my Home dir is not on the same partition as the operative system)

---

### Post by heimo on 2005-07-26
Before fresh install, it doesn't cost much to try
 ```
sudo rm -f /var/lib/dpkg/info/gnome-pilot*
``` 
If that fails to remove the files, your filesystem is badly messed up. In that case, I'd try running fsck on it. But somehow I think it's just couple of files, bad dpkg database, just as azz said.

EDIT: And after that you should probably try 
 ```
sudo apt-get remove gnome-pilot
sudo apt-get install gnome-pilot

```

---

### Post by tseliot on 2005-07-26
You're GREAT man. You saved me!!!


THANKS

---

