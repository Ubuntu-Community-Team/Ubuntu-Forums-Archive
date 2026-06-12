---
title: "Installing dosemu emulator: 'make' problem"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by idstealth on 2010-10-04
Hi all,

Please move this if it belongs somewhere else. (: Anyway, I'm trying to install dosemu to play the old DOS games, it came in a tarball. I unzipped it just fine, ./configure went without a hitch, but 'make' kept returning errors. I am not sure if the code itself was bad/syntax error, but I don't think that's the problem. Could it be my linux header files? I don't know! Advice?

Here's the make dialog:
```
idstealth@RAGINGBULL:~/Downloads/dosemu-1.4.0$ make
make[1]: Entering directory `/home/idstealth/Downloads/dosemu-1.4.0/src'
make[2]: Entering directory `/home/idstealth/Downloads/dosemu-1.4.0/src/tools'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/idstealth/Downloads/dosemu-1.4.0/src/tools'
make[2]: Entering directory `/home/idstealth/Downloads/dosemu-1.4.0/src/commands'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/idstealth/Downloads/dosemu-1.4.0/src/commands'
make[2]: Entering directory `/home/idstealth/Downloads/dosemu-1.4.0/src/tools/periph'
gcc -c -MP -MMD -I../../../src/include -I../../../src/plugin/include -I. -Wall -Wstrict-prototypes -Wmissing-declarations -Wnested-externs -O2 -fomit-frame-pointer -fno-strict-aliasing -Wno-pointer-sign -pipe  -o dexeconfig.o dexeconfig.c
dexeconfig.c: In function ‘viewconf’:
dexeconfig.c:104: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
dexeconfig.c: In function ‘putconf’:
dexeconfig.c:177: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
dexeconfig.c:188: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
dexeconfig.c:190: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
dexeconfig.c:210: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
dexeconfig.c:211: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
dexeconfig.c: In function ‘getconf’:
dexeconfig.c:226: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
dexeconfig.c:233: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
dexeconfig.c:246: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
In file included from /usr/include/fcntl.h:205,
                 from dexeconfig.c:13:
In function ‘open’,
    inlined from ‘main’ at dexeconfig.c:241:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[2]: *** [dexeconfig.o] Error 1
make[2]: Leaving directory `/home/idstealth/Downloads/dosemu-1.4.0/src/tools/periph'
make[1]: *** [tools/periph] Error 2
make[1]: Leaving directory `/home/idstealth/Downloads/dosemu-1.4.0/src'
make: *** [default] Error 2

```

---

### Post by andrewthomas on 2010-10-04
Do you have the build-essential package?

```
sudo apt-get install build-essential checkinstall
```You really should use checkinstall also

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by lykeion on 2010-10-04
Any specific reason why you want to compile dosemu yourself? Otherwise it's in the repositories, install with:
```
sudo apt-get install dosemu
```
As for playing old DOS games I'd highly recommend [DOSBox Game Launcher]("http://members.quicknet.nl/blankendaalr/dbgl/") (install instructions on homepage)

---

### Post by kostkon on 2010-10-04
Just install dosbox from the software center.

---

### Post by idstealth on 2010-10-05
Alright, didn't realize it was listed in the apt repositories. Thanks! :D

---

