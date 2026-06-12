---
title: "[SOLVED] Seriously borked system (libc6)"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by excogitation on 2008-10-05
I don't know exactly how I managed to end up where I am now - but if I try to update  using update-manager I end up getting this error > E: Internal Error, Could not perform immediate configuration (1) on libc6


> # apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done


> # apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
14 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
E: Internal Error, Could not perform immediate configuration (1) on libc6


> # dpkg --configure -a
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted


> ~# dpkg --force-all -i /home/excogitation/Desktop/new/libc6_2.8~20080505-0ubuntu7_i386.deb
(Reading database ... 173600 files and directories currently installed.)
Preparing to replace libc6 2.8~20080505-0ubuntu7 (using .../libc6_2.8~20080505-0ubuntu7_i386.deb) ...
Unpacking replacement libc6 ...
dpkg: also configuring `libgcc1' (required by `libc6')
Setting up libc6 (2.8~20080505-0ubuntu7) ...

dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted


As I see it the libc6 installation didn't finish and after two days of trying - I still have no idea how to fix it.

---

### Post by wgrant on 2008-10-05
> **excogitation said:**
> I don't know exactly how I managed to end up where I am now - but if I try to update  using update-manager I end up getting this error 

As I see it the libc6 installation didn't finish and after two days of trying - I still have no idea how to fix it.

That looks like a dpkg bug. Please [file a bug](https://bugs.launchpad.net/ubuntu/+source/dpkg/+filebug).

---

### Post by nowshining on 2008-10-05
try:
```

sudo apt-get clean 
```

and try again..

---

### Post by excogitation on 2008-10-05
> **wgrant said:**
> That looks like a dpkg bug. Please [file a bug](https://bugs.launchpad.net/ubuntu/+source/dpkg/+filebug).
I think I broke it.

> **nowshining said:**
> try:
```

sudo apt-get clean 
```

and try again..

Here we go again:
> # apt-get clean
> # dpkg --configure -a
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted


> # dpkg --force-all -i /home/excogitation/Desktop/new/libc6_2.8~20080505-0ubuntu7_i386.deb
(Reading database ... 173600 files and directories currently installed.)
Preparing to replace libc6 2.8~20080505-0ubuntu7 (using .../libc6_2.8~20080505-0ubuntu7_i386.deb) ...
Unpacking replacement libc6 ...
dpkg: also configuring `libgcc1' (required by `libc6')
Setting up libc6 (2.8~20080505-0ubuntu7) ...

dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted


---

### Post by nowshining on 2008-10-05
hehe i didn't notice wgrant is a ubuntu dev - best do what they suggest.. :)

---

### Post by excogitation on 2008-10-05
> **nowshining said:**
> hehe i didn't notice wgrant is a ubuntu dev - best do what they suggest.. :)

[bug report]("https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/278804")

---

### Post by zbrox on 2008-10-06
I had a similar problem. The libc6 package wasn't installed during an upgrade to Intrepid. After that nothing worked. Not even simple commands like "ls".

Check out this, maybe it can be of some help > [http://ubuntuforums.org/showpost.php?p=5915347&postcount=27](http://ubuntuforums.org/showpost.php?p=5915347&postcount=27)

---

### Post by excogitation on 2008-10-06
> **zbrox said:**
> I had a similar problem. The libc6 package wasn't installed during an upgrade to Intrepid. After that nothing worked. Not even simple commands like "ls".

Check out this, maybe it can be of some help > [http://ubuntuforums.org/showpost.php?p=5915347&postcount=27](http://ubuntuforums.org/showpost.php?p=5915347&postcount=27)

What do you mean by install the Intrepid libc6 packages by using the LC_ALL=C.

I can't install the libc6:
> # dpkg --force-all -i /home/excogitation/Desktop/new/libc6_2.8~20080505-0ubuntu7_i386.deb 
(Reading database ... 173600 files and directories currently installed.)
Preparing to replace libc6 2.8~20080505-0ubuntu7 (using .../libc6_2.8~20080505-0ubuntu7_i386.deb) ...
Unpacking replacement libc6 ...
dpkg: also configuring `libgcc1' (required by `libc6')
Setting up libc6 (2.8~20080505-0ubuntu7) ...

dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted


---

### Post by excogitation on 2008-10-06
If anybody's interested ... here is how I solved it:

> # cat /var/lib/dpkg/status | grep Triggers-Awaited
Triggers-Awaited: man-db

> # dpkg -P man-db
dpkg: dependency problems prevent removal of man-db:
 yelp depends on man-db (>= 2.5.1-1); however:
  Package man-db is to be removed.
 ubuntu-standard depends on man-db.
 debhelper depends on man-db (>= 2.5.1-1); however:
  Package man-db is to be removed.
dpkg: error processing man-db (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 man-db

As you can see man-db wasn't even removed, but now it works again:
> # apt-get install man-db
Reading package lists... Done
Building dependency tree       
Reading state information... Done
man-db is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
12 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libstdc++6 (4.3.2-1ubuntu9) ...

Setting up libgmp3c2 (2:4.2.2+dfsg-3ubuntu1) ...

Setting up libmpfr1ldbl (2.3.1.dfsg.1-2ubuntu1) ...

Setting up cpp-4.3 (4.3.2-1ubuntu9) ...
Setting up man-db (2.5.2-2) ...
Updating database of manual pages ...

Setting up binutils (2.18.92.20081003-0ubuntu1) ...

Setting up libgomp1 (4.3.2-1ubuntu9) ...

Setting up gcc-4.3 (4.3.2-1ubuntu9) ...
Setting up libc6-dev (2.8~20080505-0ubuntu7) ...
Setting up libgfortran3 (4.3.2-1ubuntu9) ...

Setting up g++-4.3 (4.3.2-1ubuntu9) ...
Setting up libstdc++6-4.3-dev (4.3.2-1ubuntu9) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by zbrox on 2008-10-06
> **excogitation said:**
> What do you mean by install the Intrepid libc6 packages by using the LC_ALL=C.

I can't install the libc6:

It seems this is a different problem from what I've experienced.

---

