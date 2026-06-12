---
title: "server-expert install method not being honored in Dapper"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by jkugler on 2007-01-25
I'm trying to install Dapper using the server-expert method of installing.  I've looked in the pxelinux.cfg/default file, and there is a LABEL defined as server-expert, as indicated in the installer's help.  But, when I type server-expert at the 'boot:' prompt, I am told "Could not find kernel image: server-expert"  However, "install" "server" or "expert" all work fine.  Just not "server-expert."

](*,) 

This is a 6.06.1 Server CD, BTW.

Anyone else run into this? Anyone have a fix?

j

---

### Post by jkugler on 2007-01-25
Well, more digging.  the pxelinux.cfg/default file is, obviously, not used when booting off a CD.  The isolinux.cfg file in fact *does not* have a server-expert option, although there is a "lamp-server-expert" option.  So, the help file for the installer menu is wrong.

Here is what I did: I selected the expert install.  Since the CD is server-only, expert is implied to be server-expert, as indicated by the preseed file and the DEBCONF_PRIORITY=low parameter.

Sorry for the noise, but it would be nice if the help file was correct. :)

j

---

