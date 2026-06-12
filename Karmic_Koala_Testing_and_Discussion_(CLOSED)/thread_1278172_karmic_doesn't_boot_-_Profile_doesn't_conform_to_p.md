---
title: "karmic doesn't boot - Profile doesn't conform to protocol"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by vibra on 2009-09-29
Hi everyone



I have updated my sound driver to the 1.0.21 version. But i think it is not related to that. Now my laptop doesn't boot anymore. 

It hangs in the following point of boot:

* Starting init crypto disks... [ OK ]

And, after a Crt+alt+F1, it shows me the following error messages:

Boot from... 
Starting up....
/sbin/apparmor_parser: Unable to replace "/sbin/dhclient3". Profile doesn't conform to protocol
Sikkiping profile in /etc/apparmor.d/disable: usr.bin.firefox-3.5
/sbin/apparmor_parser: Unable to replace "/usr/sbin/mysql". Profile doesn't conform to protocol

etc...



I found a bug that looks similar to this one.
[https://bugs.launchpad.net/ubuntu/+source/tcpdump/+bug/429872](https://bugs.launchpad.net/ubuntu/+source/tcpdump/+bug/429872)


I'm very worried because I even can't get a shell. 



Thanks for any help

---

### Post by vibra on 2009-09-29
Can someone point me out some tips to get a shell? 

I tried ctr+alt+fx but it doesn't give me a shell. :confused:

---

### Post by lidex on 2009-09-29
try booting from your live disk

---

### Post by vibra on 2009-09-29
Running LiveCD  I can't see my hard drive. Running df -h doesn't gives me my HardDisk location

What this means? or, am I missing something? :confused:

---

### Post by vibra on 2009-09-29
With LiveCD i solved  the problems with profiles/protocol (upgrading the system did the trick).

But, it keeps freezing after :
* Starting init crypto disks...

I have no idea what can be wrong... 

:(

---

