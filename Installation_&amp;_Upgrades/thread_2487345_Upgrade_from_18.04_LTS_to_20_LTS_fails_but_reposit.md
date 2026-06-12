---
title: "Upgrade from 18.04 LTS to 20 LTS fails but repository server seems reachable"
date: 2023-05-31
forum: Installation &amp; Upgrades
---

### Post by riccardo-ciro-romano on 2023-05-31
Hallo to all,
I'm trying to upgrade a virtual machine in cloud from Ubuntu 18.04 LTS to Ubuntu 20.04 LTS.

I managed to complete the first steps with the commands:

```

sudo apt-get update
sudo apt-get --with-new-pkgs upgrade

```

using these lines in my /etc/apt/sources.list:

```

deb mirror://mirrors.ubuntu.com/mirrors.txt bionic main restricted universe multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt bionic-updates main restricted universe multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt bionic-backports main restricted universe multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt bionic-security main restricted universe multiverse

```

I'm now trying to upgrade from the 18 to the 20 major version of Ubuntu, but I get this error:

```

$ sudo do-release-upgrade
Checking for a new Ubuntu release
Err Upgrade tool signature
  Connection failed [IP: 90.147.160.73 80]
Err Upgrade tool
  Connection failed [IP: 90.147.160.70 80]
Fetched 0 B in 6s (0 B/s)
WARNING:root:file 'focal.tar.gz.gpg' missing
Failed to fetch
Fetching the upgrade failed. There may be a network problem.

```

I tried to change the repository servers in the /etc/apt/sources.list with several other servers, but to no avail.
I'm now using these servers' entries in the sources.list file (as I'm in Italy):
```

deb http://it.archive.ubuntu.com/ubuntu/ bionic main universe restricted multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ bionic main universe restricted multiverse

```

As the error says there may be a network problem, I monitored the network traffic with tcpdump and I can see a data exchange between the machine and the repository server; so, as far as I understand, the connection is working.

```

tcpdump -i ens3 -q -n -nn not port 22
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on ens3, link-type EN10MB (Ethernet), capture size 262144 bytes
13:24:15.739122 IP 10.10.0.12.35184 > 90.147.160.70.80: tcp 0
13:24:15.757184 IP 90.147.160.70.80 > 10.10.0.12.35184: tcp 0
13:24:15.757227 IP 10.10.0.12.35184 > 90.147.160.70.80: tcp 0
13:24:15.757317 IP 10.10.0.12.35184 > 90.147.160.70.80: tcp 200
13:24:15.774574 IP 90.147.160.70.80 > 10.10.0.12.35184: tcp 0
13:24:15.774658 IP 90.147.160.70.80 > 10.10.0.12.35184: tcp 284
13:24:15.774667 IP 10.10.0.12.35184 > 90.147.160.70.80: tcp 0
13:24:15.774727 IP 90.147.160.70.80 > 10.10.0.12.35184: tcp 0
13:24:15.775207 IP 10.10.0.12.35184 > 90.147.160.70.80: tcp 0
13:24:15.785345 IP 10.10.0.12.35198 > 90.147.160.70.80: tcp 0
13:24:15.792102 IP 90.147.160.70.80 > 10.10.0.12.35184: tcp 0
13:24:15.802504 IP 90.147.160.70.80 > 10.10.0.12.35198: tcp 0
13:24:15.802536 IP 10.10.0.12.35198 > 90.147.160.70.80: tcp 0
13:24:15.802619 IP 10.10.0.12.35198 > 90.147.160.70.80: tcp 196
13:24:15.819602 IP 90.147.160.70.80 > 10.10.0.12.35198: tcp 0
13:24:15.819860 IP 90.147.160.70.80 > 10.10.0.12.35198: tcp 290
13:24:15.819868 IP 10.10.0.12.35198 > 90.147.160.70.80: tcp 0
13:24:15.819879 IP 90.147.160.70.80 > 10.10.0.12.35198: tcp 0
13:24:15.820419 IP 10.10.0.12.35198 > 90.147.160.70.80: tcp 0
13:24:15.831547 IP 10.10.0.12.35210 > 90.147.160.70.80: tcp 0
13:24:15.837205 IP 90.147.160.70.80 > 10.10.0.12.35198: tcp 0
13:24:15.848987 IP 90.147.160.70.80 > 10.10.0.12.35210: tcp 0
13:24:15.849017 IP 10.10.0.12.35210 > 90.147.160.70.80: tcp 0
13:24:15.849150 IP 10.10.0.12.35210 > 90.147.160.70.80: tcp 164
13:24:15.866650 IP 90.147.160.70.80 > 10.10.0.12.35210: tcp 0
13:24:15.866948 IP 90.147.160.70.80 > 10.10.0.12.35210: tcp 433
13:24:15.866958 IP 10.10.0.12.35210 > 90.147.160.70.80: tcp 0
(...)

```

The TCP data exchange suddenly stops, and the upgrade process doesn't start.

As the error message says "Err Upgrade tool signature", I also tried to reinstall the upgrade tool with the command:
```

sudo apt-get install --reinstall ubuntu-release-upgrader-core

```
but that didn't help.

Thank you in advance for any help.

---

### Post by MAFoElffen on 2023-06-01
Please confirm that this is what your /etc/apt/sources.list now looks like:
```

deb http://it.archive.ubuntu.com/ubuntu/ bionic main restricted universe multiverse 
deb http://it.archive.ubuntu.com/ubuntu/ bionic-security main restricted universe multiverse 
deb http://it.archive.ubuntu.com/ubuntu/ bionic-updates main restricted universe multiverse 
deb http://it.archive.ubuntu.com/ubuntu/ bionic-proposed main restricted universe multiverse 
deb http://it.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse 

```

---

### Post by riccardo-ciro-romano on 2023-06-01
Hallo and thank you for you prompt reply,
I commented out anything in the sources.list file and put the lines you've written, but the behaviour is the same.

I captured the terminal output in a file (to read all the lines which are overwritten by the terminal), and after giving the command "sudo do-release-upgrade" the machine seems to connect but stops shortly after, waiting for headers:

```

0% [Connecting to it.archive.ubuntu.com]
0% [Connecting to it.archive.ubuntu.com (90.147.160.70)]
0% [Connected to it.archive.ubuntu.com (90.147.160.70)]
0% [Waiting for headers]

```

Then, after a minute or so, it declares failure, and tries another connection, but again it stops with the "waiting for headers" print:

```

$ sudo do-release-upgrade
Checking for a new Ubuntu release
Err Upgrade tool signature
  Connection failed [IP: 90.147.160.73 80]
0% [Waiting for headers]

```

Then, after another minute or so, it declares failure and stops. This is the final printout on the terminal:

```


$ sudo do-release-upgrade
Checking for a new Ubuntu release
Err Upgrade tool signature
  Connection failed [IP: 90.147.160.73 80]
Err Upgrade tool
  Connection failed [IP: 90.147.160.70 80]
Fetched 0 B in 6s (0 B/s)
WARNING:root:file 'focal.tar.gz.gpg' missing
Failed to fetch
Fetching the upgrade failed. There may be a network problem.

```

---

### Post by MAFoElffen on 2023-06-01
Please post the results of
```

mtr --report it.archive.ubuntu.com

```
To compare, this is the results I get for that:
```

mafoelffen@Mikes-B460M:~$ mtr --report it.archive.ubuntu.com
Start: 2023-06-01T01:19:57-0700
HOST: Mikes-B460M                 Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 2601:603:4900:77e0:a656:c  0.0%    10    6.0   5.0   3.1  10.3   2.0
  2.|-- 2001:558:4082:58::1        0.0%    10   14.4  29.2  11.4  79.8  25.8
  3.|-- po-305-1210-rur202.tumwat  0.0%    10   13.3  14.3  12.7  16.9   1.2
  4.|-- 2001:558:a0:f6ac::1        0.0%    10   12.0  14.0  12.0  15.5   1.0
  5.|-- 2001:558:a0:2016::1       80.0%    10   20.7  20.1  19.5  20.7   0.8
  6.|-- be-36121-cs02.seattle.wa.  0.0%    10   18.3  18.4  16.0  19.8   1.1
  7.|-- be-2212-pe12.seattle.wa.i  0.0%    10   16.6  18.1  16.6  19.8   0.9
  8.|-- ???                       100.0    10    0.0   0.0   0.0   0.0   0.0
  9.|-- 2001:2000:3080:21c1::1     0.0%    10   63.6  73.7  62.5 119.1  20.4
 10.|-- nyk-bb1-v6.ip.twelve99.ne  0.0%    10   79.5  81.7  79.5  90.6   3.3
 11.|-- ldn-bb2-v6.ip.twelve99.ne 90.0%    10  153.2 153.2 153.2 153.2   0.0
 12.|-- prs-bb2-v6.ip.twelve99.ne  0.0%    10  158.1 160.9 154.9 203.1  14.9
 13.|-- 2001:760:ffff:ffaa::180:1  0.0%    10  188.8 191.3 188.8 195.4   2.0
 14.|-- 2001:760:ffff:b2::3a       0.0%    10  191.3 191.2 189.3 199.7   3.1
 15.|-- 2001:760:ffff:b6:4:100:0:  0.0%    10  189.2 189.8 188.8 192.3   1.0
 16.|-- 2001:760:ffff:b6:4:100:0:  0.0%    10  189.2 191.1 189.1 197.9   2.6

```

---

### Post by riccardo-ciro-romano on 2023-06-01
This is the output of the mtr command on my machine:

```

~$ mtr --report it.archive.ubuntu.com
Start: 2023-06-01T08:42:13+0000
HOST: *****.*****.it         Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.6.66               0.0%    10    1.1   2.1   1.1   8.7   2.3
  2.|-- 192.168.6.1                0.0%    10    1.2   1.8   1.1   5.4   1.3
  3.|-- 169.254.97.97              0.0%    10    1.1   1.5   1.1   2.0   0.3
  4.|-- 131.1.240.1                0.0%    10    1.8   2.0   1.8   2.5   0.2
  5.|-- 172.29.5.100               0.0%    10    1.6   2.0   1.6   2.4   0.3
  6.|-- 172.29.5.102               0.0%    10    1.9   2.1   1.9   2.5   0.2
  7.|-- 172.29.5.59                0.0%    10    2.4   2.6   2.3   3.1   0.2
  8.|-- 172.29.5.45                0.0%    10    2.2   2.4   2.1   3.0   0.3
  9.|-- 10.54.2.134                0.0%    10    4.3   6.0   3.8  22.0   5.6
 10.|-- 10.54.1.214                0.0%    10    3.7   7.5   3.7  26.3   7.7
 11.|-- 10.54.1.186                0.0%    10    3.6   7.5   3.5  32.7   9.3
 12.|-- 10.54.2.97                 0.0%    10    4.1   5.5   3.7  19.4   4.9
 13.|-- 172.17.66.143              0.0%    10   12.4   5.8   3.6  13.9   3.9
 14.|-- re1-rm02-rs1-bo01.bo01.ga  0.0%    10    8.9   9.7   8.9  15.6   2.1
 15.|-- rs1-bo01-rs1-ba01.ba01.ga  0.0%    10   18.1  18.2  17.7  20.0   0.7
 16.|-- 185.191.180.19             0.0%    10   17.3  17.7  17.3  20.2   0.9
 17.|-- dc2-bari-rx1-ba1.ba1.garr  0.0%    10   31.3  19.7  17.6  31.3   4.4
 18.|-- 90.147.160.174             0.0%    10   17.5  17.7  17.4  19.0   0.5
 19.|-- 90.147.160.70              0.0%    10   17.3  17.5  17.2  18.8   0.5

```

---

### Post by MAFoElffen on 2023-06-01
It is connecting with no network problems...

I mean, I see no reason why it isn't working. maybe that repo is having a problem internally(?)

Have you tried one fo the Mirrors on this list for Italy:
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by riccardo-ciro-romano on 2023-06-01
I just tried a couple of mirrors, but the behaviour is the same.
I will check with other collegues if there's some reason why the NGFW could possibly interrupt the upgrade at some point.

thank you

---

