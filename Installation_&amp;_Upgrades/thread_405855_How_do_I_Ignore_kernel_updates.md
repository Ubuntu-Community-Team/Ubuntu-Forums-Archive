---
title: "How do I Ignore kernel updates?"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by Tamerz on 2007-04-10
I have a server with custom RAID modules installed. I don't want to install the kernel updates and wipe it out. When I run an "apt-get upgrade" it shows one of the packages to be installed as "linux-amd64-server" but also shows a "linux-image-amd64-server" package being kept back.

---

### Post by bulldog on 2007-04-10
Go into your packet manager synaptic's and lock the current kernel.
This will avoid updates.

It's under the tab 'package' in synaptics

---

### Post by Tamerz on 2007-04-10
Sorry, I should have mentioned that there is no X on that machine. Command line over SSH only, so no Synaptic. Is there a way to do this from the shell?

---

### Post by bulldog on 2007-04-10
Well I saw a posting  in an other thread about locking a kernel.
And it seems you can try ```
sudo aptitude forbid-version package_name
```

[http://ubuntuforums.org/showthread.php?t=405083](http://ubuntuforums.org/showthread.php?t=405083)

---

