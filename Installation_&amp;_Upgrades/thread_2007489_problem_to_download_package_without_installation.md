---
title: "problem to download package without installation"
date: 2012-06-20
forum: Installation &amp; Upgrades
---

### Post by masuch on 2012-06-20
Hi,

I would like to download package without installation:
sudo apt-get source libc6-dev-i386 --download-only
As you can see from the following some magic decision has been made and it decided to download different package:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'eglibc' as source package instead of 'libc6-dev-i386'
Need to get 25.3 MB of source archives.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main eglibc 2.15-0ubuntu10 (dsc) [5,826 B]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main eglibc 2.15-0ubuntu10 (tar) [23.5 MB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main eglibc 2.15-0ubuntu10 (diff) [1,821 kB]                                                                                                                     
Fetched 25.3 MB in 45s (551 kB/s)                                                                                                                                                                                
Download complete and in download only mode



I would like to really download that specific package ?
How to force it by apt-get command or is it bug ?

thank you,
kind regards,
M.

---

