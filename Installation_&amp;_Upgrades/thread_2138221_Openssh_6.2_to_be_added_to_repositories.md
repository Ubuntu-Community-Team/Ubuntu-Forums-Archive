---
title: "Openssh 6.2 to be added to repositories?"
date: 2013-04-23
forum: Installation &amp; Upgrades
---

### Post by shiela on 2013-04-23
Is there a plan to add the latest version of openssh 6.2 to the repositories?  It has a lot of very helpful features and improvements over 5.9.

---

### Post by Cheesemill on 2013-04-23
I doubt it very much, that's not how the Ubuntu repositories work.

When a version of Ubuntu is released all of the packages are frozen at whatever version they are currently on. The only updates that will make it into the repositories are bug fixes and security updates, you will never get major version jumps.

For example 12.04 was released with the 3.5.4 version of Libreoffice and it will only ever get minor upgrades, for example 3.5.5, 3.5.6 as these are all bug fixes and security updates. Version 4.x.x will never be available in the official Ubuntu repositories for 12.04, in 4 years time it will still only be on version 3 even if LibreOffice have since released 5, 6 etc...

You can see which version of a package is available for different versions of Ubuntu by searching the package database...
[http://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=openssh-server&searchon=names](http://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=openssh-server&searchon=names)

---

### Post by shiela on 2013-04-23
thanks - that explanation was both clear and helpful

---

