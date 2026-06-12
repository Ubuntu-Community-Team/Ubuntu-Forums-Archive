---
title: "Install problem with base system"
date: 2004-10-15
forum: Installation &amp; Upgrades
---

### Post by Miguel1132 on 2004-10-15
I've been trying to install ubuntu using the download iso. Everything goes fine until the base system install starts and it aborts trying to install bsdutils saying it can't fetch it. Aren't the bsdutils on the iso disc. I even tried burning the iso at a slower speed but it made no difference. Any suggestions. I would like to try ubuntu.  

Thanks,
Mike

---

### Post by Miguel1132 on 2004-10-16
Greetings. Well, I finally solved the install problem. I originally burned the iso in WinXP only because I happened to be using it at the time. I decided to do the right thing and try to download and burn the iso in Linux. I simply used cdrecord to burn the iso and it installed perfectly. Apparently my burning software didn't like the iso. :-). Anyway, ubuntu is installed and I must say I like what I see. I am impressed by this distro. What is even more rewarding is that I was able to configure my Netgear wireless pci card without a problem. Congratulations to all those involved in this project.  It's been a while since I've used Debian, but I should be able to relearn. :-)

Regards,
Mike

---

### Post by sophomERIC on 2005-04-10
What model of Netgear NIC do you have? The install detects mine and installs fine, but does not actually work once inside the desktop environment. I have a 802.11 'super' g model.

---

### Post by beow on 2005-05-01
[QUOTE=Miguel1132]I've been trying to install ubuntu using the download iso. Everything goes fine until the base system install starts and it aborts trying to install bsdutils saying it can't fetch it. Aren't the bsdutils on the iso disc. I even tried burning the iso at a slower speed but it made no difference. Any suggestions. I would like to try ubuntu.  

Thanks,
Mike[/QUOTE]

A lot of people seems to have the same problem with bsdutils.deb on the installation disc. Seems that even though the downloaded iso image is correct (checked with md5sum) the burned image becomes corrupted in som cases. Could there be some specific pattern in that file that is hard to burn?

Nevertheless, I followed the workaround from 

[http://www.ubuntulinux.org/wiki/RecoveryFromBadInstallCD](http://www.ubuntulinux.org/wiki/RecoveryFromBadInstallCD)

which worked perfectly. The lucky thing with that workaround is that "wget" is installed early in the process so that it was accessible after the red screen. Think this is something that maintainers should consider, since it in fact is a "poor mans net installation" procedure.

---

