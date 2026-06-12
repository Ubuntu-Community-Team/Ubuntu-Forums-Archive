---
title: "Problems After Upgrading To 10.04"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by ClarkG on 2011-03-31
Greetings and salutations,

I just upgraded to 10.04, and (well, long story short,) I had several issues with getting Ubuntu to run once I rebooted. I am currently able to get into Linux, but I have to hit left-shift during the boot and select a previous kernel to run. If I don't do this, my screen goes blank and I'm not able to log in.

How do I tell Linux to run this kernel automatically so I don't have to do it manually? I hope all this makes sense - I've been at this several hours and now I'm brain dead.

Thanks for the help

---

### Post by falko on 2011-03-31
Go to /etc/grub.d/ and make sure that the working kernel has the lowest number of all the kernels in there. For example, if your kernel is 50_linux, rename the file to 10_linux (just an example, but make sure it has the lowest number of all kernels).

---

### Post by sikander3786 on 2011-03-31
Welcome to the forums :-)

The easiest way to achieve what you want is to use a GUI to serve the purpose. See here.

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

You will find the option for default entry under Preferences in that GUI.

Keep updating and you might get those errors fixed.

```
sudo apt-get update && sudo apt-get upgrade
```

---

