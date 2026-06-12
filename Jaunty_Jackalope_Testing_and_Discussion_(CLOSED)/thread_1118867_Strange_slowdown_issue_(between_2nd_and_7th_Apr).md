---
title: "Strange slowdown issue (between 2nd and 7th Apr)"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by planetf1 on 2009-04-07
Hi,
 I applied jaunty updates today, having last updates on 2nd April.

 System is x86 32 bit 3.4 Ghz P4 HT 3Gb ram & has Intel integrated gfx 945.

 Symptom is that the system is now very slow -- for some things
 - random delays just doing simple ls (can take a few seconds)
 - very slow to login (gnome)
 - windows/pointer motion normal
 - atop shows negligible CPU
 - tried removing my ldap config -- no difference
 - dns lookups fine/immediate
 - nothing especially bad from dmesg
 - tried both server (in use prior to today) & generic kernels (on 2.6.28-11 #40 currently), and also 2.6.27-11 server
 - forced use of VESA driver (even though 945 had previously been fine) -- didn't help

Ideas on possible breakage in those 5 days?

Right now I suspect it's something ldap/dns/pam that's slowing stuff down perhaps co-incidental with the updates?

---

### Post by Eclipse. on 2009-04-07
Open system monitor or run top from the terminal and look at what processes are eating all your ram/cpu, that should help you pin point the problem

Could be something as simple as a memory leak.

---

### Post by planetf1 on 2009-04-07
This is only affecting users managed via ldap, with nfs mounted remote directories ... local users fine. So perhaps an NFS issue. more checking to be done.

---

