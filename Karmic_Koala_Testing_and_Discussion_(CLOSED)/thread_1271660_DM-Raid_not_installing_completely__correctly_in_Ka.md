---
title: "DM-Raid not installing completely / correctly in Karmic"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phyrewall on 2009-09-21
Whenever I install Ubuntu on my raid system, I've always let it run on its defaults until Ubiquity crashes at the end. This isn't a problem, it just needs the last few steps completed manually. (See the Wiki on FakeRaid installation). This is not what's broken.

Ever since Alpha 5, I've found that after Ubiquity "quits", when I chroot to check if dmraid is installed, apt-get tells me it is already installed. However, when I try to run "dmraid -ay" it tells me that it is not installed. So, I purge dmraid and re-install it. After running it again, I find that the library that dmraid requires is also "installed" but is actually missing.

Some code for reference:

```
root@ubuntu:/# apt-get install dmraid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dmraid is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

root@ubuntu:/# dmraid -ay
The program 'dmraid' is currently not installed.  You can install it by typing:
apt-get install dmraid
dmraid: command not found

root@ubuntu:/# apt-get purge dmraid

root@ubuntu:/# apt-get install dmraid

root@ubuntu:/# dmraid -ay
dmraid: error while loading shared libraries: libdmraid.so.1.0.0.rc15: cannot open shared object file: No such file or directory
root@ubuntu:/# 

```So I purge/re-install libdmraid, and then dmraid finally works.

Could someone help me clean this up in a way so that I can search the bugtracker to see if this bug already exists, or post a new one? Thanks

---

