---
title: "No Desktop - Ubuntu 12.10"
date: 2013-01-20
forum: Installation &amp; Upgrades
---

### Post by bigbankclub on 2013-01-20
Ok I have read [http://askubuntu.com/questions/207813/why-does-an-ubuntu-12-10-guest-in-virtualbox-run-very-very-slowly/214968#214968 ]("http://askubuntu.com/questions/207813/why-does-an-ubuntu-12-10-guest-in-virtualbox-run-very-very-slowly/214968#214968")

I did the following:

To check if your Ubuntu 12.10 guest is using 3D acceleration, run this command:

```
/usr/lib/nux/unity_support_test -p
```And got the same results. I followed all the commands and when I used:

```
sudo ./VBoxLinuxAdditions.run
```

It could not find it. When I installed the Guest Additions and running this command from the CD-ROM's directory, the install happened automatically.

Has anyone had the same issue? Am I not doing something right? Any help would be grateful.

---

