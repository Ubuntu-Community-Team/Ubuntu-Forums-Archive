---
title: "2 issues after upgraded to Ubuntu 21.10"
date: 2021-10-30
forum: Installation &amp; Upgrades
---

### Post by nchh on 2021-10-30
Hi everyone,

I'd been using Ubuntu 20.04 installed (alongside with Windows 10 on physical PC) with no issue. 

A couple of days ago, I attempted to upgrade to Ubuntu 21.04 then 21.10. The upgrade process ran into some issue but finally got upgraded successfully to 21.10.

Since the upgrade, I've run into 2 issues:
* Could not run node or npm. If I run "node" or "npm" on Terminal, I got this error below. I tried to uninstall and reinstalled node but it didn't fix the issue. The current file I could find in my disk is libnode.so.72.
```
node: error while loading shared libraries: libnode.so.64: cannot open shared object file: No such file or directory
```

* See error message like below when writing files to my shared folder and searching on local drive
```
Error: Operation not supported (/run/user/1000/gvfs/smb-share:server=....."
```

```
$ sudo find / -name libmod2find: 

File system loop detected; &#8216;/run/timeshift/backup&#8217; is part of the same file system loop as &#8216;/&#8217;.
find: &#8216;/run/user/1000/doc&#8217;: Permission denied
find: &#8216;/run/user/1000/gvfs&#8217;: Permission denied
```


Everything else seems to be okay. 

When the upgrade seemed to be alright, I had to delete all Timeshift snapshots to free up some disk space for the additional updates and package installations. I hope it didn't cause the problem. 

I spent some time searching on the internet but couldn't find any solution that works. Please help! 

Thanks!

---

### Post by Impavidus on 2021-10-31
I don't know about node or npm, but it appears that the node on your system was compiled against libnode version 64. That's the version present on Ubuntu 20.04, but on 21.10 you get libnode version 72. If you install everything from the official Ubuntu repositories, you should get a version compiled for your release of Ubuntu. Apparently, node has some sort of package management system of its own, which may complicate matters. Somehow, your version of node and npm were not upgraded along with the rest of your system.

---

### Post by nchh on 2021-11-05
Yes, thank you mate! I thought so too, been searching around but couldn't find any way to fix it. Really frustrating, I need NodeJS to run my automated scripts.

---

