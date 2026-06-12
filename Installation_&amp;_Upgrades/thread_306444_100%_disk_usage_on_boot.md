---
title: "100% disk usage on /boot ?"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by MdaG on 2006-11-25
After upgrading from Dapper to Edgy I get a warning message upon boot that "100% disk usage on /boot". Is this something gone wrong or is it suppose to be that way, if so, why the warning message?

Other than that most seems to have gone alright apart from Firefox dying now and then due to unexplained reason...

---

### Post by po0f on 2006-11-25
MdaG,

Is /boot a separate partition?  And if so, what's the output of:
```
$ df -h | grep boot
```
Also, if it is the default ext3, there is [a way](http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/ref-guide/s1-filesystem-ext2-revert.html) to convert it to ext2, saving you the space from ext3's journal.

I've never performed an upgrade from Dapper to Edgy; are Dapper's kernels still laying around?

---

### Post by K.Mandla on 2006-11-25
Is your /boot a separate partition? If so, you might have made so many kernel upgrades that the /boot partition is full. I did that once with Dapper and it confused me for a bit, until I uninstalled the three oldest versions.

---

### Post by MdaG on 2006-11-25
Yes /boot is a separate partition, here's the output.
```
$ df -h | grep boot
/dev/hda2              30M   29M     0 100% /boot
```

I have a couple of kernels there, but it's not something I've compiled myself, it's been done by the Dapper installer and by the Edgy upgrade
```
:/boot$ ls -lh
total 28M
-rw-r--r-- 1 root root 261K 2006-09-08 23:51 abi-2.6.15-26-386
-rw-r--r-- 1 root root 261K 2006-09-16 05:47 abi-2.6.15-27-386
-rw-r--r-- 1 root root 280K 2006-10-13 21:03 abi-2.6.17-10-386
-rw-r--r-- 1 root root  69K 2006-09-08 21:52 config-2.6.15-26-386
-rw-r--r-- 1 root root  69K 2006-09-16 03:49 config-2.6.15-27-386
-rw-r--r-- 1 root root  74K 2006-10-13 16:38 config-2.6.17-10-386
drwxr-xr-x 2 root root 1.0K 2006-11-24 23:57 grub
-rw-r--r-- 1 root root 6.5M 2006-09-15 10:17 initrd.img-2.6.15-26-386
-rw-r--r-- 1 root root 6.7M 2006-11-24 23:54 initrd.img-2.6.15-27-386
-rw-r--r-- 1 root root 6.5M 2006-11-24 23:56 initrd.img-2.6.17-10-386
drwxr-xr-x 2 root root  12K 2006-09-05 21:34 lost+found
-rw-r--r-- 1 root root  93K 2006-10-20 13:44 memtest86+.bin
-rw-r--r-- 1 root root 710K 2006-09-08 23:51 System.map-2.6.15-26-386
-rw-r--r-- 1 root root 709K 2006-09-16 05:48 System.map-2.6.15-27-386
-rw-r--r-- 1 root root 697K 2006-10-13 21:04 System.map-2.6.17-10-386
-rw-r--r-- 1 root root 1.4M 2006-09-08 23:51 vmlinuz-2.6.15-26-386
-rw-r--r-- 1 root root 1.4M 2006-09-16 05:47 vmlinuz-2.6.15-27-386
-rw-r--r-- 1 root root 1.6M 2006-10-13 21:03 vmlinuz-2.6.17-10-386
```

Now, I've never removed old kernels in Ubuntu, how can it be done in a safe way?

---

### Post by po0f on 2006-11-26
MdaG,

Since you upgraded from Dapper to Edgy, I'm assuming you can just delete them, as the packages Dapper's kernels are in are not in Edgy's repos.  You might want to confirm this with someone more knowledgeable though.

---

### Post by louieb on 2006-11-26
I have used both Synaptic (probally safer) and the rm command to remove kernel files that I no longer use. 
Synaptic will also remove the kernel entry from /boot/grub/menu.lst.
 
Ubuntu installs 4 files for each kernel version.[LIST]
[*]vmlinux-...
[*]initrd-...
[*]config-...
[*]abi-...[/LIST]Together all 4 add up to about 10 mb.
If it were mine I would use System>Adimistration>Synaptic and do a remove purge of the 2.6.15-26-386 kernel files. 
Oh for some reason Synaptic reports it will remove 80 - 100 meg of files. I was was puzzled by it but I came to the conclusion that it just can't add.
That should work until the next time there is a kernel update.
 
Btw 30 meg as you have guessed by is a little small for a /boot partition.
A lot of the stuff I have read recommends 75 - 100 meg. I usally make mine around 66 meg. 
I would not bother trying to resize it now. But if you ever have to re-partition your disk, think about making  the /boot partition larger.

---

### Post by MdaG on 2006-11-27
> **louieb said:**
> Btw 30 meg as you have guessed by is a little small for a /boot partition.
A lot of the stuff I have read recommends 75 - 100 meg. I usally make mine around 66 meg. 
I would not bother trying to resize it now. But if you ever have to re-partition your disk, think about making  the /boot partition larger.

The small boot partition is an old Gentoo habit of mine. The Gentoo handbook recommends 32Mb for the boot partition and I guess I'm just use to that.

---

