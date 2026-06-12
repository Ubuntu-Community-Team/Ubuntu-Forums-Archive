---
title: "New install Ubuntu server 10 with raid 5 failing"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by pug2694328 on 2010-05-01
I am installing Ubuntu server 10 and having a little trouble booting.

I used the server install CD for partitioning as well as OS install.

During Ubuntu server setup I partitioned each of 5 1GB drives into two partitions, a small one for swap and the rest for /

I set their type to be used for RAID.
I went into the the RAID configure bit and created two RAID arrays from the 10 partitions.

I then saved that and set the smaller raid array to be used for swap and the larger to be used as /.  I then continued and installed the Ubuntu server OS.  Everything seemed fine, but when I rebooted at the end of install I hit this:

```
error: file not found
grub rescue>
```

when I do an ls, I am pretty sure I can see my raid arrays (md0 and md1:

```
(md0) (md1) (hd0,5) (hd0,1), (hd1,1) (hd1,2) (hd2,5), (hd2,1), (hd3), (hd3,5) (hd3,1) (hd4) (hd4,5) (hd4,1)
```

I suspect it's a problem with grub since the installer appeared to be successfully installing the OS.  Any help would be greatly appreciated!

---

### Post by pug2694328 on 2010-05-02
bump

---

### Post by pug2694328 on 2010-05-02
No ideas?  I read this doc, but none of the commands 'help' for example, seem to work.  Do I need to do something to my bios to get it to boot?  I currently have it set to boot to the first drive in my RAID array.

[http://grub.enbug.org/Manual#head-d782c3ed07197a089c4fdf66abce08744adcc0eb](http://grub.enbug.org/Manual#head-d782c3ed07197a089c4fdf66abce08744adcc0eb)

---

### Post by pug2694328 on 2010-05-05
bump again?

---

### Post by pug2694328 on 2010-05-05
This thread suggests that I might have to put /boot on raid1...  can someone in the know confirm the inability to boot to raid5 in ubuntu server 10?

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1253810](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1253810)

---

### Post by pug2694328 on 2010-05-05
Okay that worked.  Here's what I did:
My server consists of 5 1TB drives
Create three partitions on each drive (so repeat 5 times).
One very large partition.
One Partition = 2x the system memory.
One rather small one (1gb).
As you create them set each to use as = RAID.

Then in the RAID configuration make 3 RAID arrays.
Two RAID5 arrays, one for the very large partitions and one for the smaller partitions.

Create one RAID1 array using two of the very small partitions.
So you will not use 3 of the very small partitions at all.

Now set the very large RAID5 to be used as /.
Set the smaller RAID5 array to be used as swap (that's why you want 2x the system memory).
Set the RAID1 array to be used as /boot (this I believe is the key to making it bootable.

Complete the installation and when you boot for the first time you should get a logon prompt.

I am not thrilled about this setup, but maybe someone can allay my fears.  What are the consequences if the RAID 1 array (/boot) loses both drives at the same time?

Is there a better way to do this?
Is it possible to boot to RAID5?

---

