---
title: "Wired network EXTREMELY Flaky after upgrade - HELP!!"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by joel@parke.ods.org on 2008-11-04
Hi,

After upgrading, things are a real mess.  I have internet connectivity in phases.  For a while it works well and then it drops out.  This is extremely frustrating and is my worst upgrade experience in 4 years.

In terms of debugging I am not sure what direction to move in.  
The Good news is that the desktop is up and running and I can even now receive emails some of the time.  

Has anyone else seen this problem?  Are there any solutions out there?

IN terms of details:
I am running 
eth1 on 192.168.1.91 
eth2 on 192.168.1.90
gateway in both cases 192.168.1.1
DNS servers:
208.67.222.222, 208.67.220.220

I don't have anything exotic and so this should just work!
I can even occasionally post to ubuntuforums! Yuck what a mess.

Thanks,
Joel Parke

---

### Post by joel@parke.ods.org on 2008-11-04
I thought I should add that my hardware is:
Realtek Semiconductor Co., Ltd.
RTL-8110SC/8169SC Gigabit Ethernet

But much is listed as undefined - Do I need a new driver or something?

---

### Post by joel@parke.ods.org on 2008-11-04
I did resolve a big piece of this.  After eliminating eth1 and rebooting - I am left with just one network adapter and that makes the system stable again.  It appears in 8.10 that when there are two network adapters, it get confused.  So beware....  This doesn't happen with 8.04

Thanks,
Joel Parke

---

