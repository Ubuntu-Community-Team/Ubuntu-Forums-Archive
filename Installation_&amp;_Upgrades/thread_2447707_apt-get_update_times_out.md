---
title: "apt-get update times out"
date: 2020-07-24
forum: Installation &amp; Upgrades
---

### Post by davidmcq on 2020-07-24
I have two machines on my network, no obvious network problems.
One does apt-get update normally, the other times out. To try to resolve the problem, I tried using wget to retrieve the InRelease file as follows:
Both are Ubuntu 16.04. I have other systems that are 18.04 and they work perfectly.

> 
SUCCESSFUL TEST:

david@david:~/test$ wget [http://au.archive.ubuntu.com/ubuntu/dists/bionic-security/InRelease](http://au.archive.ubuntu.com/ubuntu/dists/bionic-security/InRelease)
--2020-07-24 16:24:15--  [http://au.archive.ubuntu.com/ubuntu/dists/bionic-security/InRelease](http://au.archive.ubuntu.com/ubuntu/dists/bionic-security/InRelease)
Resolving au.archive.ubuntu.com (au.archive.ubuntu.com)... 91.189.91.38, 91.189.88.142, 91.189.88.152, ...
Connecting to au.archive.ubuntu.com (au.archive.ubuntu.com)|91.189.91.38|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 88724 (87K)
Saving to: 'InRelease’

InRelease           100%[===================>]  86.64K   116KB/s    in 0.7s    

2020-07-24 16:24:17 (116 KB/s) - 'InRelease’ saved [88724/88724]

david@david:~/test$ 
-rw-rw-r-- 1 david david 88724 Jul 24 16:08 InRelease
david@david:~/test$ 

UNSUCCESSFUL TEST:
root@ns:~# wget [http://au.archive.ubuntu.com/ubuntu/dists/bionic-security/InRelease](http://au.archive.ubuntu.com/ubuntu/dists/bionic-security/InRelease)
--2020-07-24 16:23:49--  [http://au.archive.ubuntu.com/ubuntu/dists/bionic-security/InRelease](http://au.archive.ubuntu.com/ubuntu/dists/bionic-security/InRelease)
Resolving au.archive.ubuntu.com (au.archive.ubuntu.com)... 91.189.91.39, 91.189.88.142, 91.189.91.38, ...
Connecting to au.archive.ubuntu.com (au.archive.ubuntu.com)|91.189.91.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 88724 (87K)
Saving to: 'InRelease’

InRelease             9%[>                   ]   8.14K  --.-KB/s    eta 70m 36s
^C
root@ns:~# ls -l InRelease 
-rw-r--r-- 1 root root 8338 Jul 24 16:23 InRelease
root@ns:~#


As you can see, I get a partial download but it stalls for no reason I can figure out.
As a result, I can't upgrade or install anything. This has only started recently.
I've recently upgraded my internet connection from synchronous DSL to fibre. Not sure how that would make a difference, but all my other systems work fine.

The box with the problem is a server - no GUI.

Any suggestions gratefully received.

---

### Post by davidmcq on 2020-07-24
Solved! 

The problem was MTU. The solution was:

* edit /etc/netplan/01-netcfg.yaml thus:
```

network:
  version: 2
  renderer: networkd
  ethernets:
    ens3:
      dhcp4: no
      addresses: [nnn.nnn.nnn.nnn/24]
      gateway4: nnn.nnn.nnn.nnn
      mtu: 1492
      nameservers:
              addresses: [8.8.8.8,4.4.4.4]

```

* restart netplan:
```
# netplan apply
```

I was able to verify the correct mtu using this:

```
$ ping -M do -s 1466 au.archive.ubuntu.com
```

"-M do" prohibits fragmentation, "-s 1466" sets the MTU size. Adjust the size and retry until you get optimal MTU. Default is 1500.

I have no clue why this suddenly failed when it worked before.

---

### Post by ActionParsnip on 2020-07-24
Have you tried rebooting your router?

---

### Post by davidmcq on 2020-07-24
No... didn't think of rebooting router since other computers on this side of the router were still OK.
If it happens again, I will try that :)

---

