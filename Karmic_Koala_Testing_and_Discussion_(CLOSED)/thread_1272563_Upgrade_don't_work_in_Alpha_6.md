---
title: "Upgrade don't work in Alpha 6"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by theozzlives on 2009-09-22
I tried update-manager and cdromupgrade on the Alternate. It just plain does nothing. running Jaunty

---

### Post by kansasnoob on 2009-09-22
Unless you have horribly slow internet I'd skip the alternate and:

> To upgrade from Ubuntu 9.04 on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. 

Read all the release notes:

[http://www.ubuntu.com/testing/karmic/alpha6](http://www.ubuntu.com/testing/karmic/alpha6)

You should also know that ext3 filesystems will not be automatically upgraded to ext4, nor will legacy grub be upgraded to grub 2.

---

### Post by slakkie on 2009-09-22
Instead of running update-manager -d in a system console, just run do-release-upgrade -d which will do the same. It will not invoke a GUI unlike update-manager does.

---

### Post by theozzlives on 2009-09-22
> **kansasnoob said:**
> Unless you have horribly slow internet I'd skip the alternate and:



Read all the release notes:

[http://www.ubuntu.com/testing/karmic/alpha6](http://www.ubuntu.com/testing/karmic/alpha6)

You should also know that ext3 filesystems will not be automatically upgraded to ext4, nor will legacy grub be upgraded to grub 2.

I did both ways, and it did nothing after the password.

---

### Post by kansasnoob on 2009-09-22
Well, thinking here .............. post the output of:

```
cat /etc/apt/sources.list

```

---

### Post by theozzlives on 2009-09-23
> **kansasnoob said:**
> Well, thinking here .............. post the output of:

```
cat /etc/apt/sources.list

```

To late, I already did a fresh install.

---

