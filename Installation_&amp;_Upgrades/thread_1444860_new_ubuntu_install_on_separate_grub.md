---
title: "new ubuntu install on separate grub?"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by peedeeramone on 2010-04-01
may be a simple question but here goes: i have a tripleboot system, with ubuntu karmic, windows 7, and an unused mint distro. i also have an external hard drive. i want to install ubuntu studio as a separate installation to either where mint is or on a partition on the external hd. thing is i always seem to screw something up when i install a new grub with a new linux distro. though i can usually fix it, it tends to be a hassle id rather not deal with. my question is this:

can i install a new grub for ustudio on its own partition and have my original grub chainload into it, or would it be easier to just let it overwrite the old grub and run grub-configure or whatever the command is?

thanks

---

### Post by mikewhatever on 2010-04-01
Not only can, you should change the default grub installation location, when installing to an external media. The default is the MBR of the first hdd, which obviously isn't ideal. The way to change that is simple, after partitioning and entering username and password, you get the last windows before the actual file copying and installation begin, which has the 'Advanced' button in the bottom right corner. Hit that and change the default to (hdX,Y), where X,Y are the numbers pointing to the new Ubuntu installation.

---

