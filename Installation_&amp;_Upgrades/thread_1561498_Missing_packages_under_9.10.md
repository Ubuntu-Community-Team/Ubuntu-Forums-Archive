---
title: "Missing packages under 9.10"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by abell@safenet-inc.com on 2010-08-26
[FONT=Consolas][SIZE=3]I recently installed v9.10 (kernel version 2.6.31-14) and and trying to setup the desktop machine for some specific development.  I been using 7.10 and 8.10 for the last couple years without issues like this.[/SIZE][/FONT]
[FONT=Consolas][SIZE=3][/SIZE][/FONT] 
[FONT=Consolas][SIZE=3]Most of the packages I am trying to install state they are not available or obsolete?[/SIZE][/FONT]
[FONT=Consolas][SIZE=3][/SIZE][/FONT] 
[FONT=Consolas][SIZE=3]I looked through the package manager. [/SIZE][/FONT][FONT=Consolas][SIZE=3]In fact the list seems MUCH smaller than it was under 7.10 and 8.10.[/SIZE][/FONT]
[FONT=Consolas][SIZE=3] [/SIZE][/FONT]
[FONT=Consolas][SIZE=3]It also shows every package in the package manager as already installed.[/SIZE][/FONT]
[FONT=Consolas][SIZE=3]Under development I have gcc, gdb, binutils, etc. but there is no build-essentials or bison or automake, etc.[/SIZE][/FONT]
[FONT=Consolas][SIZE=3] [/SIZE][/FONT]
[FONT=Consolas][SIZE=3]I get the same result when I try apt-get - it fails to find the packages I have come to know and love.[/SIZE][/FONT]
[FONT=Consolas][SIZE=3] [/SIZE][/FONT]
[FONT=Consolas][SIZE=3]automake[/SIZE][/FONT]
[FONT=Consolas][SIZE=3]autoconf[/SIZE][/FONT]
[FONT=Consolas][SIZE=3]gawk[/SIZE][/FONT]
[FONT=Consolas][SIZE=3]awk[/SIZE][/FONT]
[FONT=Consolas][SIZE=3]bison[/SIZE][/FONT]
[FONT=Consolas][SIZE=3] [/SIZE][/FONT]
[FONT=Consolas][SIZE=3]All are missing from the package manager and apt-get install fails too.[/SIZE][/FONT]
[FONT=Consolas][SIZE=3] [/SIZE][/FONT]
[FONT=Consolas][SIZE=3]What am I missing.[/SIZE][/FONT]
[FONT=Consolas][SIZE=3][/SIZE][/FONT] 
[FONT=Consolas][SIZE=3]Adam[/SIZE][/FONT]
[FONT=Consolas][SIZE=3] [/SIZE][/FONT]

---

### Post by sisco311 on 2010-08-26
Hi and welcome to the forums!

Go to System -> Administration -> Software Sources and make sure that the repositories are enabled and in Synaptic click the Reload button to resynchronize the package index files from their sources.

---

### Post by abell@safenet-inc.com on 2010-08-26
Thanks,
 
I have the following selected (by default)
Canonical
Community
Proptrietary drivers
Software Restrictred
I can NOT select Software (no check mark appears, brown box gets cleared) - I tried it both ways with No change
CDrom is not selected
 
I have tried US Server and Main server with no change
 
I tried Other Software without a change as well.
 
Do I need to know about a magic repositiory?

---

### Post by abell@safenet-inc.com on 2010-08-26
I went  into sources>Updates and unchecked 'Important Security Updates' and 'Recommended Updates' and when this was applied, 15 new files were downloaded
and everything works as expected, I can see all the available packages now.
 
I went back in and checked these 2 again, everything still works.
 
Can anyone explain this behavior?
 
Thanks,
Adam

---

### Post by abell@safenet-inc.com on 2010-08-26
It seems the package index was not in sync for some reason.
a reload makes everything work as expected.
 
Thanks for all the help

---

