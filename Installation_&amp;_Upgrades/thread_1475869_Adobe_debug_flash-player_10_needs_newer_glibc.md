---
title: "Adobe debug flash-player 10 needs newer glibc"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by bloem on 2010-05-07
Hi all,

I'm trying to install the latest debug flashplayer available here:

[http://download.macromedia.com/pub/flashplayer/updaters/10/flash_player_10_linux_dev.tar.gz]("http://download.macromedia.com/pub/flashplayer/updaters/10/flash_player_10_linux_dev.tar.gz")

linked from this page

[http://www.adobe.com/support/flashplayer/downloads.html]("http://www.adobe.com/support/flashplayer/downloads.html")

I follow the embedded instructions and this is the error:


root@vostro-ubuntu:~# /home/berrie/work/download/install_flash_player_10_linux/flashplayer-installer 
[: 258: closing paren expected

ERROR: Your glibc library is older than 2.3.
       Please update your glibc library.

root@vostro-ubuntu:~# aptitude search glibc
p   eglibc-source                                           - Embedded GNU C Library: sources                                   
v   glibc-2.10-1                                            -                                                                   
p   glibc-doc                                               - GNU C Library: Documentation                                      
v   glibc-doc-reference                                     -                                                                   
v   glibc-pic                                               -                                                                   
root@vostro-ubuntu:~# 

I'm running Ubuntu Karmic Koala and it is up to date. 

Could it be that the flash installer parses the version number wrong as previously it was glibc-2.9-1, a '9' after the dot, now there is a '1'.

Seems daft. Anyone got any ideas?

Cheers,

BB

---

### Post by sylvester_0 on 2010-05-07
My google-fu is strong. See the link below.

[http://rahulsinghai.blogspot.com/2009/12/install-flash-player-10-debugger-verion.html](http://rahulsinghai.blogspot.com/2009/12/install-flash-player-10-debugger-verion.html)

P.S. Any reason why you haven't upgraded to Lucid yet?

---

### Post by bloem on 2010-05-11
Thanks Sylvester, this did the trick:

Line 73 from:

    ICONVVER=`echo "$ICONV" | awk '{print $4}'`

to:

    ICONVVER=`echo "$ICONV" | awk '{print $3}'`

Tis an appalling bit of coding that function, just imagine when glibc version 3.0 hits the shelves...

BB

---

### Post by bloem on 2010-05-11
About Lucid: can't risk the downtime at the moment. I'll do it when I have more time.

BB

---

