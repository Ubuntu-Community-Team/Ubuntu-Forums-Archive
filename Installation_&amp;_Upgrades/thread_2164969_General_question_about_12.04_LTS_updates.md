---
title: "General question about 12.04 LTS updates"
date: 2013-08-02
forum: Installation &amp; Upgrades
---

### Post by lamer305 on 2013-08-02
Hi,

I would like to set up an Ubuntu Server and wondering if I should use 12.04 LTS or 13.04?

On one hand I like the idea to have the long term support, on the other hand I would like to have the newest versions
and bug fixes included.

Is it possible (and if yes, how?) to keep the 12.04 LTS up to date so it will contain the same features/versions etc. of the version 13.04,
or will there be still major differences between the versions even after applying all the available updates?

Thanks for an explanation!

---

### Post by TheFu on 2013-08-02
[http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release](http://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release) might explain stuff.  Latest is not always "best" - often, it means "buggy."

---

### Post by lamer305 on 2013-08-03
Great article, thanks!

A few fundamental questions are not covered exactly, maybe you can help me out with this:

Will the repositories for the LTS contain always the same versions of the packages (i.e. Nagios) like in the newer distributions (i.e. 13.04)?

And what is with the kernel? Can it be updated (with regular tools) on an LTS version so it basically will be as up to date as the newer distributions?


Thanks!

---

### Post by mikewhatever on 2013-08-03
Q:  Will the repositories for the LTS contain always the same versions of the packages (i.e. Nagios) like in the newer distributions (i.e. 13.04)?
A: Yes. Most package versions are kept unchanged, as that is the point of a stable release.

Q:  And what is with the kernel? Can it be updated (with regular tools) on an LTS version so it basically will be as up to date as the newer distributions?
A: No. Kernel updates only provide security patched, bug fixes, and, sometimes, support for newer hardware, but the original precise kernel 3.2.xxx will be supported for 5years. You can upgrade to newer kernels, as kernels from 12.10 and 13.04 has been backported to 12.04, and can be installed with:
```

apt-get install linux-image-generic-lts-quantal

apt-get install linux-image-generic-lts-raring

```
Support for those will last only throughout the life cycle of the original releases.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by TheFu on 2013-08-03
> **lamer305 said:**
> A few fundamental questions are not covered exactly, maybe you can help me out with this:
 Probably not. I don't know very much.

> **lamer305 said:**
> 
Will the repositories for the LTS contain always the same versions of the packages (i.e. Nagios) like in the newer distributions (i.e. 13.04)?
 How and when a specific version of a package gets updated in a release is not known to me.  I can only guess and that doesn't help you very much.  My expectations are that the version released remains the same, with only security patches back-ported.
The way that YOU patch the system also impacts how things are updated.  There are 2 different patching commands:
* apt-get upgrade
* apt-get dist-upgrade
Read up on the difference between these to understand the choices better. I do not know of any exact, definite, rules, however.  I use dist-upgrade weekly to keep kernels at the latest available levels, though a newer distro will always have a newer kernel if you _stay on the reservation_ and don't build kernels yourself.

> **lamer305 said:**
> 
And what is with the kernel? Can it be updated (with regular tools) on an LTS version so it basically will be as up to date as the newer distributions?!

The dist-upgrade option on apt-get will install a newer kernel, not just the back-ported patches to the current kernel.

PPAs are fantastic, but can be risky. You might want to read up on them. In short, you can make almost any updates that you wish if you run your own PPA. There can be difficulties due to dependencies. I think that is why distros have different releases - it is a way to manage base libraries and all the dependencies that follow.

It sounds like you want a rolling release distribution.  Gentoo and Arch are the most popular versions of that idea.  I've found that rolling releases often are unstable. Like I've said before, new is not often better.  Having new versions all the time can have a terrible impact on system stability. Dependency issues can become very complex too.
 
Perhaps the Ubuntu Help documents [https://help.ubuntu.com/](https://help.ubuntu.com/) will explain their overall philosophy?

Sorry, I don't have any definite answers.

---

### Post by lamer305 on 2013-08-04
Hi folks,

thanks for your answers, they were all very helpful! I will go for 12.04 LTS now.

Best regards
Heinz

---

### Post by lamer305 on 2013-08-04
Hi,

i´ve got a view more questions around the 12.04 LTS I didn´t find an answer yet, maybe someone could help.

Initially i thought that "LTS" (Long Term Support) means, that the most important/popular software packages will be maintained as packages,
so they can be installed/upgraded (via apt-get dist-upgrade) easily. I just installed 12.04, did an "apt-get update" and found out, that the
Apache2 server is only available in version 2.2.22, which is now 20 month old (the newest version is 2.2.25). Similiar it´s with the package
Nagios3 (version 3.2.3 is contained, which is now 3 years old).

My question now is: How do you install the newest (or newer) versions of these packages, if they are not available via apt-get directly (maybe 
you can attach other repositories in /etc/apt/sources.list ?), and does the installation of newer packages somehow affect the further, regular
update procedures of the overall server installation (apt-get update + apt-get dist-upgrade)?

And by the way: What is the best method to quickly find out which versions are actually installed on the server? I use dpkg -list, is that correct?

Thanks for your patience with me
Heinz

---

### Post by TheFu on 2013-08-04
If you always want the latest version of every package available, then you probably want a rolling release distro, NOT Ubuntu.
For a small number of programs, it is often possible to find a PPA from the developers that contains the latest versions available. I do this for nginx. PPAs are NOT from Canonical, so there is an increased risk that system stability can be impacted.  After adding a PPA to your system - read up on how to do that, it is very easy - updates will be integrated into the apt-get processes.

This is one of the greatest things about Linux package managers and the PPA facility.

When I want to know what version of something is installed, I use something like 
**$ dpkg-query -l fail2ban** or
**$ dpkg -l |grep -i ssh** if I'm not positive of the package name

---

### Post by mikewhatever on 2013-08-05
Please check out the [Stable Release Updates wiki]("https://wiki.ubuntu.com/StableReleaseUpdates").
As others have mentioned, if you want recent/new software, an LTS is not for you.

---

