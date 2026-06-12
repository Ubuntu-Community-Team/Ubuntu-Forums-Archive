---
title: "apt list --upgradable offers me php7.2* when I already have php7.3.19"
date: 2021-09-13
forum: Installation &amp; Upgrades
---

### Post by modernape on 2021-09-13
My web server has been offered php7.2 on apt list --upgradable, and yet I already have php7.3.19 installed. This seems odd behaviour, or is it not worth worrying about? 

For now I have run ```
[COLOR=#000000][FONT=Menlo]apt-mark hold php7.2*[/FONT][/COLOR] 
```

---

### Post by TheFu on 2021-09-13
Are there any php7.2 packages left over?  Php gets security updates from time to time, so I'd let those through ... or purge all the php7.2 packages.

Just because we've installed php7.3, if we didn't go through every place on the system that references php, some scripts could be still using the 7.2 versions.  If it were me, I'd search all php scripts and "alternative" settings to ensure they point to 7.3 ... create an excellent backup (or at least an LVM snapshot), then purge all the 7.2 packages, reboot, and to some testing to ensure everything important is working on the website.  This can take from 3 minutes to 48 hours, depending on your skills and knowledge.  I know Linux, but not php, so I'd only do this when I have 3-5 hrs available to correct stuff.  

I messed up and put 3 different php webapps on the same virtual machine, initially, they all used the same version, but over the years, the necessary version has changed for each of the webapps.  Really wish that I'd used either different VMs for each or a different LXD container for each.  Live and learn.  At least I didn't mix the 30 webapps I maintain onto the same systems.  Most are 1 app = 1 VM, but not with the php ones. My mistake.  And don't get me started about the separate DBMS versions each supports.  That's a different issue.

---

### Post by deadflowr on 2021-09-13
Where did the php7.3 version that come from?

---

### Post by modernape on 2021-09-13
> **deadflowr said:**
> Where did the php7.3 version that come from?
That's the version I installed when I built it.

---

### Post by deadflowr on 2021-09-13
So it's from source then?

---

### Post by modernape on 2021-09-13
> **deadflowr said:**
> So it's from source then?
Yep

---

### Post by modernape on 2021-09-13
> **TheFu said:**
> Are there any php7.2 packages left over?  Php gets security updates from time to time, so I'd let those through ... or purge all the php7.2 packages.


Ah, it seems php7.2 is indeed installed

---

### Post by modernape on 2021-09-13
> **TheFu said:**
> 
Just because we've installed php7.3, if we didn't go through every place on the system that references php, some scripts could be still using the 7.2 versions.  If it were me, I'd search all php scripts and "alternative" settings to ensure they point to 7.3 ... create an excellent backup (or at least an LVM snapshot), then purge all the 7.2 packages, reboot, and to some testing to ensure everything important is working on the website.  This can take from 3 minutes to 48 hours, depending on your skills and knowledge.  I know Linux, but not php, so I'd only do this when I have 3-5 hrs available to correct stuff.  


I've only got Wordpress and phpBB on there, and they both point to 7.3.19, so it sounds like I can safely purge 7.2

---

