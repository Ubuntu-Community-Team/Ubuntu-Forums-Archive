---
title: "Apt-get cannot use proxy-server with digest-authentication"
date: 2014-09-12
forum: Installation &amp; Upgrades
---

### Post by senblue on 2014-09-12
My newly installed virtual ubuntu-server sits behind a firewall and i can only access the internet via a proxy with digest authentication. 
I understand that apt-get is using wget to download packages, but wget's only method is basic-authentication. 
so i am seeing lots of "407  Proxy Authentication Required". 

Are there any workarounds for this situation? 

I googled a lot and i tried 
  * changing http to ftp in /etc/apt/sources.list. It did'nt work. i did not expect to.
  * cntlm. It did'nt work because digest is the only method.
  * manually download packages with curl, manually find dependencies (apt-rdepends) and using dpkg etc. Wish to avoid this !!!

Is there somethings like cntlm working as a proxy for digest-authentication ?
Can apt-get switch to curl instead of wget ?

And ...
no, i cant persuade the proxy admin to add basic authentication !!

---

