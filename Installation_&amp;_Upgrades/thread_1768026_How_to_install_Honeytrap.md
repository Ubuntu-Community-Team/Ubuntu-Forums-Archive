---
title: "How to install Honeytrap?"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by Skyo on 2011-05-26
Hallo folks!

Im trying to install Honeytrap desperately on my Ubuntu 11.04 box.
Link1 >[ Official Homepage]("http://honeytrap.carnivore.it/")
Link2 >[ Sourceforge: Code]("http://sourceforge.net/projects/honeytrap/")

Unfortunately I miss a good and whats more, recent guide.
Following the recommendation of the install-readme, I installed libnetfilter_queue via Synaptic.

Configure works well now.

[COLOR="Green"]/honeytrap-1.0.0$ ./configure --with-stream-mon=nfq [/COLOR]
```

 
 (some Checks)
 
  ----- honeytrap configuration -----
 
   General options
     ( )  Debugging
     ( )  Profiling
     ( )  Unstable Modules
     ( )  Electric Fence
 
   Connection monitor
     ( )  Linux ip_queue (ipq)
     ( )  FreeBSD ipfw (ipfw)
     (X)  Linux libnetfilter_queue (nfq)
     ( )  Libpcap (pcap)
 
   Optional plugins
     ( )  ClamAV
     ( )  cpuEmu
     ( )  CSPM
     ( )  PostgeSQL
     ( )  SpamSum
     ( )  submitMwserv
 

```

The next step is, afaik, make.
Yeah, little bit GERMAN in it, though relevant parts should be english.

[COLOR="Green"]/honeytrap-1.0.0$ make[/COLOR]
```

 make  all-recursive
 make[1]: Betrete Verzeichnis '/home/skyo/job/honeytrap-1.0.0'
 Making all in doc
 make[2]: Betrete Verzeichnis '/home/skyo/job/honeytrap-1.0.0/doc'
 make[2]: Für das Ziel »all« ist nichts zu tun.
 make[2]: Verlasse Verzeichnis '/home/skyo/job/honeytrap-1.0.0/doc'
 Making all in src
 make[2]: Betrete Verzeichnis '/home/skyo/job/honeytrap-1.0.0/src'
 Making all in modules
 make[3]: Betrete Verzeichnis '/home/skyo/job/honeytrap-1.0.0/src/modules'
 make[4]: Betrete Verzeichnis '/home/skyo/job/honeytrap-1.0.0/src/modules'
 /bin/sh ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I../   -Wall -Werror -g -O2 -Wall -c -o htm_SaveFile.lo htm_SaveFile.c
  gcc -DHAVE_CONFIG_H -I. -I../.. -I../ -Wall -Werror -g -O2 -Wall -c htm_SaveFile.c  -fPIC -DPIC -o .libs/htm_SaveFile.o
 In file included from /usr/include/fcntl.h:252:0,
                  from ../logging.h:17,
                  from htm_SaveFile.c:29:
 In function 'open',
     inlined from 'save_to_file' at htm_SaveFile.c:145:5:
 /usr/include/bits/fcntl2.h:51:24: error: call to '__open_missing_mode' declared with attribute error: open with O_CREAT in second argument needs 3 arguments
 In function 'open',
     inlined from 'save_to_file' at htm_SaveFile.c:172:6:
 /usr/include/bits/fcntl2.h:51:24: error: call to '__open_missing_mode' declared with attribute error: open with O_CREAT in second argument needs 3 arguments
 make[4]: *** [htm_SaveFile.lo] Fehler 1
 make[4]: Verlasse Verzeichnis '/home/skyo/job/honeytrap-1.0.0/src/modules'
 make[3]: *** [all-recursive] Fehler 1
 make[3]: Verlasse Verzeichnis '/home/skyo/job/honeytrap-1.0.0/src/modules'
 make[2]: *** [all-recursive] Fehler 1
 make[2]: Verlasse Verzeichnis '/home/skyo/job/honeytrap-1.0.0/src'
 make[1]: *** [all-recursive] Fehler 1
 make[1]: Verlasse Verzeichnis '/home/skyo/job/honeytrap-1.0.0'
 make: *** [all] Fehler 2

```

I guess, i have to reconfigute the make-files, havent I?
Regards, Skyo.

---

