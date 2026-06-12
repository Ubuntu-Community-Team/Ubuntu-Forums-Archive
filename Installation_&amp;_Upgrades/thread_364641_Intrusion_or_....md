---
title: "Intrusion or ... ?"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by glarus on 2007-02-18
Hello !

I have installed Ubuntu 6.10 one week ago and I also have a Debian Etch on my other partitions. 

My question is : does Ubuntu change any folder permittions on other partitions during its installation ? Or was I attacked ?

Today, as I was using my Debian I noticed something very unpleasant : I was able to enter the /root and the /sbin directory with my regular user account - something that I normally could not do. I checked the permitions of the /root and the /sbin folders and they looked like :

drwxr-xr-x

Then I mounted the partition on which Ubuntu was installed (I have never done it before, neither I have it listed in /etc/fstab) and I saw the same access permittions for the same folders. This made me think that this happened while I was using Ubuntu (I used the Debian partitions in Ubuntu to exchange files).

I install almost never packets which does not come from the official repositories and I also have a firewall on my home router (I doupt this was an attack). And I never use the root account to run applications like a browser or download manager etc.
So I really cannot understand how could this possibly happen.

If anyone have ever had a similar problem I will very grateful I he/she could give me some tips what could I do.

---

### Post by an.echte.trilingue on 2007-02-19
On my debian box (etch), this is what I have
```

desktop:/# ls -n | grep root
drwxr-xr-x  18 0  0  4096 2007-02-01 10:32 root
desktop:/# ls -n | grep sbin
drwxr-xr-x   2 0  0  4096 2007-02-18 11:25 sbin

```

Take care
-mat

---

