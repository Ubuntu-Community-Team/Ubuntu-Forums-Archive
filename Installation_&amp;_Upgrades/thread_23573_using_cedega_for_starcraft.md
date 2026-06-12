---
title: "using cedega for starcraft"
date: 2005-04-02
forum: Installation &amp; Upgrades
---

### Post by Arachnopuppy on 2005-04-02
I just downloaded cedega.  Been reading their "how to" file for a while but I still don't know how to install it.  Anyone that have cedega can help?

[http://downloads.transgaming.com/files/Cedega_howto_4.3-1.1.1.1.txt](http://downloads.transgaming.com/files/Cedega_howto_4.3-1.1.1.1.txt)

---

### Post by bored2k on 2005-04-02
After you install cedega.
In a terminal go to the Starcraft disc. Find the installer name [setup.exe or install.exe, whatever it is] and run 
cedega setup.exe [change this with the real installer .exe name], after that, its a normal install .

---

### Post by Arachnopuppy on 2005-04-02
Um... I don't even know how to install cedega.  I'm a newbie with ubuntu.  WHat's the command to install cedega in terminal?

---

### Post by bored2k on 2005-04-02
[QUOTE=Arachnopuppy]Um... I don't even know how to install cedega.  I'm a newbie with ubuntu.  WHat's the command to install cedega in terminal?[/QUOTE]
 It depends, what cedega file do you have, a .deb? a .tgz? an .rpm? a .bin?

---

### Post by Arachnopuppy on 2005-04-02
Which one do I need for ubuntu?

---

### Post by bored2k on 2005-04-02
[QUOTE=Arachnopuppy]Which one do I need for ubuntu?[/QUOTE]
 Any will do, preferably the .deb.
After you get it, sudo dpkg -i filename.deb

---

### Post by Arachnopuppy on 2005-04-03
keep getting error.

root@Arachnopuppy:/home/hector # sudo dpkg -i cedega_4-1.3-1_i386.deb
Selecting previously deselected package cedega.
(Reading database ... 62846 files and directories currently installed.)
Unpacking cedega (from cedega_4-1.3-1_i386.deb) ...
dpkg: dependency problems prevent configuration of cedega:
 cedega depends on libpng3; however:
  Package libpng3 is not installed.
dpkg: error processing cedega (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cedega

---

### Post by NateC on 2005-04-03
Yes I am getting that error too.

---

### Post by Buffalo Soldier on 2005-04-03
[QUOTE=Arachnopuppy]Um... I don't even know how to install cedega.  I'm a newbie with ubuntu.  WHat's the command to install cedega in terminal?[/QUOTE][QUOTE=Arachnopuppy]keep getting error.

root@Arachnopuppy:/home/hector # sudo dpkg -i cedega_4-1.3-1_i386.deb
Selecting previously deselected package cedega.
(Reading database ... 62846 files and directories currently installed.)
Unpacking cedega (from cedega_4-1.3-1_i386.deb) ...
dpkg: dependency problems prevent configuration of cedega:
 cedega depends on libpng3; however:
  Package libpng3 is not installed.
dpkg: error processing cedega (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cedega[/QUOTE]I have no experience in running Cedega. But I love starcraft.

Anyway, something out of topic. Running as root user is kinda dangerous, especially for a newbie. Just wanted you to know that and curious why don't you just use the **sudo** command?

---

### Post by adun on 2005-04-03
ehm, obviously cedega depends on libpng3, so install it...

---

### Post by NateC on 2005-04-03
[QUOTE=adun]ehm, obviously cedega depends on libpng3, so install it...[/QUOTE]

;) yeah that'd probably work, will try. Can't believe I was so stupid.

---

### Post by Arachnopuppy on 2005-04-03
It worked!!!!!  You can download libpng3 at [http://packages.debian.org/testing/libs/libpng3.html](http://packages.debian.org/testing/libs/libpng3.html)

---

### Post by NateC on 2005-04-03
Indeed, it does work, but after you restart, or re-login, steam will not run.

---

