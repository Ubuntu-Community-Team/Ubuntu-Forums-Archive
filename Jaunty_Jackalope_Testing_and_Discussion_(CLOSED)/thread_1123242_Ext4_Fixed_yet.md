---
title: "Ext4 Fixed yet?"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by chris062689 on 2009-04-12
I heard of a bug in the Ext4 filesystem that could corrupt files if the power was cut?  Has this been resolved in the daily builds?  Will this be fixed by 9.04?  Will it be a kernel update?

---

### Post by slavik on 2009-04-12
YOU found the bug???

Isn't this something that has been discussed ad nauseam on slashdot and has already seen a response from the ext4 devs and a way to get ext3 like behavior through a config file?

---

### Post by chris062689 on 2009-04-12
> **slavik said:**
> YOU found the bug???

Isn't this something that has been discussed ad nauseam on slashdot and has already seen a response from the ext4 devs and a way to get ext3 like behavior through a config file?

What!?  I never said I found this said bug.. 
I simply said I heard about it on one of the topics... :lolflag:
Is it something I should really worry about?
Has there been a fixed commited?
Does launchpad have a listing?
EDIT: Found it.  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781?comments=all)

====================



This bug was fixed in the package linux - 2.6.28-10.32

Is this true?
Does the daily build have 2.6.28-10.32?

==================
After reading all of the comments there, it appears that it's still not fixed?

---

### Post by slavik on 2009-04-12
apologies ... late night reading makes you see things.
```

slavik@slavik-desktop:~$ apt-cache showpkg linux
Package: linux
Versions: 
2.6.28.11.14 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-amd64_Packages
                  MD5: e1f3af50c53d3b40815e9810a03f60ee


Reverse Depends: 
Dependencies: 
2.6.28.11.14 - linux-image (5 2.6.28.11.14) linux-restricted-modules (5 2.6.28.11.14) 
Provides: 
2.6.28.11.14 - 
Reverse Provides: 
type-handling 0.2.23

```

---

### Post by chris062689 on 2009-04-12
Ok, so it's using an updated kernel.
It never really came to a conclusion though on the comments, has anyone here noticed any data loss when cutting power?

---

### Post by krazyd on 2009-04-12
> **chris062689 said:**
> 
Has there been a fixed commited?

[Yes, here (see Theodore T'so's patches).]("https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/317781/comments/173")

---

### Post by olskar on 2009-04-12
Check my thread here [http://ubuntuforums.org/showthread.php?t=1115098](http://ubuntuforums.org/showthread.php?t=1115098)

---

