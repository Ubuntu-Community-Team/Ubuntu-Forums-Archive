---
title: "Loss of connection after upgrade to 12.04"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by mulanee on 2012-06-10
Hi there,
After upgrading to 12.04, and after 1st reboot, I discovered that there is no connection with outside from my home network.
My home network works.
Here is ifconfig answer:
> 
root@box:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:b0:d0:ed:b7:e9
          inet adr:192.168.1.5  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: 2a01:e35:398d:4c00:fc9d:5169:41ec:22e1/64 Scope:Global
          adr inet6: 2a01:e35:398d:4c00:2b0:d0ff:feed:b7e9/64 Scope:Global
          adr inet6: fe80::2b0:d0ff:feed:b7e9/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reÃ§us:106 erreurs:0 :0 overruns:0 frame:0
          TX packets:153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reÃ§us:27036 (27.0 KB) Octets transmis:25779 (25.7 KB)
          Interruption:10 Adresse de base:0xc400

lo        Link encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:HÃ´te
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reÃ§us:1799 erreurs:0 :0 overruns:0 frame:0
          TX packets:1799 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reÃ§us:594446 (594.4 KB) Octets transmis:594446 (594.4 KB)


Any advise is welcome, thank you.

---

### Post by sanderj on 2012-06-10
Your ifconfig looks. And you have IPv6 ... cool!

Post the output of these commands:

ip route show
mtr -nrc2 8.8.8.8

---

### Post by mulanee on 2012-06-10
Hi,

Here is the result:

> root@box:~# ip route show
default via 192.168.1.50 dev eth0  metric 100
169.254.0.0/16 dev eth0  scope link  metric 1000
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.5
root@box:~# mtr -nrc2 8.8.8.8
HOST: box                         Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.1.50               0.0%     2    0.8   2.5   0.8   4.3   2.5
  2.|-- 83.152.212.254             0.0%     2   21.7  21.9  21.7  22.2   0.3
  3.|-- 213.228.30.254            50.0%     2   21.5  21.5  21.5  21.5   0.0
  4.|-- 212.27.50.17               0.0%     2   22.0  22.7  22.0  23.5   1.1
  5.|-- 212.27.50.29               0.0%     2   22.7  23.0  22.7  23.4   0.5
  6.|-- 149.6.165.217              0.0%     2   23.8  23.6  23.5  23.8   0.2
  7.|-- 130.117.1.221              0.0%     2   23.8  23.2  22.6  23.8   0.8
  8.|-- 130.117.50.17              0.0%     2   32.2  32.2  32.2  32.2   0.0
  9.|-- 154.54.57.178              0.0%     2   32.3  32.7  32.3  33.2   0.6
 10.|-- 154.54.61.214              0.0%     2   32.3  32.7  32.3  33.0   0.5
 11.|-- 149.6.146.30               0.0%     2  173.2 143.6 114.0 173.2  41.9
 12.|-- 209.85.255.84              0.0%     2   31.3  63.8  31.3  96.4  46.0
 13.|-- 209.85.253.92              0.0%     2   32.4  32.4  32.4  32.5   0.1
 14.|-- 209.85.243.33              0.0%     2   39.0  38.5  38.1  39.0   0.6
    |  `|-- 209.85.240.28
 15.|-- 216.239.49.28              0.0%     2   42.6  42.3  41.9  42.6   0.5
    |  `|-- 216.239.49.36
 16.|-- 209.85.255.126             0.0%     2   46.2  44.5  42.8  46.2   2.4
 17.|-- 8.8.8.8                    0.0%     2   42.5  42.8  42.5  43.0   0.3


---

### Post by sanderj on 2012-06-10
That looks good.

How about:

mtr -rc2 8.8.8.8
time host [www.google.com](www.google.com)
wget -O/dev/null [ftp://ftp.xs4all.nl/pub/test/3mb.bin](ftp://ftp.xs4all.nl/pub/test/3mb.bin)

---

### Post by mulanee on 2012-06-10
For this one it took time:
> root@box:~# mtr -rc2 8.8.8.8
HOST: box                         Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- freebox                    0.0%     2    0.8   0.8   0.8   0.8   0.0
  2.|-- 83.152.212.254             0.0%     2   21.1  21.6  21.1  22.1   0.7
  3.|-- 213.228.30.254             0.0%     2   22.8  23.4  22.8  24.0   0.8
  4.|-- 212.27.50.17               0.0%     2   23.1  22.7  22.3  23.1   0.6
  5.|-- 212.27.50.29               0.0%     2   22.2  22.7  22.2  23.2   0.7
  6.|-- 149.6.165.217              0.0%     2   23.0  23.2  23.0  23.4   0.3
  7.|-- 130.117.1.221              0.0%     2   24.1  23.3  22.6  24.1   1.1
  8.|-- 130.117.50.17              0.0%     2   32.4  32.6  32.4  32.7   0.2
  9.|-- 154.54.57.178              0.0%     2   30.8  31.8  30.8  32.9   1.5
 10.|-- 154.54.61.214              0.0%     2   31.4  32.2  31.4  33.0   1.1
 11.|-- 149.6.146.30               0.0%     2  116.7 118.6 116.7 120.5   2.7
 12.|-- 209.85.255.84              0.0%     2   32.3  36.5  32.3  40.7   5.9
 13.|-- 209.85.253.196             0.0%     2   31.6  34.9  31.6  38.3   4.8
 14.|-- 209.85.240.28              0.0%     2   39.6  39.3  39.0  39.6   0.4
 15.|-- 216.239.49.36              0.0%     2   42.7  42.8  42.7  42.9   0.1
 16.|-- 209.85.255.126             0.0%     2   53.2  49.5  45.8  53.2   5.2
 17.|-- 8.8.8.8                    0.0%     2   41.7  42.5  41.7  43.3   1.1


The second one too
> root@box:~# time host [www.google.com](www.google.com)
;; connection timed out; no servers could be reached

real    0m12.222s
user    0m0.004s
sys     0m0.036s


The last one doesn't work
> root@box:~# wget -O/dev/null [ftp://ftp.xs4all.nl/pub/test/3mb.bin](ftp://ftp.xs4all.nl/pub/test/3mb.bin)
--2012-06-10 22:08:02--  [ftp://ftp.xs4all.nl/pub/test/3mb.bin](ftp://ftp.xs4all.nl/pub/test/3mb.bin)
           => Â«/dev/nullÂ»
RÃ©solution de ftp.xs4all.nl (ftp.xs4all.nl)... Ã©chec: Nom ou service inconnu.
wget : impossible de rÃ©soudre l'adresse de l'hÃ´te Â«ftp.xs4all.nlÂ»


---

### Post by sanderj on 2012-06-10
Easy: you have no (working) nameserver defined.

Now the difficult part: since 12.04 the nameserver setup has changed, and I'm not sure about the setup. So let's discover it ...

What's the output of:

cat /etc/resolv.conf
host [www.google.com](www.google.com) localhost
host [www.google.com](www.google.com) 8.8.8.8

---

### Post by mulanee on 2012-06-10
Something connected to DNS servers??

Results:

> root@box:~# cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

> root@box:~# host [www.google.com](www.google.com) localhost
;; connection timed out; no servers could be reached

> root@box:~# host [www.google.com](www.google.com) 8.8.8.8
Using domain server:
Name: 8.8.8.8
Address: 8.8.8.8#53
Aliases:

[www.google.com](www.google.com) is an alias for [www.l.google.com](www.l.google.com).
[www.l.google.com](www.l.google.com) has address 173.194.78.99
[www.l.google.com](www.l.google.com) has address 173.194.78.106
[www.l.google.com](www.l.google.com) has address 173.194.78.103
[www.l.google.com](www.l.google.com) has address 173.194.78.105
[www.l.google.com](www.l.google.com) has address 173.194.78.147
[www.l.google.com](www.l.google.com) has address 173.194.78.104
[www.l.google.com](www.l.google.com) has IPv6 address 2a00:1450:4007:802::1013

---

### Post by sanderj on 2012-06-10
Yup, it's your DNS.

On Ubuntu 12.04, it seems there is a namerserver locally (='localhost'). Which is not the case for your system, so that's wrong and the root cause.

However I don't know which process should be running. On my 12.04 I checked, and there is a nameserver running on port :53, but I can't find the name: not named, not bind.

Ah ... found it:

```
sander@R540:~$ sudo netstat -apon | grep :53 | grep -i LISTEN
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      13828/dnsmasq    off (0.00/0/0)
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN      1330/dnsmasq     off (0.00/0/0)
sander@R540:~$

sander@R540:~$ which dnsmasq
/usr/sbin/dnsmasq
sander@R540:~$


```

Can you start "sudo dnsmasq"? If so, does "host www.google.com" work then?

---

### Post by mulanee on 2012-06-10
Answer:

> root@box:~# sudo dnsmasq
root@box:~# host [www.google.com](www.google.com)
Host [www.google.com](www.google.com) not found: 5(REFUSED)


---

### Post by mulanee on 2012-06-10
More:

> root@box:~# sudo netstat -apon | grep :53 | grep -i LISTEN
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN      5181/dnsmasq     off (0.00/0/0)
tcp6       0      0 :::53                   :::*                    LISTEN      5181/dnsmasq     off (0.00/0/0)


---

### Post by sanderj on 2012-06-10
As an ugly hack you could edit /etc/resolv.conf to contain "nameserver 8.8.8.8" (and only that). Then name resolving should work. Please test.

However, as /etc/resolv.conf itself says, the file will be overwritten after a reboot, or even earlier.

However, worth a try.

---

### Post by sanderj on 2012-06-10
If the above works, this might be a solution: de-install and remove dnsmasq, and then install it again. So:

sudo apt-get install dnsmasq
sudo apt-get remove dnsmasq
sudo apt-get purge dnsmasq
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install dnsmasq

... and then reboot (just to be sure).

For more info: [https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)

---

### Post by mulanee on 2012-06-10
It sounds good.
> 
root@box:~# vi /etc/resolv.conf
root@box:~# host [www.google.com](www.google.com)
[www.google.com](www.google.com) is an alias for [www.l.google.com](www.l.google.com).
[www.l.google.com](www.l.google.com) has address 173.194.78.99
[www.l.google.com](www.l.google.com) has address 173.194.78.103
[www.l.google.com](www.l.google.com) has address 173.194.78.104
[www.l.google.com](www.l.google.com) has address 173.194.78.147
[www.l.google.com](www.l.google.com) has address 173.194.78.105
[www.l.google.com](www.l.google.com) has address 173.194.78.106
[www.l.google.com](www.l.google.com) has IPv6 address 2a00:1450:4007:802::1013
root@box:~# ping google.com
PING google.com (173.194.78.139) 56(84) bytes of data.
64 bytes from wg-in-f139.1e100.net (173.194.78.139): icmp_req=1 ttl=47 time=32.5 ms
64 bytes from wg-in-f139.1e100.net (173.194.78.139): icmp_req=2 ttl=47 time=33.8 ms
64 bytes from wg-in-f139.1e100.net (173.194.78.139): icmp_req=3 ttl=47 time=33.0 ms
64 bytes from wg-in-f139.1e100.net (173.194.78.139): icmp_req=4 ttl=47 time=32.3 ms
^C
--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 32.333/32.932/33.850/0.590 ms
root@box:~#

Just to be sure it it will stay after a reboot.
I'll try later.
If it disappears, I can probably do a copy action in init.d directory.
Not so beautiful, but if it works....

---

### Post by sanderj on 2012-06-10
... a "Merci" would be nice, don't you think?

---

### Post by mulanee on 2012-06-10
I don't want a dhcp server working in my station because I already have one in my router, I suppose it's not a good idea to have two servers, how to stop this one?

It seems I have another problem:

> root@box:~# sudo apt-get update
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease

Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise InRelease

Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates InRelease

Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease

Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
  Ne parvient pas Ã* rÃ©soudre Â«Â*extras.ubuntu.comÂ*Â»
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise Release.gpg
  Ne parvient pas Ã* rÃ©soudre Â«Â*fr.archive.ubuntu.comÂ*Â»
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
  Ne parvient pas Ã* rÃ©soudre Â«Â*security.ubuntu.comÂ*Â»
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates Release.gpg
  Ne parvient pas Ã* rÃ©soudre Â«Â*fr.archive.ubuntu.comÂ*Â»
Lecture des listes de paquets... Fait
W: Impossible de rÃ©cupÃ©rer [http://fr.archive.ubuntu.com/ubuntu/dists/precise/InRelease](http://fr.archive.ubuntu.com/ubuntu/dists/precise/InRelease)

W: Impossible de rÃ©cupÃ©rer [http://fr.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease](http://fr.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease)

W: Impossible de rÃ©cupÃ©rer [http://extras.ubuntu.com/ubuntu/dists/precise/InRelease](http://extras.ubuntu.com/ubuntu/dists/precise/InRelease)

W: Impossible de rÃ©cupÃ©rer [http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease](http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease)

W: Impossible de rÃ©cupÃ©rer [http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Ne parvient pas Ã* rÃ©soudre Â«Â*extras.ubuntu.comÂ*Â»

W: Impossible de rÃ©cupÃ©rer [http://fr.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://fr.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Ne parvient pas Ã* rÃ©soudre Â«Â*fr.archive.ubuntu.comÂ*Â»

W: Impossible de rÃ©cupÃ©rer [http://fr.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://fr.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Ne parvient pas Ã* rÃ©soudre Â«Â*fr.archive.ubuntu.comÂ*Â»

W: Impossible de rÃ©cupÃ©rer [http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Ne parvient pas Ã* rÃ©soudre Â«Â*security.ubuntu.comÂ*Â»

W: Le tÃ©lÃ©chargement de quelques fichiers d'index a Ã©chouÃ©, ils ont Ã©tÃ© ignorÃ©s, ou les anciens ont Ã©tÃ© utilisÃ©s Ã* la place.


---

### Post by mulanee on 2012-06-10
> ... a "Merci" would be nice, don't you think? Sure but you write too quickly I didn't have time :popcorn:

Well, you are very efficient and of course I thank you for your support!!

[FONT=Arial Black][SIZE=4]**Merci beaucoup**[/SIZE][/FONT]

---

### Post by sanderj on 2012-06-10
BTW: your webserver is accessible via the IPv6 address you posted in the ifconfig. Is that OK with you? It's OK with me: I laughed very hard at the Bush joke and the Sarkozy joke.

---

### Post by mulanee on 2012-06-11
For information, my server doesn't pick up its IP from DHCP server.
This is the reason why resolv.conf doesn't survive to a reboot.
Just need to uninstall resolvconf and add > nameserver 8.8.8.8 to /etc/resolv.conf
Thank you for having given me the first white stone.

---

