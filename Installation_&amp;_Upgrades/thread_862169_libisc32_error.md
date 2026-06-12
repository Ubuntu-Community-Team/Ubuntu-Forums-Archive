---
title: "libisc32 error"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by nareshpunia on 2008-07-17
Dear friends,
I am facing a very strange problem. Whenever I go for any software updates I get same following error:
 
*E: /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.36_i386.deb: files list file for package `libisc32' is missing final newline*

I tried following but failed:
sudo apt-get update
sudo apt-get autoremove

Please help me what can be done.

Thanks in Advance

---

### Post by lesergi on 2008-07-17
Hi,

Try removing the package:

```
rm -f /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.36_i386.deb
```

Now, try again!

---

### Post by nareshpunia on 2008-07-18
> **lesergi said:**
> Hi,

Try removing the package:

```
rm -f /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.36_i386.deb
```

Now, try again!

Thanks for your reply. 
But, problem is still as it is.

---

### Post by Partyboi2 on 2008-07-18
You could try [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showpost.php?p=1635843&postcount=9")

---

### Post by nareshpunia on 2008-07-18
> **Partyboi2 said:**
> You could try [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showpost.php?p=1635843&postcount=9")

Thanks dear my problem is solved now.
I did try only first 4 steps.

naresh punia

---

