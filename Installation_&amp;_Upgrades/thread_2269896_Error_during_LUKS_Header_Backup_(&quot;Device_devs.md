---
title: "Error during LUKS Header Backup (&quot;Device /dev/sd... doesn't exist or access denied&quot;)"
date: 2015-03-18
forum: Installation &amp; Upgrades
---

### Post by r.pfeiffer222 on 2015-03-18
Hello everyone!

I am fairly new to using (x)ubuntu, so please excuse me if there is an obvious solution to this problem. However, I could not find the answer anywhere on the web, hence this post.

I am trying to install a LUKS-encrypted Xubuntu 14.04.2 Desktop (i386) distribution on my Acer Aspire One 533.

As mentioned above, I am a ubuntu-newbie, so I followed [this ]("http://thesimplecomputer.info/full-disk-encryption-with-ubuntu")tutorial exactly, and everything worked out exactly as it should (according to the tutorial) until I reach Step 9, where I am supposed to back up my LUKS-headers.

When I type in the terminal (according to the tutorial I linked to above)

```
root@xubuntu:/# cryptsetup luksHeaderBackup /dev/sda2 --header-backup-file /home/sda2backup.img
```

I receive the error message

```
Device /dev/sda2 doesn't exist or access denied.
```

I redid the whole process multiple times now, and everything works until I get to this point.

I will greatly appreciate any help.

Thank you in advance!

Cheers,
Ronald


**Edit:**

My System has the following specs:

Acer Aspire One 533-13Drr
Intel Atom N455
1 GB DDR3 RAM
250 GB HDD

The partitions I am trying to install are:
[TABLE="width: 500"]
[TR]
[TD]sda1
[/TD]
[TD]/boot
[/TD]
[TD]500 MB
[/TD]
[/TR]
[TR]
[TD]sda2
[/TD]
[TD]/
[/TD]
[TD]20 GB
[/TD]
[/TR]
[TR]
[TD]sda3
[/TD]
[TD]swap
[/TD]
[TD]2 GB
[/TD]
[/TR]
[TR]
[TD]sda4
[/TD]
[TD]/home
[/TD]
[TD]the rest
[/TD]
[/TR]
[/TABLE]

---

