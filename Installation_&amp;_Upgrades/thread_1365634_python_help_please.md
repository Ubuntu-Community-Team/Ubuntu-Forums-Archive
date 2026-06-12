---
title: "python help please"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by teage3 on 2009-12-27
Hi, I am wanting to upgrade my python installation. Im not sure if it is possible to just upgrade it or do i have to uninstall my current installation then install a newer version.

---

### Post by gregsmith_to on 2009-12-27
Python allows multiple installation of different minor release versions (you can have 2.6.x and 2.5.x, but not 2.5.1 and 2.5.3). The libraries and add-ons are stored in $prefix/lib/python2.x

($prefix is /usr with the 'normal' install and /usr/local if you build python from source).

So if you 'upgrade' from 2.5 to 2.6 your 2.5 will still be there and any packages you added to 2.5 will probably need to be re-added to 2.6.

---

### Post by Cheesemill on 2009-12-27
Whatever you do; **don't uninstall python**.

If you try and remove python it will automatically remove all of the programs which depend on it, this is about 90% of your programs. Doing so is likely to completely brick your system.

You can have more than one version of python installed at the same time, so just install the newer version as well.

---

### Post by lukeiamyourfather on 2009-12-27
> **teage3 said:**
> Hi, I am wanting to upgrade my python installation. Im not sure if it is possible to just upgrade it or do i have to uninstall my current installation then install a newer version.

What version are you trying to install?

---

### Post by teage3 on 2009-12-28
3.1.1 is the version I would like to install. I have currently installed 2.6, Thanks for the info guys. I am glad i didnt uninstall my current. I had no idea it was running so much on my system. Thanks again.

---

### Post by lukeiamyourfather on 2009-12-28
> **teage3 said:**
> 3.1.1 is the version I would like to install. I have currently installed 2.6, Thanks for the info guys. I am glad i didnt uninstall my current. I had no idea it was running so much on my system. Thanks again.

This should get you going. Its already in the repositories. The fist command below will install it. Answer yes if asked.

```

lukeo@moore:~$ sudo apt-get install python3
[sudo] password for lukeo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python3-minimal python3.1 python3.1-minimal
Suggested packages:
  python3-doc python3-tk python3-profiler python3.1-doc python3.1-profiler
The following NEW packages will be installed:
  python3 python3-minimal python3.1 python3.1-minimal
0 upgraded, 4 newly installed, 0 to remove and 5 not upgraded.
Need to get 5,285kB of archives.
After this operation, 19.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic-updates/universe python3.1-minimal 3.1.1-0ubuntu5 [1,538kB]
Get:2 http://us.archive.ubuntu.com karmic-updates/universe python3.1 3.1.1-0ubuntu5 [3,726kB]                               
Get:3 http://us.archive.ubuntu.com karmic/universe python3-minimal 3.1-1ubuntu1 [10.0kB]                                    
Get:4 http://us.archive.ubuntu.com karmic/universe python3 3.1-1ubuntu1 [11.1kB]                                            
Fetched 5,285kB in 53s (99.5kB/s)                                                                                           
Selecting previously deselected package python3.1-minimal.
(Reading database ... 163011 files and directories currently installed.)
Unpacking python3.1-minimal (from .../python3.1-minimal_3.1.1-0ubuntu5_amd64.deb) ...
Selecting previously deselected package python3.1.
Unpacking python3.1 (from .../python3.1_3.1.1-0ubuntu5_amd64.deb) ...
Selecting previously deselected package python3-minimal.
Unpacking python3-minimal (from .../python3-minimal_3.1-1ubuntu1_all.deb) ...
Selecting previously deselected package python3.
Unpacking python3 (from .../python3_3.1-1ubuntu1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Setting up python3.1-minimal (3.1.1-0ubuntu5) ...

Setting up python3.1 (3.1.1-0ubuntu5) ...

Setting up python3-minimal (3.1-1ubuntu1) ...
Setting up python3 (3.1-1ubuntu1) ...
Processing triggers for menu ...
lukeo@moore:~$ python3
Python 3.1.1+ (r311:74480, Nov  2 2009, 15:45:00) 
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
lukeo@moore:~$ python
Python 2.6.4 (r264:75706, Dec  7 2009, 18:43:55) 
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
lukeo@moore:~$ 


```

That's the whole deal right there. Note at the bottom of the copied terminal session that "python" is still Python 2.6 so your system can run everything else, and "python3" is Python 3.1.1. Cheers!

---

