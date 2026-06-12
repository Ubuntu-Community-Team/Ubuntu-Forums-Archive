---
title: "BIND9 FAILS to start under Ubuntu 12.04.2 LTS"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by mypcnetworks on 2013-03-26
Hello group.

I am setting up a local server for wireless authentication and accounting testing purposes, with this I elected to install Ubuntu 12.04.2 following the howto: [http://www.howtoforge.com/perfect-server-debian-squeeze-ispconfig-2](http://www.howtoforge.com/perfect-server-debian-squeeze-ispconfig-2). Yes I realize that this howto is for debian squeeze, however debian seams to be much like Ubuntu with some respects.

This is a fresh installation, nothing other than OpenSSH installed prior to this installation

At this point BIND9 fails to start.

The output of cat /var/log/syslog | grep bind
```
Mar 25 14:02:03 RADIUS kernel: [    0.191665] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 25 14:02:03 RADIUS kernel: [    0.193242] TCP: Hash tables configured (established 131072 bind 65536)
Mar 25 14:29:59 RADIUS kernel: [    0.187650] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 25 14:29:59 RADIUS kernel: [    0.189159] TCP: Hash tables configured (established 131072 bind 65536)
Mar 25 15:14:36 RADIUS kernel: [    0.187724] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 25 15:14:36 RADIUS kernel: [    0.189298] TCP: Hash tables configured (established 131072 bind 65536)
Mar 25 19:40:32 RADIUS named[17621]: starting BIND 9.8.1-P1 -u bind
Mar 25 19:40:32 RADIUS named[17621]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro' 'CPPFLAGS=-D_FORTIFY_SOURCE=2'
Mar 25 19:40:32 RADIUS named[17621]: loading configuration from '/etc/bind/named.conf'
Mar 25 19:40:32 RADIUS named[17621]: reading built-in trusted keys from file '/etc/bind/bind.keys'
Mar 25 19:40:32 RADIUS named[17621]: set up managed keys zone for view _default, file 'managed-keys.bind'
Mar 25 19:40:32 RADIUS named[17621]: managed-keys-zone ./IN: loading from master file managed-keys.bind failed: file not found

```

From viewing the error log above it seems obvious that the file 'bind.keys' is unavailable to BIND??
BIND has been moved from */etc/bind* to */var/lib/named/etc* as per the howto I am following.

**The contents of /var/lib/named/etc**
```
bind       db.0    db.255    db.local  named.conf                named.conf.local    rndc.key
bind.keys  db.127  db.empty  db.root   named.conf.default-zones  named.conf.options  zones.rfc1918

```

I have located a bug report pertaining to Ubuntu 12.04.2 and BIND9 specifically also: [https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/920202](https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/920202)

**I have also edited /etc/bind/named.conf to**
```
include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
include "/etc/bind/bind.keys";                      
```

However BIND9 still FAILS when I attempt to start it...

---

### Post by mypcnetworks on 2013-03-26
INFO UPDATE

**When I run /var/lib/named/etc# ls -l **
```
total 56
drwxr-sr-x 2 bind bind 4096 Mar 25 21:47 bind
-rw-r--r-- 1 root root 2389 Dec  5 13:37 bind.keys
-rw-r--r-- 1 root root  237 Dec  5 13:37 db.0
-rw-r--r-- 1 root root  271 Dec  5 13:37 db.127
-rw-r--r-- 1 root root  237 Dec  5 13:37 db.255
-rw-r--r-- 1 root root  353 Dec  5 13:37 db.empty
-rw-r--r-- 1 root root  270 Dec  5 13:37 db.local
-rw-r--r-- 1 root root 2994 Dec  5 13:37 db.root
-rw-r--r-- 1 root bind  503 Mar 25 21:50 named.conf
-rw-r--r-- 1 root bind  490 Dec  5 13:37 named.conf.default-zones
-rw-r--r-- 1 root bind  165 Dec  5 13:37 named.conf.local
-rw-r--r-- 1 root bind  890 Mar 25 19:40 named.conf.options
-rw-r----- 1 bind bind   77 Mar 25 19:40 rndc.key
-rw-r--r-- 1 root root 1317 Dec  5 13:37 zones.rfc1918
```

---

### Post by Doug S on 2013-03-26
> The output of cat /var/log/syslog | grep bindDo this instead:```
grep named /var/log/syslog
```Then you will get all Bind9 related entries, as the daemon is called "named".> BIND has been moved from *[FONT=Thread-00001dcc-Id-0000004a]/etc/bind[/FONT]* to *[FONT=Thread-00001dcc-Id-0000004a]/var/lib/named/etc[/FONT]* as per the howto I am following.
Don't move the directory and toss your howto. Suggest the [Ubuntu serverguide ]("https://help.ubuntu.com/12.04/serverguide/dns.html")instead.

---

### Post by mypcnetworks on 2013-03-26
Thank you very much for the reply Doug...

Here are the results of grep named /var/log/syslog
```
Mar 25 19:40:40 RADIUS named[17621]: error (unexpected RCODE REFUSED) resolving 'E.ROOT-SERVERS.NET/AAAA/IN': 198.41.0.4#53
Mar 25 19:40:40 RADIUS named[17621]: error (network unreachable) resolving 'E.ROOT-SERVERS.NET/AAAA/IN': 2001:500:2f::f#53
Mar 25 19:40:40 RADIUS named[17621]: error (unexpected RCODE REFUSED) resolving 'C.ROOT-SERVERS.NET/AAAA/IN': 198.41.0.4#53
Mar 25 19:40:40 RADIUS named[17621]: error (network unreachable) resolving 'C.ROOT-SERVERS.NET/AAAA/IN': 2001:500:2f::f#53
Mar 25 19:40:40 RADIUS named[17621]: error (unexpected RCODE REFUSED) resolving 'D.ROOT-SERVERS.NET/AAAA/IN': 198.41.0.4#53
Mar 25 19:40:40 RADIUS named[17621]: error (network unreachable) resolving 'D.ROOT-SERVERS.NET/AAAA/IN': 2001:500:2f::f#53
Mar 25 19:40:40 RADIUS named[17621]: error (unexpected RCODE REFUSED) resolving 'G.ROOT-SERVERS.NET/AAAA/IN': 198.41.0.4#53
Mar 25 19:40:40 RADIUS named[17621]: error (network unreachable) resolving 'G.ROOT-SERVERS.NET/AAAA/IN': 2001:500:2f::f#53
Mar 25 19:40:41 RADIUS named[17621]: error (unexpected RCODE REFUSED) resolving 'E.ROOT-SERVERS.NET/AAAA/IN': 192.33.4.12#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'E.ROOT-SERVERS.NET/AAAA/IN': 2001:7fd::1#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'E.ROOT-SERVERS.NET/AAAA/IN': 2001:500:3::42#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'E.ROOT-SERVERS.NET/AAAA/IN': 2001:503:c27::2:30#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'E.ROOT-SERVERS.NET/AAAA/IN': 2001:dc3::35#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'E.ROOT-SERVERS.NET/AAAA/IN': 2001:7fe::53#53
Mar 25 19:40:41 RADIUS named[17621]: error (unexpected RCODE REFUSED) resolving 'B.ROOT-SERVERS.NET/AAAA/IN': 192.33.4.12#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'B.ROOT-SERVERS.NET/AAAA/IN': 2001:7fd::1#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'B.ROOT-SERVERS.NET/AAAA/IN': 2001:500:3::42#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'E.ROOT-SERVERS.NET/AAAA/IN': 2001:500:1::803f:235#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'E.ROOT-SERVERS.NET/AAAA/IN': 2001:503:ba3e::2:30#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'B.ROOT-SERVERS.NET/AAAA/IN': 2001:503:c27::2:30#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'B.ROOT-SERVERS.NET/AAAA/IN': 2001:dc3::35#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'B.ROOT-SERVERS.NET/AAAA/IN': 2001:7fe::53#53
Mar 25 19:40:41 RADIUS named[17621]: error (unexpected RCODE REFUSED) resolving 'C.ROOT-SERVERS.NET/AAAA/IN': 192.33.4.12#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'C.ROOT-SERVERS.NET/AAAA/IN': 2001:7fd::1#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'C.ROOT-SERVERS.NET/AAAA/IN': 2001:500:3::42#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'B.ROOT-SERVERS.NET/AAAA/IN': 2001:500:1::803f:235#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'B.ROOT-SERVERS.NET/AAAA/IN': 2001:503:ba3e::2:30#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'C.ROOT-SERVERS.NET/AAAA/IN': 2001:503:c27::2:30#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'C.ROOT-SERVERS.NET/AAAA/IN': 2001:dc3::35#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'C.ROOT-SERVERS.NET/AAAA/IN': 2001:7fe::53#53
Mar 25 19:40:41 RADIUS named[17621]: error (unexpected RCODE REFUSED) resolving 'D.ROOT-SERVERS.NET/AAAA/IN': 192.33.4.12#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'D.ROOT-SERVERS.NET/AAAA/IN': 2001:7fd::1#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'D.ROOT-SERVERS.NET/AAAA/IN': 2001:500:3::42#53
Mar 25 19:40:41 RADIUS named[17621]: error (unexpected RCODE REFUSED) resolving 'G.ROOT-SERVERS.NET/AAAA/IN': 192.33.4.12#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'G.ROOT-SERVERS.NET/AAAA/IN': 2001:7fd::1#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'G.ROOT-SERVERS.NET/AAAA/IN': 2001:500:3::42#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'C.ROOT-SERVERS.NET/AAAA/IN': 2001:500:1::803f:235#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'C.ROOT-SERVERS.NET/AAAA/IN': 2001:503:ba3e::2:30#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'D.ROOT-SERVERS.NET/AAAA/IN': 2001:503:c27::2:30#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'D.ROOT-SERVERS.NET/AAAA/IN': 2001:dc3::35#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'D.ROOT-SERVERS.NET/AAAA/IN': 2001:7fe::53#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'G.ROOT-SERVERS.NET/AAAA/IN': 2001:503:c27::2:30#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'G.ROOT-SERVERS.NET/AAAA/IN': 2001:dc3::35#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'G.ROOT-SERVERS.NET/AAAA/IN': 2001:7fe::53#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'D.ROOT-SERVERS.NET/AAAA/IN': 2001:500:1::803f:235#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'D.ROOT-SERVERS.NET/AAAA/IN': 2001:503:ba3e::2:30#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'G.ROOT-SERVERS.NET/AAAA/IN': 2001:500:1::803f:235#53
Mar 25 19:40:41 RADIUS named[17621]: error (network unreachable) resolving 'G.ROOT-SERVERS.NET/AAAA/IN': 2001:503:ba3e::2:30#53
```

Thanks for the suggestion of the Ubuntu Server Guide too!

Best Regards

---

### Post by Doug S on 2013-03-26
O.K. so now named is running. As far as I know (which I am not an expert) it is not unusual to get some Refused replies, but I suspect it is unusual from the root servers. I do not know about your IPv6 unreachable stuff, as I do not use IPv6. In general, is your name server working now?
Just for possible comparison here are the named entries for my system for yesterday (no entries yet today):```
doug@doug-64:/etc/bind$ [COLOR=#ff0000]grep named /var/log/syslog.1[/COLOR]
Mar 25 13:48:44 doug-64 named[30381]: success resolving 'www.nationalledger.com/A' (in 'nationalledger.com'?) after disabling EDNS
Mar 25 21:38:23 doug-64 named[30381]: error (unexpected RCODE SERVFAIL) resolving 'customer124148.megacable.com.ar/A/IN': 200.123.158.99#53
Mar 25 21:38:23 doug-64 named[30381]: error (connection refused) resolving 'ns.cableway.net.AR/A/IN': 200.80.18.69#53
Mar 25 23:06:25 doug-64 named[30381]: success resolving 'ns2.hostease.com/A' (in 'hostease.com'?) after disabling EDNS
Mar 25 23:06:28 doug-64 named[30381]: success resolving 'ns1.hostease.com/A' (in 'hostease.com'?) after disabling EDNS
Mar 25 23:06:41 doug-64 named[30381]: error (connection refused) resolving 'movshare.net/A/IN': 78.152.56.84#53
Mar 25 23:06:41 doug-64 named[30381]: error (connection refused) resolving 'www.divxstage.eu/A/IN': 78.152.56.84#53
Mar 25 23:06:41 doug-64 named[30381]: error (connection refused) resolving 'videoweed.es/A/IN': 78.152.56.84#53
Mar 25 23:07:29 doug-64 named[30381]: error (unexpected RCODE REFUSED) resolving 'cdn.celebified.com/A/IN': 144.198.29.53#53
Mar 25 23:23:58 doug-64 named[30381]: lame server resolving '56.117.206.218.in-addr.arpa' (in '117.206.218.in-addr.arpa'?): 211.103.13.101#53
Mar 25 23:23:58 doug-64 named[30381]: lame server resolving '56.117.206.218.in-addr.arpa' (in '117.206.218.in-addr.arpa'?): 211.138.200.69#53
Mar 25 23:23:59 doug-64 named[30381]: success resolving 'ns1.cnmobile.net/A' (in 'cnmobile.net'?) after disabling EDNS
Mar 25 23:23:59 doug-64 named[30381]: success resolving 'ns2.cnmobile.net/A' (in 'cnmobile.net'?) after disabling EDNS
```

---

### Post by mypcnetworks on 2013-03-26
Hi Doug...

No BIND9 fails at the start command.

I don't use IPV6, so I have disabled it, but BIND9 still fails to start 

I did notice a strange situation however: when I access /var/lib/named/etc...
Which looks like:
```
bind       db.0    db.255    db.local  named.conf                named.conf.local    rndc.key
bind.keys  db.127  db.empty  db.root   named.conf.default-zones  named.conf.options  zones.rfc1918

```

If I cd into the DIR bind, it is infinite, I could continue cd'ing into bind until the cows come home

---

### Post by Doug S on 2013-03-26
Oh, I did not realize that bind was still not running for you.

Isn't the /var/lib/named directory left over from your first attempts, at the start of this thread? I do not have such a directory.
Maybe supply us with some of your configuration files.

Please be aware that the serverguide troubleshooting section where it mentions editing resolv.conf it out of date. Editing resolv.conf directly is no longer the way.

---

### Post by mypcnetworks on 2013-03-26
FIXED IT!

after uninstalling BIND9 and doing some cleanup, I then re-installed BIND9 successfully and it starts and runs ;-)  YEEEEEHAAWWW!

Anyhow, thank you very much for your responses and help with my dilemma Doug. Thank you

Best Regards
Pat Taylor

---

