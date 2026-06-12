---
title: "help please wine"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by Medec5 on 2007-11-02
hey guys i managed to get it working but evertime i go to build and install i keep getting

gcc -c -I. -I. -I../../include -I../../include  -DINCLUDEDIR="\"/usr/local/include/wine\""  -Wall -pipe -mpreferred-stack-boundary=2 -fno-strict-aliasing -gstabs+ -Wdeclaration-after-statement -Wpointer-arith  -g -O2  -o lex.yy.o lex.yy.c
lex.yy.c:2610: error: expected ‘;’, ‘,’ or ‘)’ before numeric constant
make[2]: *** [lex.yy.o] Error 1
make[2]: Leaving directory `/home/rob/Desktop/wine-0.9.6/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/rob/Desktop/wine-0.9.6/tools'
make: *** [tools] Error 2

Compilation failed, aborting install.
rob@rob-desktop:~/Desktop/wine-0.9.6$ 


can somone please tell me what i am doing wrong thank u

---

### Post by PmDematagoda on 2007-11-02
Why are you trying to compile Wine?

Use either this:

```
sudo apt-get wine
```

or here

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

