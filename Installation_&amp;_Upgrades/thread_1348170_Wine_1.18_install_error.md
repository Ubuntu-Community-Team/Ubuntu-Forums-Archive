---
title: "Wine 1.18 install error"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by Haggard88 on 2009-12-06
I am currently in the process of install WOTLK on Ubuntu 9.10. I got up to BC installed but I was using wine 1.0.1 which apparently is not a working version to install WOTLK and be able to click the EULA agree button. I am now trying to upgrade wine to 1.1.8. I uninstalled the older version of wine all together. Now after using ./configure and make dep I get an error after I input make.

make[2]: Entering directory `/home/joe/Downloads/wine-1.1.8/dlls/jscript'
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__  -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wtype-limits -Wpointer-arith  -g -O2  -o parser.tab.o parser.tab.c
/usr/local/share/bison.simple: In function &#8216;parser_parse&#8217;:
/usr/local/share/bison.simple:219: error: number of arguments doesn&#8217;t match prototype
/usr/local/share/bison.simple:153: error: prototype declaration
parser.y: In function &#8216;script_parse&#8217;:
parser.y:1580: error: too many arguments to function &#8216;parser_parse&#8217;
make[2]: *** [parser.tab.o] Error 1
make[2]: Leaving directory `/home/joe/Downloads/wine-1.1.8/dlls/jscript'
make[1]: *** [jscript/__install__] Error 2
make[1]: Leaving directory `/home/joe/Downloads/wine-1.1.8/dlls'
make: *** [dlls/__install__] Error 2

I just want to play Warcraft lol I have been trouble shooting the EULA for a few days now and now im having problems with wine itself. Any help or advice will be appreciated.

---

### Post by joes7 on 2009-12-07
Why don't you just simply delete your old Wine and install the newer version? I am sure that you know that one can do this using Ubuntu's Add / Remove program feature.

---

