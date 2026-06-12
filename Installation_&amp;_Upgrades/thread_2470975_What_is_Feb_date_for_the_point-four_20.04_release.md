---
title: "What is Feb date for the point-four 20.04 release?"
date: 2022-01-18
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2022-01-18
I've seen that the "point-four" release for Ubuntu-20.04 LTS is set for sometime next month (February 2022).  

Does anyone know if there is a specific date set for this?

Also, would anyone know which kernel it will arrive with?

My own guess is that it may be kernel version 5.13.  (This is based only on the fact that 20.04.3 came with version 5.11.)  Thanks.

---

### Post by deadflowr on 2022-01-18
Feb [s]27th[/s] 24th; edit, kept reading wrong part, lol.
You can keep track of any changes here: [https://wiki.ubuntu.com/FocalFossa/ReleaseSchedule]("https://wiki.ubuntu.com/FocalFossa/ReleaseSchedule")

If you have the hwe kernel stack, then it'll most likely arrive before that, as they roll HWE out slowly.
See: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack]("https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack")

And yes, 20.04.4 should come with the 5.13 kernel series. It's the same one used by 21.10.
(the HWE stacks are the same the current short term release kernels.)

---

### Post by howefield on 2022-01-18
According to 

[https://wiki.ubuntu.com/FocalFossa/ReleaseSchedule](https://wiki.ubuntu.com/FocalFossa/ReleaseSchedule)
[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)

24th February for release and kernel 5.13

---

### Post by watchpocket on 2022-01-18
Excellent.  Thank you both!

---

### Post by tea for one on 2022-01-18
> **watchpocket said:**
> My own guess is that it may be kernel version 5.13.  (This is based only on the fact that 20.04.3 came with version 5.11.)  

Kernel 5.13.0-25 arrived today 18 January 2022.
```
edited@edited:~$ ls /boot | grep vmlinuz-
vmlinuz-5.11.0-44-generic
vmlinuz-5.11.0-46-generic
[COLOR="#0000FF"]vmlinuz-5.13.0-25-generic[/COLOR]
edited@edited:~$ 
```
Although the version is still
```
edited@edited:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	[COLOR="#0000FF"]Ubuntu 20.04.3 LTS[/COLOR]
Release:	20.04
Codename:	focal
edited@edited:~$
```

---

### Post by watchpocket on 2022-01-18
I'm slightly confused that the Wikipedia [says that kernel 5.13 has reached EOL as of September 2021]("https://en.wikipedia.org/wiki/Linux_kernel_version_history").
What does that actually mean, if 5.13.25 was released today?

Using 5.13.25 with 20.04.3 is for the adventurous, no?   Isn't 5.4.0.xx considered more stable?

---

### Post by CatKiller on 2022-01-18
> **watchpocket said:**
> I'm slightly confused that the Wikipedia says that kernel 5.13 has reached EOL as of September 2021.
What does that actually mean, if 5.13.25 was released today? 

That means that there aren't updates for 5.13 from the kernel developers. There are updates from the Ubuntu developers. Bugfixes and security updates are patched into Ubuntu packages. 

> Using 5.13.25 with 20.04.3 is for the adventurous, no?   Isn't 5.4.0.xx considered more stable?

No. 5.4 is "stable" in the sense that it doesn't change, for those users who rely on things not changing. Support for new hardware comes with the new kernels, which is why newer kernels are part of the Hardware Enablement stack.

5.13 debuted for Ubuntu in 21.10 where it was tested for a while, then it's been in HWE-Edge for a while already, then it will roll out for everyone as the HWE kernel, and then they'll make a 20.04.4 install image that includes it.

---

### Post by watchpocket on 2022-01-18
Thank you for that very clear explanation!

---

