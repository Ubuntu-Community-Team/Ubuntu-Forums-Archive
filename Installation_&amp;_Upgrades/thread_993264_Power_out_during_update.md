---
title: "Power out during update"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by Evil Overlord on 2008-11-25
Ubuntu 8.10 fresh install on Gateway 7422GX laptop

Complete newb to Linux

Once I (somehow) got wireless to work...

I started the update manager, which downloaded 103 updates.  Once downloaded, I started installing.  Partway through, my laptop abruptly closed down (as it sometimes does - unrelated to OS).

I restarted, and opened up the update manager again.  It said I could install 39 updates (top of the list is libxml2-utils).  
- I click the 'Install Updates' button.
- Message box: An error occured:
   E: dpkg was interrupted, you must manually run 'dpkg --configure - a' to correct the problem.
   E: _cache->open() failed, please report.

- I open terminal, and type sudo dpkg --configure -a (because without sudo, I'm told the operation requires superuser privilege).
- I get: "Parse error, in file 'var/lib/dpkg/updates/0034' near line 1: newline in field name 'padding' "
- I tried running gedit on var/lib/dpkg/updates/0034, but gedit said it couldn't open the file.  (I tried various encodings).

Help!  I can't install any more updates.

---

### Post by taurus on 2008-11-25
Perhaps try running these.

```
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by Evil Overlord on 2008-11-25
> **taurus said:**
> Perhaps try running these.

```
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get update
```

On the 1st: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to crrect the problem.
2nd: as before, parse error...
3rd: I get a long list of Hit and Ign, and then the same error. "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to crrect the problem."

I found this referring to the same problem in 7.10: [https://lists.ubuntu.com/archives/xubuntu-devel/2008-January/004877.html](https://lists.ubuntu.com/archives/xubuntu-devel/2008-January/004877.html)

Note that trying gksudo says that --configure is an unrecognized option.

---

### Post by Evil Overlord on 2008-11-25
I deleted /var/lib/dpkg/updates/0034 and a file named tmp.i
and then typed sudo dpkg --configure -a

For better or worse, lots of things happened (including a fair number of error messages).  Still, it seemed a step forward.

As luck would have it, my laptop gave up again during this new operation. :-(  (it seems to overheat).

After restart, update manager still wouldn't work.  I tried 
sudo dpkg --configure -a
then your three commands again

then went back to update manager, which (after several error lines) proceeded to install the remainder of the packages.

After all this, things seem back to normal.

In brief, the solution was:
 delete the file referred to in the error message (in my case 0034) and tmp.i, both of which appeared corrupt.
Execute the following:
 sudo apt-get -f install
 sudo dpkg --configure -a
 sudo apt-get update

---

