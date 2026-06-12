---
title: "is this normal? (apt-get update)"
date: 2005-09-23
forum: Installation &amp; Upgrades
---

### Post by narmenia on 2005-09-23
here's what the Konsole says.
Im using Kubuntu 5.04 (fresh install)
```
ws02@ws02:~$ sudo apt-get update
Password:
Err http://security.ubuntu.com hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ph.archive.ubuntu.com hoary Release.gpg
  Could not connect to ph.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Ign http://security.ubuntu.com hoary-security Release
Err http://ph.archive.ubuntu.com hoary-updates Release.gpg
  Could not connect to ph.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Ign http://security.ubuntu.com hoary-security/main Packages
Ign http://ph.archive.ubuntu.com hoary Release
Ign http://security.ubuntu.com hoary-security/restricted Packages
Ign http://ph.archive.ubuntu.com hoary-updates Release
Ign http://security.ubuntu.com hoary-security/main Sources
Ign http://ph.archive.ubuntu.com hoary/main Packages
Ign http://security.ubuntu.com hoary-security/restricted Sources
Ign http://ph.archive.ubuntu.com hoary/restricted Packages
Ign http://security.ubuntu.com hoary-security/universe Packages
Ign http://ph.archive.ubuntu.com hoary/main Sources
Ign http://security.ubuntu.com hoary-security/universe Sources
Ign http://ph.archive.ubuntu.com hoary/restricted Sources
45% [Connecting to ph.archive.ubuntu.com (1.0.0.0) [Connecting to security.ubu
```

is this it downloading updates or just having problems connecting...
whats with the (1.0.0.0) are they supposed to be ip addresses???
im on a LAN using DHCP... no Proxy... internet is fine in this box...
im from the Philippines btw... that's why it has a .ph...

heres my sources.list;
```
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://ph.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://ph.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ph.archive.ubuntu.com/ubuntu hoary universe
deb-src http://ph.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe
```

---

### Post by drogoh on 2005-09-24
It seems to me that your DNS is out of whack or perhaps your route to .uk is bad.  ie., no it is not normal.  Yes, 1.0.0.0 appears to be what your DNS returned for those two hosts, even though it is wrong.  It should be 82.211.81.151 and 82.211.81.182 instead of 1.0.0.0.

---

### Post by narmenia on 2005-09-24
after searching on the forums for "apt-get 1.0.0.0"

i found these:
[http://ubuntuforums.org/showthread.php?t=60223&highlight=apt-get+1.0.0.0](http://ubuntuforums.org/showthread.php?t=60223&highlight=apt-get+1.0.0.0)
[http://ubuntuforums.org/showthread.php?t=53354&highlight=apt-get+1.0.0.0](http://ubuntuforums.org/showthread.php?t=53354&highlight=apt-get+1.0.0.0)

my problem is what will i put on my resolv.conf???
currently it has:
```
nameserver 192.168.0.1
``` 

im using a modem&router combo to connect to the internet (router: DLINK DSL-500T)
my setup: internet > modem/router > switch > my linux BOX
im connected to my ISP using a dynamic IP...
browsing the web has no problems using Konqueror...
but using apt-get update is driving me NUTZ!!!  ](*,)

*Edit: IM on DHCP and the ip of the router is 192.168.0.1
THanX for the help

---

### Post by drogoh on 2005-09-24
Assuming your router has an administration interface, go into there with Firefox and grab at least one of the nameserver IPs and plug that into resolv.conf above the line with 192.168.0.1

Your resolv.conf should look like:

```

nameserver ISP.nameserver.IP.here
nameserver 192.168.0.1

``` 

after you're done.  Your problem appears identical to both, so I would try the solution gordonbp had with his problem.  It won't hurt to at least try.

---

### Post by narmenia on 2005-09-24
i've added the ISP DNS server IP.

usually when the ISP assigns my router to IP 203.177.245.101 (just an examlpe coz i only have a dynamic IP usually from 203.177.245.x - 203.177.255.x...)
soo the ISP DNS server's IP is 203.177.245.1 <-- it usually has the 1st IP number. (is this correct???)

resolv.conf #1
```
nameserver 203.177.245.1
nameserver 192.168.0.1

``` 
still the same 1.0.0.0 problem.

resolv.conf #2
```
nameserver 203.177.245.1
##nameserver 192.168.0.1

``` 
now also web browsing is disabled!!! :-x 

everytime i close Konsole i cant run apt-get update again...  ](*,)
it says:
```
E: Could not get lock /var/lib/apt/list/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
```

so i restart Kubunto...
after i restart the resolv.conf file now restores it self to the original
```
nameserver 192.168.0.1

```

im really fustrated!!!  ](*,)  ](*,) 
it has been almost 4 days and all i could do is install kubuntu, use open office, surf.

i really want to install firefox, gaim, maybe update openoffice, set-up file sharing, etc...
but im stuck at apt-get update!  ](*,)  ](*,)  ](*,)

---

### Post by phex on 2005-09-24
It is not the problem of your resolv.conf since your router is configured as DHCP Server I assume. So you get all the information from the router for your IP adress and the DNS Servers listed in the resolv.conf for each reboot. Try to change it on the router!

Once I also had such strange problem. I live in austria and used the DNS servers of my internet service provider. but i couldnt browse to some pages which should in fact function. so i used the DNS servers of another internet service provider in austria and this did the trick. ;) but anyway. web browsing is functioning so that i assume all is correct configured. have you tried synaptic package manager and tried to list all packages which are on the server. i think you dont have the extra repository in your list. i am not sure but i think you need the extra repository for firefox and multimedia components.

Can it be that your router is configured also as DNS Server?
so gl.

added:
soo the ISP DNS server's IP is 203.177.245.1 <-- it usually has the 1st IP number. (is this correct???)
-> no. this is not correct. the ISP DNS Server has normally a total different IP adress. just google for your ISP and its 2 DNS IP adresses,

---

### Post by narmenia on 2005-09-24
weeeeeeeeeeeeeeeeeeee!!! FIXED!!!

thanx man!!!

just to recap so if som1 has the same problems...

google the IP address of your ISP's DNS server... they usually have 2... a primary and an alternate... place them both in the DNS portion of your ROUTER...

THANX A MILLION!!! i almost gave up on linux...  :grin:

---

### Post by phex on 2005-09-24
no problem. ubuntu > windows ;)  :grin:  :grin:  :grin:  :grin:

---

