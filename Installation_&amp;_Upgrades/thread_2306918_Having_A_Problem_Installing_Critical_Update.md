---
title: "Having A Problem Installing Critical Update"
date: 2015-12-20
forum: Installation &amp; Upgrades
---

### Post by shane_faulkinbury2 on 2015-12-20
I'm having a problem installing a critical update for the 28 backspace thing on GRUB2!  When trying to install the update I get an error saying my boot sector doesn't have enough space.  Attached are screen shots of the update request, the error, and of my boot sector.  Please help me because I have a 1 TB HDD and I am only using 200 GB of it.

---

### Post by mörgæs on 2015-12-20
It's not about your boot sector, it's about your boot partition. 

How did the proposed solution work?

---

### Post by shane_faulkinbury2 on 2015-12-20
It didn't work and that is why I'm posting the question!

.

Also, I ran sudo apt-get clean and get the same message!

---

### Post by mörgæs on 2015-12-20
**sudo apt-get autoremove** is also worth trying.

---

### Post by shane_faulkinbury2 on 2015-12-20
But first, what does that remove?

---

### Post by howefield on 2015-12-20
> **shane_faulkinbury2 said:**
> But first, what does that remove?

From..

```
man apt-get
```

> autoremove (and the auto-remove alias since 1.1)
           autoremove is used to remove packages that were automatically installed to satisfy dependencies for other packages
           and are now no longer needed.

In this case, most likely an attempt to rid /boot of old kernels.

---

### Post by shane_faulkinbury2 on 2015-12-20
I tried it and it didn't work.  I get the same error.

---

### Post by ian-weisser on 2015-12-20
Ah, good old [LP #1357093]("https://bugs.launchpad.net/bugs/1357093"). Please click the 'affects me too' link at the top of the bug report.

Try using dpkg to remove one of the old kernels. WARNING: Don't remove the kernel you are currently running!
If you're not sure how to use dpkg, say so and we'll walk you through it. Also, provide the output of the command 'uname -r'
The goal is simply to free enough space in /boot for apt to complete installing the new kernel, so the package manager works again. And not causing more damage.

After apt works again, there are two ways to prevent the problem in the future:
1) Mark your wall calendar, and run 'sudo apt-get autoremove' every month or so.
2) Use the unattended-upgrades package to regularly run autoremove for  you. Edit the autoremove setting in  /etc/apt/apt.conf.d/50unattended-upgrades from 'false' to 'true'

---

### Post by shane_faulkinbury2 on 2015-12-20
I'm not sure how to run [COLOR=#000000]dpkg, but I've used it before.  Attached is the output for [/COLOR][COLOR=#000000]uname -r.[/COLOR]

---

### Post by ian-weisser on 2015-12-20
Try the following. Post all errors, please (er...copy-and-paste the text, terminal screenshots are much harder to use).
```
sudo dpkg --remove linux-image-3.19.0-37-generic
sudo apt-get autoremove
```

---

### Post by shane_faulkinbury2 on 2015-12-20
dpkg: dependency problems prevent removal of linux-image-3.19.0-37-generic:
 linux-image-extra-3.19.0-37-generic depends on linux-image-3.19.0-37-generic.


dpkg: error processing package linux-image-3.19.0-37-generic (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.19.0-37-generic

---

### Post by ian-weisser on 2015-12-20
Follow the chain down the rabbit hole:
```
sudo dpkg --remove linux-image-extra-3.19.0-37-generic
sudo dpkg --remove linux-image-3.19.0-37-generic
sudo apt-get autoremove
```

---

### Post by shane_faulkinbury2 on 2015-12-20
Much appreciated ian, that did the trick!

---

### Post by ian-weisser on 2015-12-20
Glad to read it.
Remember to look at Post #8 for ongoing prevention so it doesn't happen again.

---

