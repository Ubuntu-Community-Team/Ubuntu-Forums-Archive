---
title: "Stop Synaptic Updating one package"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by steveneddy on 2007-12-30
I am running Gutsy 64 bit and had a hwclock issue that required that I install the 32 bit version of **util-linux** from packages.ubuntu.com. 

It installed correctly using the 

```

sudo dpkg --force-architecture -i PackageName.deb

```

script to install 32 bit software on a 64 bit system.

hwclock is ticking and all other issues are working correctly now, but Synaptic wants to update back to the 64 bit version. 

The auto update manager stays on saying that I need to update and Synaptic doesn't show the version I installed. 

I need to lock Synaptic or tell Synaptic, dpkg or apt that I don't want to update that package. Since there isn't an installed version showing in Synaptic, I can't lock it or force version.

Any and all help appreciated.

Thanks.

---

### Post by confused57 on 2007-12-30
Maybe this thread will help:
[http://ubuntuforums.org/showthread.php?t=161190](http://ubuntuforums.org/showthread.php?t=161190)

---

### Post by steveneddy on 2007-12-30
But since it is not actually installed, the version showing in Synaptic cannot be locked.

The version of util-linux in Synaptic is the 64 bit version, is not installed, therefor cannot be locked.

I installed the 32 bit version of util-linux and it isn't showing up in Synaptic.

Using the --force-architecture switch made the package not registered in Synaptic lists.

Maybe there is a folder somewhere that I can remove the 64 bit version of util-linux so Synaptic won't see it anymore.

---

### Post by steveneddy on 2007-12-31
Sorry about the bump.

I know there is a way,but can't seem to remember.

---

### Post by steveneddy on 2008-01-03
No one seems to understand my problem clearly.

The software is** util-linux** and seems to be required my Ubuntu to operate correctly.

Due to problems with my version of util-linux (I am on 64 bit gutsy), I installed the 32 bit version of util-linux.

Now when I look in Synaptic, it is not marked as an installed program or package.

I am getting alerts from the update manager that I need to install this package.

If I install this 64 bit package, I will not have my 32 bit version that I installed on purpose able to complete solve the issues that i originally installed it for.

The quandary:

How to keep the update manager from looking at this package, that is not installed, and asking me to update or install said package?

How can I get synaptic or update manager to ignore this uninstalled package?

---

### Post by forestpixie on 2008-01-03
have you tried to lock the one you haven't got installed in synaptic

---

### Post by steveneddy on 2008-01-03
> **forestpixie said:**
> have you tried to lock the one you haven't got installed in synaptic

Yes - it didn't seem to help.

I have automatic updates turned off at this time, I just don't want to forget about it and one day I update and the issue starts all over again. the laptop is very stable right now and I just want to keep it that way.

I thought there was a folder or file that I could edit and Synaptic wouldn't look at that package anymore. Like the main list for Synaptic/apt.

---

### Post by Elle Stone on 2008-01-15
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin)

tells how to "pin" a package for debian.  Somewhere I read, maybe in a tutorial, how to follow the same steps for ubuntu.  I think the steps are pretty much identical, but I'm a newbie, so my "I think"s are not worth much.  Still, google around on apt pin ubuntu and you might find just the tutorial I think I saw.

Elle

---

