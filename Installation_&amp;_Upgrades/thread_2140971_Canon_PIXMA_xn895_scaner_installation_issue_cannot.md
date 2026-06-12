---
title: "Canon PIXMA xn895 scaner installation issue: cannot find -lcncpnet"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by vadzen on 2013-05-01
Hi,

Environment:
Ubuntu 12.10, Canon PIXMA XN895 via LAN
scangearmp-source-1.90-1.tar.gz

INSTALL gives next messsage:
```
libtool: link: gcc -shared  -fPIC -DPIC  .libs/libsane_canon_mfp_la-canon_mfp.o .libs/libsane_canon_mfp_la-canon_mfp_tools.o   -ldl -lcncpnet -lpthread -lz -lusb  -O2   -Wl,-soname -Wl,libsane-canon_mfp.so.1 -o .libs/libsane-canon_mfp.so.1.0.9**/usr/bin/ld: cannot find -lcncpnet**
```
```
find / -type f -name *lcncpnet*

``` returns nothing
```
find / -type f -name *cncpnet*
``` returns next/home/user/Downloads/scangearmp-source-1.90-1/com/libs_bin64/libcncpnet.so.1.2.2
/home/user/Downloads/scangearmp-source-1.90-1/com/libs_bin32/libcncpnet.so.1.2.2

P.S. The Canon PIXMA XN895 via LAN works as printer. It has installed from cnijfilter-mx890series-3.70-1-deb.tar.gz


Thanks in advance

---

### Post by pdc on 2013-05-01
.......so I'm not clear about all this .......

......I'm assuming you want to install scangear: I'm not clear how you did this

I think you are talking about an MX895 Canon MF device ?

the scangear comes from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100413402.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100413402.html) 

it comes in as [COLOR="#008000"]scangearmp-mx890series-1.90-1-deb.tar.gz[/COLOR]

the commands would 

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf scangearmp-mx890series-1.90-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd scangearmp-mx890series-1.90-1-deb[/COLOR]

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR]

and to run scangear

> [COLOR="#FF0000"]**scangearmp**[/COLOR] in the terminal, until you set up a launcher ..

---

