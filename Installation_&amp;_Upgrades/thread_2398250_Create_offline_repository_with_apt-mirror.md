---
title: "Create offline repository with apt-mirror"
date: 2018-08-09
forum: Installation &amp; Upgrades
---

### Post by UserJB on 2018-08-09
I'm trying to create an offline  repository for ubuntu version 16.04.  I followed the instructions here [https://www.tecmint.com/setup-local-repositories-in-ubuntu/](https://www.tecmint.com/setup-local-repositories-in-ubuntu/)  The title of that web-page is:[SIZE=2] "Setup Local Repositories with &#8216;apt-mirror&#8217; in Ubuntu and Debian Systems[/SIZE]".  I only deviated from the instructions at the end: it explains how to configure clients to use the local repository via ftp, and I want clients to use the repository directly from the local filesystem.  I think this should be an easy thing to do, but I'm stuck.

[FONT=arial]Here is what I've done so far: I downloaded  the entire repo with apt-mirror.  The local directory is: [/FONT]/usr/local/repo.  I added this line to /etc/apt/sources.list:

> deb file:/usr/local/repo/mirror/archive.ubuntu.com/ubuntu xenial main restricted universe multiverse  

I commented out all other lines in /etc/apt/sources.list.  I then ran "apt-get update"  as root, and I received a screenful of successful output, and I also received some errors and warning messages:

> 
File not found - /usr/local/repo/mirror/archive.ubuntu.com/ubuntu/dists/xenial/main/binary-i386/Packages (2: No such file or directory)
Reading package lists... Done                   
E: Failed to fetch file:/usr/local/repo/mirror/archive.ubuntu.com/ubuntu/dists/xenial/main/binary-i386/Packages  File not found - /usr/local/repo/mirror/archive.ubuntu.com/ubuntu/dists/xenial/main/binary-i386/Packages (2: No such file or directory)
E: Some index files failed to download. They have been ignored, or old ones used instead.



The file named Packages does not exist, and in fact, this directory "/usr/local/repo/mirror/archive.ubuntu.com/ubuntu/dists/xenial/main/binary-i386" does not exist. 

What am I doing wrong?  Did I add the incorrect directory name to  /etc/apt/sources.list?  Or should I have run another command?  Possibly [SIZE=2]dpkg-scanpackages[/SIZE]?  Why is it looking for i386 packages when I'm on a 64-bit machine?

---

### Post by UserJB on 2018-08-14
I have figured out how to solve this.  The problem is a combination of two things
     
[LIST]
[*]apt-mirror is not downloading deb files for the i386 architecture (I'm running this on a 64-bit CPU) 
[*]apt-get update' expects the i386 files to exist (or at least the i-386 Packages) 
[/LIST]
 So, my solution is to simply force apt-mirror to download the i-386 files (in addition to the amd64 files).

Previously, the /etc/apt/mirror.list file contained entries like this:
    ```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted universe multiverse
```
For each of those, I changed them to
    ```
deb-amd64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted universe multiverse
```
as well as a line for the i-386 files:
    ```
deb-i386 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted universe multiverse
```
I then ran 'apt-get update' with no error messages.

---

