---
title: "(K)ubuntu 16.04 NIS client does not work after installing"
date: 2016-04-25
forum: Installation &amp; Upgrades
---

### Post by Henk_Bos on 2016-04-25
With a clean install of (K)ubuntu 16.04 i am not able to login through NIS.
When I install NIS client yptest gives the richt resluts. How ever when I reboot the login screen does not revert tot de NIS client login.
After login with de local user I noticed that yptest does not work, it gives the error 'can not connect to ypbind'.
I have the impression that the required NIS services are not properly started through systemd at boot.

---

### Post by doherty on 2016-04-26
I was having the same issue. Take a look at [https://bugs.launchpad.net/ubuntu/+source/rpcbind/+bug/1558196](https://bugs.launchpad.net/ubuntu/+source/rpcbind/+bug/1558196)

The solution is to configure systemd to invoke rpcbind rather than allowing nis.service to do it: sudo /bin/systemctl add-wants multi-user.target rpcbind.service

---

### Post by Henk_Bos on 2016-04-27
doherty,
thank you very much, this simple command does the trick!

---

