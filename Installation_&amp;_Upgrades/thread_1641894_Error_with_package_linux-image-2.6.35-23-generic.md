---
title: "Error with package linux-image-2.6.35-23-generic"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by Ikka3990 on 2010-12-09
I recently removed some of the older kernels i wasn't using. After that, I haven't been able to perform any new installations or updates. Following is the message from apt-get -
```

E: The package linux-image-2.6.35-23-generic needs to be reinstalled, but I can't find an archive for it.

```Following is the message from aptitude -
```
E: I wasn't able to locate file for the linux-image-2.6.35-23-generic package. This might mean you need to manually fix this package.

```People please help!!

---

### Post by sikander3786 on 2010-12-10
Try,

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

And post the outputs.

---

### Post by Ikka3990 on 2010-12-22
```
[LEFT]~$: sudo apt-get clean
~$: sudo apt-get autoclean 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
~$: sudo dpkg --configure -a
~$: sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-image-2.6.35-23-generic
Suggested packages:
  fdutils linux-lts-backport-maverick-doc-2.6.35 linux-lts-backport-maverick-source-2.6.35 linux-lts-backport-maverick-tools
The following packages will be upgraded:
  linux-image-2.6.35-23-generic
1 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
1 not fully installed or removed.
Need to get 33.8MB of archives.
After this operation, 143kB disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com/ubuntu/ lucid-proposed/main linux-image-2.6.35-23-generic i386 2.6.35-23.41~lucid1 [33.8MB]
Fetched 33.8MB in 2min 4s (271kB/s)                                                                                                                  
(Reading database ... 336155 files and directories currently installed.)
Preparing to replace linux-image-2.6.35-23-generic 2.6.35-23.37 (using .../linux-image-2.6.35-23-generic_2.6.35-23.41~lucid1_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.35-23-generic ...
```
And then it has just stuck at that for the last couple of hours. :(
[/LEFT]

---

### Post by Ikka3990 on 2010-12-22
Yippy! Found a workaround!
I just chose one of the older kernels in grub and removed and reinstalled the new one. Everything seems to be fine now!
:p

---

### Post by sikander3786 on 2010-12-22
> **Ikka3990 said:**
> Yippy! Found a workaround!
I just chose one of the older kernels in grub and removed and reinstalled the new one. Everything seems to be fine now!
:p
That means you were running out of disk space on the /boot partition. Keep an eye there ;-)

And as the issue is solved now, you can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

### Post by Ikka3990 on 2010-12-25
> **sikander3786 said:**
> That means you were running out of disk space on the /boot partition. Keep an eye there ;-)

And as the issue is solved now, you can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!
I don't have a separate partition for boot and the / partition has about 2 GB space left which should be sufficient. I and, as I have now noticed, many other users have been having problems with unpacking of packages after upgrading to new kernels (>2.6.35-22-generic).

---

