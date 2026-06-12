---
title: "[SOLVED] Edgy aptitude update problem"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by mrlarone on 2007-07-02
Hello,

i'm trying to update my pkg list but getting the following

<code>

me@puter:/etc/apt$ sudo aptitude update

Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Translation-en_US
  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Translation-en_US
  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
Reading package lists... Done

me@puter:/etc/apt$

</code>

i've also tried apt-get update and get the same result: here's my sources.list

<code>

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
##deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
##deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
## deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
## deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

##deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
##deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
##deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
##deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

</code>

this was working yesterday when i upgraded something from the security (i've commented out all non-essential repo's as part of my ltd debug), but now nada :(.

any scoobies

p.s. i can ping these IP's and i access this computer remotely so it's not a connection issue!?

---

### Post by Rui Pais on 2007-07-02
> **mrlarone said:**
> p.s. i can ping these IP's and i access this computer remotely so it's not a connection issue!?

Hi,

you say you can ping the IPs, can you ping them both in ip form and:
```
ping -c3 gb.archive.ubuntu.com
```
form?

---

### Post by mrlarone on 2007-07-02
er, no

here's the result

ping: unknown host [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)

---

### Post by Rui Pais on 2007-07-02
> **mrlarone said:**
> er, no

here's the result

ping: unknown host [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)

sorry, without the http:// part, just:
```
ping -c3 gb.archive.ubuntu.com
```

---

### Post by mrlarone on 2007-07-02
in that case yes,

PING gb.archive.ubuntu.com (194.169.254.10) 56(84) bytes of data.
64 bytes from gb.archive.ubuntu.com (194.169.254.10): icmp_seq=1 ttl=58 time=58.6 ms
64 bytes from gb.archive.ubuntu.com (194.169.254.10): icmp_seq=2 ttl=58 time=53.0 ms
64 bytes from gb.archive.ubuntu.com (194.169.254.10): icmp_seq=3 ttl=58 time=56.5 ms

--- gb.archive.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 53.028/56.052/58.621/2.322 ms

---

### Post by Rui Pais on 2007-07-02
Seems ok...

Do you connect to internet with a router?
Do you have at /etc/resolv.conf the ip of the router and only that?

---

### Post by mrlarone on 2007-07-02
yes there's a router and yes it's the only thing listed in /etc/resolv.conf

the router is using NAT, but that's never stopped apt-get before, has there been a change in yesterday's security upgrade?

if so which port(s) do i need to route?

---

### Post by Rui Pais on 2007-07-02
i don't know if something changed on yesterdays upgrade... 
but when i started to use my adsl2 router a few month ago i found the same "connection timed out" with net working normally at FF.

It turned to be an DNS issue with the router. Very frequent at the time. 
It was usually solved by replacing router IP with DNS IPs on the resolv.conf or using the [openDNS]("http://www.opendns.com/start/unix.php") ones.
Don't know if thats the source of your problem, but try won't hurt.

The interesting part, is that later the problem stopped, and i could set the usual router ip alone in resolv.conf... i guess something meanwhile had been fixed.
So i wonder if it starts to affect now other routers (before seems to bug specially D-Links and Linksys) or if the bug come back again.

---

### Post by mrlarone on 2007-07-02
not quite sure what you mean :D.

i change to .conf to use the openDNS IP's:

nameserver 208.67.222.222
nameserver 208.67.220.220

but still got the same err.

what do you mean by "replacing router IP with DNS IPs"

---

### Post by Rui Pais on 2007-07-02
> **mrlarone said:**
> not quite sure what you mean :D.

i change to .conf to use the openDNS IP's:

nameserver 208.67.222.222
nameserver 208.67.220.220

but still got the same err.

what do you mean by "replacing router IP with DNS IPs"

Sorry, :( i mean the ones that your Internet provider use (they are listed on router windows config, on status or DNS section) 

bad luck, if openDNS didn't work i doubt the others will ... 

Yours is a difficult problem. 
Have you tried change the repos servers? 
Synaptic can be use to do it very easily.

Beyond that i'm out of more ideas :(

Best of luck

---

### Post by mrlarone on 2007-07-02
cool,

i'll try that when i get home.

thanks all the same.

T

---

### Post by mrlarone on 2007-07-03
well what ever was happening it went away when i rebooted. go fig.

thanks again

---

