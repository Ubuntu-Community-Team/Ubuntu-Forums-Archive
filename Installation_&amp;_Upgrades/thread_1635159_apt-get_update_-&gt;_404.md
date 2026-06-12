---
title: "apt-get update -&gt; 404"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by Unkraut on 2010-12-01
Hello!
I have the following problem:

```

trollkotze@schrotthaufen-mobil:~$ sudo apt-get update
Ign http://archive.ubuntu.com intrepid Release.gpg
Ign http://archive.ubuntu.com intrepid/main Translation-de
Ign http://archive.ubuntu.com intrepid/restricted Translation-de
Ign http://archive.ubuntu.com intrepid/multiverse Translation-de
Ign http://archive.ubuntu.com intrepid/universe Translation-de
Ign http://archive.ubuntu.com intrepid-updates Release.gpg
Ign http://archive.ubuntu.com intrepid-updates/main Translation-de
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-de
Ign http://archive.ubuntu.com intrepid-updates/multiverse Translation-de
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-de
Ign http://archive.ubuntu.com intrepid-security Release.gpg
Ign http://archive.ubuntu.com intrepid-security/main Translation-de
Ign http://archive.ubuntu.com intrepid-security/restricted Translation-de
Ign http://archive.ubuntu.com intrepid-security/multiverse Translation-de
Ign http://archive.ubuntu.com intrepid-security/universe Translation-de
Ign http://archive.ubuntu.com intrepid Release
Ign http://archive.ubuntu.com intrepid-updates Release
Ign http://archive.ubuntu.com intrepid-security Release
Ign http://archive.ubuntu.com intrepid/main Packages
Ign http://archive.ubuntu.com intrepid/restricted Packages
Ign http://archive.ubuntu.com intrepid/multiverse Packages
Ign http://archive.ubuntu.com intrepid/main Sources
Ign http://archive.ubuntu.com intrepid/restricted Sources
Ign http://archive.ubuntu.com intrepid/universe Packages
Ign http://archive.ubuntu.com intrepid/universe Sources
Ign http://archive.ubuntu.com intrepid-updates/main Packages
Ign http://archive.ubuntu.com intrepid-updates/restricted Packages
Ign http://archive.ubuntu.com intrepid-updates/multiverse Packages
Ign http://archive.ubuntu.com intrepid-updates/main Sources
Ign http://archive.ubuntu.com intrepid-updates/restricted Sources
Ign http://archive.ubuntu.com intrepid-updates/universe Packages
Ign http://archive.ubuntu.com intrepid-updates/universe Sources
Ign http://archive.ubuntu.com intrepid-security/main Packages
Ign http://archive.ubuntu.com intrepid-security/restricted Packages
Ign http://archive.ubuntu.com intrepid-security/multiverse Packages
Ign http://archive.ubuntu.com intrepid-security/main Sources
Ign http://archive.ubuntu.com intrepid-security/restricted Sources
Ign http://archive.ubuntu.com intrepid-security/universe Packages
Ign http://archive.ubuntu.com intrepid-security/universe Sources
Fehl http://archive.ubuntu.com intrepid/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid-updates/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid-updates/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid-updates/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid-updates/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid-updates/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid-updates/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid-security/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid-security/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid-security/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid-security/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid-security/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid-security/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Fehl http://archive.ubuntu.com intrepid-security/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

W: Konnte http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz nicht holen  404 Not Found [IP: 91.189.88.31 80]

E: Einige Indexdateien konnten nicht heruntergeladen werden, sie wurden ignoriert oder alte an ihrer Stelle benutzt.


```

And I think I have this problem for a long time already. Have not been able to update the package information for almost a year I guess. But I just did not bother to care about it until now.
What is wrong?

Regards
Unkraut

---

### Post by Quackers on 2010-12-01
Is Intrepid still supported? If so, maybe the site is down temporarily.

---

### Post by sikander3786 on 2010-12-01
> **Quackers said:**
> Is Intrepid still supported? If so, maybe the site is down temporarily.
No, Intrepid is not supported any longer. Support ended on 30th April, 2010.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

To the OP: You can still upgrade that to a newer version.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by oldos2er on 2010-12-01
8.10 reached its end-of-life last April: [http://en.wikipedia.org/wiki/Ubuntu_(operating_system)#Releases](http://en.wikipedia.org/wiki/Ubuntu_(operating_system)#Releases)

---

### Post by Unkraut on 2010-12-01
> **sikander3786 said:**
> 
To the OP: You can still upgrade that to a newer version.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)


Thanks. I will try that later.

---

