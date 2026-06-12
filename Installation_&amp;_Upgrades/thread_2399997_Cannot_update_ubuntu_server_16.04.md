---
title: "Cannot update ubuntu server 16.04"
date: 2018-09-01
forum: Installation &amp; Upgrades
---

### Post by data-com on 2018-09-01
Hi there!

I have problem with updating 16.04 ubbuntu server. This is the probelm: 

```
Hit:1 [http://si.archive.ubuntu.com/ubuntu](http://si.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://si.archive.ubuntu.com/ubuntu](http://si.archive.ubuntu.com/ubuntu) xenial-updates InRelease [109 kB]
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [107 kB]
Hit:4 [http://si.archive.ubuntu.com/ubuntu](http://si.archive.ubuntu.com/ubuntu) xenial-backports InRelease                                                      
Get:5 [http://dl.hhvm.com/ubuntu](http://dl.hhvm.com/ubuntu) xenial InRelease [2,411 B]                                
Get:6 [https://dl.hhvm.com/ubuntu](https://dl.hhvm.com/ubuntu) xenial InRelease [2,411 B]    
Get:7 [https://dl.hhvm.com/ubuntu](https://dl.hhvm.com/ubuntu) xenial/main amd64 Packages [2,243 B]
Get:8 [http://dl.hhvm.com/ubuntu](http://dl.hhvm.com/ubuntu) xenial/main amd64 Packages [2,243 B]
Fetched 225 kB in 0s (279 kB/s)                            
Reading package lists... Done
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.hhvm.com/ubuntu xenial InRelease' doesn't support architecture 'i386'
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'https://dl.hhvm.com/ubuntu xenial InRelease' doesn't support architecture 'i386'
E: Failed to stat /var/lib/apt/lists/partial/dl.hhvm.com_ubuntu_dists_xenial_InRelease - pkgAcqTransactionItem::TransactionState-stat (2: No such file or directory)
E: Failed to stat /var/lib/apt/lists/partial/dl.hhvm.com_ubuntu_dists_xenial_main_binary-amd64_Packages - pkgAcqTransactionItem::TransactionState-stat (2: No such file or directory)
W: Duplicate sources.list entry [https://dl.hhvm.com/ubuntu](https://dl.hhvm.com/ubuntu) xenial Release
```

Can you help me solve it? 

Kind Regards!

Jus Kondic

---

### Post by TheFu on 2018-09-01
Is the HDD/storage full?

The easy answer is to wait a day or 2 and try again.
To troubleshoot, it is common to copy the error message, remove things that are only for your specific machine and google the error.   The first link returned for me with the error was : [https://askubuntu.com/questions/775784/error-e-failed-to-stat-var-lib-apt-lists-partial-while-update-ubuntu-16-04](https://askubuntu.com/questions/775784/error-e-failed-to-stat-var-lib-apt-lists-partial-while-update-ubuntu-16-04) with a possible solution.  AskUbuntu.com is a reputable site.

```
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade
```

It just might work.

---

