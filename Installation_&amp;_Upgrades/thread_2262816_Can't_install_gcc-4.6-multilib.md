---
title: "Can't install gcc-4.6-multilib"
date: 2015-01-27
forum: Installation &amp; Upgrades
---

### Post by fox14 on 2015-01-27
I need to install gcc-4.6-multilib in order to run some software. However, I can't get it to install.  When I run "sudo aptitude install gcc-4.6-multilib" I get the following error:

The following NEW packages will be installed:
  gcc-4.6-multilib gcc-multilib{a} lib32gomp1{a} lib32quadmath0{a} 
  libc6-dev-i386{ab} 
0 packages upgraded, 5 newly installed, 0 to remove and 228 not upgraded.
Need to get 4,267 kB of archives. After unpacking 10.6 MB will be used.
The following packages have unmet dependencies:
 libc6-dev-i386 : Depends: libc6-i386 (= 2.15-0ubuntu10.10) but 2.19-0ubuntu6 is installed.
                  Depends: libc6-dev (= 2.15-0ubuntu10.10) but 2.19-0ubuntu6 is installed.
The following actions will resolve these dependencies:


     Keep the following packages at their current version:
1)     gcc-4.6-multilib [Not Installed]                   
2)     gcc-multilib [Not Installed]                       
3)     libc6-dev-i386 [Not Installed] 

-------------------------

What can I do to install gcc-4.6-multilib without killing my system?

---

### Post by ubfan1 on 2015-01-27
Try running
 sudo apt-get update 
  then try 
sudo apt-get install gcc-4.6-multilib

---

### Post by MAFoElffen on 2015-01-27
Please post the results of:
```

lsb_release -a
uname -a

```
Thinking the dependencies may be arch related... If so, I'll explain how to get around that. (That package needs both 64bit and 32bit dev libraries...)

---

