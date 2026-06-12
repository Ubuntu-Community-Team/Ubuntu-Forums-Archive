---
title: "404 Fetching Error when trying to update xubuntu 14.04 to 16.04"
date: 2017-02-24
forum: Installation &amp; Upgrades
---

### Post by vbmacit on 2017-02-24
when I use this command sudo do-release-upgrade I always get the error which is given below

```
Err http://us.archive.ubuntu.com xenial/universe Sources                                                                                            

Err http://us.archive.ubuntu.com xenial/universe amd64 Packages                                                                                     

Err http://us.archive.ubuntu.com xenial/universe i386 Packages                                                                                      

Err http://us.archive.ubuntu.com xenial/universe Sources                                                                                            
  404  Not Found [IP: 91.189.91.26 80]                                                                                                              
Err http://us.archive.ubuntu.com xenial/universe amd64 Packages                                                                                     
  404  Not Found [IP: 91.189.91.26 80]                                                                                                              
Err http://us.archive.ubuntu.com xenial/universe i386 Packages                                                                                      
  404  Not Found [IP: 91.189.91.26 80]                                                                                                              
Fetched 2.874 kB in 6s (0 B/s)                                                                                                                      

Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

W:Failed to fetch 
http://us.archive.ubuntu.com/ubuntu/dists/xenial/universe/source/Sources 
404 Not Found [IP: 91.189.91.26 80] 
, W:Failed to fetch 
http://us.archive.ubuntu.com/ubuntu/dists/xenial/universe/binary-amd64/Packages 
404 Not Found [IP: 91.189.91.26 80] 
, W:Failed to fetch 
http://us.archive.ubuntu.com/ubuntu/dists/xenial/universe/binary-i386/Packages 
404 Not Found [IP: 91.189.91.26 80] 
, E:Some index files failed to download. They have been ignored, or 
old ones used instead. 
```

---

### Post by #&amp;thj^% on 2017-02-24
The simplest solution is to do the following two steps:

   1. Backup your sources list
 ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

```
    Open the sources file** /etc/apt/sources.list** and rename all the instances of "us.archive" or archive in

    **[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)**

    to

  ```
  http://old-releases.ubuntu.com/ubuntu/
```

    Also do the same for all the ubuntu.com xenial entry's.


    Run:
 ```
sudo apt update ##after doing the above.
```

That "should" fix the issue.

---

