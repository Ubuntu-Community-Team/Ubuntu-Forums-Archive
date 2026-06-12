---
title: "Can I get Breezy on this laptop?"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by kewa on 2005-11-15
I've received my Breezy CDs from Shipit and want to install it on an old Compaq Armada M7750 laptop.  It's only got 32Mb RAM which may be a flaw though.

I had tried to load Hoary some time ago without success.  That consistently fell over unpacking nic-extra-modules-2.6.10-5-386-di.

This time I wiped the hard drive and have tried repartioning as Linux drive and swap in various configurations.  Whatever I do in terms of setting a larger swap file it never seems enough as the installation always goes into low memory mode and Breezy says it's "Killed" when it gets to unpacking md-modules-2.6.12.9-386-di.  This happens whatever type of install I choose.

I know it's an old low spec laptop but it's ideal for me to tinker with Ubuntu and learn new things so I'd really like to get Breezy on if I can.  What's more frustrating is Win2K installs no problem - it's just not the OS I want to use.

I'd appreciate any ideas that might get me up and running even if it means somehow cutting the install right back and then loading the rest of the files on to a more basic setup.

Thanks a lot

---

### Post by kewa on 2005-11-16
Any ideas please?????

---

### Post by kalin on 2005-11-16
It appears someone else had the same problem before, here's the thread with the solution (the last post):

[http://ubuntuforums.org/showthread.php?t=50616](http://ubuntuforums.org/showthread.php?t=50616)

In short: the workaround is to create a swap partition and use it during the installation, to avoid going out of memory.

---

### Post by taurus on 2005-11-16
When you say a larger swap, how large are you talking about here?  I don't see why Ubuntu 5.10 wouldn't install on your laptop.  On the other hand, I recommand you use one of the lighter desktops like XFce4, fluxbox, or blackbox...  You will hate your machine if you intend to use Gnome or KDE!

---

### Post by estel on 2005-11-16
Can you do a server install?

---

### Post by kewa on 2005-11-16
Thanks a lot for the replies.

I never get as far as the Ubuntu Partition process before it falls over so I manually deleted all partitions on the hard drive and created a linux swap partition of varying sizes up to 2Gb none of which worked.

I've tried the server install but it falls over in exactly the same place - unpacking md-modules-2.6.12.9-386-di.

Next step is to try Kalin's suggestion and see if that does the trick otherwise it's either a lighter desktop which would be even newer ground or god forbid back to Win2k which has to be a last resort as I'm keen to get into Ubuntu in particular.

Thanks again

---

### Post by kalin on 2005-11-16
I tried the procedure above on a virtual machine with 32MB RAM (a normal server install fails exactly as you described it).

It seems that timing is important, you need to "swapon" as soon as the device node for the swap partition is created (that's after the CD drivers are loaded). Doing that right lets me install the server.

If you wait too long something goes wrong and brings me to the installer menu and fails to continue.

---

### Post by delaguer on 2005-11-17
I did try to install Hoary on my 266 MMX machine and it installed right away and it runs fine (slow but sure :D ), but that old machine has 160mb memory, so I guess the extra memory helps?!

if you want the lighter-version of Ubuntu, perhaps you could try Beatrix. It is Ubuntu-based distro and you feel like you are running Ubuntu. :smile:

---

