---
title: "How do I install nfs-common on Jaunty?"
date: 2011-06-06
forum: Installation &amp; Upgrades
---

### Post by Carl H on 2011-06-06
I'm running 9.04 on an EeePC and I want to connect to an NFS share. 

When trying to install nfs-common, apt-get returns a load of 404 errors. I'm guessing this is because the 9.04 repositories are no longer online? 

So I tried to do a dist-upgrade with Update Manager, and got a message saying that upgrading from jaunty to lucid was not supported. 

Can someone please tell me how I can install nfs-common and anything else I need to connect to an NFS share?

---

### Post by mörgæs on 2011-06-06
It is better to do a fresh install of a supported version rather than upgrading one unsupported (9.04) version to another (9.10) and from there to something recent. 

A new install will also give you Grub 2 and the option of using Ext4.

---

### Post by Carl H on 2011-06-06
U9.04 runs perfectly well on it, as does my T-Mobile 3G/HSPDA USB modem - which took a bit of messing about to get to work - so I'm a bit wary of doing something that might break it. 

A fresh install may well bring new problems, and to me seems like a big solution to a small problem. 

All I'm really trying to achieve is to access my NFS mounts from my EeePC. This requires the nfs-common package, which I can no longer obtain. Is it possible to get the correct .deb files from somewhere else?

---

### Post by mörgæs on 2011-06-06
The main problem with using 9.04 is not stability, but that there have not been given out security updates for more than half a year.

---

### Post by SeijiSensei on 2011-06-06
Try downloading the [10.04.2 CD]("http://releases.ubuntu.com/lucid/") and running from it.  Don't install, just use the LiveCD mode?  This will let you know if your hardware will work properly after upgrading.

---

### Post by Carl H on 2011-06-07
> **SeijiSensei said:**
> Try downloading the [10.04.2 CD]("http://releases.ubuntu.com/lucid/") and running from it.  Don't install, just use the LiveCD mode?  This will let you know if your hardware will work properly after upgrading.

Thanks, I'll try that.

---

### Post by Elfy on 2011-06-07
Have a look here - [http://ubuntuforums.org/showthread.php?t=1133291](http://ubuntuforums.org/showthread.php?t=1133291)

You should be able to use the old-releases repos.

Though I would say, bearing in mind the lack of security updates, that you'd be better if possible going to 10.04 which is supported till April 2013.

---

### Post by Carl H on 2011-06-10
That's exactly the sort of answer I was hoping for! Thanks! 

I take your point about upgrading  - all my other machines are up to date. This is for an EeePC that I only use occasionally, and as 9.04 was, for me, that last problem free version, I'm reluctant on gambling on doing a fresh install when what I've already got works perfectly.

---

