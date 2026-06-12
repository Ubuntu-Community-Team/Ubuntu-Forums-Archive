---
title: "Trouble installing Brother DCP 8025D"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by alighieri on 2006-11-09
I've run into serious trouble trying to install the driver for the Brother DCP8025D.

For some reason /etc/init.d/cups and/or /etc/init.d/cupsys appear to be missing so dpkg -i of dcp8025dlpr-1.1.2-1.i386.deb failed.

I thought ok, lets just reinstall cups using apt-get but no, i get the error 

E: The package dcp8025dlpr needs to be reinstalled, but I can't find an archive for it.

Ok, so lets try dpkg -r dcp8025dlpr
Nope

dpkg: error processing dcp8025dlpr (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 dcp8025dlpr

so now i'm stuck as installing gives the following errors

/var/lib/dpkg/info/dcp8025dlpr.postrm: line 3: /etc/init.d/lpd: is a directory
dpkg: warning - old post-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: is a directory
dpkg: error processing /home/toby/dcp8025dlpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 126
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: is a directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 126

](*,) 

Anyone any bright ideas?

---

### Post by zooooz on 2007-07-06
had the same problem. this helped me:
[http://ubuntuforums.org/showthread.php?p=468613]("http://ubuntuforums.org/showthread.php?p=468613")

on feisty (7.04) i first just used the System -> Adminstration -> Printing -> New Printer functionality of gnome. then i was able to make the printer spit out an error message on the page (ERROR NAME; configurationerror ... and so on. only tried printing with acroread though). then i failed to install the deb's from brother and purged the zombie installation from my system with the link above.
so i don't know if messing with these very bad deb's is necessary at all. does feisty have everything on board to make this printer work?
im not in the mood right now to test this on a fresh installation, so maybe someone else can clarify.

maybe someone will someday gain from this post, since the one it responds to is rather old itself. who knows...

---

### Post by quigi on 2008-04-05
I'm printing to a Brother 8840DN using cups (from Ubuntu Edgy or Breezy or Dapper -- don't know how to determine).  I set it up as a PostScript printer, so no need to mess with any debs or drivers.

It normally prints well, also from Windows clients (which print to the raw queue at IPP:ubuntuhost).  Windows always prints well.  But after Windows did, the *first* job from Linux fails with the error page that Zooooz quotes:
```

ERROR Name;
        configurationerror
COMMAND;
        setpagedevice
OPERAND STACK;
        --dictttype--

```

Immediately repeating the same printing command succeeds (be it lpr, a2ps, acroread->Print or anything).  I wish I knew how to fix this and make Linux print right the first time.

---

