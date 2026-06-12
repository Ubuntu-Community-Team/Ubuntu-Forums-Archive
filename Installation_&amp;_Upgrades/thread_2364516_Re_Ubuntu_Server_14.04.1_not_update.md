---
title: "Re: Ubuntu Server 14.04.1 not update"
date: 2017-06-24
forum: Installation &amp; Upgrades
---

### Post by jimeshmakawana on 2017-06-24
Hi,

I am trying to update my ubuntu server.

```
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) trusty InRelease

Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) trusty-updates InRelease

Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) trusty-backports InRelease

Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) trusty-security InRelease

Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) trusty Release.gpg
  Unable to connect to old-releases.ubuntu.com:http:
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) trusty-updates Release.gpg
  Unable to connect to old-releases.ubuntu.com:http:
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) trusty-backports Release.gpg
  Unable to connect to old-releases.ubuntu.com:http:
Err [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) trusty-security Release.gpg
  Unable to connect to old-releases.ubuntu.com:http:
Reading package lists... Done
W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/trusty/InRelease](http://old-releases.ubuntu.com/ubuntu/dists/trusty/InRelease)

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/trusty-updates/InRelease](http://old-releases.ubuntu.com/ubuntu/dists/trusty-updates/InRelease)

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/trusty-backports/InRelease](http://old-releases.ubuntu.com/ubuntu/dists/trusty-backports/InRelease)

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/trusty-security/InRelease](http://old-releases.ubuntu.com/ubuntu/dists/trusty-security/InRelease)

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://old-releases.ubuntu.com/ubuntu/dists/trusty/Release.gpg)  Unable to connect to old-releases.ubuntu.com:http:

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg](http://old-releases.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg)  Unable to connect to old-releases.ubuntu.com:http:

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg](http://old-releases.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg)  Unable to connect to old-releases.ubuntu.com:http:

W: Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg](http://old-releases.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg)  Unable to connect to old-releases.ubuntu.com:http:

W: Some index files failed to download. They have been ignored, or old ones used instead.
jimeshmakawana@it-helpdesk:~$
```

DNS is working fine.

jimeshmakawana@it-helpdesk:~$ nslookup google.com
Server:         8.8.8.8
Address:        8.8.8.8#53

Non-authoritative answer:
Name:   google.com
Address: 172.217.26.206

jimeshmakawana@it-helpdesk:~$

root@it-helpdesk:~# ping old-releases.ubuntu.com
PING old-releases.ubuntu.com (91.189.88.17) 56(84) bytes of data.
64 bytes from cocoplum.canonical.com (91.189.88.17): icmp_seq=1 ttl=48 time=165 ms
64 bytes from cocoplum.canonical.com (91.189.88.17): icmp_seq=2 ttl=48 time=192 ms
64 bytes from cocoplum.canonical.com (91.189.88.17): icmp_seq=3 ttl=48 time=319 ms
64 bytes from cocoplum.canonical.com (91.189.88.17): icmp_seq=4 ttl=48 time=192 ms
64 bytes from cocoplum.canonical.com (91.189.88.17): icmp_seq=5 ttl=48 time=148 ms
^C
--- old-releases.ubuntu.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 148.779/203.617/319.992/60.497 ms
root@it-helpdesk:~#

---

### Post by deadflowr on 2017-06-24
14.04 is still supported, so...
They have no archives in the old-release archives.
You'll need to reverse whatever it was you did to make the sources look for the repositories in the old-releases archives.

---

