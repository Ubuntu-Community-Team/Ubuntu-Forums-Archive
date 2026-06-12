---
title: "How to save time installing Ubuntu on VMs?"
date: 2013-11-21
forum: Installation &amp; Upgrades
---

### Post by chortle on 2013-11-21
I run Ubuntu under Virtual Box. I just installed Saucy Salamander (Ubuntu 13.10). As usual, I told Ubuntu to download updates while it installed. 

When I get SS installed I can make a copy and use that updated copy for any further VMs which I want to make using Virtual Box. That will save me some time. But, each time there is an update each VM will want to download files.

Is anyone using a program *like* rsync to keep downloaded packages up to date within Ubuntu VMs? You save the downloaded packages into a shared directory on the host. The VM that happens to grab a download updates the shared folder. All others pick it up next time they run the sync process. If the sync process were run with user interaction that would avoid some problems with more than one VM simultaneously updating the shared folder. 

Does Ubuntu check /var/cache/apt/archives before it goes and grabs an update from the web?

Has anyone done this?

---

### Post by Lars Noodén on 2013-11-21
If you are downloading the same packages in different VMs you might set up apt-cacher or apt-cacher-ng on your host system or elsewhere on your LAN.  That way, only the first download comes from the Internet.  Subsequent uses of that same package then come from the cache.  apt-cacher has worked very well for me in the past, I can expect that apt-cacher-ng is an improvement.

---

### Post by chortle on 2013-11-21
Unfortunately my host is Windows. It may be tough/impossible to install over my Windows 8 HP DV7 laptop. 

I could hack my NAS to run the s/w. But then I would somehow have to direct the NAS apt-cacher to download the needed bits.

---

### Post by Lars Noodén on 2013-11-21
What about elsewhere on the LAN?  Any Linux, BSD or OS X box should work, at least for apt-cacher which is ported or easy to manually port.  

Can the VMs connect to each  other?  If so, *maybe* one could run apt-cacher.

---

### Post by chortle on 2013-11-21
It sounds like just the job for me. Thank you. I will go and read about apt-cacher. Once I do that I'm sure I will figure out where I can set it up.

---

### Post by Lars Noodén on 2013-11-21
You could also run Squid instead, if you are more familiar with that.  Apt-cacher / apt-cacher-ng are also proxies, just specialized for APT packages.  None do anything on their own.  Instead you adjust APT on each client machine to use the proxy.  

With hacking your NAS, if it can run the software and has storage for the downloaded packages, then it might work.

---

