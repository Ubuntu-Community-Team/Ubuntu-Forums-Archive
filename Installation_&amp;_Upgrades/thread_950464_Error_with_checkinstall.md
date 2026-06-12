---
title: "Error with checkinstall"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by uythenti on 2008-10-17
While I compile Wine in the third step, I replace the command: 

make install

by:

checkinstall -D make install

--->to ease uninstallation of software compiled from source, and create deb file for using next time.

(I've install checkinstall before).

I gets message:
```

make[1]: Entering directory `/tmp/wine-1.1.6/tools'
make[1]: `makedep' is up to date.
make[1]: Leaving directory `/tmp/wine-1.1.6/tools'
make[1]: Entering directory `/tmp/wine-1.1.6/libs'
make[2]: Entering directory `/tmp/wine-1.1.6/libs/port'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/wine-1.1.6/libs/port'
make[2]: Entering directory `/tmp/wine-1.1.6/libs/wine'
(GIT_DIR=../../.git git describe HEAD 2>/dev/null || echo "wine-1.1.6") | sed -n -e '$s/\(.*\)/const char wine_build[] = "\1";/p' >version-stamp || (rm -f version-stamp && exit 1)
make[2]: Leaving directory `/tmp/wine-1.1.6/libs/wine'
make[2]: Entering directory `/tmp/wine-1.1.6/libs/wpp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/wine-1.1.6/libs/wpp'
make[1]: Leaving directory `/tmp/wine-1.1.6/libs'
make[1]: Entering directory `/tmp/wine-1.1.6/tools'
make[2]: Entering directory `/tmp/wine-1.1.6/tools/widl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/wine-1.1.6/tools/widl'
make[2]: Entering directory `/tmp/wine-1.1.6/tools/winebuild'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/wine-1.1.6/tools/winebuild'
make[2]: Entering directory `/tmp/wine-1.1.6/tools/winedump'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/wine-1.1.6/tools/winedump'
make[2]: Entering directory `/tmp/wine-1.1.6/tools/winegcc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/wine-1.1.6/tools/winegcc'
make[2]: Entering directory `/tmp/wine-1.1.6/tools/wmc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/wine-1.1.6/tools/wmc'
make[2]: Entering directory `/tmp/wine-1.1.6/tools/wrc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/wine-1.1.6/tools/wrc'
make[1]: Leaving directory `/tmp/wine-1.1.6/tools'
make[1]: Entering directory `/tmp/wine-1.1.6/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/tmp/wine-1.1.6/include'
make[1]: Entering directory `/tmp/wine-1.1.6/dlls'
make[2]: Entering directory `/tmp/wine-1.1.6/dlls/adsiid'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/wine-1.1.6/dlls/adsiid'
make[2]: Entering directory `/tmp/wine-1.1.6/dlls/dxerr8'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/wine-1.1.6/dlls/dxerr8'
make[2]: Entering directory `/tmp/wine-1.1.6/dlls/dxerr9'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/wine-1.1.6/dlls/dxerr9'
make[2]: Entering directory `/tmp/wine-1.1.6/dlls/dxguid'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/wine-1.1.6/dlls/dxguid'
make[2]: Entering directory `/tmp/wine-1.1.6/dlls/strmiids'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/wine-1.1.6/dlls/strmiids'
make[2]: Entering directory `/tmp/wine-1.1.6/dlls/uuid'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/wine-1.1.6/dlls/uuid'
make[2]: Entering directory `/tmp/wine-1.1.6/dlls/winecrt0'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/wine-1.1.6/dlls/winecrt0'
make[2]: Entering directory `/tmp/wine-1.1.6/dlls/dinput'
make[2]: `libdinput.def.a' is up to date.
make[2]: Leaving directory `/tmp/wine-1.1.6/dlls/dinput'
make[2]: Entering directory `/tmp/wine-1.1.6/dlls/acledit'
../../tools/mkinstalldirs -m 755 /usr/local/lib/wine
mkdir /usr/local/lib/wine
chmod 755 /usr/local/lib/wine
chmod: changing permissions of `/usr/local/lib/wine': No such file or directory
make[2]: *** [/usr/local/lib/wine] Error 1
make[2]: Leaving directory `/tmp/wine-1.1.6/dlls/acledit'
make[1]: *** [acledit/__install__] Error 2
make[1]: Leaving directory `/tmp/wine-1.1.6/dlls'
make: *** [dlls/__install__] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```
Please, give me some ideas for it!

Ah, in the second step of compiling, I use: make depend && make. It's take a lot of time. what does "make depend" mean?

Thanks.

---

### Post by ajgreeny on 2008-10-17
You may have very good reasons for doing the compiling, but do you know that wine is available either from repos using synaptic, or direct from wine as a .deb package, so compiling is not usually necessary.

---

### Post by uythenti on 2008-10-17
I have known there are available for wine in .deb file. I have installed it in such way. Now I want to experience with compiling it.

I also want to check "checkinstall" to create deb file for using next time.

Please, help me!

---

### Post by andrew.46 on 2008-11-21
Hi:

```
sudo checkinstall -D --fstrans=no --install=yes 
```

  Andrew

---

### Post by OliW on 2008-11-25
Andrew that worked beautifully but why? What do those args do?

---

### Post by andrew.46 on 2008-11-26
Hi OliW:

> **OliW said:**
> Andrew that worked beautifully but why? What do those args do?

But when I explain it the magic dies a little bit :-). There is a little smoke and mirrors in there. The -D option (build a Debian package) and the --install option are not necessary and in fact I believe that --install=yes is actually the default.

The --fstrans=no gets around a bug that has been present in checkinstall for over 12 months now but seems to only be affecting Ubuntu since Intrepid Ibex. The problem is that checkinstall cannot deal with newer versions of the [gnu coreutils]("http://en.wikipedia.org/wiki/GNU_Core_Utilities"). The workaround is:

> The workaround for checkinstall-1.6.1 is to disable filesystem translation with --fstrans=no. This time however, it is not due to a fstrans bug. It just happens to be that by disabling fstrans then any not-installwatch-catched system call will have no problem finding the files where it expects them to be. 

Details of this bug can be found [here]("http://checkinstall.izto.org/cklist/msg00319.html"). It is a pretty serious bug and checkinstall was booted out of Slackware 12 for this reason. I am a little unsure why the problem is now so old with no fix release released by the checkinstall guys although I believe a fix exists in git.

 All the best,

  Andrew

---

