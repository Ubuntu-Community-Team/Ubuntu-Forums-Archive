---
title: "Using CD as upgrade source"
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by haresear on 2012-05-18
I know I can use the Alternate-install CD as a source for upgrading, but can someone tell me if the Live CD can also be used as an upgrade source or does it have to be the Alternate CD? I'm referring to upgrading via command line. The Live CD GUI install does not give me the option to upgrade an existing install, perhaps because I have too many partitions with existing installs.

---

### Post by jadtech on 2012-05-18
do you have upgrade disabled in software updater ??

---

### Post by haresear on 2012-05-18
> **jadtech said:**
> do you have upgrade disabled in software updater ??
No. The Update Manager does offer an upgrade, but I don't want to use that because needs an internet connection. I want to update using a CD I've already downloaded.

---

### Post by prshah on 2012-05-18
> **haresear said:**
> I know I can use the Alternate-install CD as a source for upgrading, but can someone tell me if the Live CD can also be used as an upgrade source or does it have to be the Alternate CD? I'm referring to upgrading via command line. The Live CD GUI install does not give me the option to upgrade an existing install, perhaps because I have too many partitions with existing installs.

Sorry, normally the live CD cannot be used to upgrade an existing system. You need the alternate CD.

However, I have noticed the newer installers offer an option to upgrade an existing "old" installation to the new version (comes during the partitioning option, see pic below). However, I have never used it, and don't know how well (or if!) it works. 

Even the alternate CD GUI installer is iffy. I have only been able to successfully perform an offline install by commandline.```
sudo sh ./cdromupgrade --without-network --frontend=DistUpgradeViewText
```

[ATTACH]218213[/ATTACH]

Yes, I know it's offering to upgrade FROM 12.04 TO 11.10, but you get the idea...

---

### Post by haresear on 2012-05-18
> **prshah said:**
> 
However, I have noticed the newer installers offer an option to upgrade an existing "old" installation to the new version (comes during the partitioning option, see pic below). However, I have never used it, and don't know how well (or if!) it works. 

Thanks for the reply. I've noticed the references to an upgrade option via the live CD that you describe, but for some reason I don't get that option displayed. I was speculating that it is because I have multiple existing Ubuntu installs, and the installer can't decide which one to upgrade. (I also don't get any user accounts offered to import from any of my existing Ubuntu installs.)

---

