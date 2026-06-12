---
title: "No Windows 7 option in grub"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by ZeroCoo on 2013-02-10
Gys I installed ubuntu 12.04 on my desktop which had windows 7 previously.
  After installing ubuntu their was no option for boot selection and  ubuntu 12.04 was getting booted automatically. I used boot repair to fix  this problem, but now grub shows the options to boot into ubuntu only.  Here is the log from boot repair: [http://paste.ubuntu.com/1633565/](http://paste.ubuntu.com/1633565/)

---

### Post by darkod on 2013-02-10
All your ntfs partitions are logical. That is fine for data partitions but windows can't boot directly from a logical unless there is a primary partition with its boot files. I guess you had that partition but deleted it not knowing what it does. Now you don't have the win7 boot files for grub2 to detect.

One thing you can do is convert sda7 to primary but for that you will have to delete the swap sda8 first.

Even if you convert sda7 to primary, you will have to do the win7 repair procedure so that it can put its boot files on sda7.

Here is what I suggest:
1. Boot the computer with the ubuntu cd in live mode.
2. Download and run fixparts.
[www.rodsbooks.com/fixparts/](www.rodsbooks.com/fixparts/)
Use it to convert sda7 to primary partition.
3. Open Gparted, remove the boot flag on sda1 and put a boot flag on the win7 partition (it will probably not be called sda7 any more, maybe sda3).

Get the win7 dvd and run the repair process few times until it gets win7 booting. After that you will need to restore grub2 to the MBR because the win7 repair process will delete it.

You can do that from live mode again, in terminal with:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

After that it will still boot directly to ubuntu. When it boots open terminal and run:
```
sudo update-grub
```

That will detect the win7 boot files and create the correct entry in the boot menu.

---

### Post by schragge on 2013-02-10
Look if you have *os-prober* installed
```
which os-prober
```
If not then
```

sudo apt-get install os-prober
sudo update-grub

```

---

### Post by darkod on 2013-02-10
> **schragge said:**
> Look if you have *os-prober* installed
```
which os-prober
```
If not then
```

sudo apt-get install os-prober
sudo update-grub

```

That won't help anything. Read my post above and look more carefully in the OP bootinfo results. There are no win7 boot files and the partition is logical.

---

### Post by U202E on 2013-02-10
when I used win7 to partition the hdd something told me that there can be only 4(or so) primary partitions and that windows can't boot from a logic partition.
according to that info it's an error of windows, and you could try to move the windows-partition. (so that win7 will be on the 2nd partition or so)

before trying anything look here: [https://www.google.nl/search?client=ubuntu&channel=fs&q=primary+partition+windows+7&ie=utf-8&oe=utf-8&redir_esc=&ei=xuAXUeDvGOnD0QXxvIDIDw](https://www.google.nl/search?client=ubuntu&channel=fs&q=primary+partition+windows+7&ie=utf-8&oe=utf-8&redir_esc=&ei=xuAXUeDvGOnD0QXxvIDIDw)

---

### Post by ZeroCoo on 2013-02-10
@darkod
I didnt have the boot primary partition previously.
What I did while installating was just delete one primary partition and make two partitions form it:
1)ext4fs
2)swap
I didnt delete any more partitions.

The layout before partitioning included two primary partitions:
1) Windows XP (I removed this one)
2) Windows 7 + 2 NTFS drives.

---

### Post by darkod on 2013-02-10
> **U202E said:**
> when I used win7 to partition the hdd something told me that there can be only 4(or so) primary partitions and that windows can't boot from a logic partition.
according to that info it's an error of windows, and you could try to move the windows-partition. (so that win7 will be on the 2nd partition or so)

before trying anything look here: [https://www.google.nl/search?client=ubuntu&channel=fs&q=primary+partition+windows+7&ie=utf-8&oe=utf-8&redir_esc=&ei=xuAXUeDvGOnD0QXxvIDIDw](https://www.google.nl/search?client=ubuntu&channel=fs&q=primary+partition+windows+7&ie=utf-8&oe=utf-8&redir_esc=&ei=xuAXUeDvGOnD0QXxvIDIDw)

Moving a partition is much more dangerous than simply converting it to primary. The disk has 1 primary and 1 extended, which means another primary partition can exist without problems. The mentioned fixparts program can convert logical to primary partition and that would be the easiest thing to do.

Of course, running the win7 repair will have to be done in any case, to create the correct boot files.

---

### Post by darkod on 2013-02-10
> **ZeroCoo said:**
> @darkod
I didnt have the boot primary partition previously.
What I did while installating was just delete one primary partition and make two partitions form it:
1)ext4fs
2)swap
I didnt delete any more partitions.

The layout before partitioning included two primary partitions:
1) Windows XP (I removed this one)
2) Windows 7 + 2 NTFS drives.

In that case the win7 boot files were combined with the XP ones. When you deleted that partition, all of them were gone. Windows combines the boot files when you install multiple versions. Another thing it doesn't actually tell you when installing.

---

### Post by U202E on 2013-02-10
> **darkod said:**
> Moving a partition is much more dangerous than simply converting it to primary. The disk has 1 primary and 1 extended, which means another primary partition can exist without problems. The mentioned fixparts program can convert logical to primary partition and that would be the easiest thing to do.

Of course, running the win7 repair will have to be done in any case, to create the correct boot files.
you're right, moving partitions is dangerous, but you could make a backup...
^^every help/wiki page says you have to backup your hdd before partitioning...

---

