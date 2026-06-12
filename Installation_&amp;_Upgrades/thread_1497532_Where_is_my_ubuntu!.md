---
title: "Where is my ubuntu!"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by coolman98 on 2010-05-30
I installed backtrack linux and now cannot boot my ubuntu partition. What can I do ?

---

### Post by hansdown on 2010-05-30
Hi coolman98.

Backtrack likely installed to the entire disk.

If you have a live ubuntu disk, you can "try ubuntu without changes", and click system> administration> gparted.

You should be able to see if the ubuntu partition is there, or not.

---

### Post by coolman98 on 2010-05-30
No I dual booted. HELP

---

### Post by Sef on 2010-05-30
> No I dual booted.  HELP

With a Live CD open the Terminal, then copy and paste in this code:

```
sudo fdisk -l
``` 

That will show you what your partitions currently are.

Then copy and paste the results back here.

---

### Post by hansdown on 2010-05-30
> **coolman98 said:**
> No I dual booted. HELP

You can still use the live CD to make sure your ubuntu install is safe.

We can help you, if we know what we are dealing with.

---

### Post by coolman98 on 2010-05-30
Disk /dev/sda: 160.0 GB, 160041885696 bytes 255 heads, 63 sectors/track, 19457 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x000033d9     Device Boot      Start         End      Blocks   Id  System /dev/sda1   *           1       13049   104815068+  83  Linux /dev/sda2           13050       19458    51473893+   5  Extended /dev/sda5           19087       19458     2978816   82  Linux swap / Solaris /dev/sda6           13050       18834    46467949+  83  Linux /dev/sda7           18835       19086     2024158+  82  Linux swap / Solaris  Partition table entries are not in disk order  Disk /dev/sdb: 2000 MB, 2000682496 bytes 62 heads, 62 sectors/track, 1016 cylinders Units = cylinders of 3844 * 512 = 1968128 bytes Disk identifier: 0x00000000     Device Boot      Start         End      Blocks   Id  System /dev/sdb1   *           1        1016     1952721    c  W95 FAT32 (LBA) root@bt:~#

---

### Post by darkod on 2010-05-30
Can you paste that inside CODE tags please?

Select the text and hit the # button in the toolbar above when creating the post.

PS. But to get a better look what is what, and which distro is installed where, you should really run the boot info script and post the content of the results file, again in CODE tags, as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by coolman98 on 2010-05-30
is there anything that I could just
do in grub

---

### Post by darkod on 2010-05-30
> **coolman98 said:**
> is there anything that I could just
do in grub

Without more detailed information we can't really tell you anything. Issuing commands "on blind" can make things worse.

Besides, when installing backtrack you didn't need to install grub with it. When you already had one grub2 from ubuntu, it can boot any linux distro. No need to install grub again with every other linux install.

---

### Post by coolman98 on 2010-05-30
sorry, the error was  "error 15 file not found"
does that help?

---

### Post by coolman98 on 2010-05-30
I install with the installer witch uses a modifies
version of ubiquity.

---

### Post by coolman98 on 2010-05-30
hello.............

---

### Post by wilee-nilee on 2010-05-30
> **coolman98 said:**
> hello.............

I would follow darkods advice.;)

---

