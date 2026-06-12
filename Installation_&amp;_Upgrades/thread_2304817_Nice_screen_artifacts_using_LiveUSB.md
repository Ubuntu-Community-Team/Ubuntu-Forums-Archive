---
title: "Nice screen artifacts using LiveUSB"
date: 2015-11-30
forum: Installation &amp; Upgrades
---

### Post by gianluca9 on 2015-11-30
Hi to all community and technical staff.
It's been a while since ii used to play with Linux and Ubuntu, but now for some needs I want to come back the Unix system. And of course I stuck in an issue.
I am trying to install Ubuntu 15.10 (last release) on my laptop; it's a pretti "old" notebook HP-Pavilion dv5165 with a Geforce Go 7400 mounted on.
Here the problem: When I try to start Ubuntu from LiveCD (actaully a usb drive) I got a very nice colored screen full of artifacts, kind of rainbow. I cannot do anything...
I have the same behavior with any kind of Ubuntu based distro; I tried Ubuntu, UbuntuGNOME, Lubunutu, Xubuntu, Kubuntu, Linux Mint and all the versions 12.04, 14.05 and 15.10.
The only distro that seems to wotk is the 11.04, but it's not supported anymore.
The USB drive works, since I tried the live USB on another PC and it works perfectly. So I am wondering if this could be related with some Nvidia driver.
The only Linux distro that works on the wanted laptop is Fedora23.
Any solution or anyone else that got this issue?
Thanks

---

### Post by The Cog on 2015-11-30
As the live USB boots, you get an image of a keyboard and a little man. Pressing Enter here gets you some extra options. Try going into the extra options and enabling the nomodeset setting. I forget the exact key sequence though.

---

### Post by ajgreeny on 2015-11-30
> **The Cog said:**
> As the live USB boots, you get an image of a keyboard and a little man. Pressing Enter here gets you some extra options. Try going into the extra options and enabling the nomodeset setting. I forget the exact key sequence though.
It's F6 for the many and various boot-options.

Try nomodeset first, but if that does not work try others and you should find one that works for your Geforce card, which is the most likely cause of your problem.

---

