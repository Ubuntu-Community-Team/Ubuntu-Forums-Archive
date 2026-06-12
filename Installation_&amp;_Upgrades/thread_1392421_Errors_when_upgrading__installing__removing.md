---
title: "Errors when upgrading / installing / removing"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by admay on 2010-01-28
Needs some help please. I am running Karmic on a Dell M1330 laptop and it seems to have got itself into a position where whenever I run Update Manager, install new packages or remove packages I get an error popup which says "Package Operation Failed" and in the details gives this:

Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up hicolor-icon-theme (0.10-2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing hicolor-icon-theme (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 hicolor-icon-theme

The install/upgrade/removal seems to work. I have tried performing a reinstall of hicolor-icon-theme  but this makes no difference. I was going to try a complete removal and reinstallation but half of my software depends on it and would be removed as well. 

Is there anything else that I should be trying?

Thanks,

Andrew

---

### Post by admay on 2010-01-29
If this is too specific a problem is there any way that I can find out what exit status 2 means when returned by a post-installation script?

Andrew

---

### Post by Harbard on 2010-02-14
I have a partial solution for you.....

open a terminal and run this command:

sudo dpkg --configure -a

That will 'fix' the installation for you.

I too get this error message every time I install software.  I'm trying to eliminate it also

---

