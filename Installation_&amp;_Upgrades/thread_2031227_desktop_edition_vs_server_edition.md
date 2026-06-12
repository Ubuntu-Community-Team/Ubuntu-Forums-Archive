---
title: "desktop edition vs server edition"
date: 2012-07-21
forum: Installation &amp; Upgrades
---

### Post by vectorthorn on 2012-07-21
i was wondering if any one knew the difference between desktop edition and server edition.

i ASSUME that it is merely a matter of what packages are bundled with the initial download, but i would like to know that to be accurate before i install it.

i'm switching from fedora to ubuntu, and need to run services, etc, on the local machine, as it is my development machine and test server, as well as my personal computer.

i assume i can just install desktop edition and install any thing i want after i'm up and running, just like with fedora, right?

TIA

---

### Post by JKyleOKC on 2012-07-21
The most obvious difference is that the server edition has no GUI at all; only the command line. It omits the entire X window system. However you can install any of several desktop packages later, to add the GUI of your choice, if you want.

Less obvious differences exist, but since you plan to use the system as your personal workstation in addition to being a server, the GUI/no-GUI distinction is probably the most significant.

I'm using a desktop version here, but have installed a few server packages to fill my needs. Since the underlying kernel and system configuration is essentially the same for both, either way will work well.

---

### Post by vectorthorn on 2012-07-21
no initial gui, eh? that sounds like fun :D. freebsd did that same thing -you had to set the gui up yourself if you needed it.

well, i'm glad to hear they're other wise the same. that's what i was hoping for.

thanks.

---

### Post by codemaniac on 2012-07-21
+ Ubuntu server installs a server-optimized kernel by default.

---

### Post by vectorthorn on 2012-07-21
ok, now that's interesting. would you happen to know what makes this kernel optimised?
 
 i'll do a bit of digging on that while i run ubuntu from disk for a bit  to see if it's got all the packages i need (mdadm, asterisk, callweaver,  apache, bind, postfix, mysql, etc, etc). i was trying to see if i could  dig through a repo to make sure those packages exist for ubuntu, but i  could not find a way, so, i'll just run it from cd and check out the  software center, and, if they're there, i'll just go ahead and install.

thanks for that bit of news.

---

### Post by wheeze on 2012-07-21
> **codemaniac said:**
> + Ubuntu server installs a server-optimized kernel by default.

I thought the distinction between kernels was removed a while back. :confused:

---

### Post by CharlesA on 2012-07-21
> **codemaniac said:**
> + Ubuntu server installs a server-optimized kernel by default.

Starting with 12.04, both desktop and server versions use the same kernel.

If you intend to install a GUI on top of Ubuntu server, just install the desktop edition. It will be less work.

---

### Post by codemaniac on 2012-07-21
> **JKyleOKC said:**
> Since the underlying kernel and system configuration is essentially the same for both, either way will work well.

The linux-image-server package is a meta package that will install the latest Server kernel version, while the linux-image-generic package is a meta package for the latest Desktop kernel version.

---

### Post by codemaniac on 2012-07-21
> **CharlesA said:**
> Starting with 12.04, both desktop and server versions use the same kernel.

If you intend to install a GUI on top of Ubuntu server, just install the desktop edition. It will be less work.

Ok I see things have been changed in 12.04 server .

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Kernel](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Kernel)

---

### Post by vectorthorn on 2012-07-21
@codemaniac:
i read that link, and see no mention of the kernels being made the same, or other wise. can i assume your comment was an affirmation that they are in fact the same, as CharlesA mentioned?

thanks.

---

### Post by codemaniac on 2012-07-21
> **vectorthorn said:**
> @codemaniac:
i read that link, and see no mention of the kernels being made the same, or other wise. can i assume your comment was an affirmation that they are in fact the same, as CharlesA mentioned?

thanks.

In the above link i can see .Yes .

> The amd64 -generic and -server kernel flavors have been merged into a single -generic kernel flavor for Ubuntu 12.04. Given the few differences that existed between the two flavors, it only made sense to merge the two and reduce the overall maintenance burden over the life of this LTS release.

---

### Post by vectorthorn on 2012-07-21
oh, i see what i did: i only read the sections under the "KERNEL" heading. sorry.

---

