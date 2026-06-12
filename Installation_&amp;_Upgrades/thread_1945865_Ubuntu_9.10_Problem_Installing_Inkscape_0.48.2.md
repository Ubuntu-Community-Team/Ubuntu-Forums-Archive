---
title: "Ubuntu 9.10 Problem Installing Inkscape 0.48.2"
date: 2012-03-23
forum: Installation &amp; Upgrades
---

### Post by Xekeno on 2012-03-23
[COLOR=Blue][COLOR=Black]Greetings and Salutations,

I am running Ubuntu 9.10 and I want to install Inkscape 0.48.2. I can't do an automatic Ubuntu repository install because I don't have the correct or updated information for my 9.10 to install it automatically.

So I have downloaded Inkscape 0.48.2 and I am trying to manually install it on Ubuntu 9.10.

When I try to ./configure it I get this Error
---------------------------------------------------------------------------------------
> 
"checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a pax tar archive... gnutar
checking for style of include used by make... GNU
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables...
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for library containing strerror... none required
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking dependency style of gcc... gcc3
checking for ranlib... ranlib
checking whether NLS is requested... yes
checking for intltool >= 0.22... 0.50.0 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... no
checking for msgmerge... no
checking for msgfmt... no
checking for gmsgfmt... no
configure: error: GNU gettext tools not found; required for intltool "---------------------------------------------------------------------------------------

As you can see the error is " GNU gettext tools not found; required for intltool "

At first before I had this GNU gettext error I had an error saying I needed " intltool "

So I downloaded Intitool 0.50.0 and I installed it. At least I think I did.

Aftwards I tried to compile inkscape 48 again but and that's when I got this last error.

Since then I downloaded gettext 0.1.18.1.1 and I tried to install it, but it won't install. I was able to configure, compile and make check, when I did the make check I had one fail and the rest passed see Below.

---------------------------------------------------------------------------------------
> 
"PASS: test-pipe2
PASS: test-posix_spawn1
PASS: test-posix_spawn2
PASS: test-quotearg-simple
PASS: test-rawmemchr
PASS: test-read-file
test-readlink.h:102: assertion failed
/bin/bash: line 5: 21852 Aborted EXEEXT='' srcdir='.' USE_ACL=0 LOCALE_FR='none' LOCALE_TR_UTF8='none' USE_ACL=0 LOCALE_FR='none' LOCALE_FR_UTF8='none' LOCALE_JA='none' LOCALE_ZH_CN='none' LOCALE_FR_UTF8='none' LOCALE_FR='none' LOCALE_FR_UTF8='none' LOCALE_JA='none' LOCALE_ZH_CN='none' LOCALE_FR_UTF8='none' LOCALE_ZH_CN='none' srcdir='.' MAKE='make' ${dir}$tst
FAIL: test-readlink
PASS: test-rmdir
PASS: test-sched
PASS: test-setenv"

---------------------------------------------------------------------------------------

Also this

---------------------------------------------------------------------------------------

> "PASS: test-xvasprintf
=======================
1 of 109 tests failed
(14 tests were not run)
=======================
: *** check-TESTS Error 1
: Leaving directory `/home/lekeno/Desktop/gettext/gettext-tools/gnulib-tests'
: *** check-am Error 2
: Leaving directory `/home/lekeno/Desktop/gettext/gettext-tools/gnulib-tests'
: *** check-recursive Error 1
: Leaving directory `/home/lekeno/Desktop/gettext/gettext-tools/gnulib-tests'
: *** check Error 2
: Leaving directory `/home/lekeno/Desktop/gettext/gettext-tools/gnulib-tests'
: ***check-recursive Error 1
: Leaving directory `/home/lekeno/Desktop/gettext/gettext-tools'
: *** check-recursive Error 1"

---------------------------------------------------------------------------------------
Then I tried to "Make Install" and I got this
---------------------------------------------------------------------------------------

> "make install
Making install in gnulib-local
: Entering directory `/home/lekeno/Desktop/gettext/gnulib-local'
: Entering directory `/home/lekeno/Desktop/gettext/gnulib-local'
: Nothing to be done for `install-exec-am'.
: Nothing to be done for `install-data-am'.
: Leaving directory `/home/lekeno/Desktop/gettext/gnulib-local'
: Leaving directory `/home/lekeno/Desktop/gettext/gnulib-local'
Making install in gettext-runtime
: Entering directory `/home/lekeno/Desktop/gettext/gettext-runtime'
Making install in doc
: Entering directory `/home/lekeno/Desktop/gettext/gettext-runtime/doc'
: Entering directory `/home/lekeno/Desktop/gettext/gettext-runtime/doc'
: Nothing to be done for `install-exec-am'.
: Nothing to be done for `install-data-am'.
: Leaving directory `/home/lekeno/Desktop/gettext/gettext-runtime/doc'
: Leaving directory `/home/lekeno/Desktop/gettext/gettext-runtime/doc'
Making install in intl
: Entering directory `/home/lekeno/Desktop/gettext/gettext-runtime/intl'
if { test "gettext-runtime" = "gettext-runtime" || test "gettext-runtime" = "gettext-tools"; } \
&& test 'no' = yes; then \
/bin/mkdir -p /usr/local/lib /usr/local/include; \
/usr/bin/install -c -m 644 libintl.h /usr/local/include/libintl.h; \
/bin/bash ../libtool --mode=install \
/usr/bin/install -c -m 644 libintl.la /usr/local/lib/libintl.la; \
if test "no" = yes; then \
dependencies=`sed -n -e 's,^dependency_libs=\(.*\),\1,p' < /usr/local/lib/libintl.la | sed -e "s,^',," -e "s,'\$,,"`; \
if test -n "$dependencies"; then \
rm -f /usr/local/lib/libintl.la; \
fi; \
fi; \
else \
: ; \
fi
if test "gettext-runtime" = "gettext-tools" \
&& test 'no' = no \
&& test yes != no; then \
/bin/mkdir -p /usr/local/lib; \
/bin/bash ../libtool --mode=install \
/usr/bin/install -c -m 644 libgnuintl.la /usr/local/lib/libgnuintl.la; \
rm -f /usr/local/lib/preloadable_libintl.so; \
/usr/bin/install -c -m 644 /usr/local/lib/libgnuintl.so /usr/local/lib/preloadable_libintl.so; \
/bin/bash ../libtool --mode=uninstall \
rm -f /usr/local/lib/libgnuintl.la; \
else \
: ; \
fi
if test 'no' = yes; then \
if test yes = no; then \
case 'linux-gnu' in \
darwin56*) \
need_charset_alias=true ;; \
darwin* | cygwin* | mingw* | pw32* | cegcc*) \
need_charset_alias=false ;; \
*) \
need_charset_alias=true ;; \
esac; \
else \
need_charset_alias=false; \
fi; \
if $need_charset_alias; then \
/bin/mkdir -p /usr/local/lib; \
fi; \
temp=/usr/local/lib/t-charset.alias; \
dest=/usr/local/lib/charset.alias; \
if test -f /usr/local/lib/charset.alias; then \
orig=/usr/local/lib/charset.alias; \
sed -f ref-add.sed $orig > $temp; \
/usr/bin/install -c -m 644 $temp $dest; \
rm -f $temp; \
else \
if $need_charset_alias; then \
orig=charset.alias; \
sed -f ref-add.sed $orig > $temp; \
/usr/bin/install -c -m 644 $temp $dest; \
rm -f $temp; \
fi; \
fi; \
/bin/mkdir -p /usr/local/share/locale; \
test -f /usr/local/share/locale/locale.alias \
&& orig=/usr/local/share/locale/locale.alias \
|| orig=./locale.alias; \
temp=/usr/local/share/locale/t-locale.alias; \
dest=/usr/local/share/locale/locale.alias; \
sed -f ref-add.sed $orig > $temp; \
/usr/bin/install -c -m 644 $temp $dest; \
rm -f $temp; \
else \
: ; \
fi
if test "gettext-runtime" = "gettext-tools"; then \
/bin/mkdir -p /usr/local/share/gettext/intl; \
/usr/bin/install -c -m 644 VERSION /usr/local/share/gettext/intl/VERSION; \
/usr/bin/install -c -m 644 ChangeLog.inst /usr/local/share/gettext/intl/ChangeLog; \
dists="COPYING.LIB-2.0 COPYING.LIB-2.1 Makefile.in config.charset locale.alias ref-add.sin ref-del.sin export.h libintl.rc gmo.h gettextP.h hash-string.h loadinfo.h plural-exp.h eval-plural.h localcharset.h lock.h relocatable.h tsearch.h tsearch.c xsize.h printf-args.h printf-args.c printf-parse.h wprintf-parse.h printf-parse.c vasnprintf.h vasnwprintf.h vasnprintf.c os2compat.h libgnuintl.h.in bindtextdom.c dcgettext.c dgettext.c gettext.c finddomain.c hash-string.c loadmsgcat.c localealias.c textdomain.c l10nflist.c explodename.c dcigettext.c dcngettext.c dngettext.c ngettext.c plural.y plural-exp.c localcharset.c threadlib.c lock.c relocatable.c langprefs.c localename.c log.c printf.c setlocale.c version.c osdep.c os2compat.c intl-exports.c intl-compat.c"; \
for file in $dists; do \
/usr/bin/install -c -m 644 ./$file \
/usr/local/share/gettext/intl/$file; \
done; \
chmod a+x /usr/local/share/gettext/intl/config.charset; \
dists="plural.c"; \
for file in $dists; do \
if test -f $file; then dir=.; else dir=.; fi; \
/usr/bin/install -c -m 644 $dir/$file \
/usr/local/share/gettext/intl/$file; \
done; \
dists="xopen-msg.sed linux-msg.sed po2tbl.sed.in cat-compat.c COPYING.LIB-2 gettext.h libgettext.h plural-eval.c libgnuintl.h libgnuintl.h_vms Makefile.vms libgnuintl.h.msvc-static libgnuintl.h.msvc-shared Makefile.msvc"; \
for file in $dists; do \
rm -f /usr/local/share/gettext/intl/$file; \
done; \
else \
: ; \
fi
: Leaving directory `/home/lekeno/Desktop/gettext/gettext-runtime/intl'
Making install in intl-java
: Entering directory `/home/lekeno/Desktop/gettext/gettext-runtime/intl-java'
: Entering directory `/home/lekeno/Desktop/gettext/gettext-runtime/intl-java'
: Nothing to be done for `install-exec-am'.
/bin/mkdir -p /usr/local/share/gettext
/bin/mkdir: cannot create directory `/usr/local/share/gettext': Permission denied
: *** install-classes-no Error 1
: Leaving directory `/home/lekeno/Desktop/gettext/gettext-runtime/intl-java'
: *** install-am Error 2
: Leaving directory `/home/lekeno/Desktop/gettext/gettext-runtime/intl-java'
: *** install-recursive Error 1
: Leaving directory `/home/lekeno/Desktop/gettext/gettext-runtime'
make: *** install-recursive Error 1"

---------------------------------------------------------------------------------------

So if anyone out there who has more experience knows of a way to fix this situation or get inkscape installed on my ubuntu 9.10 please let me know. I greatly appreciate any and all who help me solve my problem.

Thank you in Advanced.
Best Regards.
Xekeno:KS

[/COLOR][/COLOR]

---

### Post by mörgæs on 2012-03-24
Hi, welcome to the fora.

9.10 is unsupported and hence a security threat. I would recommend that you begin with a fresh install of one of the [supported versions]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline").


When that works, feel free to post again.

---

### Post by tx99h4 on 2012-03-24
Hello!

If you're still struggled with that, try to upgrade your ubuntu to lucid or maverick.. 

I installed Inkscape 0.48 today and it works well!


Good luck :)

---

### Post by Xekeno on 2012-03-25
I like the version I have just fine thank you.

---

