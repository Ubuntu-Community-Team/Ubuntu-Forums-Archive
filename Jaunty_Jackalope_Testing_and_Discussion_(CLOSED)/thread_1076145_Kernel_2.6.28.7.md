---
title: "Kernel 2.6.28.7"
date: 2009-02-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-02-21
Its been released. Lots of EXT4 changes. Shouldnt be long before the kernel team have it in Ubuntu.

---

### Post by DougieFresh4U on 2009-02-21
I thought were up to:

---

### Post by Nullack on 2009-02-21
The upstream versioning is 2.6.28.7, released on the 20th.

---

### Post by Kevbert on 2009-02-21
2.6.28-8 Ubuntu/Kubuntu are working well... What's this upstream version ???

---

### Post by Nullack on 2009-02-21
[http://kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.28.7](http://kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.28.7)

---

### Post by Starks on 2009-02-21
Isn't the 2.6.28.8 basically just 2.6.28.7 with 2.6.29rc5 backports?

---

### Post by Nullack on 2009-02-21
No mate, the ubuntu kernel team git web is last tagged from upstream as .6. You can look on their git web. Ubuntu is missing the latest .7 change from Feb 20th.

---

### Post by Starks on 2009-02-21
Wow. If that's the case, then Ubuntu Kernel Team's naming scheme is absolutely horrid.

---

### Post by plun on 2009-02-21
> **Nullack said:**
> Its been released. Lots of EXT4 changes. Shouldnt be long before the kernel team have it in Ubuntu.

Well, first you should have a 2.6-28-8 kernel 


```
plun@plun:~/$ **sudo update-grub**
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.29-rc5-candela
Found kernel: /boot/vmlinuz-2.6.29-rc4-candela
**Found kernel: /boot/vmlinuz-2.6.28-8-generic**
Found kernel: /boot/vmlinuz-2.6.28-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

The EXT4 changes should already be within -8 kernel


"The master bug" for EXT4 data losses.

[https://bugs.launchpad.net/bugs/317781](https://bugs.launchpad.net/bugs/317781)

> This issue should be fixed with 2.6.28-7.18. I cherry picked a *_number of patches that Ted Tso is submitting for stable kernel updates_* which he says fixes this data loss problem. Please confirm.

But maybe there are more fixes coming ?


I cannot see any diff between RC5 and the -8 kernel

---

### Post by Starks on 2009-02-21
What mainline does 2.6.28-8 correspond to?

---

### Post by plun on 2009-02-21
> **Starks said:**
> What mainline does 2.6.28-8 correspond to?

Vanilla-2.6.28.6 was imported 3 days ago.

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=shortlog](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=shortlog)

But after that several patches and changes.

---

### Post by Starks on 2009-02-21
Nullack, you are confusing the hell out of me.

According to you: 2.6.28-7 = 2.6.28.7

Is this the case?

---

### Post by glasen on 2009-02-21
No. The "-7" means only the ABI-Version of the Ubuntu-kernel. It does not correspond to the minor-version (e.g. 2.6.28.**7**) of the vanilla-kernel.

Ubuntu-kernel 2.8.28-8 = vanilla-kernel 2.8.28.6 + Ubuntu specific patches

---

### Post by Starks on 2009-02-21
I must reiterate. That labelling is stupid as hell.

---

### Post by Nullack on 2009-02-21
You guys are all confused. Look at this:

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=shortlog](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=shortlog)

Note the tagging:

3 days ago
	Greg Kroah ...
	Linux 2.6.28.6

So 3 days ago they did upstreams 2.6.28.6, and now on Feb 20 upstream is at 2.6.28.7, which we need, in particular lots of ext4 fixes.

---

### Post by kurros on 2009-02-21
> **Nullack said:**
> You guys are all confused. Look at this:

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=shortlog](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=shortlog)

Note the tagging:

3 days ago
    Greg Kroah ...
    Linux 2.6.28.6

So 3 days ago they did upstreams 2.6.28.6, and now on Feb 20 upstream is at 2.6.28.7, which we need, in particular lots of ext4 fixes.

Looking at the log all of those ext4 changes in 2.6.28.7 are already in Ubuntu's sauce (backported from 2.6.29). But dont worry anything else missed will be merged soon enough.

---

### Post by plun on 2009-02-21
> **Nullack said:**
> You guys are all confused.



Nope... I am not....:D  ;)

"alles klar"....

---

