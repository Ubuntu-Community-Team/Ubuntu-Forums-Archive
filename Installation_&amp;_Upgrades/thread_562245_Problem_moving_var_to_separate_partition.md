---
title: "Problem moving /var to separate partition"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by A-1337 on 2007-09-28
Hello!
I have ubuntu distro which lives on one hard drive: /boot on one partition, / on another and swap aslo on another.
Then I've moved all data from one hard drive to another. I've carefully re-created partition layout and also made separate partition for /var directory.

I've also tuned /etc/fstab; it was:
```

-/dev/sda5      /               ext3    defaults,errors=remount-ro 0       1
-/dev/sda6      /home           ext3    defaults,user_xattr        0       2

```
become:
```

+/dev/sda7      /               ext3    defaults,errors=remount-ro 0       1
+/dev/sda8      /var            ext3    defaults 0       0
+/dev/sda9      /home           ext3    defaults,errors=remount-ro,user_xattr  

```

Then I've moved contents of /var to /dev/sda8 and leave /var on / empty.

Problem is during boot process I get error messages /var/lock and /var/run mountpoints doesn't exist.
This causes network facilities to fail to start.

I have lock and run in /var on /dev/ sda8. Why it asks for them on sda7?

---

### Post by prince_niceguy on 2007-09-28
I too used to get these errors in the boot up. but they did not create any issue with the network though. Might be you need to check something wrong with the network.

---

### Post by BarneyRubble on 2007-09-28
I wrote a [short blog entry]("http://pooterspace.blogspot.com/2007/07/moving-var-and-tmp-in-ubuntu.html") on this.  It's not a very elegant solution, but atleast it explain why you get the symptoms described (i.e. loss of loopback interface etc.) If anyone's got something better, drop me a line.

---

### Post by psusi on 2007-09-28
You get the error because /var/run and /var/lock are mounted very early in the boot process as a tmpfs.  Since your /var partition is not yet mounted, /var/run and /var/lock don't exist, so they can't be mounted.  

My advice is don't use a separate /var partition.  Why would you want to anyhow?

---

### Post by A-1337 on 2007-09-29
> **psusi said:**
> y advice is don't use a separate /var partition.  Why would you want to anyhow?
There are reasons. Preserving postgres' databases and squid's cache when moving to 7.10 for example.

---

