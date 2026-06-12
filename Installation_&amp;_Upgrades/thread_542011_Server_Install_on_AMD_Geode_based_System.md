---
title: "Server Install on AMD Geode based System"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by glen66 on 2007-09-03
Hi All

I'm trying to build an ubuntu server based on a fabiatech FX5201 system.

It's an AMD Geode LX800 with a 120Gig HD and 512 Mb of ram.

The install process on Dapper works fine, however on initial boot the system hangs after loading the kernel.

I've tried reinstalling numerous times, and no joy.

Strange thing is that the box will happily run the non-server version of ubuntu.

Any ideas?

Thanks in advance.

Glen

---

### Post by gwalker47 on 2007-12-06
Interesting that two Glens should experience the same problem. In my case I've got a Koolu: Geode LX800 512MB Ram 80GB disk. The machine came loaded with Ubuntu 7.04 Desktop, but since I just wanted it as a small home server - print, file, audio (slimserver) - I thought that the LTS server edition would be suitably smaller. The installation went without any indication of trouble, but booting from the hard disk is as you describe. 

I haven't looked into it, because I downloaded the 7.10 server version and it installs and boots without a hitch. I think running a diff on the kernel config between the server and desktop versions would probably give us a clue as to what's going on here. I'll try that and report later.
-Glen Walker

---

