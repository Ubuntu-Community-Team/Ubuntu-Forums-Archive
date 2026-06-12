---
title: "There was a problem installing the selected software"
date: 2005-11-26
forum: Installation &amp; Upgrades
---

### Post by Doughsay on 2005-11-26
This is the message I get during a netboot install of Ubuntu breezy.  I tried it twice now. Same exact thing.  The first half goes well...I PXE boot the install image, it configures the network and runs the install by downloading everything it needs.  GRUB is installed and the installer wants to reboot.  I reboot, select the default boot in grub, and the installer continues...installing and configureing packages.  It gets about 6% or so and then gives me that message sayin that one or more packages failed to install, and something about bugs in the packages or out of disk space.  I'm definately not out of disk space.

Anyway...it says I can go back and try again, or go back to the package selecting step, but all it gives me is an OK.  After hitting it it drops me to the console and that's that.  Everytime I reboot, it goes through the boot up process with the ubuntu logo and everything but then drops me to the console again.

Can anyone help me out?  I've already done a succesful install of Ubuntu on my desktop and the netboot is the only way I can get it onto my cdrom-less tablet pc...

Thanks in advance for any help.

---

### Post by Doughsay on 2005-11-27
I solved the problem with the help from another thread:

[http://www.ubuntuforums.org/showthread.php?t=95178](http://www.ubuntuforums.org/showthread.php?t=95178)

After being dropped to the console I ran the following commands as suggested:

$ sudo apt-get update
$ sudo apt-get -f install
$ sudo apt-get install ubuntu-desktop

And everything works great!

The first two commands didn't do anything, but for a slightly different situation might be useful.

---

