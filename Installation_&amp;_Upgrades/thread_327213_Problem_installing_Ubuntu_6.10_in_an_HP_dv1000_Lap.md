---
title: "Problem installing Ubuntu 6.10 in an HP dv1000 Laptop"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by ishtiaq on 2006-12-28
Trying to install Ubuntu 6.10 in my HP dv1000 notebook.

I have tried several "live" distros. Some (Ubuntu, Fedora 6), worked fine, others didn't show up.

Installation of Ubuntu 6.10 is stuck at 33% ("Copying files..."). Sometimes it loaded fine (and then got stuck at 33% while installing), other times it showed an error about reading some buffer.

Since my disc is already partitioned and formatted, I have no way of reverting to a working OS. It's not picking up anything other than these two live distros.

Would anyone be kind enough to give some pointers? Thanks in advance and sorry for the inconvenience.

Best wishes.

---

### Post by Sef on 2006-12-28
How does the Live CD work?  Do you have any problems with it or does it work with no problems?

---

### Post by ishtiaq on 2006-12-28
The Live CDs work just fine. I ran the Memory Test, it didn't return any errors. The Live CDs even pick up my audio drivers seamlessly. All the trouble occurs when I try to install the OS into my hard drive.

Also, the Live CDs worked with Ubuntu 6.10 and Kubuntu 6.10; Ubuntu 6.06 LTS kept giving the buffer error. Kubuntu installation stalls at the same "Copying files..." location (15% in this case).

---

### Post by ishtiaq on 2006-12-28
Here's the error that I have been seeing a lot.

[17180619.464000] Buffer I/O error on device hdb, logical block 184204

This is just one of the many similar lines. Another variation is the following:

[17180619.280000] SQUASHFS error: sb_bread failed reading block 0x5903a
[17180619.280000] SQUASHFS error: Unable to read page, block 1640d7dd, 10e2

I hope this helps you identify the problem. :(

---

