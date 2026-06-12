---
title: "The SAFE way to Dual Boot"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by MarceloSP on 2007-06-01
Hello there.
I am new here, my first post, and I post it so that you or anybody else has to spend hours as I did, and as most of you did, trying to figure out some way to do the Dual boot running on low risks.

Here is a link to a file stored at symantec's ftp 

[ftp://ftp.symantec.com/public/english_us_canada/tools/pq/utilities/head.zip](ftp://ftp.symantec.com/public/english_us_canada/tools/pq/utilities/head.zip)

that has a file called mbrutil.exe, which at command line inside windows xp, you get the job done.

just be careful not to unzipp it all, it has some other executables, that will cause a total disgrace if you run, for example the file wipetrk.exe, that will instead of helping you to backup the MBR, delete it....watch out!!

only unzip the MBRUTIL.EXE it's all u need

very simple to use, if I can remember ( my memory is more volatile than querosene ) I typed:

c:\mbrutil /sh=mbr_backup.bin 

but check typing mbrutil /? first.

I already did it, and it copies the MBR to that file. Store it somewhere else.....for obvious reasons...pendrive, whatever....

it recovers the mbr too... 

Now I will do the dual boot install, without any fear to mess it up...
by the way, i found:

[http://phoenix.csc.calpoly.edu/~kvoelker/cgi-bin/counter/cis122/dual-boot.cgi](http://phoenix.csc.calpoly.edu/~kvoelker/cgi-bin/counter/cis122/dual-boot.cgi)

and 

[http://gentoo-wiki.com/HOWTO_Dual_boot](http://gentoo-wiki.com/HOWTO_Dual_boot)

as well as some more info in the forum that explains how to..

Hope it helps !
Marcelo
from Brazil

---

