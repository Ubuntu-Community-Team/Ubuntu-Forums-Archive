---
title: "Ubuntu noob - wireshark installation question..."
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by nleachman on 2006-10-09
Hi, 

I have some Linux experiense - mainly RH and SUSE; but I've just installed my first Ubuntu system (Dapper). I'm now trying to figure out to install Wireshark on it. I don't see it listed in Add/Remove programs; but I read a post that seems to imply that either it or ethereal should be available there. Am I missing something obvious?

Can someone please outline the proper steps to install Wireshark on 6.06? I'd rather not use ethereal at this point; but if I have to I will.

Many thanks!
Nick

---

### Post by mark_g on 2006-10-09
At this time the repositories still only have Ethereal which you can get with > apt-get install ethereal
(make sure you have all repositories enabled!)
but they will change it to Wireshark, although I can't tell you when.
If you must have the latest version, Wireshark, you could install it from source. Just download the file from the website at

> [http://www.wireshark.org/download/src/wireshark-0.99.3a.tar.gz](http://www.wireshark.org/download/src/wireshark-0.99.3a.tar.gz)

Open a terminal, go to the directory the file is and execute

> ./configure && make && make install

If you have any error messages, just let me know.

---

### Post by nleachman on 2006-10-10
Hi Mark, 

First, thanks for the fast reply - I'm sorry it's taken me this long to try the install. 

Second, I decided to go with Wireshark; and I'm afraid that I do get an error complaining of no C compiler:

tracepc@tracepc-laptop01:~/wireshark-0.99.3a$ ./configure && make && makeinstall
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
tracepc@tracepc-laptop01:~/wireshark-0.99.3a$

When I check the installer I have the following pkgs installed:
gcc-3.3-base, gcc-3.4, gcc-3.4-base, gcc-4.0-base, g++-3.4, g++-4.0, gcj-4.1-base, libgcc1, and libgcj7 - when I search against gcc and compiler. And libpcap0.8 is installed as well.

I can attach the config.log if that would be of help. 

From what I've included can you tell what pkg I'm missing please?

Thanks again, 
Nick

---

### Post by mark_g on 2006-10-10
Do you have build-essential installed?

---

### Post by nleachman on 2006-10-10
In an attempt to get the installation of the wireshark to complete I had to keep adding packages - it was satisfied with libpcap0.7, build-essential, and several of the libglib pkgs. However, I then got complaints about pcap.h (which is mentioned in the wireshark FAQ's) and while trying to correct it things went south in a hurry! I got many screens-ful of garbage while trying to satisfy the pcap.h issue; so...

...I decided that the system was no longer in a state that I could trust so I reloaded it from scratch, ran Add/Remove again - which now lists "ethereal"!, and installed it.

I'm left confused as to why ethereal wasn't showing as available in Add/Remove yesterday...was it just added to the source server?

The ethereal installation went just fine...so all's well now.

- nick

---

### Post by candyoff on 2006-10-21
hi!

I am new in this...
I was trying to install wireshark. 
But seem there were something wrong... 
I have to keep adding packages until ./configure run smooth. 
The "make" command seem doesnt run smooth... 
As you can see in the code below, it keep display unarrange wierd codes non stop (at least it run for 5 mins non stop then i stoppped it) 
I only copied a little bit of the unarrange codes. 
Hope someone can help me with this

Regards



```
The Wireshark package has been configured with the following options.
                    Build wireshark : yes
                       Build tshark : yes
                     Build capinfos : yes
                      Build editcap : yes
                      Build dumpcap : yes
                     Build mergecap : yes
                    Build text2pcap : yes
                      Build idl2wrs : yes
                      Build randpkt : yes
                       Build dftest : yes

                     Install setuid : no
                        Use plugins : yes
                   Build lua plugin : no
                Use GTK+ v2 library : yes
                       Use threads : no
            Build profile binaries : no
                  Use pcap library : yes
                  Use zlib library : yes
                  Use pcre library : no
              Use kerberos library : no
              Use GNU ADNS library : no
            Use GNU crypto library : no
            Use SSL crypto library : no
          Use IPv6 name resolution : yes
     Use UCD SNMP/Net-SNMP library : no
                Use gnutls library : no
root@USERNAME-laptop:/home/USERNAME/Desktop/mixed/wireshark# make
/usr/bin/perl ./make-version.pl .
Version configuration file version.conf not found.  Using defaults.
This is not a SVN build.
svnversion.h is up-to-date.
make  all-recursive
make[1]: Entering directory `/home/USERNAME/Desktop/mixed/wireshark'
Making all in tools
make[2]: Entering directory `/home/USERNAME/Desktop/mixed/wireshark/tools'
Making all in lemon
make[3]: Entering directory `/home/USERNAME/Desktop/mixed/wireshark/tools/lemon'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/USERNAME/Desktop/mixed/wireshark/tools/lemon'
make[3]: Entering directory `/home/USERNAME/Desktop/mixed/wireshark/tools'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/USERNAME/Desktop/mixed/wireshark/tools'
make[2]: Leaving directory `/home/USERNAME/Desktop/mixed/wireshark/tools'
Making all in wiretap
make[2]: Entering directory `/home/USERNAME/Desktop/mixed/wireshark/wiretap'
make  all-am
make[3]: Entering directory `/home/USERNAME/Desktop/mixed/wireshark/wiretap'
make[3]: Leaving directory `/home/USERNAME/Desktop/mixed/wireshark/wiretap'
make[2]: Leaving directory `/home/USERNAME/Desktop/mixed/wireshark/wiretap'
Making all in doc
make[2]: Entering directory `/home/USERNAME/Desktop/mixed/wireshark/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/USERNAME/Desktop/mixed/wireshark/doc'
Making all in epan
make[2]: Entering directory `/home/USERNAME/Desktop/mixed/wireshark/epan'
Making all in ftypes
make[3]: Entering directory `/home/USERNAME/Desktop/mixed/wireshark/epan/ftypes'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/USERNAME/Desktop/mixed/wireshark/epan/ftypes'
Making all in dfilter
make[3]: Entering directory `/home/USERNAME/Desktop/mixed/wireshark/epan/dfilter'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/USERNAME/Desktop/mixed/wireshark/epan/dfilter'
Making all in dissectors
make[3]: Entering directory `/home/USERNAME/Desktop/mixed/wireshark/epan/dissectors'
make  all-am
make[4]: Entering directory `/home/USERNAME/Desktop/mixed/wireshark/epan/dissectors'
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I. ./.. -I./../.. -I./..   -I/usr/local/include  -DINET6 -D_U_="__attribute__((unus ed))" -Wall -Wpointer-arith -W  -g -O2 -I/usr/local/include -pthread -I/usr/incl ude/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cai ro -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -MT packet-olsr.lo -MD -MP -MF ".deps/packet-olsr.Tpo" -c -o packet-olsr.lo pa cket-olsr.c; \
        then mv -f ".deps/packet-olsr.Tpo" ".deps/packet-olsr.Plo"; else rm -f " .deps/packet-olsr.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I./../.. -I./.. -I/usr/local/include -DINE T6 "-D_U_=__attribute__((unused))" -Wall -Wpointer-arith -W -g -O2 -I/usr/local/ include -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/includ e/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -MT packet-olsr.lo -MD -MP -MF .deps/packet-olsr.Tpo
```

---

