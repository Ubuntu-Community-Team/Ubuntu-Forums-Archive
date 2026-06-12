---
title: "How can I acess ubuntu files from Windows 7"
date: 2012-04-12
forum: Installation &amp; Upgrades
---

### Post by chicoCarvalho on 2012-04-12
Hello. 
Today I was updating my ubuntu to the newer version when my suddently my computer restarted alone and when I went back to ubuntu, it has just lost its interface and I can't really get back to it. So my question is how can I really acess ubuntu files from Windows 7 64 bits? I installed ubuntu using wubi.


Thanks in advance!

---

### Post by bcbc on 2012-04-12
If you get a grub prompt when you boot Ubuntu, then you likely have a corruption of the root.disk. See [here]("http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html")

If it's just the user interface not showing, then you can access the root.disk from Windows with this: [http://ext2read.blogspot.ca/](http://ext2read.blogspot.ca/)
Download, run, point it at C:\ubuntu\disks\root.disk (change drive letter if necessary) and you get read-only access to the files.

---

### Post by chicoCarvalho on 2012-04-12
Thanks alot, it worked :)

---

