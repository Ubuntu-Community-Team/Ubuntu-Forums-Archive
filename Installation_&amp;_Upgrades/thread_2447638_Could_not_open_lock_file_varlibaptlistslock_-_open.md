---
title: "Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)"
date: 2020-07-22
forum: Installation &amp; Upgrades
---

### Post by manjotsc on 2020-07-22
I added a user "dcauth" to group "root" but can't run apt update

Thanks.

[HTML]MySQL login: dcauthPassword: Welcome to Ubuntu 20.04 LTS (GNU/Linux 5.4.34-1-pve x86_64)
 * Documentation:  https://help.ubuntu.com * Management:     https://landscape.canonical.com * Support:        https://ubuntu.com/advantage
Last login: Thu Jul 23 02:08:08 UTC 2020 on tty1dcauth@MySQL:~$ apt updateReading package lists... DoneE: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)E: Unable to lock directory /var/lib/apt/lists/W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)dcauth@MySQL:~$ groupsdcauth rootdcauth@MySQL:~$ groups dcauthdcauth : dcauth rootdcauth@MySQL:~$ [/HTML]


[IMG]https://drive.google.com/uc?export=download&id=1QwVqo_YjDgYGFAQH4J6dbJxIzjpVBAio[/IMG]
[IMG]https://drive.google.com/file/d/1QwVqo_YjDgYGFAQH4J6dbJxIzjpVBAio/view?usp=sharing[/IMG]

---

### Post by deadflowr on 2020-07-22
You need to be a part of the sudo group.
Then run as root with sudo.

Currently you're trying to run root commands as a non-root member.
Being part of root group doesn't matter.

General information on root and sudo here:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

