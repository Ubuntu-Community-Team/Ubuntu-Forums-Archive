---
title: "Install Older Version Of Samba Help"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by ShapeShiftme on 2012-07-12
Good Day all.

Ive been using backuppc for about 3 years now on my ubuntu server machine for many of my clients.

im now having the following problem when running a backup

```
NT_STATUS_ACCESS_DENIED listing \\*
```
Everything i have read tells me that samba changed recently and that is causing a problem and i should down grade smbclient to version smbclient 3.5.11 will fix it.

Now i have never downgraded something so im gathering i do the following

1) Uninstall smbclient

```

sudo apt-get remove smbclient

The following packages will be REMOVED:
  backuppc smbclient


```2) Find smbclient 3.5.11
Can I find this using apt or must i download and if so where is the best place to locate archive 

3) install smbclient

4) install backuppc

Any help with this regard will be apriciated

---

### Post by dino99 on 2012-07-12
here is the ubuntu packages:

[https://launchpad.net/ubuntu/+source/samba](https://launchpad.net/ubuntu/+source/samba)

download the required packages into an empty folder, then from it:

sudo dpkg -i *

this will install that package(s), but its possible you get dependency issue(s)

you should pay attention to deja-dup

It hides the complexity of backing up the
Right Way (encrypted, off-site, and regular) and uses duplicity as the
backend.

Features:
 * Support for local, remote, or cloud backup locations, such as Amazon S3,
   Rackspace Cloud Files, and Ubuntu One
 * Securely encrypts and compresses your data
 * Incrementally backs up, letting you restore from any particular backup
 * Schedules regular backups
 * Integrates well into your GNOME desktop

---

