---
title: "alien not generation deb package from maya rpm"
date: 2012-12-31
forum: Installation &amp; Upgrades
---

### Post by howhy on 2012-12-31
i am trying to convert rpm file to deb but its giving error package fails to build..

```
	mkdir Maya2012_0_64-2012.0/debian
	hostname
	date -R
	hostname
	date -R
	chmod 755 Maya2012_0_64-2012.0/debian/rules
	debian/rules binary 2>&1
Package build failed; could not run generated debian/rules file.
	find Maya2012_0_64-2012.0 -type d -exec chmod 755 {} ;
	rm -rf Maya2012_0_64-2012.0

```

any idea what could be causing it ?

---

### Post by dino99 on 2012-12-31
have you followed that howto ?

[https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

---

