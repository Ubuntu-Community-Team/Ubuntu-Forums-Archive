---
title: "Can't run Ubuntu"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by bex91 on 2010-03-16
Hi, I bought a Vaio VPC EB1J1E last week, and since then I've been trying to install Ubuntu 9.10.

I always get the same error: the screen goes blank and I have to force the laptop to shut down.

When I try to install it through a CD, I can get to the menu but when I click "Install Ubuntu" the screen goes blank. Through the alternate CD I get to install Ubuntu, but when the choice of the OS appears and I choose Ubuntu, the screen will go blank again.

I've already installed in my desktop with no problems.

I tried everything I found on the Internet but with no success. I also tried to install Linux Mint but the problem persists. It must have something to do with my pc's configurations...

Can anyone help me?

Thanks

---

### Post by dstew on 2010-03-17
If you think you have successfully installed Ubuntu using the Alternate Install CD, try booting into Recovery Mode. It gives you a command-line interface, and root privleges. Does this work OK? If so, you know that the basic installation is sound. That would mean the problem is configuration of your graphical user interface.

You can check this by entering the command **startx** on the command line. It it goes blank, then it is pretty certain you have to reconfigure your graphical interface. The interface is run by software called the xserver.

In older versions of Ubuntu you could do this with the command```
dpkg-reconfigure xserver-xorg
```After Hardy (8.04) you have to do some of it by hand. [This thread]("http://ubuntuforums.org/showthread.php?p=8302145#post8302145") is a kind of How-To on configuring your display. You can either do it from a Recovery mode boot (you don't need to preface the commands with sudo) or get a command-line console from your (failed) normal boot using the key combination Ctrl-Alt-F1 as mentioned in Step 4 of the How-To.

---

