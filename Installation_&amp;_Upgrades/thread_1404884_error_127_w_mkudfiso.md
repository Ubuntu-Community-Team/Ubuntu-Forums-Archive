---
title: "error 127 w/ mkudfiso"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by jsmnuk on 2010-02-11
I am trying to install a Blu-Ray authoring tool from SourceForge.net in Ubuntu 9.10: "mkudfiso-svn-checkout-20100208.tar.gz" . As you can see from the screenshot, I started by configuring the "mkudfiso" file and sending it to "~/src". The "configure" and "make" commands went OK, but when I did the "make install" command, it couldn't find the command "@MKDIR_P@" and I got an "Error 127" message. I had found that the makefile from the **old version** of this program (mkudfiso-20080323-0107.tar.gz) contained the script line "MKDIR_P=@MKDIR_P@" , but the new version (mkudfiso-svn-checkout-20100208.tar.gz)  makefile did not have that line. 

I have tried to install by: 1) not using "sudo" for "make install", and 2) editing the new version makefile script by squeezing in the script line "MKDIR_P=@MKDIR_P@" in the same place as in the old version makefile and trying to install again. Neither way is working; the installation needs that command in order to go any further.

Any ideas? I'm into making Blu-Ray movies, not decrypting them. And yes, I have "build-essentials" installed.

---

### Post by Satoru-san on 2010-02-11
you set your prefix to /~/src ... this will not work 
as you can see 

```
Satoru@localhost ~ $ ls /~/
ls: cannot access /~/: &#12381;&#12398;&#12424;&#12358;&#12394;&#12501;&#12449;&#12452;&#12523;&#12420;&#12487;&#12451;&#12524;&#12463;&#12488;&#12522;&#12399;&#12354;&#12426;&#12414;&#12379;&#12435;

```

You need to configure it with the prefix of ~/src
also make sure the src directory exists.

---

### Post by northrup on 2010-02-12
It looks like it's just trying to create a directory; maybe replace the @mkdir_p@ "command" with just mkdir?  Linux script files (especially makefiles and such) are far from my expertise, but that would be my guess.

---

