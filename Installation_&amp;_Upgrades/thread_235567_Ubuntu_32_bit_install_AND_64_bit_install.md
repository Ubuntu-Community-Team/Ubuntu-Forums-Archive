---
title: "Ubuntu 32 bit install AND 64 bit install?"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by aceracer24 on 2006-08-13
I currently have a 32 bit install of dapper. I want to also install the 64 bit version. I have found one guide that explains teh dual distro procedure but my question is will 2 differant arches cause problems? I have to copy 3 files from the 64 bit /boot to my current 32 bits /boot. I am not sure how many things are 64bit only. 

Here is a link to the guide i am planning to follow:

[http://www.ubuntuforums.org/showthread.php?t=194597&highlight=multiple+distro%27s]("http://www.ubuntuforums.org/showthread.php?t=194597&highlight=multiple+distro%27s")

---

### Post by ajgreeny on 2006-08-13
Do you mean you want two separate installs, one of 32 and one of 64 bit architecture, and if so will they use the same home partition separate from root in both cases?  If so, I suspect you could have some difficulties with configuration of programs which will probably be different in the two systems.

If you set up with separate home partitions for both systems, ie keep them on / or in different home partitions for each install, and allow to double boot (or triple boot with windows if you have it) you should be OK.

---

