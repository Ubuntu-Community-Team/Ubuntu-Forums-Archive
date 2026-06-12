---
title: "Problem with (belated) upgrade from 10.10 (Maverick) to 11.04 (Natty)"
date: 2013-04-14
forum: Installation &amp; Upgrades
---

### Post by cobaltinfinity on 2013-04-14
Got rather behind with my updates on my desktop and never tried upgrading from Maverick until today. The upgrade fails and gives me this message: 
```
W:Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources.gz  404  Not Found
, W:Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages.gz  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

I found a couple of older threads with similar, if not precisely the same, problems. One thing they suggested was changing the download server back to 'main server' but that didn't appear to help me.

Do I need to go straight to the next version somehow as Natty is no longer supported either? 

Thanks :)


***EDIT: I am marking this post as solved because I have decided to install 12.04 and am no longer attempting a version-by-version upgrade. ***

---

### Post by howefield on 2013-04-14
Have a read here,

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

You'll need to point your sources.list to the old-releases repositories where the Maverick ones now reside.

Perhaps it's time for a fresh install, otherwise you have a way to go to get to a supported version.

---

### Post by snowpine on 2013-04-14
i recommend a backup then fresh install of a supported release. i think 12.04 lts is a good choice for you. :)

---

### Post by cobaltinfinity on 2013-04-14
Thanks for the quick replies guys. I would like to do a clean install but my only concern is that when I set up this desktop, I put the system files onto my 60GB SSD and mounted my /home/ stuff on a separate HDD (which I didn't find easy lol), and I get the feeling something will go horribly wrong with this arrangement if I clean install. :D

---

### Post by cobaltinfinity on 2013-04-14
Sorry to bump own thread, but I have a related question: 

If my /home folder is on a different disk, is it possible for me to install the 12.4 LTS over 10.10 (which is on a different drive), without affecting my /home partition whatsoever? 

This is probably a dumb question but I'm seriously out of practice, hehe. =P~

---

