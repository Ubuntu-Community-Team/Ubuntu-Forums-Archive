---
title: "The installation or removal of a software package failed."
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by qasibeat on 2011-04-26
**Package Operation Failed**
The installation or removal of a software package failed.

```
installArchives() failed: (Reading database ...  (Reading database ...  5% (Reading database ... 10% (Reading database ... 15% (Reading database  ... 20% (Reading database ... 25% (Reading database ... 30% (Reading  database ... 35% (Reading database ... 40% (Reading database ...  45% (Reading database ... 50% (Reading database ... 55% (Reading  database ... 60% (Reading database ... 65% (Reading database ...  70% (Reading database ... 75% (Reading database ... 80% (Reading  database ... 85% (Reading database ... 90% (Reading database ...  95% (Reading database ... 100% (Reading database ... 125853 files and  directories currently installed.) 
Preparing to replace libc6-dev 2.12.1-0ubuntu6 (using .../libc6-dev_2.12.1-0ubuntu10.2_i386.deb) ... 
Unpacking replacement libc6-dev ... 
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid block type' 
dpkg-deb: subprocess <decompress> returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/libc6-dev_2.12.1-0ubuntu10.2_i386.deb (--unpack): 
 short read on buffer copy for backend dpkg-deb during `./usr/lib/xen/libc.a' 
Errors were encountered while processing: 
 /var/cache/apt/archives/libc6-dev_2.12.1-0ubuntu10.2_i386.deb 
Setting up libc6 (2.12.1-0ubuntu10.2) ... 
Generating locales... 
  en_AG.UTF-8... done 
  en_AU.UTF-8... done 
  en_BW.UTF-8... done 
  en_CA.UTF-8... done 
  en_DK.UTF-8... done 
  en_GB.UTF-8... done 
  en_HK.UTF-8... done 
  en_IE.UTF-8... done 
  en_IN.UTF-8... done 
  en_NG.UTF-8... done 
  en_NZ.UTF-8... done 
  en_PH.UTF-8... done 
  en_SG.UTF-8... done 
  en_US.UTF-8... done 
  en_ZA.UTF-8... done 
  en_ZW.UTF-8... done 
Generation complete. 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
```
i am trying to fix this problem on ubunto 10 10, but when it goes to repair, it gives the above error
please help me on this.

---

### Post by tommcd on 2011-04-27
What commands are you running when you get these errors?
Did you do a clean install of Ubuntu 10.10? Or was this a dist-upgrade from a previous Ubuntu install?
Are you using any third party repositories? This includes those all too problematic PPA repos.
Post your */etc/apt/sources.list*.
Also post the contents of any files in your */etc/apt/sources.d/* directory.
> **qasibeat said:**
> 
i am trying to fix this problem on ubunto 10 10, but when it goes to repair, it gives the above error
please help me on this.
What exactly have you done to try to fix this? 
Please provide as much detail as you can.
This looks a problem with upgrading **libc6**, which is a library that a great many things depend on.

And welcome to the Ubuntu forums!

---

