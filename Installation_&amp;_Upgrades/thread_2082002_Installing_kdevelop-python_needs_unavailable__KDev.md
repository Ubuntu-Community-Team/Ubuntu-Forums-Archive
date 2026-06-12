---
title: "Installing kdevelop-python needs unavailable  KDevPlatformConfig.cmake"
date: 2012-11-08
forum: Installation &amp; Upgrades
---

### Post by alex2356 on 2012-11-08
Hi, 

I am stuck in the usual installation nightmare (Installing package A gives error; need to find out by try and error which package B to install; this gives error, need to find out by try and error which package C might be needed etc)
and to install the package "kdevelop-python-master" (of which I am not sure if this is the rigt package anyway, I am just looking how to indent a marked block of python code at once in kdevelop) with CMake I get the error:

```

Could not find a configuration file for package KDevPlatform.

  Set KDevPlatform_DIR to the directory containing a CMake configuration file
  for KDevPlatform.  The file will have one of the following names:

    KDevPlatformConfig.cmake
    kdevplatform-config.cmake
```The problem is that I either do not have those cmake files, or do now know where. I am able to find some KDevPlatformConfig.cmake.in files in the internet, but this does not help much. 

I would appreciate some help in either
- find the proper  KDevPlatformConfig.cmake or   kdevplatform-config.cmake files on my computer (12.04.1 LTS)
- download the poper configuration files
- what package to install with apt-get to solve this problem
- how to 'convert' the cmake.in file to a .cmake file
- or anything else that works. 


Thanks, 
  Alex

---

### Post by geralds on 2012-12-17
> **alex2356 said:**
> 
I would appreciate some help in either
...
- what package to install with apt-get to solve this problem


try
```
sudo apt-get install kdevplatform-dev
```
for the above error; however, to make it through the whole build, you'll likely need
```
sudo apt-get install kdevplatform-dev kdevelop-pg-qt kdevelop-dev
```

If cmake still complains, check if you have the correct version of kdevplatform as kdev-python currently requires 1.4 (which is included in *ubuntu 12.10.
hth

---

