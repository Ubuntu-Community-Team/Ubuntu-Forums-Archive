---
title: "dpkg was interrupted you must manually run 'sudo dpkg --configure -a' to"
date: 2020-02-23
forum: Installation &amp; Upgrades
---

### Post by larrytx on 2020-02-23
I literally just installed Ubuntu 19.10 connected via PuTTY, and tried to do something very simple, and this error came up. I've literally run ```
sudo dpkg --configure -a
``` this code from the command line 20 or 30 times.  It never finishes without errors, the most common being
[INDENT]```
dpkg: error: need an action option
```[/INDENT]
I'm new to Ubuntu and don't know what to do next. What can I do to resolve this? I must say that I'm rapidly discovering that Ubuntu is vastly more difficult that Windows, to the point of being virtually impossible.

---

### Post by Impavidus on 2020-02-24
Yes, Ubuntu is completely different from Windows. I've difficulty understanding how people can actually work with Windows, so I imagine that people who do may have difficulty understanding how people can actually work with Ubuntu. Which is easy, in my opinion.

Could you show the complete output of```
sudo dpkg --configure -a
```Error messages tend to be helpful.

---

### Post by larrytx on 2020-02-24
Thank you for being understanding. (And yes, I find Windows very simple, now if I convince my Mac friends of that.) Anyway, Here's the output of dpkg --configure -a:

ubuntu@FilesDBSrv:~$ sudo dpkg --configure -a
dpkg: error: failed to write status database record about 'cpp-9' to '/var/lib/dpkg/status': No space left on device

This is much clearer than anything I've gotten before. Also much more difficult to believe. There is simply no way that this device could be full or "No space left on device." I repartitioned the disk drive reformatted prior to using it. Burned the Ubuntu ISO to it, after which there was plenty of space left. (Sorry, I didn't write it down, and I'm reluctant to say without having the correct figure.).

---

### Post by guiverc on 2020-02-24
When you format a disk a fixed number of in-nodes are created (most of the time we use defaults), once they're used disk is full.

You should check your disk space, eg. to view local disks with human output you can use

```
df -hl
```

To check you have innodes

```
df -hli
```

(-h is human as I dislike big numbers, -l to restrict to local drives as I usually have network shares mounted too, but both -h & -l are optional).

The first will check you have free space available to store data, the second to ensure you haven't used all directory/file-system space with millions/billions of tiny files that have filled the directory tables and thus extra space cannot be allocated anymore

---

