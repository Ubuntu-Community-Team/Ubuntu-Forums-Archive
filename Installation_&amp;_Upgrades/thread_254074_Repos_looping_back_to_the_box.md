---
title: "Repos looping back to the box"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by sp0nge on 2006-09-09
I've been trying to update my system for a few days and when I do so, I have gotten these messages:

"W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)"

As you can see, the repos seem to be looking back at the box to update. I've racked my brain to figure this out to no avail. Any helpful tips?:confused:

---

### Post by taurus on 2006-09-09
Try to remove the "us" in your /etc/apt/sources.list and see if you can connect again...

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by sp0nge on 2006-09-09
I removed the us from all repos and tried to connect again. I get the same errors when I use your suggested code. When I tried to update via synaptic, I get a new message: 

"The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

The repo addresses have not been modified since I installed and as much as I hate to admit it, I'm just not understanding WHY it keeps looking at the box.

---

### Post by HAARP on 2006-09-09
Post your /etc/hosts

---

### Post by sp0nge on 2006-09-09
Current hosts:

[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)
[http://wine.budgetdedicated.com/apt/dists/dapper/Release.gpg](http://wine.budgetdedicated.com/apt/dists/dapper/Release.gpg)

---

### Post by HAARP on 2006-09-09
No, I mean the file
/etc/hosts

---

### Post by sp0nge on 2006-09-09
127.0.0.1 localhost Laptop
127.0.1.1 Laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by HAARP on 2006-09-09
Looks fine to me. 
Are you using a router?

---

### Post by sp0nge on 2006-09-09
Yes I am.

---

### Post by HAARP on 2006-09-09
Can you look into it's settings? Filters and redirection and stuff like that might be interesting.

Also, try pinging those servers. Is it still redirected?

---

### Post by sp0nge on 2006-09-09
The router has filtering disabled. I've tried pinging the servers and each says can not be found. I've even gone so far as to reset the router to default settings to no avail.

---

