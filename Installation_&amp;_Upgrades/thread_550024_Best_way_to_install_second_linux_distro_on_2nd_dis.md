---
title: "Best way to install second linux distro on 2nd disk?"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by rfurman24 on 2007-09-13
I have a hd with Fiesty on it that I do not want to mess with. I have a second drive that I would like to  have its own boot loader but do not want it in control. The second disk already has a /boot partition. I want the first disk to control the second and chain load to the second boot loader. I want to use the second disk for playing with other linux distros. Is there a way this can be done so that the newly installed system will not control the existing system? The reason I would like to keep two separate boot loaders is in case I wanted to remove the hd and install in a different system. I need suggestions/help deciding the best easiest way to do this.

---

### Post by rsambuca on 2007-09-13
When I play around with different distros, I like to keep my ubuntu setup as my "main" distro like you.  

To keep the ubuntu grub in control of things, just make sure that the ubuntu drive is first in the bios boot order, and then when you install distro2 to the second drive, just make sure you direct its grub to load onto the second drive.  Then add distro2 to the bottom of the ubuntu /boot/grub/menu.lst file.  I have a bunch of distros on my rig right now set up this exact way.  You will have to change the drive numbers, but just for an example, here is the bottom of my menu.lst with the chainloaders so you can refer to it```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
#savedefault
makeactive
chainloader     +1

title           Gentoo
root            (hd2,6)
chainloader     +1


title           Debian
root            (hd2,7)
chainloader     +1

title           Sabayon Linux
root            (hd2,8)
chainloader   +1

```

---

### Post by kellemes on 2007-09-13
Is this what you want?
You simply point to the menu.lst in the second-OS bootpartition.
[http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile")

---

### Post by rfurman24 on 2007-09-13
That is what I was thinking. Thanks for the info and the quick reply.

---

### Post by rfurman24 on 2007-09-13
> **kellemes said:**
> Is this what you want?
You simply point to the menu.lst in the second-OS bootpartition.
[http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile")

I had read that and was a little unclear about what would happen if I installed the second boot loader in the second /boot partition. Rsambuca, I think, backed up what I was thinking after reading the page you posted. Thanks.

---

