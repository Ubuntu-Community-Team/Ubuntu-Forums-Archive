---
title: "OEM Install?"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by mark on 2005-10-14
Has anybody done the OEM install yet?  I just gave it a "dry run" up to partitioning and so far it looks the same as a normal install.  I'm assuming/hoping that the magic happens after it completes & reboots...

I'm gonna throw a scratch drive in my system sometime this weekend and run it through, but I was curious to see if anybody else had any feedback on this method.  Odd, there seems to be no documentation on this, anywhere (at least that I've been able to find).

---

### Post by mark on 2005-10-16
Tests with the Ubuntu 5.10 “OEM” Installer

Goal: To enable the installation of Ubuntu GNU/Linux on a variety of computers, with the target user having unknown networking capabilities.  The desired result is that an end-user that is possessed of broadband Internet connectivity should have a positive experience.

Initial results of very desultory testing of the Ubuntu 5.10 GNU/Linux “OEM” installer.  NOTE: This test supposes some form of broadband Internet access is available on end-user installation – dial-up is not a methodology I have an opportunity to test.

Case One:  Install with no network connectivity:

1.Install proceeded as usual; responded to queries regarding language, keyboard, etc.
2.Slowed on attempt at DHCP detection; resolution was to skip network detection at this time.
3.Remainder of install as per normal.
4.“First-time” (end-user) boot: required access to System > Administration > Networking to set up and enable networking; subsequent to network enable, necessary to enable APT repositories (via System > Synaptic Package Manager, System > Update Manager or by manually editing /etc/apt/sources.list).

Case Two:  Install with DHCP (i.e. a router) but no network connectivity:

1.Install proceeded as usual; responded to queries regarding language, keyboard, etc.
2.DHCP detection as normal; install proceeds.
3.“First-time” (end-user) boot: necessary to enable APT repositories (via System > Synaptic Package Manager, System > Update Manager or by manually editing /etc/apt/sources.list).

Case Three:  Install with full network connectivity:

1.Install proceeded as usual; responded to queries regarding language, keyboard, etc.
2.DHCP detection as normal; install proceeds. 
3.Enable Universe and Multiverse in  System > Synaptic Package Manager, System > Update Manager or by manually editing /etc/apt/sources.list.

Discussion:  Localization is good (for English-speaking countries; at least, I assume so – it seems good for USA English); the question is what to do about connectivity.  There are still many people out there that use dial-up – how do we deal with them?

---

### Post by Nasso on 2005-10-16
how does the configuration, that you get when you restart you computer after install, look?
I assume that you dont have and pictures? anyone know if there are any screenshots anywhere?

---

### Post by mark on 2005-10-16
[QUOTE=Nasso]how does the configuration, that you get when you restart you computer after install, look?
I assume that you dont have and pictures? anyone know if there are any screenshots anywhere?[/QUOTE]
All the dialogues look pretty much the same as a "normal" install.  I don't know how to do screenshots of the process.  And after the "end-user" reboot, it looks just like a "normal" install.

---

