---
title: "Correct way to upgrade from 12.04.1 to 12.04.2 to get 3.5 kernel?"
date: 2013-03-17
forum: Installation &amp; Upgrades
---

### Post by ahallubuntu on 2013-03-17
I'd like to get the 3.5 kernel in 12.04.1 but don't want to add any sources to my repositories that won't be supported until 2017.  3.5 hasn't automatically showed up as an update since the release of 12.04.2 - still stuck on 3.2.0.38.  Adding the "upubuntu-com" source would probably do it, but isn't that going to break at some point before 2017?  I just want the officially supported, stable 3.5 kernel for 12.04.2.

---

### Post by sanderj on 2013-03-17
It looks like 12.04 precise provides a 3.5 kernel; see [http://packages.ubuntu.com/precise/kernel/](http://packages.ubuntu.com/precise/kernel/) . Maybe you need to activate special source options, like 'security'

So I would say it's supported.

---

### Post by ahallubuntu on 2013-03-17
Thanks, but I already have "http://security.ubuntu.com/ubuntu" in my apt sources.list .  

In fact, I have a new install of 12.04.2 (3.5 kernel) on another computer, and its apt sources.list is identical to the one I'm using on 12.04.1 .

How does one know to grab 3.2 kernel updates and the other 3.5 kernel updates?

---

### Post by plucky on 2013-03-18
> **ahallubuntu said:**
> Thanks, but I already have "http://security.ubuntu.com/ubuntu" in my apt sources.list .  

In fact, I have a new install of 12.04.2 (3.5 kernel) on another computer, and its apt sources.list is identical to the one I'm using on 12.04.1 .

How does one know to grab 3.2 kernel updates and the other 3.5 kernel updates?

If you do normal updates on a 12.04.1 system, it will upgrade your kernel to 3.5 and your system to 12.04.2.

Post your **Sources.list** file.

What does ```
sudo apt-get update && sudo apt-get dist-upgrade
``` show you?

Good Luck

---

### Post by howefield on 2013-03-18
> **plucky said:**
> If you do normal updates on a 12.04.1 system, it will upgrade your kernel to 3.5 and your system to 12.04.2.

No, it won't.

If you want the 3.5 kernel you will need to fresh install with 12.04.2 or manually install the relevant packages.

---

### Post by Cheesemill on 2013-03-18
You can upgrade your system to a full 12.04.2 installation (with the upgraded kernel and graphics stack) with the following command...
```
sudo apt-get install linux-generic-lts-quantal xserver-xorg-lts-quantal
```

For more information on the LTS Enablement Stack check out the wiki...
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by plucky on 2013-03-18
Learn something every day.

Just assumed that 64-bit system that I installed 12.04.2 and which uses the 3.5 kernel was the same as my x86 systems.

Just looked at my x86 test system which was upgraded from 10.04 and it is still using the 3.2 kernel.

Ran the commands given by @Cheesemill and the system is now running the 3.5 kernel.

Thanks Chaps

Plucky

---

### Post by mörgæs on 2013-03-18
That was news to me, too. Thanks. 

I thought that all 12.04.x installations would reach the same version of packages after applying all updates, but apparently not.

---

