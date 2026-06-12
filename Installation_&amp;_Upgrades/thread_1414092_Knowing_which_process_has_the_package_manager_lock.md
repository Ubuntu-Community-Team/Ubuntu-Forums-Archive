---
title: "Knowing which process has the package manager lock"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by borncrusader on 2010-02-23
Hi,

Is there any way to know which process is currently holding the dpkg lock. I tried using lsof on the file with no avail.

Thanks,
Srinath

---

### Post by lloyd_b on 2010-02-23
> **borncrusader said:**
> Hi,

Is there any way to know which process is currently holding the dpkg lock. I tried using lsof on the file with no avail.

Thanks,
Srinath

Which file were you checking?  And were you using a "sudo" on the "lsof" command (searching for root locks requires root permission).

At any rate, the following command should work:```
sudo lsof | grep "\/var\/lib\/dpkg\/lock"
```

Lloyd B.

---

### Post by borncrusader on 2010-02-24
```
sanantha@klinux:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory
sanantha@klinux:~$
```

I got it working when I checked for /var/lib/apt/lists/lock with

```
sudo lsof /var/lib/apt/lists/lock
```

It's just that lsof takes some time to display the output! So, thought there was no output at all and interrupted the program.

Thanks anyways!

---

