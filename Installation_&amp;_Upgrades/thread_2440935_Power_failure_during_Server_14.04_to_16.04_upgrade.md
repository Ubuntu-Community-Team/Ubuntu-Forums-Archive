---
title: "Power failure during Server 14.04 to 16.04 upgrade"
date: 2020-04-16
forum: Installation &amp; Upgrades
---

### Post by Lukas_Carls on 2020-04-16
I have an old server that I dug out of the back room that had some old projects on it. I decided to do some distro upgrades because 14.04 is ancient history at this point. I started do-release-upgrade and let it do its thing. It downloaded all the packages and was working on installing them when the power went out for a few minutes because of a storm. When the power came back on, the server rebooted into a bash shell prompt. No tty login or anything. I have next to null experience with bash prompts, so I don't know my way around them. It write-protected the partitions for safety but I think I got that switched around in GRUB's advanced options. Furthermore, there is no way that I can connect to the network.

When I boot up, these lines show up before the bash prompt:

```
Begin: Running /scripts/local-bottom ... done
Begin: Running /scripts/init-bottom ... done
run-init: /sbin/init: No such file or directory
run-init: /etc/init: Permission denied
run-init: /bin/init: No such file or directory
/bin/sh: 0: can't access tty: job control turned off
#
```

Next I burned a Live CD of 16.04 and tried running the option for repairing a broken system, hoping that it would go around the issue of there being no /sbin/init file or no network connectivity. However, I still run into not having any network connectivity, so when I try any apt commands to download/fix packages or rerun the upgrade, all I get is "Temporary error resolving 'us.archive.ubuntu.com'" (or anywhere else a package lives). I checked /etc/apt/sources.list and everything points to the correct xenial repos.

How can I get the network to connect in either circumstance? Furthermore, Is there any way that I can recover this system without a fresh install? If that's the route I absolutely need to take, I can do it. I just need to find a way to get my files out of /var/www/html first and find some way to back up my MySQL database.

Thank you and cheers.

---

### Post by Impavidus on 2020-04-17
A fresh install is definitely the easiest way out. You can skip 16.04 and go directly to 18.04. Or skip 18.04 too and install 20.04. I wouldn't even attempt a release upgrade from an unsupported release or a double release upgrade. And I don't even live in a country where storms cause power outages.

---

### Post by CelticWarrior on 2020-04-17
> **Impavidus said:**
> A fresh install is definitely the easiest way out. You can skip 16.04 and go directly to 18.04. Or skip 18.04 too and install 20.04. I wouldn't even attempt a release upgrade from an unsupported release or a double release upgrade. And I don't even live in a country where storms cause power outages.

+1 for 20.04

---

### Post by kneutron on 2020-04-29
--It's not going to help you now, but it may help you and others in the future: Connect your computers to UPS power and always do a full backup before you try updating your system.

---

