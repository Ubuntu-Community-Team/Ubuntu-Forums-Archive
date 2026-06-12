---
title: "How to run VirtualBox"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by jcobban on 2010-02-23
I have installed VirtualBox 3.1.4.  It appears in the package list displayed by Synaptic.  Now how do I run it?  It does not appear in any of the sub-lists under the Applications menu.  The How-Tos all say that it is supposed to be under Applications -> System Tools, but there is no such sub-menu on my Karmic system.

---

### Post by elliotbeken on 2010-02-23
i had the same problem what i did was to reinstall the package using the download that you used before

or

go in the terminal and just type virtualbox or sudo virtualbox

---

### Post by ajgreeny on 2010-02-23
I think it is listed in the menus as Sun VirtualBox, and I think also the executable file is called VirtualBox as well, and as linux is case sensitive, you must get it right.

Use command ```
locate -i virtualbox | grep /bin
``` to find all the files that have that name in /usr/bin.  The "-i" option in the command searches case insensitive, so will find it even if I'm not right about the file name case.

---

### Post by jcobban on 2010-02-25
When I rebooted Ubuntu the menu item appeared.  But I do not feel that I should have to reboot just to run something that Ubuntu thinks is an application.

---

### Post by ajgreeny on 2010-02-26
This may be because it was the PUEL version direct from Sun.  I think the repo version would install an icon.

---

