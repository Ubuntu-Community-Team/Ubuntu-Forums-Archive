---
title: "Fresh install ... most apps won't start"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by djtopper on 2007-07-09
Just did a fresh install ... Slackware convert here (or potentially).  The thing is, most apps (eg., calc, terminal, etc...) won't start.  Just a little message at the bottom of the display stating "Starting <app>." 

Anyone have a guess why?

Thanks,

DT

---

### Post by stchman on 2007-07-09
> **djtopper said:**
> Just did a fresh install ... Slackware convert here (or potentially).  The thing is, most apps (eg., calc, terminal, etc...) won't start.  Just a little message at the bottom of the display stating "Starting <app>." 

Anyone have a guess why?

Thanks,

DT

Your DNS more than likely suck and your hosts and hostname have junk.

[http://www.stchman.com/conf_host.html](http://www.stchman.com/conf_host.html)
[http://www.stchman.com/openDNS.html](http://www.stchman.com/openDNS.html)

This happened to me and these cured it.

---

### Post by Odrodzona-Sarmacja on 2007-07-09
> **djtopper said:**
> Just did a fresh install ... Slackware convert here (or potentially).  The thing is, most apps (eg., calc, terminal, etc...) won't start.  Just a little message at the bottom of the display stating "Starting <app>." 

Anyone have a guess why?

Thanks,

DT

Corrupted file system? Ubuntu installer doesn't seem to format any ext3 partitions from my experiences. It looks like it is scavenging them from the earlier installs of ext3.

Last time I had the same errors on my Xubuntu, was my entire ext3 xubuntu file system so corrupted I had to reinstall. I needed to convert entire partition to fat32, low format it (or secure erase it) and then format fresh ext3 partitions in its place with alternative partition program and only then I succeded in clean install of xubuntu.

If you are installing over corrputed ubuntu ext3 partition or Slackware ext3 partition, then I think you need do the same. Good luck ;)

---

### Post by djtopper on 2007-07-09
Ok, got this one too.  It was either because I changed eth0 to static and/or changed the hostname on my box.

Reboot and it works now.

---

### Post by pikul on 2007-07-10
> **stchman said:**
> Your DNS more than likely suck and your hosts and hostname have junk.

[http://www.stchman.com/conf_host.html](http://www.stchman.com/conf_host.html)
[http://www.stchman.com/openDNS.html](http://www.stchman.com/openDNS.html)

This happened to me and these cured it.

That host modd really help :popcorn: thanks, ill check the OpenDNS thing at home :guitar:

---

