---
title: "Kernel Upgrade?"
date: 2005-11-18
forum: Installation &amp; Upgrades
---

### Post by aberry7670 on 2005-11-18
Hi all! 

I installed Ubuntu 5.10 and it is successfully running on my dual boot PC, wich is a Pentium 4, 2.80Ghz, 256MB, 40GB HDD. Now, when I issue the command uname -r it tell me that the kernel version is 2.6.12-9-386. I downloaded the i386 ISO image and now I believe that I should have downloaded the i686 image instead.

My question is since my PC is a Pentium 4 should I not be running the kernel version 2.6.12-9-686? Can I upgrade the existing kernel without upgrading all the apps that I installed using the Add Applications and Synaptic Package manager? If the upgrade is possible then what pacakge do I need to install and from where can I get the pacakge? To be honest I do not want to screw around too much with my current install because it works fine, but then again if the i686 kernel would be better then I am willing to take the chance.

Please suggest.

---

### Post by tseliot on 2005-11-18
[QUOTE=aberry7670]My question is since my PC is a Pentium 4 should I not be running the kernel version 2.6.12-9-686? Can I upgrade the existing kernel without upgrading all the apps that I installed using the Add Applications and Synaptic Package manager?[/QUOTE]

Have a look at this guide: [http://www.ubuntuforums.org/showthread.php?t=85917]("http://www.ubuntuforums.org/showthread.php?t=85917")

---

### Post by aberry7670 on 2005-11-18
Thanks for the reply. The link provided the right info. Now I am running the 686 kernel version.

---

### Post by cyborgspiders on 2007-03-14
As to not updating all packages, I am not sure. I just did a generic CD install of Ubuntu 5.10 (that is the disk I have). The install went very well on a Dell Latitude Laptop. Then, to upgrade the kernel.

$ gksudo "update-manager -d"

And now I am running Linux 2.6.15-28-386
What a great kernel updater!

---

### Post by deronde on 2007-03-15
Just an update on this.. with the Edgy updated 2.6.17-10 kernel I was getting all kinds of Soft lockups galore, so I desperately googled around to figure out how to upgrade my kernel in hopes of stopping it.. this thread definitely helped :)

I had to download and install (in order) with dpkg -i:

libc6_2.5-0ubuntu11_i386.deb
linux-headers-2.6.20-10_2.6.20-10.17_i386.deb
linux-headers-2.6.20-10-server_2.6.20-10.17_i386.deb
linux-image-2.6.20-10-server_2.6.20-10.17_i386.deb

I also installed this, but I'm not sure if it was necessary:
linux-libc-dev_2.6.20-10.17_i386.deb

Now apt-get will bitch every time I run apt-get upgrade saying that my libc6 is the wrong version.. if i run it with -f it wants to remove my libc6-2.5 but I'm afraid to let it. I'll just live with apt-get complaining with the peace of mind that my server will no longer soft-lock! (hopefully)

It's a stock emachines W2646 btw with ubuntu edgy 6.10. I'm pretty damn noob at this.. fedora and gentoo both crashed while trying to install on this machine.

---

### Post by perro84 on 2007-09-21
If you want to upgrade your Ubuntu Feisty Kernel to the last one (2.6.22-10) follow this simple tutorial!:
[Upgrade Ubuntu Kernel to 2.6.22-10]("http://www.justubuntu.com/install_2_6_22-10_ubuntu")

---

### Post by svenkatesan on 2007-10-03
Hi
If I don't have internet connection,how to upgrade the kernel?
I mean, what patches need to download?
This needed to get my wireless USB card.
Right now I am using Ubuntu 7.04 on 2.6.20.15.
Pl help.
Thanks

---

