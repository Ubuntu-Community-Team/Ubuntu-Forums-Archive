---
title: "Roll back installation | Darktable"
date: 2014-11-15
forum: Installation &amp; Upgrades
---

### Post by divyansh2 on 2014-11-15
Hi.

I wanted to install Darktable on my system and since I didn't know my way around things I started the installation using the first code I came across. Subsequently it came to my knowledge that I shouldn't have used that code. It'll be really helpful if someone can help me roll back the installation (partially done).

Here's what I ran: 

```
$ sudo apt-get install debhelper dpkg-dev fakeroot
```

After that, the following I ran the following code but stopped it mid-way using ^c

```
$ sudo apt-get build-dep darktable
```

Any help would be appreciated.

---

### Post by grahammechanical on 2014-11-15
Did you install on to a B-Tree file system (btrfs)? If not then it is not possible to "roll back." But you can uninstall/remove packages that have been installed. 

```
apt-get remove <package_name>
```

or 

```
apt-get purge <package_name>
```

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Regards.

---

