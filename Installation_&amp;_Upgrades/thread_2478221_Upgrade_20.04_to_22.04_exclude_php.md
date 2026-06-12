---
title: "Upgrade 20.04 to 22.04 exclude php"
date: 2022-08-20
forum: Installation &amp; Upgrades
---

### Post by huhas12 on 2022-08-20
Hello, 

Can anybody shed some light on my problem?

I run ubuntu server and I would like to uprgade to the newest version without upgrading PHP7.4. My server runs Owncloud and php8.1 is not supported, so which would be the best way to do it without messing my installation?

Thank you in advance! :P

---

### Post by &amp;KyT$0P# on 2022-08-20
To get php 7.4 in 22.04 you could use [Ond&#345;ej Surý's PPA]("https://deb.sury.org/")

---

### Post by huhas12 on 2022-08-20
hello halogen2, 

Is it possible to guide me through? I have not yet upgraded to 22.04. Currently I use php7.4 can I use [COLOR=#232629][FONT=ui-monospace]sudo apt-mark hold php7.4?
[/FONT][/COLOR]

---

### Post by &amp;KyT$0P# on 2022-08-20
> **huhas12 said:**
> hello halogen2, 

Is it possible to guide me through?

Sorry, that's outside my knowledge level.  I have zero experience with or knowledge of in-place upgrades or Owncloud, and I'm anyway not familiar enough with Ubuntu Server to be able to guide.

> can I use sudo apt-mark hold php7.4

I wouldn't.  The php7.4 binary build for your current version of Ubuntu may depend on libraries that no longer exist in 22.04 due to being upgraded to newer versions - or, worse, this could cause a conflict with 22.04 packages and result in a damaged upgrade.  Using a php7.4 built specifically on/for 22.04 eliminates these risks.

---

### Post by Impavidus on 2022-08-22
Do you really have to upgrade to Ubuntu 22.04? Staying on 20.04 until Owncloud (I've no experience with that) supports PHP8 may be much easier.

---

### Post by SeijiSensei on 2022-08-22
I actually downgraded a server from 22.04 to 20.04 to solve a dependency problem with 22.04.

---

### Post by TheFu on 2022-08-22
I run nextcloud, which started as a fork of owncloud.  It is still on 18.04, but when I move to a newer release, my nextcloud will be put into an LXD container to reduce the total dependencies for that 1 system.  Using any container-based solution for things like this is a chief reason why containers were created.

Or you can use a virtual machine.  I'm using a VM now, running 18.04, but linux containers are 1/10th the overhead of a VM.

---

### Post by huhas12 on 2022-08-24
Yes, I will stick with this one. I will wait until owncloud supports php8, because I do not know what are the containers and how they work. I just run my owncloud in an Ubuntu VM.

Thanks for the reply!

---

### Post by TheFu on 2022-08-24
> **huhas12 said:**
> Yes, I will stick with this one. I will wait until owncloud supports php8, because I do not know what are the containers and how they work. I just run my owncloud in an Ubuntu VM.

Thanks for the reply!

The marketing of LXD: [https://linuxcontainers.org/lxd/introduction/](https://linuxcontainers.org/lxd/introduction/)   If you've heard of docker, it is like that, but more like a VM, but still very light, about 1/10th the overhead of a VM.

---

