---
title: "trouble installing airsnort"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by chr3681 on 2007-05-12
[B][U][U]***EDIT: Got it installed through Synaptic Package Manager!***
[/U][/U][/B]

Hi, I am having trouble installing airsnort on Ubuntu Feisty Fawn. At first the trouble was in the fact that I hadn't yet installed gtk and necessary libraries. now, after installing those, when I do ./configure everything seems to work fine but when issuing the 'make' command, i get this list of errors:

make  all-recursive
make[1]: Entering directory `/home/chris/Desktop/airsnort-0.2.7e'
Making all in src
make[2]: Entering directory `/home/chris/Desktop/airsnort-0.2.7e/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12      -g -O2 -MT callbacks.o -MD -MP -MF ".deps/callbacks.Tpo" -c -o callbacks.o callbacks.c; \
        then mv -f ".deps/callbacks.Tpo" ".deps/callbacks.Po"; else rm -f ".deps/callbacks.Tpo"; exit 1; fi
callbacks.c:9:18: error: pcap.h: No such file or directory
In file included from PacketSource.h:31,
                 from callbacks.c:24:
/usr/include/linux/wireless.h:646: error: expected specifier-qualifier-list before &#8216;__s32&#8217;
/usr/include/linux/wireless.h:659: error: expected specifier-qualifier-list before &#8216;__u16&#8217;
/usr/include/linux/wireless.h:673: error: expected specifier-qualifier-list before &#8216;__s32&#8217;
/usr/include/linux/wireless.h:684: error: expected specifier-qualifier-list before &#8216;__u8&#8217;
/usr/include/linux/wireless.h:700: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:713: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:740: error: expected specifier-qualifier-list before &#8216;__u8&#8217;
/usr/include/linux/wireless.h:802: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:816: error: expected specifier-qualifier-list before &#8216;__u16&#8217;
/usr/include/linux/wireless.h:830: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:838: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:847: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:859: error: expected specifier-qualifier-list before &#8216;__u16&#8217;
/usr/include/linux/wireless.h:882: error: &#8216;IFNAMSIZ&#8217; undeclared here (not in a function)
/usr/include/linux/wireless.h:897: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:941: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:1042: error: expected specifier-qualifier-list before &#8216;__u32&#8217;
/usr/include/linux/wireless.h:1060: error: expected specifier-qualifier-list before &#8216;__u16&#8217;
In file included from callbacks.c:24:
PacketSource.h:153: error: expected specifier-qualifier-list before &#8216;pcap_t&#8217;
PacketSource.h:178: warning: &#8216;struct pcap_pkthdr&#8217; declared inside parameter list
PacketSource.h:178: warning: its scope is only this definition or declaration, which is probably not what you want
PacketSource.h:179: warning: &#8216;struct pcap_pkthdr&#8217; declared inside parameter list
callbacks.c:79: error: &#8216;PCAP_ERRBUF_SIZE&#8217; undeclared here (not in a function)
callbacks.c: In function &#8216;fillDeviceList&#8217;:
callbacks.c:121: error: storage size of &#8216;ir&#8217; isn&#8217;t known
callbacks.c:129: error: &#8216;IFF_LOOPBACK&#8217; undeclared (first use in this function)
callbacks.c:129: error: (Each undeclared identifier is reported only once
callbacks.c:129: error: for each function it appears in.)
make[2]: *** [callbacks.o] Error 1
make[2]: Leaving directory `/home/chris/Desktop/airsnort-0.2.7e/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/chris/Desktop/airsnort-0.2.7e'
make: *** [all] Error 2


I am pretty new to linux and would love any help i can get! thanks in advance for your time!

---

### Post by abedbajia on 2008-06-08
i have the same problem if you get it fixed post it here 
thanks

---

### Post by Monicker on 2008-06-08
abedbajia - He edited the post to show that he installed it from Synaptic, because there is an Ubuntu package for airsnort.

[http://packages.ubuntu.com/feisty/airsnort](http://packages.ubuntu.com/feisty/airsnort)


Also, I would have to say that aircrack-ng is a much better tool for cracking WEP.  It is a command line application though.

---

### Post by abedbajia on 2008-06-08
i have used aircrack-ng 

but when i use airoplay to inject packets the computer freezes ?

---

