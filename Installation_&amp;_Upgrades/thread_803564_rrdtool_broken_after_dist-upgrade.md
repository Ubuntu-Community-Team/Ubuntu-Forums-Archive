---
title: "rrdtool broken after dist-upgrade"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by greenmoss on 2008-05-22
So, I recently upgraded from edgy to gutsy. I would have gone to hardy, but somehow it didn't sink in to my head at the time that hardy was the latest release. So for now I'm at gutsy.

Before the upgrade, I was able to run rrdtool fine:

rrdtool graph - --width=500 --height=100 --start 1211377324 --end 1211391724 --vertical-label "" --title "myhost / Current_Load" --lower=0 DEF:var1=/usr/local/nagios/share/perfdata/myhost/Current_Load.rrd:1:AVERAGE AREA:var1#EACC00:"load1 " LINE1:var1#000000:"" GPRINT:var1:LAST:"%3.4lf %s LAST " GPRINT:var1:MAX:"%3.4lf %s MAX " GPRINT:var1:AVERAGE:"%3.4lf %s AVERAGE \n" HRULE:8.00#FFFF00:"Warning on 8.00\n" HRULE:12.00#FF0000:"Critical on 12.00\n" COMMENT:"Default Template\r" COMMENT:"Check Command check_nrpe\r"



After the upgrade, I got errors when running the same command:

rrdtool: symbol lookup error: /usr/lib/librrd.so.2: undefined symbol: art_alloc



In an attempt to fix it, I tried compiling rrdtool using debuild, but it died:

(...compilation verbosity has been trimmed away...)

(cd .libs && rm -f librrd_th.la && ln -s ../librrd_th.la librrd_th.la)
/bin/bash ../libtool --tag=CC --mode=link gcc  -O2 -I/usr/include/tcl8.4 -fno-strict-aliasing -Wall -std=gnu99 -pedantic -Wshadow -Wpointer-arith -Wcast-align -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Winline -W  -fPIC -DPIC   -o rrdtool   librrd.la 
gcc -O2 -I/usr/include/tcl8.4 -fno-strict-aliasing -Wall -std=gnu99 -pedantic -Wshadow -Wpointer-arith -Wcast-align -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Winline -W -fPIC -DPIC -o .libs/rrdtool  ./.libs/librrd.so -lpng -lz -lm
./.libs/librrd.so: undefined reference to `art_alloc'
./.libs/librrd.so: undefined reference to `art_free'
collect2: ld returned 1 exit status
make[3]: *** [rrdtool] Error 1




So it looks like rrdtool has some kind of anger issue with art_alloc. Here are versions of hopefully-relevant packages:

ii  libart-2.0-2      2.3.19-3          Library of functions for 2D graphics - runtime fil
ii  libc6             2.7-10ubuntu3     GNU C Library: Shared libraries
ii  libfreetype6      2.3.5-1ubuntu4    FreeType 2 font engine, shared library files
ii  libpng12-0        1.2.15~beta5-2ubu PNG library - runtime
ii  librrd2           1.2.19-1ubuntu1   Time-series data storage and display system (runti
ii  ttf-dejavu        2.23-1            Metapackage to pull in ttf-dejavu-core and ttf-dej
ii  zlib1g            1:1.2.3.3.dfsg-7u compression library - runtime



Maybe I have mixed versions, or incorrect packages? How do I figure out what's wrong?

---

### Post by greenmoss on 2008-05-27
So, anyone? art_alloc and rrdtool? Am I going to have to re-install this box from scratch? That would really suck.

---

