---
title: "How can i install WineCVS"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by FuzZy2006 on 2006-11-08
I've just downloaded the WineCVS.sh from this link: [http://sourceforge.net/projects/winecvs](http://sourceforge.net/projects/winecvs) and I tried to install it. The problem is that it gives me some errors at compile time: 
```
--------- Error log - file /home/fuzzy/.WineCVS/sources/cvscedega/ErrorLog : ---------
./ppl.l:1337: warning: implicit declaration of function &#8216;max&#8217;
./ppl.l:1337: error: &#8216;ALLOCBLOCKSIZE&#8217; undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1346: warning: conflicting types for &#8216;macro_add_arg&#8217;
./ppl.l:1346: error: static declaration of &#8216;macro_add_arg&#8217; follows non-static declaration
./ppl.l:493: error: previous implicit declaration of &#8216;macro_add_arg&#8217; was here
./ppl.l: In function &#8216;macro_add_arg&#8217;:
./ppl.l:1349: error: &#8216;macexpstackentry_t&#8217; undeclared (first use in this function)
./ppl.l:1349: error: &#8216;mep&#8217; undeclared (first use in this function)
./ppl.l:1368: error: &#8216;debuglevel&#8217; undeclared (first use in this function)
./ppl.l:1368: error: &#8216;DEBUGLEVEL_PPLEX&#8217; undeclared (first use in this function)
./ppl.l:1370: error: &#8216;input_name&#8217; undeclared (first use in this function)
./ppl.l:1371: error: &#8216;line_number&#8217; undeclared (first use in this function)
./ppl.l:1378: error: &#8216;pp_macexp&#8217; undeclared (first use in this function)
./ppl.l:1379: warning: implicit declaration of function &#8216;push_buffer&#8217;
./ppl.l: In function &#8216;macro_add_expansion&#8217;:
./ppl.l:1387: error: &#8216;macexpstackentry_t&#8217; undeclared (first use in this function)
./ppl.l:1387: error: &#8216;mep&#8217; undeclared (first use in this function)
./ppl.l:1396: error: &#8216;debuglevel&#8217; undeclared (first use in this function)
./ppl.l:1396: error: &#8216;DEBUGLEVEL_PPLEX&#8217; undeclared (first use in this function)
./ppl.l:1398: error: &#8216;input_name&#8217; undeclared (first use in this function)
./ppl.l:1399: error: &#8216;line_number&#8217; undeclared (first use in this function)
./ppl.l: At top level:
./ppl.l:1411: warning: conflicting types for &#8216;put_buffer&#8217;
./ppl.l:1411: error: static declaration of &#8216;put_buffer&#8217; follows non-static declaration
./ppl.l:476: error: previous implicit declaration of &#8216;put_buffer&#8217; was here
./ppl.l: In function &#8216;put_buffer&#8217;:
./ppl.l:1415: error: &#8216;pass_data&#8217; undeclared (first use in this function)
./ppl.l: In function &#8216;do_include&#8217;:
./ppl.l:1439: error: &#8216;includelogicentry_t&#8217; undeclared (first use in this function)
./ppl.l:1439: error: &#8216;iep&#8217; undeclared (first use in this function)
./ppl.l:1441: error: &#8216;includelogiclist&#8217; undeclared (first use in this function)
./ppl.l:1462: warning: implicit declaration of function &#8216;open_include&#8217;
./ppl.l:1462: warning: assignment makes pointer from integer without a cast
./ppl.l:1467: error: &#8216;seen_junk&#8217; undeclared (first use in this function)
./ppl.l:1468: error: &#8216;include_state&#8217; undeclared (first use in this function)
./ppl.l:1469: error: &#8216;include_ppp&#8217; undeclared (first use in this function)
./ppl.l:1470: error: &#8216;pass_data&#8217; undeclared (first use in this function)
./ppl.l:1473: error: &#8216;debuglevel&#8217; undeclared (first use in this function)
./ppl.l:1473: error: &#8216;DEBUGLEVEL_PPMSG&#8217; undeclared (first use in this function)
./ppl.l:1474: error: &#8216;input_name&#8217; undeclared (first use in this function)
./ppl.l:1474: error: &#8216;line_number&#8217; undeclared (first use in this function)
./ppl.l:1474: error: &#8216;include_ifdepth&#8217; undeclared (first use in this function)
./ppl.l: In function &#8216;push_ignore_state&#8217;:
./ppl.l:1488: error: &#8216;pp_ignore&#8217; undeclared (first use in this function)
make[2]: *** [lex.ppl.o] Error 1
make[2]: Leaving directory `/home/fuzzy/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/fuzzy/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Error 2

```
I read the guide from [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS&amp;amp;amp;amp;back=HOWTO+INDEX+Wine](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS&amp;amp;amp;amp;back=HOWTO+INDEX+Wine) and I guess I need Mesa (resp. xorg-x11-Mesa, XFree86-Mesa) Mesa-devel (resp. xorg-x11-Mesa-devel, XFree86-Mesa-devel) freeglut freeglut-devel SDL SDL-devel. Where can I find these? If your install is succesfull pls tell me how did you do it. (I choose get profile - the first one - 0 - cedega_head_userinstall). 
**Or better - is there any method to do this from Synaptic, by adding a repository?**
I have installed xlibmesa-glu but nothing happened :((

---

### Post by YokoZar on 2006-11-08
Don't bother with a script, just do this:

apt-get build-dep wine (this will get you all the build dependencies for making the wine package, which will allow you to have them when you compile by hand as well)

Then get the wine source by CVS or GIT:
./configure
make
make install

Pretty standard compile there.

---

### Post by FuzZy2006 on 2006-11-09
what I actually want to install is the free cedega package or winex.

---

### Post by patrick295767 on 2007-01-14
[http://ubuntuforums.org/showthread.php?t=193814&highlight=cvscedega+automatic](http://ubuntuforums.org/showthread.php?t=193814&highlight=cvscedega+automatic)

---

