---
title: "MD5sum mismatch while upgrading Kubuntu 6.10 to 7.04"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by kuovsk.anekask on 2007-06-22
I've been wanting to upgrade Kubuntu 6.10 to 7.04 since the day 7.04 was released, but when I run the upgrade tool it fetches the files ("Preparing the upgrade") then comes back with an error. 

```
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.bz2 MD5Sum mismatch
```

At different times when I've run this it's come back with different errors, but they're always MD5Sum mismatches. Is this my fault or a bug? 

Also, I just tried to run the cdromupgrade from the 7.04 alternate CD, and I got this, even though the file is there. 

```
/media/cdrom0$ ./cdromupgrade
tar: ./dists/stable/main/dist-upgrader/binary-all//feisty.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
Could not find the upgrade application in the archive, exiting

```

That double-slash in the path will be causing it. But I don't have the knowledge to fix it. 

The main reason I want to upgrade is because the file sharing setup dialog is unusable (all greyed out even as superuser), and I'm sure it wouldn't be a problem in the latest version. 

Any help greatly appreciated.

---

### Post by Pablitox on 2007-06-23
Hi, I have the same error but when I try to update Synaptic... this is what it says:

```
http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2: MD5 sum mismatch
http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2: MD5 sum mismatch
```

If anyone knows what's going on, please write!!

---

### Post by kuovsk.anekask on 2007-06-30
Heh. Now it works without any errors. I'm upgrading now. 

Problem solved itself.

---

