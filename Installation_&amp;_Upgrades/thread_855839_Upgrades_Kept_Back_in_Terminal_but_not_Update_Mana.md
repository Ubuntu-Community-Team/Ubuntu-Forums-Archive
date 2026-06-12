---
title: "Upgrades Kept Back in Terminal but not Update Manager"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by justinmiller87 on 2008-07-10
So I have a bizarre thing going on. I prefer to use Terminal for most things because it's a nice throwback to my old DOS days and other CLI stuff that I learned on primarily. 

So anyway, I pretty regularly run apt-get update && apt-get upgrade, and since I (clean) installed 8.04, I've noticed that I continue getting the following type of error:

```
The following packages have been kept back:
  bind9-host dnsutils language-support-writing-en libbind9-30 libisccfg30
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
```

I can install them no problem though through the GUI Update Manager (which I have since done). Is there a reason for this? If so, how do I get around it so I only have to use one update process?

Thanks in advance.

---

### Post by iaculallad on 2008-07-10
It means that there are new versions of these packages ready for download which will not be installed for some reasons. It could be that the package on which it depends doesn't have a version available for download or it can also be that the package has come to depend on new packages since the last version.

Had you tried:

```
sudo apt-get -u upgrade
```

---

### Post by justinmiller87 on 2008-07-10
> **iaculallad said:**
> It means that there are new versions of these packages ready for download which will not be installed for some reasons. It could be that the package on which it depends doesn't have a version available for download or it can also be that the package has come to depend on new packages since the last version.

Had you tried:

```
sudo apt-get -u upgrade
```
Your response would make sense... if I wasn't able to perform the upgrade by some other method. If it didn't work in Terminal or Update Manager I'd get that, but that's not the case.

And no, I've not tried sudo apt-get -u upgrade yet.

---

### Post by justinmiller87 on 2008-07-11
Bump check.

---

### Post by baju on 2008-07-12
The problem with these packages is that they depend on libdn35.
I simply did ```
sudo apt-get dist-upgrade
``` and they were updated.

---

