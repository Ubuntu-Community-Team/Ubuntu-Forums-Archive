---
title: "aptitude update fails"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by hounddog32 on 2008-01-21
I am running Ubuntu on an Eee-pc with the scripts from google-code (if that helps with the problem, but I think not)

I am a long-time Ubuntu user (since Warty) and I have Ubuntu gutsy on my desktop too. Same internet connection there as here, no problems with updates.

When I try to run an update from terminal I get this:
```
~$ sudo aptitude update
Err http://gb.archive.ubuntu.com gutsy Release.gpg                              
  Could not connect to 10.131.100.50:8080 (10.131.100.50), connection timed out
Err http://security.ubuntu.com gutsy-security Release.gpg                       
  Could not connect to 10.131.100.50:8080 (10.131.100.50), connection timed out
Err http://archive.canonical.com gutsy Release.gpg                              
  Could not connect to 10.131.100.50:8080 (10.131.100.50), connection timed out
Err http://gb.archive.ubuntu.com gutsy/main Translation-en_GB
```Etc.

I am connected to the internet, no proxy, I am writing this from the same PC. I can ping successfully: ```
~$ ping archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.31) 56(84) bytes of data.
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=1 ttl=56 time=26.6 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=2 ttl=56 time=25.9 ms
64 bytes from leningradskaya.canonical.com (91.189.88.31): icmp_seq=3 ttl=56 time=25.8 ms

--- archive.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 25.881/26.158/26.685/0.372 ms

```but as you can see, it's looking at some weird IP address. Why?
Atp-get does the same as aptitude, synaptic and update manager fail in their own ways, timing out,as this IP does not exist.

---

### Post by taurus on 2008-01-21
Open synaptic -> Settings -> Repositories and try another server/location.

---

### Post by hounddog32 on 2008-01-21
Yes, here you go with the results - same thing!
```
~$ sudo apt-get update
Err http://mirror.ox.ac.uk gutsy Release.gpg    
  Could not connect to 10.131.100.50:8080 (10.131.100.50), connection timed out
0% [Connecting to 10.131.100.50 (10.131.100.50)]

```
```
~$ ping mirror.ox.ac.uk
PING mirror.ox.ac.uk (163.1.2.231) 56(84) bytes of data.
64 bytes from mirror1.oucs.ox.ac.uk (163.1.2.231): icmp_seq=1 ttl=54 time=31.0 ms
64 bytes from mirror1.oucs.ox.ac.uk (163.1.2.231): icmp_seq=2 ttl=54 time=30.9 ms
64 bytes from mirror1.oucs.ox.ac.uk (163.1.2.231): icmp_seq=3 ttl=54 time=30.1 ms

--- mirror.ox.ac.uk ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 30.156/30.723/31.067/0.428 ms
```

---

