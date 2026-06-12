---
title: "updating ubuntu kernel"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by virag on 2007-09-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131268](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131268) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				i have dg33fb motherboard whose network card is not being identified
by ubuntu kernel 2.6.20 -15 generic .
 
so how can i connect to net to update kernel as network card is not being identified. ?

also i have windows installed so is there anyway that i can download kernel updates to windows and then run it on
ubuntu ?

---

### Post by PacketCollision on 2007-09-14
Hello, after doing some research, it appears that the driver has been backported to feisty, so you don't need to upgrade your kernel at all.  What you need to do is install the package 'linux-backports-modules-generic' from the 'feisty-updates' apt repository.

To do that, the easiest way is to download this file and get it to your linux machine:
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.20/linux-backports-modules-2.6.20-16-generic_2.6.20-16.11_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.20/linux-backports-modules-2.6.20-16-generic_2.6.20-16.11_i386.deb)
Then, on your linux machine run 
```

sudo dpkg -i linux-backports-modules-2.6.20-16-generic_2.6.20-16.11_i386.deb
sudo modprobe e1000_ich9

```

Let me know if those commands work, if they don't, please post the error messages.

---

### Post by Gremlinzzz on 2007-09-14
If you need too upgrade further the deb packages for 2.6.22-11-generic can be found here.

[http://packages.ubuntu.com/gutsy/base/](http://packages.ubuntu.com/gutsy/base/)
lookup linux

---

### Post by Gremlinzzz on 2007-09-14
> **Gremlinzzz said:**
> If you need too upgrade further the deb packages for 2.6.22-11-generic can be found here.

[http://packages.ubuntu.com/gutsy/base/](http://packages.ubuntu.com/gutsy/base/)
lookup linux

very helpful post
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

### Post by PacketCollision on 2007-09-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/feisty/+source/linux-backports-modules-2.6.20/+bug/121187](https://bugs.launchpad.net/ubuntu/feisty/+source/linux-backports-modules-2.6.20/+bug/121187) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				@Gremlinzzz:
True, that post to upgrade to the Gutssy kernel is helpful, but I was working off of information from the bug report that spawned this thread.  Virag's problem is the lack of support for the onboard intel network card, which according to [https://bugs.launchpad.net/ubuntu/feisty/+source/linux-backports-modules-2.6.20/+bug/121187](https://bugs.launchpad.net/ubuntu/feisty/+source/linux-backports-modules-2.6.20/+bug/121187) is supported in the latest release of linux-backports-modules.

Since I personally have experienced problems with the new kernel on this board (fixable, but not intuative unless you've spent *way* too much time configuring X with various arcane options and different drivers (being a gentoo convert has it's advantages sometimes)), so I was trying to suggest the option that doesn't require using alpha software.

I also think that the method of installing the 2.6.22 kernel discribed is generally a bad practice, and would be better done via dpkg and pinning or custom compiling.  However, it seems to work for people, so I guess no harm done. 

If the needed functionality can be supplied with a kernel module, I see no reason not to use the stock (supported) kernel and avoid things like messy scripts to temporarily upgrade apt to gutsy for one package.

---

### Post by virag on 2007-09-16
I installed the backports modules as instructed  and ran the commands on my ubuntu(2.6.20-15)

sudo dpkg -i linux-backports-modules-2.6.20-16-generic_2.6.20-16.11_i386.deb
sudo modprobe e1000_ich9

but the following error messages were displayed

dpkg:error processing linux -backports-modules-2.6.20-16-generic-2.6.20-16.11_i386.deb(--install):
cannot access archive:no such file or directory
Errors were encountered while processing:
linux-backports-modules-2.6.20-16-generic_2.6.20-16.11_i386.deb

---

### Post by PacketCollision on 2007-09-16
Are you running that command from the same directory as the archive is stored? If not, you have to prepend the path to the 'linux-backports-modules-2.6.20-16-generic_2.6.20-16.11_i386.deb' part.

---

