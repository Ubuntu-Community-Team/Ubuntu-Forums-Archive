---
title: "Kernel keeps trying to downgrade?"
date: 2014-07-18
forum: Installation &amp; Upgrades
---

### Post by terrykiwi83 on 2014-07-18
Ok so currently I have the following kernel installed on my Ubuntu 14.04 x64 Machine

> 
Linux POSEIDON 3.15.5-031505-lowlatency #201407091543 SMP PREEMPT Wed Jul 9 19:52:10 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


And Update Manager keeps trying to "Update" my kernel and download this version:

Kernel 3.13.0

Is there any particular reason for this and can I stop update manager from recommending it?

Cheers

---

### Post by ibjsb4 on 2014-07-18
You should have linux-headers-lowlatency installed.  That would give you automatic kernel updates.  Have you anything else like that installed?  Like linux-image-current-generic; linux-image-generic; ect.

---

### Post by Bucky Ball on 2014-07-18
*Thread moved to **Other OS/Distro Support**.*

Although based on Ubuntu, the Poseidon Linux spin is not supported in the main support areas here. Good luck.

---

### Post by terrykiwi83 on 2014-07-18
Posiedon Linux? Posiedon is the name of my computer not the distribution.

---

### Post by terrykiwi83 on 2014-07-18
> **ibjsb4 said:**
> You should have linux-headers-lowlatency installed.  That would give you automatic kernel updates.  Have you anything else like that installed?  Like linux-image-current-generic; linux-image-generic; ect.

This is what I have installed

```

terry@POSEIDON:~$ dpkg --list | grep linux-image
ii  linux-image-3.13.0-30-generic                               3.13.0-30.55                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.14.0-031400rc4-generic                        3.14.0-031400rc4.201402232235                       amd64        Linux kernel image for version 3.14.0 on 64 bit x86 SMP
ii  linux-image-3.15.5-031505-generic                           3.15.5-031505.201407091543                          amd64        Linux kernel image for version 3.15.5 on 64 bit x86 SMP
ii  linux-image-3.15.5-031505-lowlatency                        3.15.5-031505.201407091543                          amd64        Linux kernel image for version 3.15.5 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-30-generic                         3.13.0-30.55                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                         3.13.0.30.36                                        amd64        Generic Linux kernel image
terry@POSEIDON:~$ 

```

Not sure what to do next really?

---

### Post by ibjsb4 on 2014-07-18
If you remove linux-image-generic that should stop the 3.13 kernel update.

Again, if you want auotmatic updates for your lowlatency kernel, install linux-image-lowlatency.

Edit
Synaptic may give you more
[ATTACH=CONFIG]254827[/ATTACH]

---

### Post by coffeecat on 2014-07-19
> **terrykiwi83 said:**
> Posiedon Linux? Posiedon is the name of my computer not the distribution.

It wasn't clear where you posted originally, so I've moved this to Installation & Upgrades, which would be suitable. Sorry for the inconvenience. There is a Poseidon Linux based on Ubuntu and people are for ever posting requests for help with Ubuntu-derived non-official distributions in the areas reserved for Ubuntu and the official Ubuntu flavours only, all the while protesting that they are running Ubuntu. Hence the mistake. 

But to your problem. The linux-image-lowlatency series in the main 14.04 repository is 3.13, so if you install that metapackage, your system will still try to install 3.13 series kernels, albeit the low latency ones. I agree with ibjsb4 that if you remove the linux-image-generic metapackage, you should no longer get generic kernel upgrades of the 3.13 series. But for people to be able to advise a complete solution, I suggest you describe how you installed the 3.15 series kernels in the first place. I see you also have a 3.14 kernel. PPA? Compiled from source?

Perhaps you could also clarify which version of Ubuntu 14.04 you are running. The standard Ubuntu or Ubuntu Studio or something else? It might be relevant.

---

