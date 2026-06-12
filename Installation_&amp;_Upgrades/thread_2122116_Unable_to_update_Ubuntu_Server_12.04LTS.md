---
title: "Unable to update Ubuntu Server 12.04LTS"
date: 2013-03-04
forum: Installation &amp; Upgrades
---

### Post by RighardZw on 2013-03-04
Trying to do an update, the update manager tells me that the package system is broken and should try apt-get install -f

Details:
The following packages have unmet dependencies:

linux-server: Depends: linux-image-server (=3.2.0.37.44) but 3.2.0.38.46 installed
Depends: linux-headers-server (=3.2.0.37.44) but (3.2.0.38.46 installed

Running apt-get install -f 

Errors were encountered while processing:
  linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any clue?

---

### Post by ibjsb4 on 2013-03-04
Try a dist-upgrade, see if that gets you anywhere.  If not, please post the errors.

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

```
sudo apt-get dist-upgrade
```

---

### Post by RighardZw on 2013-03-04
> **ibjsb4 said:**
> Try a dist-upgrade, see if that gets you anywhere.  If not, please post the errors.

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

```
sudo apt-get dist-upgrade
```

It didn't work giving the same problem... Forcing the dist-upgrade (-f) worked, took a long time to finish, but afterwards, the problem is still is there:

The update manager tells me that ***the package system is broken and should try apt-get install -f***

***Details:***
***The following packages have unmet dependencies:***

***linux-server: Depends: linux-image-server (=3.2.0.37.44) but 3.2.0.38.46 installed***
***Depends: linux-headers-server (=3.2.0.37.44) but (3.2.0.38.46 installed***


Running apt-get install -f 

***Errors were encountered while processing:***
***linux-server***
***E: Sub-process /usr/bin/dpkg returned an error code (1)***

---

