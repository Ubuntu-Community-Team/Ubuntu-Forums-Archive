---
title: "Trying to install gui on 7.10 server"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by akaney on 2008-02-25
Hello all,

I am new to linux, and have been pushing through, but hit a roadblock. I have tried to install ubuntu desktop, sudo apt-get install ubuntu-desktop, and it looks as though it completed sucessfully, but I think that it may have gone into the wrong directory.  It installed in my home directory, and when I do 'startx etc.' I get the following error(s)

xauth:  creating new authority file /home/administrator/.serverauth.12512
xauth:  /home/administrator/.Xauthority not writable, changes will be ignored
xauth:  error in locking authority file /home/administrator/.Xauthority
xauth:  error in locking authority file /home/administrator/.Xauthority
xauth:  error in locking authority file /home/administrator/.Xauthority
X: user not authorized to run the X server, aborting.
xinit:  Server error.
xauth:  error in locking authority file /home/administrator/.Xauthority
Couldnt get a file descriptor referring to the console

Also, I don't know if it makes a difference, but I am trying to start the gui through ssh and then connect to the machine using vnc.

Any help on which direction I should head would be appreciated.

---

### Post by taurus on 2008-02-25
It is NOT installed in your $HOME.  It probably has something to do with the permissions of your $HOME directory.

Can you post the output of this command?

```
ls -la ~
```

---

### Post by akaney on 2008-02-25
Here are the results of that command


total 25916
drwxr-xr-x 23 administrator administrator    12288 2008-02-25 20:06 .
drwxr-xr-x  6 root          root              4096 2008-02-23 20:25 ..
-rw-r-----  1 administrator administrator   268280 2008-02-08 20:06 aclocal.m4
-r-xr-----  1 administrator administrator     9587 2008-01-29 14:52 align.py
drwxr-----  2 administrator administrator     4096 2008-02-08 20:08 base
-rw-------  1 administrator administrator     5176 2008-02-25 21:11 .bash_histor    y
-rw-r--r--  1 administrator administrator      220 2008-02-23 13:55 .bash_logout
-rw-r--r--  1 administrator administrator     2298 2008-02-23 13:55 .bashrc
-r-xr-----  1 administrator administrator    27677 2008-01-22 14:02 check.py
drwxr-----  3 administrator administrator     4096 2008-02-08 20:08 Cheetah
drwxr-----  4 administrator administrator     4096 2008-02-08 20:08 cherrypy
-r-xr-----  1 administrator administrator     7837 2008-01-29 14:52 clean.py
-r-xr-----  1 administrator administrator    10672 2008-01-29 14:52 colorcal.py
-rwxr-----  1 administrator administrator     3707 2006-12-06 09:55 compile
-rwxr-----  1 administrator administrator    44208 2006-11-08 01:44 config.guess
-rw-r--r--  1 administrator administrator    43545 2008-02-25 09:48 config.log
-rwxr-xr-x  1 administrator administrator    30807 2008-02-25 09:48 config.statu    s
-rwxr-----  1 administrator administrator    32560 2006-11-08 01:44 config.sub
-rwxr-----  1 administrator administrator   814173 2008-02-08 20:06 configure
-r-xr-----  1 administrator administrator    11167 2008-02-08 20:06 configure.in
drwxr-----  2 administrator administrator     4096 2008-02-08 20:08 copier
-r--r-----  1 administrator administrator    17941 2007-08-20 14:27 COPYING
-rw-r--r--  1 administrator administrator     1155 2008-02-25 09:48 cupsext.la
-rw-r--r--  1 administrator administrator      343 2008-02-25 09:48 cupsext_la-c    upsext.lo
drwxr-----  9 administrator administrator     4096 2008-02-08 20:08 data
-rwxr-----  1 administrator administrator    15936 2006-12-06 09:55 depcomp
drwxr-xr-x  2 administrator administrator    12288 2008-02-25 09:51 .deps
drwxr-----  9 administrator administrator     4096 2008-02-08 20:08 doc
-r-xr-----  1 administrator administrator    24050 2008-01-23 12:45 fab.py
-rw-r--r--  1 administrator administrator    27052 2008-02-25 09:50 fat.o
drwxr-----  4 administrator administrator     4096 2008-02-08 20:08 fax
-r-xr-----  1 administrator administrator     6182 2008-01-29 14:52 firmware.py
-rw-r-----  1 administrator administrator    19729 2008-02-08 20:06 foomatic_drv    .inc
-rwxr-xr-x  1 administrator administrator     4508 2008-02-25 09:50 hp
-rwxr-xr-x  1 administrator administrator     5859 2008-02-25 09:50 hpijs
-rw-r--r--  1 administrator administrator    44924 2008-02-25 09:50 hpijs-apollo    21xx.o
-rw-r--r--  1 administrator administrator    38436 2008-02-25 09:50 hpijs-apollo    2560.o
-rw-r--r--  1 administrator administrator    57016 2008-02-25 09:50 hpijs-apollo    2xxx.o
-rw-r--r--  1 administrator administrator    12688 2008-02-25 09:49 hpijs-breaks    _open.o
-rw-r--r--  1 administrator administrator      881 2008-02-25 09:49 hpijs-captur    e.o
-rw-r--r--  1 administrator administrator    21688 2008-02-25 09:49 hpijs-colorm    atcher_open.o
-rw-r--r--  1 administrator administrator    32512 2008-02-25 09:49 hpijs-colorm    atch.o
-rw-r--r--  1 administrator administrator    49224 2008-02-25 09:49 hpijs-compre    ssion.o
-rw-r--r--  1 administrator administrator    73060 2008-02-25 09:49 hpijs-contex    t.o
-rw-r--r--  1 administrator administrator    12608 2008-02-25 09:49 hpijs-create    _so.o
-rw-r--r--  1 administrator administrator    20816 2008-02-25 09:49 hpijs-creato    r.o
-rw-r--r--  1 administrator administrator    21188 2008-02-25 09:50 hpijs-dj3320    _cmap.o
-rw-r--r--  1 administrator administrator   166012 2008-02-25 09:50 hpijs-dj3320    .o
-rw-r--r--  1 administrator administrator    47716 2008-02-25 09:50 hpijs-dj350.    o
-rw-r--r--  1 administrator administrator    18292 2008-02-25 09:50 hpijs-dj3600    _cmap.o
-rw-r--r--  1 administrator administrator    39868 2008-02-25 09:50 hpijs-dj3600    .o
-rw-r--r--  1 administrator administrator    62080 2008-02-25 09:50 hpijs-dj4100    _cmap.o
-rw-r--r--  1 administrator administrator    51472 2008-02-25 09:50 hpijs-dj540.    o
-rw-r--r--  1 administrator administrator     8596 2008-02-25 09:50 hpijs-dj600_    maps.o
-rw-r--r--  1 administrator administrator    55792 2008-02-25 09:49 hpijs-dj600.    o
-rw-r--r--  1 administrator administrator    56468 2008-02-25 09:49 hpijs-dj630.    o
-rw-r--r--  1 administrator administrator     5492 2008-02-25 09:50 hpijs-dj660_    maps.o
-rw-r--r--  1 administrator administrator    50352 2008-02-25 09:49 hpijs-dj660.    o
-rw-r--r--  1 administrator administrator     8588 2008-02-25 09:50 hpijs-dj690_    maps.o
-rw-r--r--  1 administrator administrator    54344 2008-02-25 09:50 hpijs-dj690.    o
-rw-r--r--  1 administrator administrator    43272 2008-02-25 09:50 hpijs-dj6xx.    o
-rw-r--r--  1 administrator administrator     5508 2008-02-25 09:50 hpijs-dj850_    maps.o
-rw-r--r--  1 administrator administrator    56140 2008-02-25 09:50 hpijs-dj850.    o
-rw-r--r--  1 administrator administrator    40464 2008-02-25 09:50 hpijs-dj890.    o
-rw-r--r--  1 administrator administrator     8624 2008-02-25 09:50 hpijs-dj895_    maps2.o
-rw-r--r--  1 administrator administrator     5476 2008-02-25 09:50 hpijs-dj895_    maps.o
-rw-r--r--  1 administrator administrator    44796 2008-02-25 09:50 hpijs-dj8x5.    o
-rw-r--r--  1 administrator administrator    62120 2008-02-25 09:50 hpijs-dj8xx.    o
-rw-r--r--  1 administrator administrator     5544 2008-02-25 09:50 hpijs-dj970_    maps2.o
-rw-r--r--  1 administrator administrator     5504 2008-02-25 09:50 hpijs-dj970_    maps3.o
-rw-r--r--  1 administrator administrator    11732 2008-02-25 09:50 hpijs-dj970_    maps.o
-rw-r--r--  1 administrator administrator    67088 2008-02-25 09:49 hpijs-dj9xx.    o
-rw-r--r--  1 administrator administrator   102212 2008-02-25 09:49 hpijs-dj9xxv    ip.o
-rw-r--r--  1 administrator administrator    59888 2008-02-25 09:50 hpijs-djgene    ricvip.o
-rw-r--r--  1 administrator administrator      883 2008-02-25 09:50 hpijs-filter    hpa.o
-rw-r--r--  1 administrator administrator    22072 2008-02-25 09:50 hpijs-global    s.o
-rw-r--r--  1 administrator administrator    37264 2008-02-25 09:50 hpijs-halfto    ner.o
-rw-r--r--  1 administrator administrator    34800 2008-02-25 09:50 hpijs-halfto    ner_open.o
-rw-r--r--  1 administrator administrator    36052 2008-02-25 09:50 hpijs-header    .o
-rw-r--r--  1 administrator administrator    29128 2008-02-25 09:50 hpijs-hpijsf    ax.o
-rw-r--r--  1 administrator administrator    34800 2008-02-25 09:50 hpijs-hpijs.    o
-rw-r--r--  1 administrator administrator    18544 2008-02-25 09:50 hpijs-hpiom.    o
-rw-r--r--  1 administrator administrator    18000 2008-02-25 09:50 hpijs-htmtxh    i.o
-rw-r--r--  1 administrator administrator     9144 2008-02-25 09:50 hpijs-ijs.o
-rw-r--r--  1 administrator administrator    30704 2008-02-25 09:50 hpijs-ijs_se    rver.o
-rw-r--r--  1 administrator administrator    20736 2008-02-25 09:50 hpijs-jccolo    r.o
-rw-r--r--  1 administrator administrator    13596 2008-02-25 09:50 hpijs-jdatad    bf.o
-rw-r--r--  1 administrator administrator    56072 2008-02-25 09:50 hpijs-job.o
-rw-r--r--  1 administrator administrator    71560 2008-02-25 09:50 hpijs-ljcolo    r.o
-rw-r--r--  1 administrator administrator    93736 2008-02-25 09:50 hpijs-ljfast    raster.o
-rw-r--r--  1 administrator administrator   117500 2008-02-25 09:50 hpijs-ljjetr    eady.o
-rw-r--r--  1 administrator administrator    47548 2008-02-25 09:50 hpijs-ljm100    5.o
-rw-r--r--  1 administrator administrator    62120 2008-02-25 09:50 hpijs-ljmono    .o
-rw-r--r--  1 administrator administrator    47288 2008-02-25 09:50 hpijs-ljzjsm    ono.o
-rw-r--r--  1 administrator administrator    68288 2008-02-25 09:50 hpijs-ljzjs.    o
-rw-r--r--  1 administrator administrator     1464 2008-02-25 09:49 hpijs-models    .o
-rw-r--r--  1 administrator administrator     8612 2008-02-25 09:50 hpijs-phobos    _cmaps.o
-rw-r--r--  1 administrator administrator    27568 2008-02-25 09:50 hpijs-pmsele    ct.o
-rw-r--r--  1 administrator administrator    23212 2008-02-25 09:50 hpijs-printe    rfactory.o
-rw-r--r--  1 administrator administrator    68516 2008-02-25 09:50 hpijs-printe    r.o
-rw-r--r--  1 administrator administrator    18704 2008-02-25 09:50 hpijs-printe    rproxy.o
-rw-r--r--  1 administrator administrator    44432 2008-02-25 09:50 hpijs-psp100    .o
-rw-r--r--  1 administrator administrator   240996 2008-02-25 09:50 hpijs-regist    ry.o
-rw-r--r--  1 administrator administrator    25260 2008-02-25 09:50 hpijs-scaler    .o
-rw-r--r--  1 administrator administrator    23880 2008-02-25 09:50 hpijs-scaler    _open.o
-rw-r--r--  1 administrator administrator      880 2008-02-25 09:50 hpijs-script    .o
-rw-r--r--  1 administrator administrator    48896 2008-02-25 09:50 hpijs-servic    es.o
-rw-r--r--  1 administrator administrator    31820 2008-02-25 09:50 hpijs-system    services.o
-rw-r--r--  1 administrator administrator    22444 2008-02-25 09:50 hpijs-transl    ator.o
-rw-r--r--  1 administrator administrator    14652 2008-02-25 09:50 hpijs-versio    ncode.o
-rw-r--r--  1 administrator administrator     1768 2008-02-25 09:50 hpijs-versio    n.o
drwxr-----  2 administrator administrator     4096 2008-02-25 09:01 .hplip
drwxr----- 18 root          root              4096 2008-02-25 09:11 hplip-2.8.2
-rwxr--r--  1 administrator administrator 14207036 2008-02-25 08:59 hplip-2.8.2.    run
-rw-r--r--  1 administrator administrator      759 2008-02-25 09:48 hplip.conf
-r--r-----  1 administrator administrator      814 2008-01-24 13:47 hplip.conf.i    n
-rw-r--r--  1 administrator administrator      333 2008-02-25 09:48 hplip.deskto    p
-r--r-----  1 administrator administrator      339 2007-08-01 16:00 hplip.deskto    p.in
-r-xr-----  1 administrator administrator      112 2007-12-14 12:34 hplip-instal    l
-rw-r-----  1 administrator administrator     5650 2008-02-25 09:21 hplip-instal    l_Mon-25-Feb-2008_09:18:39.log
-rw-r-----  1 administrator administrator    68071 2008-02-25 09:36 hplip-instal    l_Mon-25-Feb-2008_09:26:02.log
-rw-r-----  1 administrator administrator    13285 2008-02-25 09:41 hplip-instal    l_Mon-25-Feb-2008_09:41:23.log
-rw-r-----  1 administrator administrator   553300 2008-02-25 10:01 hplip-instal    l_Mon-25-Feb-2008_09:47:24.log
-rw-r--r--  1 administrator administrator     1489 2008-02-25 09:48 hpmudext.la
-rw-r--r--  1 administrator administrator      347 2008-02-25 09:48 hpmudext_la-    hpmudext.lo
-rw-r--r--  1 administrator administrator    25344 2008-02-25 09:50 hp.o
-rwxr-xr-x  1 administrator administrator  1535682 2008-02-25 09:51 hppgsz
-rw-r--r--  1 administrator administrator    44924 2008-02-25 09:51 hppgsz-apoll    o21xx.o
-rw-r--r--  1 administrator administrator    38436 2008-02-25 09:51 hppgsz-apoll    o2560.o
-rw-r--r--  1 administrator administrator    57016 2008-02-25 09:51 hppgsz-apoll    o2xxx.o
-rw-r--r--  1 administrator administrator    12688 2008-02-25 09:50 hppgsz-break    s_open.o
-rw-r--r--  1 administrator administrator      881 2008-02-25 09:51 hppgsz-captu    re.o
-rw-r--r--  1 administrator administrator    21688 2008-02-25 09:51 hppgsz-color    matcher_open.o
-rw-r--r--  1 administrator administrator    32512 2008-02-25 09:51 hppgsz-color    match.o
-rw-r--r--  1 administrator administrator    49224 2008-02-25 09:51 hppgsz-compr    ession.o
-rw-r--r--  1 administrator administrator    73060 2008-02-25 09:51 hppgsz-conte    xt.o
-rw-r--r--  1 administrator administrator    12608 2008-02-25 09:51 hppgsz-creat    e_so.o
-rw-r--r--  1 administrator administrator    20816 2008-02-25 09:51 hppgsz-creat    or.o
-rw-r--r--  1 administrator administrator    21188 2008-02-25 09:51 hppgsz-dj332    0_cmap.o
-rw-r--r--  1 administrator administrator   166012 2008-02-25 09:51 hppgsz-dj332    0.o
-rw-r--r--  1 administrator administrator    47716 2008-02-25 09:51 hppgsz-dj350    .o
-rw-r--r--  1 administrator administrator    18292 2008-02-25 09:51 hppgsz-dj360    0_cmap.o
-rw-r--r--  1 administrator administrator    39868 2008-02-25 09:51 hppgsz-dj360    0.o
-rw-r--r--  1 administrator administrator    62080 2008-02-25 09:51 hppgsz-dj410    0_cmap.o
-rw-r--r--  1 administrator administrator    51472 2008-02-25 09:51 hppgsz-dj540    .o
-rw-r--r--  1 administrator administrator     8596 2008-02-25 09:51 hppgsz-dj600    _maps.o
-rw-r--r--  1 administrator administrator    55792 2008-02-25 09:51 hppgsz-dj600    .o
-rw-r--r--  1 administrator administrator    56468 2008-02-25 09:51 hppgsz-dj630    .o
-rw-r--r--  1 administrator administrator     5492 2008-02-25 09:51 hppgsz-dj660    _maps.o
-rw-r--r--  1 administrator administrator    50352 2008-02-25 09:51 hppgsz-dj660    .o
-rw-r--r--  1 administrator administrator     8588 2008-02-25 09:51 hppgsz-dj690    _maps.o
-rw-r--r--  1 administrator administrator    54344 2008-02-25 09:51 hppgsz-dj690    .o
-rw-r--r--  1 administrator administrator    43272 2008-02-25 09:51 hppgsz-dj6xx    .o
-rw-r--r--  1 administrator administrator     5508 2008-02-25 09:51 hppgsz-dj850    _maps.o
-rw-r--r--  1 administrator administrator    56140 2008-02-25 09:51 hppgsz-dj850    .o
-rw-r--r--  1 administrator administrator    40464 2008-02-25 09:51 hppgsz-dj890    .o
-rw-r--r--  1 administrator administrator     8624 2008-02-25 09:51 hppgsz-dj895    _maps2.o
-rw-r--r--  1 administrator administrator     5476 2008-02-25 09:51 hppgsz-dj895    _maps.o
-rw-r--r--  1 administrator administrator    44796 2008-02-25 09:51 hppgsz-dj8x5    .o
-rw-r--r--  1 administrator administrator    62120 2008-02-25 09:51 hppgsz-dj8xx    .o
-rw-r--r--  1 administrator administrator     5544 2008-02-25 09:51 hppgsz-dj970    _maps2.o
-rw-r--r--  1 administrator administrator     5504 2008-02-25 09:51 hppgsz-dj970    _maps3.o
-rw-r--r--  1 administrator administrator    11732 2008-02-25 09:51 hppgsz-dj970    _maps.o
-rw-r--r--  1 administrator administrator    67088 2008-02-25 09:51 hppgsz-dj9xx    .o
-rw-r--r--  1 administrator administrator   102212 2008-02-25 09:51 hppgsz-dj9xx    vip.o
-rw-r--r--  1 administrator administrator    59888 2008-02-25 09:51 hppgsz-djgen    ericvip.o
-rw-r--r--  1 administrator administrator      883 2008-02-25 09:51 hppgsz-filte    rhpa.o
-rw-r--r--  1 administrator administrator    22072 2008-02-25 09:51 hppgsz-globa    ls.o
-rw-r--r--  1 administrator administrator    37264 2008-02-25 09:51 hppgsz-halft    oner.o
-rw-r--r--  1 administrator administrator    34800 2008-02-25 09:51 hppgsz-halft    oner_open.o
-rw-r--r--  1 administrator administrator    36052 2008-02-25 09:51 hppgsz-heade    r.o
-rw-r--r--  1 administrator administrator    18000 2008-02-25 09:51 hppgsz-htmtx    hi.o
-rw-r--r--  1 administrator administrator    20736 2008-02-25 09:51 hppgsz-jccol    or.o
-rw-r--r--  1 administrator administrator    13596 2008-02-25 09:51 hppgsz-jdata    dbf.o
-rw-r--r--  1 administrator administrator    56072 2008-02-25 09:51 hppgsz-job.o
-rw-r--r--  1 administrator administrator    71560 2008-02-25 09:51 hppgsz-ljcol    or.o
-rw-r--r--  1 administrator administrator    93736 2008-02-25 09:51 hppgsz-ljfas    traster.o
-rw-r--r--  1 administrator administrator   117500 2008-02-25 09:51 hppgsz-ljjet    ready.o
-rw-r--r--  1 administrator administrator    47548 2008-02-25 09:51 hppgsz-ljm10    05.o
-rw-r--r--  1 administrator administrator    62120 2008-02-25 09:51 hppgsz-ljmon    o.o
-rw-r--r--  1 administrator administrator    47288 2008-02-25 09:51 hppgsz-ljzjs    mono.o
-rw-r--r--  1 administrator administrator    68288 2008-02-25 09:51 hppgsz-ljzjs    .o
-rw-r--r--  1 administrator administrator     1464 2008-02-25 09:50 hppgsz-model    s.o
-rw-r--r--  1 administrator administrator     8612 2008-02-25 09:51 hppgsz-phobo    s_cmaps.o
-rw-r--r--  1 administrator administrator    27568 2008-02-25 09:51 hppgsz-pmsel    ect.o
-rw-r--r--  1 administrator administrator    23212 2008-02-25 09:51 hppgsz-print    erfactory.o
-rw-r--r--  1 administrator administrator    68516 2008-02-25 09:51 hppgsz-print    er.o
-rw-r--r--  1 administrator administrator    33716 2008-02-25 09:51 hppgsz-Print    erProperties.o
-rw-r--r--  1 administrator administrator    18704 2008-02-25 09:51 hppgsz-print    erproxy.o
-rw-r--r--  1 administrator administrator    44432 2008-02-25 09:51 hppgsz-psp10    0.o
-rw-r--r--  1 administrator administrator   240996 2008-02-25 09:51 hppgsz-regis    try.o
-rw-r--r--  1 administrator administrator    25260 2008-02-25 09:51 hppgsz-scale    r.o
-rw-r--r--  1 administrator administrator    23880 2008-02-25 09:51 hppgsz-scale    r_open.o
-rw-r--r--  1 administrator administrator      880 2008-02-25 09:51 hppgsz-scrip    t.o
-rw-r--r--  1 administrator administrator    31820 2008-02-25 09:51 hppgsz-syste    mservices.o
-rw-r--r--  1 administrator administrator    22444 2008-02-25 09:51 hppgsz-trans    lator.o
-rw-r--r--  1 administrator administrator    14652 2008-02-25 09:51 hppgsz-versi    oncode.o
-rw-r--r--  1 administrator administrator     1768 2008-02-25 09:51 hppgsz-versi    on.o
-r-xr-----  1 administrator administrator    23718 2008-01-03 14:41 hpssd.py
-rw-r--r--  1 administrator administrator     5316 2008-02-25 09:26 index.html
-rw-r--r--  1 administrator administrator     5316 2008-02-25 09:41 index.html.1
-rw-r--r--  1 administrator administrator     5316 2008-02-25 09:47 index.html.2
-r-xr-----  1 administrator administrator     6372 2008-01-29 14:52 info.py
-r--r-----  1 administrator administrator      799 2007-01-11 14:52 __init__.py
drwxr-----  7 administrator administrator     4096 2008-02-08 20:08 installer
-r-xr-----  1 administrator administrator     5381 2008-01-17 17:10 install.py
-rwxr-----  1 administrator administrator     9233 2006-12-06 09:55 install-sh
drwxr-----  4 administrator administrator     4096 2008-02-08 20:08 io
drwxr-----  2 administrator administrator     4096 2008-02-08 20:08 ip
-rw-r--r--  1 administrator administrator      319 2008-02-25 09:48 ipmain.lo
-r-xr-----  1 administrator administrator     8159 2008-01-29 14:52 levels.py
-rw-r--r--  1 administrator administrator     1140 2008-02-25 09:49 libhpip.la
-rw-r--r--  1 administrator administrator     1146 2008-02-25 09:48 libhpmud.la
-rw-r--r--  1 administrator administrator      339 2008-02-25 09:48 libhpmud_la-    dot4.lo
-rw-r--r--  1 administrator administrator      341 2008-02-25 09:48 libhpmud_la-    hpmud.lo
-rw-r--r--  1 administrator administrator      335 2008-02-25 09:48 libhpmud_la-    jd.lo
-rw-r--r--  1 administrator administrator      337 2008-02-25 09:48 libhpmud_la-    mlc.lo
-rw-r--r--  1 administrator administrator      341 2008-02-25 09:48 libhpmud_la-    model.lo
-rw-r--r--  1 administrator administrator      339 2008-02-25 09:48 libhpmud_la-    musb.lo
-rw-r--r--  1 administrator administrator      337 2008-02-25 09:48 libhpmud_la-    pml.lo
-rw-r--r--  1 administrator administrator      335 2008-02-25 09:48 libhpmud_la-    pp.lo
drwxr-xr-x  2 administrator administrator     4096 2008-02-25 09:52 .libs
-rw-r--r--  1 administrator administrator     1729 2008-02-25 09:49 libsane-hpai    o.la
-rw-r--r--  1 administrator administrator      353 2008-02-25 09:49 libsane_hpai    o_la-common.lo
-rw-r--r--  1 administrator administrator      351 2008-02-25 09:49 libsane_hpai    o_la-hpaio.lo
-rw-r--r--  1 administrator administrator      345 2008-02-25 09:49 libsane_hpai    o_la-io.lo
-rw-r--r--  1 administrator administrator      353 2008-02-25 09:49 libsane_hpai    o_la-mfpdtf.lo
-rw-r--r--  1 administrator administrator      347 2008-02-25 09:49 libsane_hpai    o_la-pml.lo
-rw-r--r--  1 administrator administrator      373 2008-02-25 09:49 libsane_hpai    o_la-sanei_init_debug.lo
-rw-r--r--  1 administrator administrator      347 2008-02-25 09:49 libsane_hpai    o_la-scl.lo
-rw-r--r--  1 administrator administrator      359 2008-02-25 09:49 libsane_hpai    o_la-soap_stub.lo
-rwxr-xr-x  1 administrator administrator   217286 2008-02-25 09:48 libtool
-rw-r-----  1 administrator administrator   196719 2006-06-19 13:36 ltmain.sh
-r-xr-----  1 administrator administrator    13735 2008-01-23 12:45 makecopies.p    y
-rw-r--r--  1 administrator administrator   464115 2008-02-25 09:48 Makefile
-r--r-----  1 administrator administrator    23878 2008-02-05 10:30 Makefile.am
-rw-r-----  1 administrator administrator   535807 2008-02-08 20:06 Makefile.in
-r-xr-----  1 administrator administrator     6208 2007-08-14 15:42 makeuri.py
-rwxr-----  1 administrator administrator    11014 2006-12-06 09:55 missing
drwxr-----  3 administrator administrator     4096 2008-02-08 20:08 pcard
-rw-r--r--  1 administrator administrator     1161 2008-02-25 09:49 pcardext.la
-rw-r--r--  1 administrator administrator      337 2008-02-25 09:49 pcardext_la-    fat.lo
-rw-r--r--  1 administrator administrator      347 2008-02-25 09:49 pcardext_la-    pcardext.lo
drwxr-----  2 administrator administrator     4096 2008-02-08 20:08 plugins
drwxr-----  2 administrator administrator    28672 2008-02-08 20:08 ppd
-r-xr-----  1 administrator administrator     5086 2008-01-25 17:02 print.py
drwxr-----  7 administrator administrator     4096 2008-02-08 20:08 prnt
-r-xr-----  1 administrator administrator     9486 2007-09-26 11:51 probe.py
-rw-r--r--  1 administrator administrator      566 2008-02-23 13:55 .profile
-rwxr-xr-x  1 administrator administrator     4529 2008-02-25 09:50 ptest
-rw-r--r--  1 administrator administrator    21328 2008-02-25 09:50 ptest.o
-rw-------  1 root          root              1024 2008-02-25 09:47 .rnd
drwxr-----  4 administrator administrator     4096 2008-02-08 20:08 scan
-rw-r--r--  1 administrator administrator     1155 2008-02-25 09:49 scanext.la
-rw-r--r--  1 administrator administrator      343 2008-02-25 09:49 scanext_la-s    canext.lo
-r-xr-----  1 administrator administrator    48570 2008-01-23 12:45 scan.py
-r-xr-----  1 administrator administrator    24770 2008-01-23 12:45 sendfax.py
-r-xr-----  1 administrator administrator    44894 2008-02-06 13:19 setup.py
-rw-r--r--  1 administrator administrator       31 2008-02-23 20:36 sudo
-rw-r--r--  1 administrator administrator        0 2008-02-23 20:15 .sudo_as_adm    in_successful
-r-xr-----  1 administrator administrator     7928 2007-09-13 18:14 testpage.py
-r-xr-----  1 administrator administrator     5439 2008-01-29 14:52 timedate.py
-r-xr-----  1 administrator administrator     5102 2008-01-23 12:45 toolbox.py
drwxr-----  2 administrator administrator     4096 2008-02-08 20:08 ui
-r-xr-----  1 administrator administrator    28289 2008-02-06 13:19 unload.py
-rw-r-----  1 administrator administrator       30 2008-02-08 20:06 unreleased.i    nc
drwx------  2 root          root              4096 2008-02-25 19:57 .vnc
-rw-------  1 root          root               101 2008-02-25 19:57 .Xauthority
-rw-------  2 administrator administrator        0 2008-02-25 20:06 .Xauthority-    c
-rw-------  2 administrator administrator        0 2008-02-25 20:06 .Xauthority-    l
-rw-r--r--  1 administrator administrator      323 2008-02-25 09:49 xbi2gray.lo
-rw-r--r--  1 administrator administrator      321 2008-02-25 09:49 xchgbpp.lo
-rw-r--r--  1 administrator administrator      323 2008-02-25 09:49 xcolrspc.lo
-rw-r--r--  1 administrator administrator      325 2008-02-25 09:48 xconvolve.lo
-rw-r--r--  1 administrator administrator      317 2008-02-25 09:49 xcrop.lo
-rw-r--r--  1 administrator administrator      325 2008-02-25 09:49 xfakemono.lo
-rw-r--r--  1 administrator administrator      315 2008-02-25 09:48 xfax.lo
-rw-r--r--  1 administrator administrator      319 2008-02-25 09:49 xgamma.lo
-rw-r--r--  1 administrator administrator      323 2008-02-25 09:49 xgray2bi.lo
-rw-r--r--  1 administrator administrator      323 2008-02-25 09:48 xgrayout.lo
-rw-r--r--  1 administrator administrator      321 2008-02-25 09:49 xinvert.lo
-rw-r--r--  1 administrator administrator      323 2008-02-25 09:48 xjpg_dct.lo
-rw-r--r--  1 administrator administrator      323 2008-02-25 09:49 xjpg_dec.lo
-rw-r--r--  1 administrator administrator      323 2008-02-25 09:49 xjpg_enc.lo
-rw-r--r--  1 administrator administrator      323 2008-02-25 09:48 xjpg_fix.lo
-rw-r--r--  1 administrator administrator      323 2008-02-25 09:49 xjpg_huf.lo
-rw-r--r--  1 administrator administrator      321 2008-02-25 09:49 xmatrix.lo
-rw-r--r--  1 administrator administrator      315 2008-02-25 09:48 xpad.lo
-rw-r--r--  1 administrator administrator      315 2008-02-25 09:49 xpcx.lo
-rw-r--r--  1 administrator administrator      315 2008-02-25 09:49 xpnm.lo
-rw-r--r--  1 administrator administrator      321 2008-02-25 09:48 xrotate.lo
-rw-r--r--  1 administrator administrator      329 2008-02-25 09:49 xsaturation.    lo
-rw-r--r--  1 administrator administrator      319 2008-02-25 09:49 xscale.lo
-rw-r--r--  1 administrator administrator      317 2008-02-25 09:48 xskel.lo
-rw-r--r--  1 administrator administrator      319 2008-02-25 09:49 xtable.lo
-rw-r--r--  1 administrator administrator      319 2008-02-25 09:49 xthumb.lo
-rw-r--r--  1 administrator administrator      317 2008-02-25 09:48 xtiff.lo
-rw-r--r--  1 administrator administrator      323 2008-02-25 09:49 xtonemap.lo
-rw-r--r--  1 administrator administrator      323 2008-02-25 09:49 xyxtract.lo

---

### Post by taurus on 2008-02-25
There's your problem.  Somehow, root owns /home/administrator/.Xauthority which means you, administrator user, can't write to it.  Try changing the ownership back so you can write to that hidden file.

```
sudo chown administrator:administrator /home/administrator/.Xauthority
ls -la ~
```

---

