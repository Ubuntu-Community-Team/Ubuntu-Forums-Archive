---
title: "eggdrop 1.6.18 &amp; tcl 8.5 from sources"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by dDaYb on 2007-04-22
Hi, 
I am trying to install eggdrop 1.6.18. 
what have I did:
1. downloaded and unpacked eggdrop sources;
2. /.configure --with-tcllib=/usr/local/tclib_donotremember (without --with-tcllib it was said that no tclib had been found)
3. got an error that tcl 8.4 was too old;
4. downloaded tcl 8.5a5 sources, unpacked;
5. /.configure;
6. make;
7. sudo make install;
8.  cd to eggdrop;
9. /.configure ;
10. make config;
11. make install;
12. got error:

> ./eggdrop: error while loading shared libraries: libtcl8.5.so: cannot open shared object file: No such file or directory
make: *** [modules] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 127

13. read readme:
> 6k. I GET "ld-elf.so.1: Shared object "libtcl80.so.1" not found" or
        "eggdrop: error in loading shared libraries libtcl8.1.so: \
        cannot open shared object file: No such file or directory" WHEN I TRY
        TO START MY BOT.

      './configure' is looking in the wrong place for Tcl; it looks like it
      compiled with one version of Tcl and tries to load another. Maybe your
      sysadmin upgraded Tcl and didn't tell you. In that case, you should just
      need to recompile your bot.

      Maybe, when upgrading, he didn't clean the old version of Tcl and
      './configure' is looking for the files in the wrong places, or trying
      to use different versions of tcl.h and libtcl*. Smack your admin and
      have him install Tcl properly. ;) 
14. sudo apt-get remove tcl8.4;
15. done steps 5-11 once again;
16. got the same error as in step 12.

Could you please help me how to install eggdrop without apt-get eggrop/tcl commands?

---

