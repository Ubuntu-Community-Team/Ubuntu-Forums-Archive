---
title: "Can't update anymore. Help."
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by Mugsy323 on 2010-07-28
Whenever I run Update Manager (from both gui and cli), I get an error that prevents any updates (or new software) from installing. :(

Running UM from the desktop, I get "trying to recover from package failure", followed by an error message:
```
"Update complete. Not all changes or updates succeeded."
 Details report: "dpkg: unrecoverable fatal error, aborting: files list
 files for package 'libcompizconfig0' is missing final newline"
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:
```
I have tried deleting the downloaded packages using:
```
sudo rm-vf /var/lib/lists/*
```
and tried again from scratch, but always with the same result.

I have tried installing updates one at a time. No diff.

Not only can I not install any new updates (up to 19 now), but I can't install any new software either from the Ubuntu Software Center.

Help!

---

### Post by lechien73 on 2010-07-28
You can try to regenerate the offending list file by following the procedure at this link: [http://uri.tl/l](http://uri.tl/l)

Or, alternatively, replace your /var/lib/dpkg/info/libcompizconfig0.list file with the following:

```
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libcompizconfig0
/usr/share/doc/libcompizconfig0/TODO
/usr/share/doc/libcompizconfig0/AUTHORS
/usr/share/doc/libcompizconfig0/copyright
/usr/share/doc/libcompizconfig0/NEWS.gz
/usr/share/doc/libcompizconfig0/changelog.Debian.gz
/usr/share/compiz
/usr/share/compiz/ccp.xml
/usr/share/compizconfig
/usr/share/compizconfig/normal.profile
/usr/share/compizconfig/extra.profile
/usr/lib
/usr/lib/libcompizconfig.so.0.0.0
/usr/lib/compizconfig
/usr/lib/compizconfig/backends
/usr/lib/compizconfig/backends/libini.so
/usr/lib/compiz
/usr/lib/compiz/libccp.so
/etc
/etc/compizconfig
/etc/compizconfig/config
/usr/lib/libcompizconfig.so.0
```

---

### Post by linux18 on 2010-07-28
a fast general synaptic fix is:

```
  sudo apt-get -f || echo "ERROR 0"
 sudo rm /var/lib/apt/lists/partial/* || echo "ERROR 1: no partial packages - harmless error"
 sudo rm /var/cache/apt/*.bin || echo "ERROR 2"
 sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ')
 sudo apt-get clean || echo "ERROR 3"
 sudo apt-get autoclean || echo "ERROR 4"
 sudo apt-get autoremove || echo "ERROR 5"
 sudo apt-get update || echo "ERROR 6"
 sudo apt-get --fix-broken upgrade || echo "ERROR 7" 
```

---

### Post by Mugsy323 on 2010-07-28
> **lechien73 said:**
> You can try to regenerate the offending list file by following the procedure at this link: [http://uri.tl/l](http://uri.tl/l)
Thanks, I found my answer at the above link... so to speak. :)

I questioned whether my downloaded packages were in fact at the path another site told me to use:
```
sudo rm-vf /var/lib/lists/*
```

It seemed to me my packages were in the "/usr/bin/dpkg" folder, but Ubu showed no "dpkg" folder. Using the alternate path the poster gave at the bottom of his repost (saying his packages were in "/var/lib/dpkg/info"), I was able to delete the corrupted packages in question, allowing me to redownload and reinstall successfully.

Big thanks. (It's a pain in the butt that Ubu hides so many folders, preventing you from finding the paths you need. This has been a problem before.) Update Manager should be smart enough to know to delete corrupted packages. :(

---

### Post by lechien73 on 2010-07-28
Good stuff, thanks for the feedback.

If you get chance, please could you use the Thread Tools and mark the thread as "Solved"?

---

### Post by linux18 on 2010-07-28
if your problem is solved, mark it SOLVED

---

### Post by Mugsy323 on 2010-07-28
> **linux18 said:**
> if your problem is solved, mark it SOLVED
Sorry. Bit of a newbie to the forum. Not sure how to mark a thread as "Solved". Apologies.

(Found it. Done.)

---

