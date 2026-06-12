---
title: "Error using &quot;make&quot; to build opentracker in /usr/bin/ld"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by blakmoon91 on 2008-09-29
Group,
Hopefully something simple, I am trying to install Opentracker on my box and I run into a issue when running the make command. I hope someone has seen this before and has a solution for this little deal. Thanks in advance for looking!

rmccullough@SAGO002448:~/opentracker$ make
cc -c -o opentracker.o -I../libowfat -Wall -pipe -Wextra  -Os  opentracker.c
cc -c -o trackerlogic.o -I../libowfat -Wall -pipe -Wextra  -Os  trackerlogic.c
cc -c -o scan_urlencoded_query.o -I../libowfat -Wall -pipe -Wextra  -Os  scan_urlencoded_query.c
cc -c -o ot_mutex.o -I../libowfat -Wall -pipe -Wextra  -Os  ot_mutex.c
cc -c -o ot_stats.o -I../libowfat -Wall -pipe -Wextra  -Os  ot_stats.c
cc -c -o ot_sync.o -I../libowfat -Wall -pipe -Wextra  -Os  ot_sync.c
cc -c -o ot_vector.o -I../libowfat -Wall -pipe -Wextra  -Os  ot_vector.c
cc -c -o ot_clean.o -I../libowfat -Wall -pipe -Wextra  -Os  ot_clean.c
cc -c -o ot_udp.o -I../libowfat -Wall -pipe -Wextra  -Os  ot_udp.c
cc -c -o ot_iovec.o -I../libowfat -Wall -pipe -Wextra  -Os  ot_iovec.c
cc -c -o ot_fullscrape.o -I../libowfat -Wall -pipe -Wextra  -Os  ot_fullscrape.c
cc -c -o ot_accesslist.o -I../libowfat -Wall -pipe -Wextra  -Os  ot_accesslist.c
cc -c -o ot_http.o -I../libowfat -Wall -pipe -Wextra  -Os  ot_http.c
cc -o opentracker opentracker.o trackerlogic.o scan_urlencoded_query.o ot_mutex.o ot_stats.o ot_sync.o ot_vector.o ot_clean.o ot_udp.o ot_iovec.o ot_fullscrape.o ot_accesslist.o ot_http.o -L../libowfat -lowfat -pthread -lz
/usr/bin/ld: cannot find -lz
collect2: ld returned 1 exit status
make: *** [opentracker] Error 1
rmccullough@SAGO002448:~/opentracker$

---

### Post by cariboo on 2008-09-30
You could use apt-file to find the missing package:

```
sudo apt-get install apt-file
```

Then once it has finished updating the db run:

```
apt-file find lz
```

This unfortunately will find all the packages with lz in it, but the package you need will be in the list.

Jim

---

### Post by blakmoon91 on 2008-09-30
Jim,
You were 100% dead on the money. Using the apt-file find command gave me a huge list of possibilities so I did a bit more digging and found that the -lz referred to a graphics library "Libz" that was missing for some reason so:

sudo aptitude install libz-dev

Resolved the problem, thanks so much for getting it going for me!

---

### Post by huanix on 2008-11-01
> **blakmoon91 said:**
> Jim,
You were 100% dead on the money. Using the apt-file find command gave me a huge list of possibilities so I did a bit more digging and found that the -lz referred to a graphics library "Libz" that was missing for some reason so:

sudo aptitude install libz-dev

Resolved the problem, thanks so much for getting it going for me!

Worked for me as well on 8.10

---

