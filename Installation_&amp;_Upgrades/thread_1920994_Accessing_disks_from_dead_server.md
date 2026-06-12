---
title: "Accessing disks from dead server"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by mwtb on 2012-02-05
I've been running Ubuntu as a general file-server and download manager for quite a while using an old Athlon64 system. The server eventually had four HDs and I used LVM to span partitions across those disks.

Just before I moved house last year, the server died (I think the CPU burned out after the fan failed). Since then it has been sitting in a box until I could do something with it.

So, my question is: what do I need to know about recovering the data from those disks? 

I doubt I'm going to be able to replace the existing hardware so that I can boot the system again so what are the options? If I stick the drives in my Core Duo system will Ubuntu boot or fail due to the hardware changes? If I use a Live CD or USB drive install, will I be able to easily mount the LVM partitions?

---

### Post by searchfgold6789 on 2012-02-05
Yes, you'll be able to mount them using a Live CD. I think.
And if that doesn't work, you'll still be able to boot Ubuntu and at the very least get to a command prompt (from there graphics are usually configurable) if you switch the hard disks to another box.

---

