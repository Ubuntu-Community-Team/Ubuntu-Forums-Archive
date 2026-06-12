---
title: "mono 1.1.12.1 installation issue"
date: 2013-02-25
forum: Installation &amp; Upgrades
---

### Post by aman pal on 2013-02-25
Hello everyone

I'm trying to install mono 1.1.12.1 in a Ubuntu 12.04 LTS linux server! Running as root I've made the .bin file executable by using:

```
chmod +x mono_1.1.12.1.bin
```and then execute it using:

```
./mono:1.1.12.1.bin
```Though it only changed command line. It accepts the code but doesn't install mono since i've even tried to check the installation with

```
mono -v
```and there was nothing. Am i doing something wrong here? Is mono 1.1.12.1 compatible with the linux version i'm using?

Thanks for the help
Best regards

---

### Post by dino99 on 2013-02-25
why not installing from the archives ?

[https://launchpad.net/ubuntu/+source/mono](https://launchpad.net/ubuntu/+source/mono)

---

### Post by MAFoElffen on 2013-02-25
> **dino99 said:**
> why not installing from the archives ?

[https://launchpad.net/ubuntu/+source/mono](https://launchpad.net/ubuntu/+source/mono)
Dino and Aman-

That's a question that ties into my questions... Sorry. I'm trying to remember this. What Aman is trying to do just baffles me!?! I "think" he just boinked his server install without realizing it.

Why install that version at all? "mono" runtime was installed by default on 10.04lts. But he is trying to install over it with an older version? If he succeeded he would lose compatibility with what he had "so far" for .NET app's.

Installing the binary manually instead of the .deb package, I'm not sure it checks version to abort with the message "already to current version." If it did check version, that's why his install failed. 

Of course if he also wanted the dev tools, "mono-complete" is the Ubuntu package that has the runtime, development tools (including compiler) and all the libraries.

Why not install that "mono-complete" package? Of course for 10.04, that package was version 2.4, and to compile code, I think you also needed "mono-devel"...

But mono 1.12.1? I thought mono was installed by default before v12.04?  And Ubuntu 8.04lts was updated through mono 1.2.6...

Why is he trying to install on something old (10.04lts) with something older? (mono 1.12.1) Is he trying/meaning to backport? He would have to uninstall the mono runtime first, right? It was default on 10.04lts, and more current than what he is trying to install, to be able to go backwards.

Current mono is now 2.10.8.10. If he went current, he would be then be compatible with current .NET app's. Installing that for Ubuntu 10.04lts:
> 
Ubuntu Lucid (10.04 LTS)

Users of Ubuntu 10.04 LTS (Lucid Lynx) can install 2.10.8.1 by using Synaptic from the badgerports repository. badgerports is an unofficial community project from one of the Debian/Ubuntu Mono developers to ship latest Ubuntu packages for Ubuntu LTS users. Please visit the URL below for full information on enabling these packages:

[http://badgerports.org/](http://badgerports.org/)

But if he upgraded to 12.04LTS, to keep his server to the current LTS support, he could go current natively through the repo's...

EDIT--
Aman-
The reason you might not have seen the version... from post #1 you had misspelling/syntax error. You said you used:
```

mono -v

```
Where it should have been "-V" or "--version" like this:
```

mafoelffen@maferr-ubuntu-1:~$ mono -V
Mono JIT compiler version 2.10.8.1 (Debian 2.10.8.1-5ubuntu1)
Copyright (C) 2002-2011 Novell, Inc, Xamarin, Inc and Contributors. www.mono-project.com
	TLS:           __thread
	SIGSEGV:       altstack
	Notifications: epoll
	Architecture:  amd64
	Disabled:      none
	Misc:          softdebug 
	LLVM:          supported, not enabled.
	GC:            Included Boehm (with typed GC and Parallel Mark)

```
If you use the following command, it should show you what mono packages are already installed:
```

dpkg -l | grep -i mono

```

---

### Post by aman pal on 2013-02-25
Hello guys. Thanks for the help but i really need mono 1.1.12.1 because its the recent version capable of running an admin tool for some bf2 servers im installing on ubuntu server 12.04. Do i have to install mono-runtime so i can install any version of mono? Is there any chance of downgrading mono?

Best regards

---

### Post by MAFoElffen on 2013-02-25
Wait one... Let me see if I can bring up one of my older 10.04LTS  backup test Servers. It's the only one I can check this on. Hopefully I didn't upgrade that (I can't remember).

---

### Post by aman pal on 2013-02-25
Ok but remenber i'm using ubuntu 12.04 server...

---

### Post by MAFoElffen on 2013-02-25
So here's what I found so far
```

Backport Packages

Mono is considered a "core framework" in Ubuntu, meaning it has many applications depending upon it (roughly 40 applications). Due to this, the chance of one of those applications breaking due to unexpected changes in their underlying framework is considered too high to risk an update.

As a result, Mono cannot officially be backported in Ubuntu.

```
Which means, when you uninstall the installed mono package about 40 applications would then crash and or be affected. (Keep a list of what gets uninstalled- just in case.

There is no deb package for mono v1.1.12 build for Precise.

I'm thinking since they say Ubuntu 8.04LTS came official with mono v1.2.6 and it was released in 4/08 (5 years ago), that the old mono precompiled binaries for 1.1.12 were compiled a year or more before that... So, what- over 6 years ago? Those 1.1.12 binaries may not run on a 3.x kernel. If the binaries don't run on them, then you are going to need to compile from source on your computer. Which would probably turn out better. 

BUT--- Then there's those 40 app's that use mono. If it were me, I would wait until you get it built before you uninstall the newer version, then install the built version. Then you are on your own testing what fails and seeing if you can patch it back together.

Without doing it myself, I don't see a clean way to do that. But then again, I have no idea what 40 apps those are.

Where to ask for that would probably be to email the mono package administrator at launchpad. He would know. 

But before you do any of that, you might want to read and try this beforehand:
[http://orangesquash.org.uk/~laney/blog/posts/2011/10/mono-gotcha/](http://orangesquash.org.uk/~laney/blog/posts/2011/10/mono-gotcha/)

---

