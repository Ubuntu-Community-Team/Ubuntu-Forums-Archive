---
title: "Installing cdrtools in Kubuntu"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by omidomid on 2008-01-25
Hi, I'm a linux newbie and am trying to install a cd-writing software called cdrtools. I managed to extract the files, and then I used make to install it. It gives me a warning from the author, and then errors that my machine is unkown. I am using Kubuntu which I installed yesterday. I'm thinking I have to install some drivers or something first? Any help is much appreciated! :) here's the code:



root@OMID-PC:/home/omidomid/downloads/cdrtools-2.01.01# make
                W A R N I N G   Messages like:

gmake[2]: Entering directory `/tmp/cdrtools-2.01/libschily'
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/cvmod.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/dat.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/fcons.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/fdown.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/fdup.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/ffileread.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/ffilewrite.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/fgetline.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/fgetstr.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/file_raise.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/fileclose.d: No such file or directory
....

are caused by a GNU make bug and not by the Schily makefile system.

The related bug has been reported to the GNU make maintainers in 1998 but
as the bug has not yet been fixed, it seems that GNU make is unmaintained :-(
A working highly portable make program is at [ftp://ftp.berlios.de/pub/smake](ftp://ftp.berlios.de/pub/smake)
RULES/rules1.top:239: incs/Dcc.i686-linux: No such file or directory
RULES/rules.cnf:57: incs/i686-linux-cc/rules.cnf: No such file or directory
        ==> CONFIGURING RULES "incs/i686-linux-cc/rules.cnf"
loading cache ./config.cache
checking host system type... Invalid configuration `unknownCPU-unknownMFR-unknownOS': machine `unknownCPU-unknownMFR' not recognized

checking if /bin/sh is bash... no
checking for object suffix... o
checking for Cygwin environment... no
checking for mingw32 environment... no
checking for EMX/OS2 environment... no
checking for executable suffix... configure: error: installation or configuration problem: compiler cannot create executables.
make: *** [incs/i686-linux-cc/rules.cnf] Error 1
root@OMID-PC:/home/omidomid/downloads/cdrtools-2.01.01#

---

### Post by PmDematagoda on 2008-01-25
Not really answering your question here, but did you try k3b? It can be installed simply by using:-
```
sudo apt-get install k3b
```

---

### Post by Eck on 2008-01-27
He's trying to install the original developer's cdrkit that has been forked to wodim, genisoimage, and icedax because of differences of opinion between the author and the various Linux distributions (at first just Debian then most others as well) regarding free software licensing standards as well as the new udev ways of accessing optical drives.

Not only that, but the author doesn't use gnu make for his packages either, but requires a different version of make as well.

I forget the link to his site, but his packages contain extensive readme's as to what is needed.  One will, I believe, need to remove the distro's wodim, genisoimage, and icedax packages as well as install his make program for the installation to work.  And don't forget whatever other dependencies as far as dev packages that are listed in his documentation.

Really, he is right that there are currently bugs in the wodim fork.  However for most purposes the GUI tools such as K3b do work around most of these to accomplish whatever tasks we need.  It's kind of a pain in the neck to switch back to the original cdrkit stuff (cdrecord, makisofs, growisofs, etc that are included in his cdrkit packages).  There's a fellow over at the Debian forums that uses this and includes links in some of his posts to the developers website.  

It can be done but is it worth the trouble?  After the installation a user also needs to make changes in his configuration files to give the cd tools root permissions and there still may be interference from udev.  The fork (wodim, that is used by most major distro's these days) does not require permission changes and works fine with udev and even uuid's.  The original cdrecord stuff needs the old /dev ways of accessing the drives.

The original author's cdrkit is more developed and less buggy than the wodim fork.  Sort of like WineX/Cedega and Wine before Wine got much better in the past year.  If it was really easy it would be preferred from a usability standpoint, but I'm not sure about the free software standards of distro's like Debian.  The author has different opinions about what licenses are free and what are not.  He's got a whole web page on his site devoted to dissing the rest of the community regarding what has happened and claiming that only his version is really free.

---

### Post by omidomid on 2008-02-01
The reason I'm trying to install cdrtools is because I need to be able to control the burn process down to the very bit for this project I'm doing. I'm trying to follow this guide:

[http://www.instructables.com/id/Burning-visible-images-onto-CD-Rs-with-data-beta/](http://www.instructables.com/id/Burning-visible-images-onto-CD-Rs-with-data-beta/)

Is there any alternate cdr program you know of? Or can anyone help me get this one working? It says in the readme I need smake to get it to work, But I'm having difficulty installing that too: [click here]("http://ubuntuforums.org/showthread.php?t=685029").

---

