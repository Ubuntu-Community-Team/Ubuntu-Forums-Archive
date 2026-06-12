---
title: "Cannot apt-get update..."
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by silvercliff on 2006-06-30
its as simple as that.  i am on the net, as im posting from my fresh kubuntu install.  its good, but i cannot install anything because i cannot 'apt-get update'.  i get a stupid error:

*Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz)  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)*

the only thing i can think of, is apt is trying to use eth0 which is not connected to anything yet (will be my my hdd server shortly) instead of eth1 which is connected to the net.

VERY annoying, its putting my off of using kubuntu...

is that enough info to help?  if so can anyone help?

---

### Post by silvercliff on 2006-06-30
ok so i tried removing the line from '/etc/resolv.conf' and it works for about 2 mins, then failed again, here is full output from 'apt-get update':

[I]Err [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg
  Could not connect to [www.beerorkid.com:80](www.beerorkid.com:80) (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Err [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg
  Could not connect to xgl.compiz.info:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
  Could not connect to wine.budgetdedicated.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release
Err [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
  Could not connect to [www.beerorkid.com:80](www.beerorkid.com:80) (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Err [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
  Could not connect to xgl.compiz.info:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
  Could not connect to wine.budgetdedicated.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Sources
  Could not connect to xgl.compiz.info:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
  Could not connect to wine.budgetdedicated.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/multiverse Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/multiverse Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/universe Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/multiverse Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/universe Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/multiverse Sources
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/multiverse Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Sources
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/multiverse Sources
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/universe Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/multiverse Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/universe Sources
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/multiverse Sources
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/dapper/Release.gpg](http://wine.budgetdedicated.com/apt/dists/dapper/Release.gpg)  Could not connect to wine.budgetdedicated.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://xgl.compiz.info/dists/dapper/Release.gpg](http://xgl.compiz.info/dists/dapper/Release.gpg)  Could not connect to xgl.compiz.info:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://www.beerorkid.com/compiz/dists/dapper/Release.gpg](http://www.beerorkid.com/compiz/dists/dapper/Release.gpg)  Could not connect to [www.beerorkid.com:80](www.beerorkid.com:80) (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz](http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz)  Could not connect to [www.beerorkid.com:80](www.beerorkid.com:80) (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz](http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz)  Could not connect to xgl.compiz.info:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-i386/Packages.gz)  Could not connect to wine.budgetdedicated.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://xgl.compiz.info/dists/dapper/main/source/Sources.gz](http://xgl.compiz.info/dists/dapper/main/source/Sources.gz)  Could not connect to xgl.compiz.info:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/dapper/main/source/Sources.gz](http://wine.budgetdedicated.com/apt/dists/dapper/main/source/Sources.gz)  Could not connect to wine.budgetdedicated.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.[/I]

ok someone please help me

---

### Post by ranf on 2006-07-01
Do you have this file on your computer: /etc/apt/apt.conf
If yes please post its content.

---

### Post by g00n on 2006-07-08
problem is your router is replying to an ipv6 request with garbage.
remove your router from your /etc/resolv.conf
usually it's:
nameserver 192.168.0.1 (or the x.x.x.1 of your IP address)

hopefully your 2nd nameserver line is from your ISP.. leave that alone.. 
save and close your /etc/resolve.conf

and retry apt-get update. 
it'll probably work.

---

### Post by stonefeet on 2006-07-09
same exact problem here

my resolv.conf
nameserver 192.168.1.1

that's my modem

nslookup address of whatever i'm trying to access works for a bit, but then dies later

weird.

ah hah
there we go
thanks g00n for the workaround, i was able to beat the actual dns servers out of my modem and it worked like a charm
now lets see if it keeps working

---

### Post by davoid87 on 2006-07-09
I am having the exact same problem as everyone else on here with this binding to 1.0.0.0 business. However, every time I change my resolve.conf file, about a minute later it is automantically changed back to

nameserver 192.168.1.1

How do I go about finding the correct DNS servers? I cant seem to be able to find anything when I log on to the router except that 192.168.1.1 is the DNS.

---

### Post by g00n on 2006-07-09
ok, it's probably changing back because for some reason dhcp reacquires your address and rewrites your /etc/resolv.conf.

I was finally able to disable ipv6 last night... 
/etc/modprobe.d/blacklist
add the line
blacklist ipv6
reboot
it no longer loads ipv6 and the problem went away

---

### Post by zhuanyi on 2006-07-10
Hello guys,
Apparently I am having the same problem. However, in my resolv.conf (somehow my file name was resolv, not resolve, I use Kubuntu 6.10), there is only 1 line:
```
nameserver 192.168.0.2
```
And I am not sure where I can find the correct DNS. Does anyone know how to find the correct nameserver? Apparently things like ipconfig is not going to work with Kubuntu :)
Thanks!

Regards,
Anyi

---

### Post by g00n on 2006-07-10
if you can.. nslookup ns1.<isp domain.suffix>
and change the 192.168.0.2 to the ip it returns.

also, add to your /etc/modprobe.d/blacklist the line:
blacklist ipv6

then reboot.. that took care of the issue for me.

---

### Post by zhuanyi on 2006-07-11
Hi,
Thanks for the quick reply!
I have ran a script written by someone else and this is what I got:
```

IP address 69.194.41.253 
Domain address CPE00146c032b51-CM00159a3b5ba.cpe.net.cable.rogers.com 

```
however, when I tried to add the name server to the IP address specified above, that does not seem to help.
I will try to run nslookup now, hope that helps!

Thanks a lot!


Regards,
Anyi

---

### Post by zhuanyi on 2006-07-11
Hello,
This is what I did and this is what I got:

```

zhuanyi@ayzhu:~$nslookup ns1.rogers.com

Non-authoritative answer:
Name:   ns1.rogers.com
Address: 142.146.39.30

zhuanyi@ayzhu:~$ sudo apt-get update
Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Err http://ca.archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 146.137.96.15 80]
Ign http://security.ubuntu.com dapper-security Release
Err http://ca.archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 146.137.96.15 80]
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://security.ubuntu.com dapper-security/restricted Packages
Err http://ca.archive.ubuntu.com dapper-backports Release.gpg
  Connection failed [IP: 146.137.96.15 80]
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://ca.archive.ubuntu.com dapper Release
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://ca.archive.ubuntu.com dapper-updates Release
Ign http://security.ubuntu.com dapper-security/universe Sources
Ign http://ca.archive.ubuntu.com dapper-backports Release
Err http://security.ubuntu.com dapper-security/main Packages
  Connection failed
Err http://security.ubuntu.com dapper-security/restricted Packages
  Connection failed
Ign http://ca.archive.ubuntu.com dapper/main Packages
Err http://security.ubuntu.com dapper-security/main Sources
  Connection failed
Ign http://ca.archive.ubuntu.com dapper/restricted Packages
Err http://security.ubuntu.com dapper-security/restricted Sources
  Connection failed
Err http://security.ubuntu.com dapper-security/universe Packages
  Connection failed
Ign http://ca.archive.ubuntu.com dapper/main Sources
Err http://security.ubuntu.com dapper-security/universe Sources
  Connection failed
Ign http://ca.archive.ubuntu.com dapper/restricted Sources
Ign http://ca.archive.ubuntu.com dapper/universe Packages
Ign http://ca.archive.ubuntu.com dapper/universe Sources
Ign http://ca.archive.ubuntu.com dapper-updates/main Packages
Ign http://ca.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://ca.archive.ubuntu.com dapper-updates/main Sources
Ign http://ca.archive.ubuntu.com dapper-updates/restricted Sources
Ign http://ca.archive.ubuntu.com dapper-backports/main Packages
Ign http://ca.archive.ubuntu.com dapper-backports/restricted Packages
Ign http://ca.archive.ubuntu.com dapper-backports/universe Packages
Ign http://ca.archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://ca.archive.ubuntu.com dapper-backports/main Sources
Ign http://ca.archive.ubuntu.com dapper-backports/restricted Sources
Ign http://ca.archive.ubuntu.com dapper-backports/universe Sources
Ign http://ca.archive.ubuntu.com dapper-backports/multiverse Sources
Err http://ca.archive.ubuntu.com dapper/main Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://ca.archive.ubuntu.com dapper/restricted Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://ca.archive.ubuntu.com dapper/main Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://ca.archive.ubuntu.com dapper/restricted Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://ca.archive.ubuntu.com dapper/universe Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://ca.archive.ubuntu.com dapper/universe Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://ca.archive.ubuntu.com dapper-updates/main Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://ca.archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://ca.archive.ubuntu.com dapper-updates/main Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://ca.archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://ca.archive.ubuntu.com dapper-backports/main Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://ca.archive.ubuntu.com dapper-backports/restricted Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://ca.archive.ubuntu.com dapper-backports/universe Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://ca.archive.ubuntu.com dapper-backports/multiverse Packages
  Connection failed [IP: 146.137.96.15 80]
Err http://ca.archive.ubuntu.com dapper-backports/main Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://ca.archive.ubuntu.com dapper-backports/restricted Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://ca.archive.ubuntu.com dapper-backports/universe Sources
  Connection failed [IP: 146.137.96.15 80]
Err http://ca.archive.ubuntu.com dapper-backports/multiverse Sources
  Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz Connection failed
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz Connection failed [IP: 146.137.96.15 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz Connection failed [IP: 146.137.96.15 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Apparently this is not helping. Do you have any other suggestions?
Thanks a lot!

Regards,
Anyi

---

### Post by zhuanyi on 2006-07-11
By the way, this is how my resolv.conf looks like:
nameserver 142.146.39.30

I have also blacklisted ipv6 as you have told me...

---

### Post by zhuanyi on 2006-07-13
Never mind guys, I managed to resolve the problem myself. The problem is with my NetGear VPN router at home that has a function called Keyword Blocking, which blocked out the word "dapper" in there. After disabling it, everything works fine now. Thanks a lot to everyone who replied!

Regards,
Anyi

---

### Post by yoghurt on 2006-07-13
Nothing seems to help me, but perhaps I'm doing something wrong. From my ISP I know that their dns is 212.65.193.157 but when I change that in /etc/resolv.conf and restarted Kubuntu, it changes back to 192.168.1.1

I've also disabled the IPv6 as advised by Goon but that still... any other advice?

PS: my modem is Ovislink AirLive ARM-104

---

### Post by Barleyman on 2006-07-13
yoghurt

try this...

delete the proxy line out the /etc/apt/apt.conf file by doing

sudo nano /etc/apt/apt.conf
delete this line with ctl-k -> Acquire::http::Proxy "false"; 
then exit and save with ctl-x ctl-s

then try sudo apt-get update

This worked for me, but I am a little baffled why.

I am using linksys wrt54g v2 with the dd-wrt firmware v23.  I am wondering if my router firmware is somehow causing this, because I did not have this issue before I installed the dd-wrt firmware, but I my previous ubuntu installed was breezy.

I would like to understand a little more why this works from some of the more experienced users.

---

### Post by jetpeach on 2006-08-04
Barleyman - yeah, this worked for me as well.  Disable ipv6 didn't help, but removing that one line did.
Very very strange, anybody else with ideas why?  Probably something lame in my router, but still maybe future ubuntu releases can fix this, I should search to see if a bug is filed.  Tomorrow maybe ;)

---

### Post by oasiao on 2006-08-14
Yes I had these problems too. And it annoyed me all I did was turn my network proxy off, for some reason With it on i couldnt update or even get my weather in the weather applet

---

### Post by cerkilr on 2006-08-24
this problem had me to i spent two days trying to get this to work. THANK YOU EVERY MUCH!=D> =D> =D> =D> =D>

---

### Post by Atomic Dog on 2006-08-28
Changing resolv.conf from showing my router ip as nameserver to the actual ip's of my ISP's nameservers solved my apt/synaptic update issues that were somewhat described here.  The error I recieved said it was unable to reach/resolve host.  regardless, this works.  The only bummer is whenever I want to get something I need to open resolv.conf and edit it.

---

### Post by londonbabs on 2006-09-29
...I need quite some help, I checked everything that was possible, changed my sources.list so many times I can't count, I'm pretty sure my resolve.conf is well configurated and I blacklisted ipv6 business,but still can't update and keep getting the same error messages listed above in zhuanyi's case
Now, I'm definitely not familiar yet with ubuntu or linux in general, quite newby actually, so if anyone thinks they could help, I'll be more than grateful, I feel totaly stuck n cannot use anything, I do connect to the net, but cannot install any package or anything, let alone updates
my sources.list :

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) dapper-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) dapper-extras main universe multiverse restricted

(P.S. I live in UK)

my resolv.conf :
nameserver 192.168.1.1
nameserver 192.168.1.2

I'm in such need of help I'm even considering switching back to windows... that'll be the end of my computer, seeing as I used to kick it in the teeth using frustrating window...
anybody ?? I really like ubuntu distro and would like to carry on using it
(btw I use a D-Link g604t router if it's got anything to do with anything...)

---

### Post by pomegranate on 2006-09-29
> **Atomic Dog said:**
> Changing resolv.conf from showing my router ip as nameserver to the actual ip's of my ISP's nameservers solved my apt/synaptic update issues that were somewhat described here.  The error I recieved said it was unable to reach/resolve host.  regardless, this works.  The only bummer is whenever I want to get something I need to open resolv.conf and edit it.

Can you tell me how to figure out my ISP's nameserver and IP? I have access to my router control but I don't know what I'm looking for.

---

### Post by Barleyman on 2006-09-29
> **pomegranate said:**
> Can you tell me how to figure out my ISP's nameserver and IP? I have access to my router control but I don't know what I'm looking for.

Usually you can see it under the the status tab on your router.  It should be called WAN info or Internet info something similar.  To find your ip WAN ip address just go to [www.whatismyip.com](www.whatismyip.com).

---

### Post by abecar on 2006-10-03
I blacklisted ipv6 and added my ISP domainservers to resolv.conf

Still no luck.  When I connect directly to my cable modem apt-get works fine.  When going through the router I can ping the apt-get sources just fine.  But the command apt-get update fails with errors like the following:

Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages

etc...

Any help would be appreciated!

---

### Post by Barleyman on 2006-10-03
> **abecar said:**
> I blacklisted ipv6 and added my ISP domainservers to resolv.conf

Still no luck.  When I connect directly to my cable modem apt-get works fine.  When going through the router I can ping the apt-get sources just fine.  But the command apt-get update fails with errors like the following:

Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages

etc...

Any help would be appreciated!


abecar, have you tried this yet?  This was what worked for me, and I posted it earlier in this thread.

-----------------
try this...

delete the proxy line out the /etc/apt/apt.conf file by doing

sudo nano /etc/apt/apt.conf
delete this line with ctl-k -> Acquire::http::Proxy "false";
then exit and save with ctl-x ctl-s

then try sudo apt-get update
-----------------

---

### Post by abecar on 2006-10-05
Hooray!

Removing the proxy line from apt-get.conf did the trick.

Strange magic.

Thanks so much!

---

### Post by Thought_Criminal on 2006-11-06
Thanks for the fix g00n. Worked great for me.

---

### Post by sirfatal on 2006-11-08
Thanks Barleyman... I've been blowing away my system for the past 2 weeks thinking something wrong with my installation... Its finally working and receiving updates...

SiR FaTaL

---

### Post by Barleyman on 2006-11-08
No problem SiR FaTaL, I racked my head on that problem for awhile too.

Just curious, what router/firmware is everyone using here who had this problem?  I suspect this might have something to do with this issue.

I currently use 

Router Model
Linksys WRT54G/GS 
Firmware Version
DD-WRT v23 SP1 Final

---

### Post by sock_snake on 2006-11-22
> **zhuanyi said:**
> Never mind guys, I managed to resolve the problem myself. The problem is with my NetGear VPN router at home that has a function called Keyword Blocking, which blocked out the word "dapper" in there. After disabling it, everything works fine now. Thanks a lot to everyone who replied!

Regards,
Anyi

Big thanx to you for finding the problem, I to had the same problem and would never come on the idea that it would have been my router "FVS318v3"
:KS

---

### Post by mefellows on 2006-12-23
Barleyman you are a gem! I have had this problem on both my laptop and my pc and was beginning to think it was a router problem also (in fact the laptop could not update using the uni wireless either, but there could be several explanations for that). I did read somewhere else that a number of routers are having similar problems, but just for the record i am using a WGT624 v2 router, firmware V4.2.4_1.0.1. I fear that a router upgrade might lead to more problems so for now i will go with the trusty old saying "If it ain't broke, don't fix it".

Thanks all!

---

### Post by yitzle on 2007-07-27
I love you! Thanks! This was driving me nuts! Deleting the proxy line fixed it!

---

### Post by yitzle on 2008-01-27
> **Barleyman said:**
> yoghurt

try this...

delete the proxy line out the /etc/apt/apt.conf file by doing

sudo nano /etc/apt/apt.conf
delete this line with ctl-k -> Acquire::http::Proxy "false"; 
then exit and save with ctl-x ctl-s

then try sudo apt-get update


This worked last time round, but the new install doesn't have an /etc/apt/apt.conf file and adding one with
Acquire::http::Proxy "true";
doesn't work.

Please help!

---

### Post by thamang on 2008-04-21
i have same problem like this, I use Ubuntu 8.04 beta and can't find any thing like /etc/apt/apt.conf so how can I turn off my proxy :'(

---

