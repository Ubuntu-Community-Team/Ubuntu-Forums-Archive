---
title: "release-upgrade from apt-mirror fails"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by lykwydchykyn on 2010-10-12
I have a local apt-mirror on my network that I use to upgrade my Ubuntu and Debian systems; works great, had it for years, used it to do release upgrades in the past.

This time I'm trying to upgrade a fairly recently-installed 64-bit Lucid kubuntu machine to Maverick.  When I try, I get this error:

```

After your package information was updated the essential package 
'ubuntu-minimal' can not be found anymore. 
This indicates a serious error, please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report.

```

Anyone know the proper way to do this?

---

### Post by lykwydchykyn on 2010-10-12
Ok, looking at the logs it seems to be rejecting my sources.list entries for the main apt mirror and commenting them out.  How do I get it to accept these?

---

