---
title: "nagios make error ubuntu 10.10"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by VamPikmin on 2011-07-28
keep getting this error when i try to make install
```

root@jupiter:/media/europa/callisto/nagios___/nagios-3.3.1/nagios# make install
cd ./base && make install
make[1]: Entering directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/base'
make install-basic
make[2]: Entering directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/base'
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/bin
/usr/bin/install -c -m 774 -o nagios -g nagios nagios /usr/local/nagios/bin
/usr/bin/install -c -m 774 -o nagios -g nagios nagiostats /usr/local/nagios/bin
make[2]: Leaving directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/base'
make strip-post-install
make[2]: Entering directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/base'
/usr/bin/strip /usr/local/nagios/bin/nagios
/usr/bin/strip /usr/local/nagios/bin/nagiostats
make[2]: Leaving directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/base'
make[1]: Leaving directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/base'
cd ./cgi && make install
make[1]: Entering directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/cgi'
make install-basic
make[2]: Entering directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/cgi'
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/sbin
for file in *.cgi; do \
                /usr/bin/install -c -m 775 -o nagios -g nagios $file /usr/local/nagios/sbin; \
        done
make[2]: Leaving directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/cgi'
make strip-post-install
make[2]: Entering directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/cgi'
for file in *.cgi; do \
                /usr/bin/strip /usr/local/nagios/sbin/$file; \
        done
make[2]: Leaving directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/cgi'
make[1]: Leaving directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/cgi'
cd ./html && make install
make[1]: Entering directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/html'
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/media
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/stylesheets
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/contexthelp
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/docs
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/docs/images
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/images
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/images/logos
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/includes
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/includes/rss
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/includes/rss/extlib
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/ssi
/usr/bin/install -c -m 664 -o nagios -g nagios robots.txt /usr/local/nagios/share
rm -f /usr/local/nagios/share/index.html
rm -f /usr/local/nagios/share/main.html
rm -f /usr/local/nagios/share/side.html
for file in *.php; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share; done
for file in stylesheets/*.css; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share/stylesheets; done
for file in contexthelp/*.html; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share/contexthelp; done
for file in images/*.gif; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share/images; done
for file in images/*.jpg; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share/images; done
for file in images/*.png; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share/images; done
for file in images/*.ico; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share/images; done
for file in images/logos/*.*; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share/images/logos; done
for file in includes/*.*; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share/includes; done
for file in includes/rss/*; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share/includes/rss; done
/usr/bin/install: omitting directory `includes/rss/extlib'
/usr/bin/install: omitting directory `includes/rss/htdocs'
/usr/bin/install: omitting directory `includes/rss/scripts'
make[1]: *** [install] Error 1
make[1]: Leaving directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/html'
make: *** [install] Error 2
root@jupiter:/media/europa/callisto/nagios___/nagios-3.3.1/nagios#

```
 
any suggestions?

---

### Post by .:grunge:. on 2011-07-29
> **VamPikmin said:**
> keep getting this error when i try to make install
```

root@jupiter:/media/europa/callisto/nagios___/nagios-3.3.1/nagios# make install
cd ./base && make install
make[1]: Entering directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/base'
make install-basic
make[2]: Entering directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/base'
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/bin
/usr/bin/install -c -m 774 -o nagios -g nagios nagios /usr/local/nagios/bin
/usr/bin/install -c -m 774 -o nagios -g nagios nagiostats /usr/local/nagios/bin
make[2]: Leaving directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/base'
make strip-post-install
make[2]: Entering directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/base'
/usr/bin/strip /usr/local/nagios/bin/nagios
/usr/bin/strip /usr/local/nagios/bin/nagiostats
make[2]: Leaving directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/base'
make[1]: Leaving directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/base'
cd ./cgi && make install
make[1]: Entering directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/cgi'
make install-basic
make[2]: Entering directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/cgi'
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/sbin
for file in *.cgi; do \
                /usr/bin/install -c -m 775 -o nagios -g nagios $file /usr/local/nagios/sbin; \
        done
make[2]: Leaving directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/cgi'
make strip-post-install
make[2]: Entering directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/cgi'
for file in *.cgi; do \
                /usr/bin/strip /usr/local/nagios/sbin/$file; \
        done
make[2]: Leaving directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/cgi'
make[1]: Leaving directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/cgi'
cd ./html && make install
make[1]: Entering directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/html'
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/media
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/stylesheets
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/contexthelp
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/docs
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/docs/images
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/images
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/images/logos
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/includes
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/includes/rss
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/includes/rss/extlib
/usr/bin/install -c -m 775 -o nagios -g nagios -d /usr/local/nagios/share/ssi
/usr/bin/install -c -m 664 -o nagios -g nagios robots.txt /usr/local/nagios/share
rm -f /usr/local/nagios/share/index.html
rm -f /usr/local/nagios/share/main.html
rm -f /usr/local/nagios/share/side.html
for file in *.php; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share; done
for file in stylesheets/*.css; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share/stylesheets; done
for file in contexthelp/*.html; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share/contexthelp; done
for file in images/*.gif; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share/images; done
for file in images/*.jpg; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share/images; done
for file in images/*.png; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share/images; done
for file in images/*.ico; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share/images; done
for file in images/logos/*.*; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share/images/logos; done
for file in includes/*.*; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share/includes; done
for file in includes/rss/*; \
        do /usr/bin/install -c -m 664 -o nagios -g nagios $file /usr/local/nagios/share/includes/rss; done
/usr/bin/install: omitting directory `includes/rss/extlib'
/usr/bin/install: omitting directory `includes/rss/htdocs'
/usr/bin/install: omitting directory `includes/rss/scripts'
make[1]: *** [install] Error 1
make[1]: Leaving directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/html'
make: *** [install] Error 2
root@jupiter:/media/europa/callisto/nagios___/nagios-3.3.1/nagios#

```any suggestions?

./configure

sed -i 's:for file in includes/rss/\*;:for file in includes/rss/\*.\*;:g' ./html/Makefile
sed -i 's:for file in includes/rss/extlib/\*;:for file in includes/rss/extlib/\*.\*;:g' ./html/Makefile

and then
make fullinstall

---

### Post by VamPikmin on 2011-07-31
[SIZE=2]cheers .:grunge:. [/SIZE]
[SIZE=2]worked like a charm![/SIZE]
[SIZE=2]it would take me million years to find that on my own[/SIZE]

---

### Post by VamPikmin on 2011-07-31
one more thing :)
 
not sure if it's related to plugin install
 
```

[EMAIL="root@jupiter:/media/europa/callisto/nagios___/nagios-plugins-1.4.15"]root@jupiter:/media/europa/callisto/nagios___/nagios-plugins-1.4.15[/EMAIL]# make install
Making install in gl
make[1]: Entering directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/gl'
rm -f configmake.h-t && \
        { echo '/* DO NOT EDIT! GENERATED AUTOMATICALLY! */'; \
          echo '#define PREFIX "/usr/local/nagios"'; \
          echo '#define EXEC_PREFIX "/usr/local/nagios"'; \
          echo '#define BINDIR "/usr/local/nagios/bin"'; \
          echo '#define SBINDIR "/usr/local/nagios/sbin"'; \
          echo '#define LIBEXECDIR "/usr/local/nagios/libexec"'; \
          echo '#define DATAROOTDIR "/usr/local/nagios/share"'; \
          echo '#define DATADIR "/usr/local/nagios/share"'; \
          echo '#define SYSCONFDIR "/usr/local/nagios/etc"'; \
          echo '#define SHAREDSTATEDIR "/usr/local/nagios/com"'; \
          echo '#define LOCALSTATEDIR "/usr/local/nagios/var"'; \
          echo '#define INCLUDEDIR "/usr/local/nagios/include"'; \
          echo '#define OLDINCLUDEDIR "/usr/include"'; \
          echo '#define DOCDIR "/usr/local/nagios/share/doc/nagios-plugins"'; \
          echo '#define INFODIR "/usr/local/nagios/share/info"'; \
          echo '#define HTMLDIR "/usr/local/nagios/share/doc/nagios-plugins"'; \
          echo '#define DVIDIR "/usr/local/nagios/share/doc/nagios-plugins"'; \
          echo '#define PDFDIR "/usr/local/nagios/share/doc/nagios-plugins"'; \
          echo '#define PSDIR "/usr/local/nagios/share/doc/nagios-plugins"'; \
          echo '#define LIBDIR "/usr/local/nagios/lib"'; \
          echo '#define LISPDIR ""'; \
          echo '#define LOCALEDIR "/usr/local/nagios/share/locale"'; \
          echo '#define MANDIR "/usr/local/nagios/share/man"'; \
          echo '#define MANEXT ""'; \
          echo '#define PKGDATADIR "/usr/local/nagios/share/nagios-plugins"'; \
          echo '#define PKGINCLUDEDIR "/usr/local/nagios/include/nagios-plugins"'; \
          echo '#define PKGLIBDIR "/usr/local/nagios/lib/nagios-plugins"'; \
          echo '#define PKGLIBEXECDIR ""'; \
        } | sed '/""/d' > configmake.h-t && \
        if test -f configmake.h && cmp configmake.h-t configmake.h > /dev/null; then \
          rm -f configmake.h-t; \
        else \
          rm -f configmake.h; mv configmake.h-t configmake.h; \
        fi
make  install-recursive
make[2]: Entering directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/gl'
make[3]: Entering directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/gl'
rm -f configmake.h-t && \
        { echo '/* DO NOT EDIT! GENERATED AUTOMATICALLY! */'; \
          echo '#define PREFIX "/usr/local/nagios"'; \
          echo '#define EXEC_PREFIX "/usr/local/nagios"'; \
          echo '#define BINDIR "/usr/local/nagios/bin"'; \
          echo '#define SBINDIR "/usr/local/nagios/sbin"'; \
          echo '#define LIBEXECDIR "/usr/local/nagios/libexec"'; \
          echo '#define DATAROOTDIR "/usr/local/nagios/share"'; \
          echo '#define DATADIR "/usr/local/nagios/share"'; \
          echo '#define SYSCONFDIR "/usr/local/nagios/etc"'; \
          echo '#define SHAREDSTATEDIR "/usr/local/nagios/com"'; \
          echo '#define LOCALSTATEDIR "/usr/local/nagios/var"'; \
          echo '#define INCLUDEDIR "/usr/local/nagios/include"'; \
          echo '#define OLDINCLUDEDIR "/usr/include"'; \
          echo '#define DOCDIR "/usr/local/nagios/share/doc/nagios-plugins"'; \
          echo '#define INFODIR "/usr/local/nagios/share/info"'; \
          echo '#define HTMLDIR "/usr/local/nagios/share/doc/nagios-plugins"'; \
          echo '#define DVIDIR "/usr/local/nagios/share/doc/nagios-plugins"'; \
          echo '#define PDFDIR "/usr/local/nagios/share/doc/nagios-plugins"'; \
          echo '#define PSDIR "/usr/local/nagios/share/doc/nagios-plugins"'; \
          echo '#define LIBDIR "/usr/local/nagios/lib"'; \
          echo '#define LISPDIR ""'; \
          echo '#define LOCALEDIR "/usr/local/nagios/share/locale"'; \
          echo '#define MANDIR "/usr/local/nagios/share/man"'; \
          echo '#define MANEXT ""'; \
          echo '#define PKGDATADIR "/usr/local/nagios/share/nagios-plugins"'; \
          echo '#define PKGINCLUDEDIR "/usr/local/nagios/include/nagios-plugins"'; \
          echo '#define PKGLIBDIR "/usr/local/nagios/lib/nagios-plugins"'; \
          echo '#define PKGLIBEXECDIR ""'; \
        } | sed '/""/d' > configmake.h-t && \
        if test -f configmake.h && cmp configmake.h-t configmake.h > /dev/null; then \
          rm -f configmake.h-t; \
        else \
          rm -f configmake.h; mv configmake.h-t configmake.h; \
        fi
make[4]: Entering directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/gl'
if test yes = no; then \
          case 'linux-gnu' in \
            darwin[56]*) \
              need_charset_alias=true ;; \
            darwin* | cygwin* | mingw* | pw32* | cegcc*) \
              need_charset_alias=false ;; \
            *) \
              need_charset_alias=true ;; \
          esac ; \
        else \
          need_charset_alias=false ; \
        fi ; \
        if $need_charset_alias; then \
          /bin/bash ../build-aux/mkinstalldirs /usr/local/nagios/lib ; \
        fi ; \
        if test -f /usr/local/nagios/lib/charset.alias; then \
          sed -f ref-add.sed /usr/local/nagios/lib/charset.alias > /usr/local/nagios/lib/charset.tmp ; \
          /usr/bin/install -c -o nagios -g nagios -m 644 /usr/local/nagios/lib/charset.tmp /usr/local/nagios/lib/charset.alias ; \
          rm -f /usr/local/nagios/lib/charset.tmp ; \
        else \
          if $need_charset_alias; then \
            sed -f ref-add.sed charset.alias > /usr/local/nagios/lib/charset.tmp ; \
            /usr/bin/install -c -o nagios -g nagios -m 644 /usr/local/nagios/lib/charset.tmp /usr/local/nagios/lib/charset.alias ; \
            rm -f /usr/local/nagios/lib/charset.tmp ; \
          fi ; \
        fi
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/gl'
make[3]: Leaving directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/gl'
make[2]: Leaving directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/gl'
make[1]: Leaving directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/gl'
Making install in tap
make[1]: Entering directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/tap'
make[2]: Entering directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/tap'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/nagios/include" || /bin/mkdir -p "/usr/local/nagios/include"
make[2]: Leaving directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/tap'
make[1]: Leaving directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/tap'
Making install in lib
make[1]: Entering directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/lib'
Making install in .
make[2]: Entering directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/lib'
make[3]: Entering directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/lib'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/lib'
make[2]: Leaving directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/lib'
Making install in tests
make[2]: Entering directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/lib/tests'
make[3]: Entering directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/lib/tests'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/lib/tests'
make[2]: Leaving directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/lib/tests'
make[1]: Leaving directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/lib'
Making install in plugins
make[1]: Entering directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/plugins'
/bin/bash ../libtool --tag=CC   --mode=link gcc -DNP_VERSION='"1.4.15"' -g -O2  -L. -o check_http check_http.o sslutils.o netutils.o utils.o ../lib/libnagiosplug.a ../gl/libgnu.a  -lnsl -lresolv -lssl -lcrypto -lpthread -ldl
libtool: link: gcc -DNP_VERSION=\"1.4.15\" -g -O2 -o check_http check_http.o sslutils.o netutils.o utils.o  -L/media/europa/callisto/nagios___/nagios-plugins-1.4.15/plugins ../lib/libnagiosplug.a ../gl/libgnu.a -lnsl -lresolv -lssl -lcrypto -lpthread -ldl
check_http.o: In function `check_http':
/media/europa/callisto/nagios___/nagios-plugins-1.4.15/plugins/check_http.c:883: undefined reference to `np_net_ssl_read'
/media/europa/callisto/nagios___/nagios-plugins-1.4.15/plugins/check_http.c:924: undefined reference to `np_net_ssl_cleanup'
/media/europa/callisto/nagios___/nagios-plugins-1.4.15/plugins/check_http.c:879: undefined reference to `np_net_ssl_write'
/media/europa/callisto/nagios___/nagios-plugins-1.4.15/plugins/check_http.c:810: undefined reference to `np_net_ssl_init_with_hostname'
/media/europa/callisto/nagios___/nagios-plugins-1.4.15/plugins/check_http.c:812: undefined reference to `np_net_ssl_check_cert'
/media/europa/callisto/nagios___/nagios-plugins-1.4.15/plugins/check_http.c:813: undefined reference to `np_net_ssl_cleanup'
collect2: ld returned 1 exit status
make[1]: *** [check_http] Error 1
make[1]: Leaving directory `/media/europa/callisto/nagios___/nagios-plugins-1.4.15/plugins'
make: *** [install-recursive] Error 1

```
 
i am able to login to /server/nagios
 
ping statistics work but i get this error for port bw
```

[[SIZE=2]Port 1 Bandwidth Usage[/SIZE]]("http://10.147.172.21/nagios/cgi-bin/extinfo.cgi?type=2&host=Fibre&service=Port+1+Bandwidth+Usage")[SIZE=2][/SIZE][SIZE=2]UNKNOWN[/SIZE][SIZE=2]08-01-2011 12:24:49[/SIZE][SIZE=2]0d 1h 46m 39s[/SIZE][SIZE=2]3/3[/SIZE][SIZE=2]check_mrtgtraf: Unable to open MRTG log file [/SIZE][SIZE=2][/SIZE][[SIZE=2]Port 1 Link Status[/SIZE]]("http://10.147.172.21/nagios/cgi-bin/extinfo.cgi?type=2&host=Fibre&service=Port+1+Link+Status")[SIZE=2][/SIZE][SIZE=2]UNKNOWN[/SIZE][SIZE=2]08-01-2011 12:25:51[/SIZE][SIZE=2]0d 1h 45m 37s[/SIZE][SIZE=2]3/3[/SIZE][SIZE=2]External command error: MIB search path: /root/.snmp/mibs:/usr/share/mibs/site:/usr/share/snmp/mibs:/usr/share/mibs/iana:/usr/share/mibs/ietf:/usr/share/mibs/netsnmp [/SIZE]

```
 
i have edited the switch.conf and the original path which was
check_command  check_local_mrtgtraf!/var/lib/mrtg/192.168.1.253_1.log!AVG!1000000,1000000!5000000,5000000!10
 }
doesn't exist on my server
so i thought i should just create the directories and the log file, change the permissions for nagios but that hasn't worked
 
what else could i try, thank you!

---

### Post by bwestover on 2011-09-22
>  ./configure 

 sed -i 's:for file in includes/rss/\*;:for file in includes/rss/\*.\*;:g' ./html/Makefile 
 sed -i 's:for file in includes/rss/extlib/\*;:for file in includes/rss/extlib/\*.\*;:g' ./html/Makefile  

 and then make fullinstall    Worked for me as well. Thank you so much.  Does anyone have an explanation as to what this command is doing, and why its needed (my 'sed' is a little rusty)

---

### Post by Fiddler_Wins on 2011-10-31
Thanks .:grunge:. this worked for me too (10.04 but with Nagios 3.3.1)

---

### Post by InfinitePatience on 2011-11-23
> **.:grunge:. said:**
> ./configure

sed -i 's:for file in includes/rss/\*;:for file in includes/rss/\*.\*;:g' ./html/Makefile
sed -i 's:for file in includes/rss/extlib/\*;:for file in includes/rss/extlib/\*.\*;:g' ./html/Makefile

and then
make fullinstall

Hi,

This worked perfectly for me, thank you.  I have a few questions though.
What does it do?  Why do we have to do this despite it not being documented?

Cheers

---

### Post by TheAncientMariner on 2012-05-07
> **InfinitePatience said:**
> Hi,

This worked perfectly for me, thank you.  I have a few questions though.
What does it do?  Why do we have to do this despite it not being documented?

Cheers

There's an error in the install script that creates "rss" as a file instead of a directory. When it tries to add files to the "rss" directory and can't (because it's actually a file), it errors out. The command given above uses the *sed* tool to fix the lines in the script that cause this problem.

---

### Post by bwestover on 2012-05-07
Awesome, thanks for the explanation!   

Now that I know the answer it seems so simple (funny how that works). 

I think it is basically doing this in plain english.  [INDENT]open the file /html/Makefile
find any instances of this string: **for file in includes/rss/*;  **
and replace it with this string: **for file in includes/rss/*.*;**
also replace this string: **for file in includes/rss/extlib/*;**
with this string: **for file in includes/rss/extlib/*.*;**[/INDENT]

---

### Post by daavidfischer on 2012-12-07
I was having the same issue. The only line in the code that I could understand was make [1]: Entering directory `/media/europa/callisto/nagios___/nagios-3.3.1/nagios/base'. I replaced the error codes with the one you provided and it works like a charm. Thanks for the help. 


__________
David Fischer
[car donation](http://www.realworldfinances.com/how-to-claim-the-tax-deduction-for-a-car-donation/)

---

