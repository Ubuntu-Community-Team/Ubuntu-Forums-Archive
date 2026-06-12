---
title: "Trouble with dns lookup"
date: 2005-08-26
forum: Installation &amp; Upgrades
---

### Post by Suzume on 2005-08-26
Hi

I have just installed Ubuntu for the first time, and am having what appears to be persistent intermittent troubles resolving domain names.   

First, after completing the installation firefox appeared to have troubles timing out connecting to web sites.  I looked on the web and found an page describing an issue with ipv6,  which suggested disabling it by putting a file named noipv6 in the /etc/modprobe.d directory containing the line alias net-pf-10 off.   I have done that and firefox appears to work, but now I am having trouble with apt.

When after editing the repository list I go to update the list, some will work but a few addresses it will say: trying [1.0.0.0]...  and time out.   Also when I try to resolve the repository address using nslookup, I will get 1.0.0.0 as the result.  This might last for a while and then it gives the correct ip address, or in some cases doesn't appear to fix itself.  Firefox also times out when going to that url.  

In /etc/resolve.conf I have the address of the same name server that my gentoo and windows installations use with no troubles.

Can anyone help?

---

### Post by amohanty on 2005-08-27
Can you post the result of:
nslookup google.com
tracert google.com

AM

---

### Post by Suzume on 2005-08-27
For the lookup:

$ nslookup google.com
Server:         192.168.0.1
Address:        192.168.0.1#53

Non-authoritative answer:
Name:   google.com
Address: 216.239.39.99
Name:   google.com
Address: 216.239.37.99
Name:   google.com
Address: 216.239.57.99

For the trace:
$ tracepath google.com
 1:  192.168.1.100 (192.168.1.100)                          0.153ms pmtu 1500
 1:  no reply
 2:  254.011.dsl.qld.iprimus.net.au (211.27.142.254)      115.479ms
 3:  no reply
 4:  vlan12.sw02.bne.iprimus.net.au (211.27.143.130)      116.518ms
 5:  ge0-1.ic02.bne.iprimus.net.au (203.134.111.228)      116.164ms
 6:  s10.ac04.syd.iprimus.net.au (203.134.2.157)          131.757ms
 7:  vlan5.sw02.syd.iprimus.net.au (210.50.143.130)       152.449ms
 8:  ge4-0-0.br02.syd.iprimus.net.au (203.134.2.182)      132.461ms
 9:  209.227.149.241 (209.227.149.241)                    asymm 11 290.309ms
10:  g1-0.10.cr1-lax.primustel.com (209.227.148.2)        292.389ms
11:  p3-0.cr1-sjc.primustel.com (209.227.128.105)         asymm  9 292.197ms
12:  p3-2.pr1.sjc.primustel.com (209.227.138.234)         asymm 10 291.825ms
13:  p3-0.pr1-piax.primustel.com (209.227.129.41)         asymm 11 291.369ms
14:  no reply
15:  no reply
and no reply after that.

I can also contact google.com with my web browser.   

Perhaps I made a mistake, and this is really an apt problem. When I go:
$ sudo apt-get update

I get:

Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/main Sources
18% [Connecting to au.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]

And at this time a nslookup will give:

$ nslookup au.archive.ubuntu.com
Server:         192.168.0.1
Address:        192.168.0.1#53

Non-authoritative answer:
Name:   au.archive.ubuntu.com
Address: 1.0.0.0

and a tracepath:

$ tracepath au.archive.ubuntu.com
 1:  192.168.1.100 (192.168.1.100)                          0.121ms pmtu 1500
 1:  no reply
 2:  254.011.dsl.qld.iprimus.net.au (211.27.142.254)      121.558ms
 3:  no reply
 4:  vlan11.sw02.bne.iprimus.net.au (203.134.111.2)       114.824ms
 5:  fe5-0-0.br01.bne.iprimus.net.au (211.27.143.67)      195.756ms
 6:  no reply
 7:  no reply
 8:  no reply

But for google.com the address still works.

It also appears that as I fiddle with running apt-get update and the sources.list it will work, and the addresses resolve to internet addresses, and the updates work and then they will stop working again (without me fiddling with it in the mean time).   It might be that doing an update with synaptic can trigger it, but I am not sure.

---

