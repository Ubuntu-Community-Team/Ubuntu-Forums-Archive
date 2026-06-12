---
title: "How to Minor Upgrade"
date: 2014-05-24
forum: Installation &amp; Upgrades
---

### Post by lalawawa on 2014-05-24
I was running 12.04 on my 2007 vintage Compaq Presario PC SR5130NX

I got 14.04 dvds on Amazon and installed them.

Tried installing 32 bit as an upgrade, when that didn't work, tried 64 bit, wiping th disk clean.

Both times, I would reboot over and over, and when I did, I got either a blank screen, or a screen with regular 1 pixel wite dots on it, in both cases with no mouse.  This was very time consuming as each time I rebooted I would wait several minutes to see if it would come to.

One reboot resulted in a visible desktop, but with no mouse.

I gave up.  An OS that will come up blank 80-90% of the time and with no mouse 100% of the time is useless.  14.04 will evidently have to wait until I get a new computer.  So I got out my old 12.04 dvds and re-installed 64 bit, wiping the disk clean.

At this point, "$ lsb_release -a" says
No LSB modules are available.
Distributor ID: Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise

As I understand it, most versions of 12 will soon be unsupported, so I want to upgrade to the latest sub-release of 12, which will continue to be supported for some time.  How do I do this?

---

### Post by Bashing-om on 2014-05-24
lalawawa; Hi !

Maybe a graphics issue in making 14.04 install ??

As you have reverted to 12.04.1 and it is working ( out of support ATI graphics card ?) .. to upgrade I prefer to use the terminal:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade ## this is not a release upgrade, but will install the latest kernel.

```
If you still desire 14.04 we will be glad to explore the issue with you and see what the problem might be.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by deadflowr on 2014-05-24
> As I understand it, most versions of 12 will soon be unsupported, so I  want to upgrade to the latest sub-release of 12, which will continue to  be supported for some time.  How do I do this? 				

Nonsense.

Your version is fully supported until 2017.
Version 12.04.2, 12.04.3, and 12.04.4 will need their kernels, and Xstack upgraded to the trusty stack when they are ready.
(sometime around August)

12.04.1 uses the same kernel and X stack as 12.04, so no need to upgrade it, if you don't want to.
[More here]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

---

