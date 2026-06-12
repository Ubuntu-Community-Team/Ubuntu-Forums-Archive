---
title: "Can you install ubuntu  rom package manager."
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by chrisv on 2005-04-14
Hello, 

I really do not like ISO's, mostly because my Cd burner has problems. So, would it be possible to get Ubuntu 5.04 using the package manager? That would be nice and easy. I mean that's what package managers are for, right? 

If it is possible please tell me how, because I searched the available packages and did not see Ubuntu 5.04.

---

### Post by andvaranaut on 2005-04-14
Hi Chris,

It depends on where you are upgrading it from.

If you already have Warty Warthog installed (Ubuntu 4.10), it is indeed possible. Open /etc/apt/sources.list and change each instance of 'warty' to 'hoary' (change also warty-security to hoary-security and the like). Then do apt-get update; apt-get dist-upgrade. You will download one hell of packages and probably get some minor quirks because of the massive updating of the system core components, but they will probably be sorted out by themselves once you reboot. I have used this method to update my Warthy (in small increments, as Hoary was maturing onto the final stable release) and it has worked flawlessly. apt is surely an impressive tool ;)

If you have another Debian-based (ie. using apt and .deb packages) distro installed, you can probably try; I think I have seen somewhere that it is possible with Debian, but it is probably a little risky (it is highly unlikely that you will lose any data, but you might end up with an unusable/unstable system). You would have to add the Hoary repositories to /etc/apt/sources.list, apt-get update, apt-get dist-upgrade, and likely apt-get install ubuntu-desktop. And probably use synaptic to remove all packages floating over from your previous installation. Not to be taken lightly, I think.

If you use Fedora or any other non-debian distro you're better off using the CD. They use deeply different package management systems and general layout. If you can't get a friend of yours to burn the ISO for you, you may order a CD free of charge from the Ubuntu website.

If you absolutely can't wait and can't get the CD writer to work, there are two possible solutions I envision... using a debian network installer and migrating the barebones debian system to ubuntu as soon as possible, or using qemu or any other emulator to install ubuntu in a virtual drive, then copying the virtual drive contents to your HD. I don't recommend any of them unless you really know what you are doing, though.

Best regards

---

