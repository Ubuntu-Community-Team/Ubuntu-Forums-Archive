---
title: "Application installation in Ubuntu...."
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by phillife on 2007-06-10
Hi there,

Forgive me for my kiddy questions regarding application in Ubuntu. As i m a windows users, i am so used to double clicking the msi or exe on installation. But here i am reading about Synaptic package manager, Sudo CLi, etc i am totally lost....

Please help me to clarify a few points below:

1) In Linux ( Ubuntu) installation of application must either be done in a automatic installer such as synaptic package maneger or in the terminal CLI?

2) If it is to be done in the Synaptic manager, the repositories contain all that is preloaded in the system? What happen if the application is not in the Synnaptic manager?

3) How do i install application not in the Synaptic manager?

4) I download a tar.gz application ( thunderbird 2) how do i install it?

Thanks alot!

---

### Post by 505 on 2007-06-10
Most software in the Linux world is distributed as source code. By compiling the software yourself you make sure it works on your system. But because most users don't like to compile their software there are package managers. Synapitic is one such package manager. It contains many programs, precompiled and configured for your distribution/system.
Synaptic contains repositories. It does not display what is preloaded on your system, but what it can download from the repositories' servers. Most programs you ever need are in Ubuntu's repositories. If not, you have a few options:
1. Find another repository that has that package. Although not always recommended, third-party repositories might not be safe.
2. Download precompiled stuf (the thunderbird tar.gz is that)
3. Download source code and compile it.

As for the thunderbird package, open it and extract it. That just run it. To integrate it in your system, and replace Ubuntu's Thunderbird 1.5 is more complicated. See [this page](https://help.ubuntu.com/community/ThunderbirdNewVersion) for more information.

---

### Post by phillife on 2007-06-10
> **505 said:**
> 

As for the thunderbird package, open it and extract it. That just run it. To integrate it in your system, and replace Ubuntu's Thunderbird 1.5 is more complicated. See [this page](https://help.ubuntu.com/community/ThunderbirdNewVersion) for more information.

Soory, how do i just run it as mention above???

---

### Post by zvacet on 2007-06-10
[http://www.cutlersoftware.com/ubuntuinstall/]("http://www.cutlersoftware.com/ubuntuinstall/")

---

### Post by gmanlivid on 2007-06-10
yeah i got problems with installations too. I worked out how to use terminal to run sh and configure stuff, but alot of the apps are giving me errors. for example, one time it said i need to install something called "Flex" and another app said i don't have "KDE" or something. where do i get them? i looked for KDE but theres so many types, i don't know which one i need. i would easily just go online with my linux and use proprioters or watever, but my modem won't work under linux.

---

