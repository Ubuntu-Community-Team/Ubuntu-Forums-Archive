---
title: "install gimpshop problems"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by alin4lex on 2006-12-29
when i try to install gimpshop i need gimpprint. ok.

i've found gimpprint.tar.gz but on ./configure 

```

loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking host system type... i686-pc-linux-gnu
checking for cups-config... /usr/bin/cups-config
checking whether to build CUPS driver... yes
checking whether to build translated CUPS PPD files... yes
checking whether to use level 3 PostScript... no
checking whether to build ghostscript driver... no
checking for foomatic-configure... /usr/bin/foomatic-configure
checking whether to build foomatic data files... yes
checking for foomatic-ppdfile... /usr/bin/foomatic-ppdfile
checking whether to make use of Foomatic 3.x features... yes
checking Foomatic printer IDs... ............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................No entry with old Foomatic printer ID found!
checking whether to use the old numerical Foomatic printer IDs... no
checking for ijs-config... no
checking whether to build IJS driver... no
checking whether to turn on debugging in build... no
checking whether to use readline... yes
checking for gimptool-1.2... no
checking for gimptool... no
checking whether to build GIMP plugin... no
checking whether to install sample images... yes
checking whether to install user guide... yes
checking whether to build escputil... yes
checking whether to build testpattern generator... no
checking whether to build test programs... no
checking if user install is enabled... no
checking for strerror in -lcposix... no
checking for mawk... mawk
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for bison... no
checking for byacc... no
checking how to run the C preprocessor... gcc -E
checking for flex... no
checking for lex... no
./configure: line 2196: flex: command not found
checking for flex... lex
checking for yywrap in -ll... no
checking lex output file root... ./configure: line 2284: lex: command not found
configure: error: cannot find output from lex; giving up
alin@Home-wks:~/Desktop/gp$ ./configure --without-lex
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking host system type... i686-pc-linux-gnu
checking for cups-config... /usr/bin/cups-config
checking whether to build CUPS driver... yes
checking whether to build translated CUPS PPD files... yes
checking whether to use level 3 PostScript... no
checking whether to build ghostscript driver... no
checking for foomatic-configure... /usr/bin/foomatic-configure
checking whether to build foomatic data files... yes
checking for foomatic-ppdfile... /usr/bin/foomatic-ppdfile
checking whether to make use of Foomatic 3.x features... yes
checking Foomatic printer IDs... ............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................No entry with old Foomatic printer ID found!
checking whether to use the old numerical Foomatic printer IDs... no
checking for ijs-config... no
checking whether to build IJS driver... no
checking whether to turn on debugging in build... no
checking whether to use readline... yes
checking for gimptool-1.2... no
checking for gimptool... no
checking whether to build GIMP plugin... no
checking whether to install sample images... yes
checking whether to install user guide... yes
checking whether to build escputil... yes
checking whether to build testpattern generator... no
checking whether to build test programs... no
checking if user install is enabled... no
checking for strerror in -lcposix... no
checking for mawk... mawk
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for bison... no
checking for byacc... no
checking how to run the C preprocessor... gcc -E
checking for flex... no
checking for lex... no
./configure: line 2196: flex: command not found
checking for flex... lex
checking for yywrap in -ll... no
checking lex output file root... ./configure: line 2284: lex: command not found
configure: error: cannot find output from lex; giving up
alin@Home-wks:~/Desktop/gp$ ./configure [--without-gimp]
configure: warning: [--without-gimp]: invalid host type
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking host system type... Invalid configuration `[--without-gimp]': machine `[--without' not recognized

checking for cups-config... /usr/bin/cups-config
checking whether to build CUPS driver... yes
checking whether to build translated CUPS PPD files... yes
checking whether to use level 3 PostScript... no
checking whether to build ghostscript driver... no
checking for foomatic-configure... /usr/bin/foomatic-configure
checking whether to build foomatic data files... yes
checking for foomatic-ppdfile... /usr/bin/foomatic-ppdfile
checking whether to make use of Foomatic 3.x features... yes
checking Foomatic printer IDs... ............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................No entry with old Foomatic printer ID found!
checking whether to use the old numerical Foomatic printer IDs... no
checking for ijs-config... no
checking whether to build IJS driver... no
checking whether to turn on debugging in build... no
checking whether to use readline... yes
checking for gimptool-1.2... no
checking for gimptool... no
checking whether to build GIMP plugin... no
checking whether to install sample images... yes
checking whether to install user guide... yes
checking whether to build escputil... yes
checking whether to build testpattern generator... no
checking whether to build test programs... no
checking if user install is enabled... no
checking for strerror in -lcposix... no
checking for mawk... mawk
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for bison... no
checking for byacc... no
checking how to run the C preprocessor... gcc -E
checking for flex... no
checking for lex... no
./configure: line 2196: flex: command not found
checking for flex... lex
checking for yywrap in -ll... no
[B]checking lex output file root... ./configure: line 2284: lex: command not found
configure: error: cannot find output from lex; giving up[/B]


```

---

### Post by Swab on 2006-12-29
try installing flex first.

sudo apt-get install flex

hope that works!

---

### Post by alin4lex on 2006-12-29
ok, that works. 

./configure --> OK
make --> OK

but make install:

```

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
/bin/sh ../../scripts/mkinstalldirs /usr/local/bin
 /usr/bin/install -c  gimpprint-config /usr/local/bin/gimpprint-config
/bin/sh ../../scripts/mkinstalldirs /usr/local/share/aclocal
 /usr/bin/install -c -m 644 ./gimpprint.m4 /usr/local/share/aclocal/gimpprint.m4
make[3]: Leaving directory `/home/alin/Desktop/gp/src/main'
make[2]: Leaving directory `/home/alin/Desktop/gp/src/main'
Making install in escputil
make[2]: Entering directory `/home/alin/Desktop/gp/src/escputil'
make[3]: Entering directory `/home/alin/Desktop/gp/src/escputil'
/bin/sh ../../scripts/mkinstalldirs /usr/local/bin
 /bin/sh ../../libtool  --mode=install /usr/bin/install -c  escputil /usr/local/bin/escputil
/usr/bin/install -c escputil /usr/local/bin/escputil
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/alin/Desktop/gp/src/escputil'
make[2]: Leaving directory `/home/alin/Desktop/gp/src/escputil'
Making install in gimp
make[2]: Entering directory `/home/alin/Desktop/gp/src/gimp'
make[3]: Entering directory `/home/alin/Desktop/gp/src/gimp'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../../scripts/mkinstalldirs /usr/local/lib/gimp/1.2/plug-ins
make[3]: Leaving directory `/home/alin/Desktop/gp/src/gimp'
make[2]: Leaving directory `/home/alin/Desktop/gp/src/gimp'
Making install in cups
make[2]: Entering directory `/home/alin/Desktop/gp/src/cups'
/bin/sh ../../libtool --mode=link gcc -Wall -Wcast-align -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Wwrite-strings -pedantic -g -O2  -o epson  epson.o ../../lib/libprintut.la -lcupsimage -lcups -ltiff -ljpeg -lpng -L/usr/lib -lgnutls -lz -lpthread -lm -lcrypt   -lz
gcc -Wall -Wcast-align -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -Wwrite-strings -pedantic -g -O2 -o epson epson.o  ../../lib/.libs/libprintut.al -lcupsimage -lcups /usr/lib/libtiff.so -lc /usr/lib/libjpeg.so -lpng -L/usr/lib /usr/lib/libgnutls.so /usr/lib/libtasn1.so /usr/lib/libgcrypt.so -lnsl /usr/lib/libgpg-error.so -lpthread -lm -lcrypt -lz
/usr/bin/ld: cannot find -lcupsimage
collect2: ld returned 1 exit status
make[2]: *** [epson] Error 1
make[2]: Leaving directory `/home/alin/Desktop/gp/src/cups'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/alin/Desktop/gp/src'
make: *** [install-recursive] Error 1


```

it seems that it can not find **lcupsimage**

---

### Post by Swab on 2006-12-29
no sure on this one, perhaps 

sudo apt-get install libcupsimage2-dev

---

### Post by alin4lex on 2006-12-29
uff... 
it works but i need **libgimpprint1** and i have installed **Gimp-Print version 4.2.7**
 where i can find libgimpprint 1?

---

### Post by alin4lex on 2006-12-29
sudo apt-get install libgimpprint-dev does not works

---

### Post by Swab on 2006-12-29
> **alin4lex said:**
> uff... 
it works but i need **libgimpprint1** and i have installed **Gimp-Print version 4.2.7**
 where i can find libgimpprint 1?

I'm running Breezy and libgimpprint1 is in the repos... not sure about later versions.

---

### Post by alin4lex on 2006-12-29
ok, i understand.
can you tell me where i can find it in repositories ? in wich archives? i can noy find it
or under what name you have it..

i found libgimp-dev

---

### Post by alin4lex on 2006-12-29
ok... now another problem:
```

root@Home-wks:/home/alin/Desktop# dpkg -i gimpshop-2.2.11.deb
(Reading database ... 134978 files and directories currently installed.)
Unpacking gimpshop (from gimpshop-2.2.11.deb) ...
dpkg: error processing gimpshop-2.2.11.deb (--install):
 trying to overwrite `/etc/gimp/2.0/gimprc', which is also in package gimp-data
Errors were encountered while processing:
 gimpshop-2.2.11.deb


```

---

### Post by Swab on 2006-12-29
Sorry I can't help any more, don't know what has gone wrong!

By the way, Gimpshop is almost identical to Gimp, just all in one window.

---

### Post by indylarry on 2007-01-28
> **alin4lex said:**
> ok... now another problem:
```

root@Home-wks:/home/alin/Desktop# dpkg -i gimpshop-2.2.11.deb
(Reading database ... 134978 files and directories currently installed.)
Unpacking gimpshop (from gimpshop-2.2.11.deb) ...
dpkg: error processing gimpshop-2.2.11.deb (--install):
 trying to overwrite `/etc/gimp/2.0/gimprc', which is also in package gimp-data
Errors were encountered while processing:
 gimpshop-2.2.11.deb


```

I got this same same message.  I haven't found an answer to this yet but i can tell you what doesn't work.  Don't delete that directory.  I tried that and still got the same message.  I am hoping someone has the answer or this thread comes to life with interest.

---

### Post by SCD on 2007-03-14
Try to remove gimp with apt or synaptic

---

### Post by zaklinux on 2008-06-10
Edit: responded to wrong thread

---

