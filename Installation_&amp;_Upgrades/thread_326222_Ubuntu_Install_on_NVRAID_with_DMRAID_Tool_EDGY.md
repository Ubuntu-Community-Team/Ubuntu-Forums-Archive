---
title: "Ubuntu Install on NVRAID with DMRAID Tool EDGY"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by Orcun on 2006-12-27
Hi Guys.

I started the Live Desktop CD. Installed DMRaid.

When I type "sudo dmraid -ay" gives no output.

But when I type "sudo dmraid -an" it gives an output like 

> ubuntu@ubuntu:~$ sudo dmraid -an
RAID set "nvidia_fabidhjb" is not active

It sees my Raid but doesn't mount it I think. Is there anyone solved this situation ?
> 
ubuntu@ubuntu:~$ sudo dmraid -s
*** Set
name   : nvidia_fabidhjb
size   : 1953588664
stride : 256
type   : stripe
status : ok
subsets: 0
devs   : 4
spares : 0
ubuntu@ubuntu:~$


---

### Post by novaraz on 2006-12-31
Hey are you still working on this problem?

I was able to get most of an Edgy install with debootstrap onto my NVRAID.  You need the latest dmraid and depedencies for the LiveCD to correctly map and mount the raid.  I am still working towards a full install.

---

