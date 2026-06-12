---
title: "The program 'apt-get' is not currently installed"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by Huwawa on 2007-05-06
I was trying to install the Kubuntu Packages over an existing installation, but the installer synaptic crashed midway through the process. 
Now when I boot up, I get the message in the title(" The program 'apt-get' is not currently installed"). Could someone please tell me what files to post? I can access the filesystem easily. Thanks to anyone who helps!

---

### Post by Big Ed on 2007-05-06
> **Huwawa said:**
> I was trying to install the Kubuntu Packages over an existing installation, but the installer synaptic crashed midway through the process. 
Now when I boot up, I get the message in the title(" The program 'apt-get' is not currently installed"). Could someone please tell me what files to post? I can access the filesystem easily. Thanks to anyone who helps!

Hmm, that's not good.  Do you still have aptitude?  It does much the same job as apt-get.

On my system I have:

me@my-desktop:/etc/apt$ ls -l /usr/bin/apt*
-rwxr-xr-x 1 root root   60888 2007-03-14 13:43 /usr/bin/apt-cache
-rwxr-xr-x 1 root root   21552 2007-03-14 13:43 /usr/bin/apt-cdrom
-rwxr-xr-x 1 root root   11696 2007-03-14 13:43 /usr/bin/apt-config
-rwxr-xr-x 1 root root   24776 2007-03-14 13:43 /usr/bin/apt-extracttemplates
-rwxr-xr-x 1 root root  198392 2007-03-14 13:43 /usr/bin/apt-ftparchive
-rwxr-xr-x 1 root root  141856 2007-03-14 13:43 /usr/bin/apt-get
-rwxr-xr-x 1 root root 2713072 2007-02-26 12:03 /usr/bin/aptitude
-rwxr-xr-x 1 root root    2230 2007-03-14 13:42 /usr/bin/apt-key
-rwxr-xr-x 1 root root    2162 2007-03-14 13:42 /usr/bin/apt-mark
-rwxr-xr-x 1 root root   31768 2007-03-14 13:43 /usr/bin/apt-sortpkgs
me@my-desktop:/etc/apt$ 

Ed

---

### Post by Huwawa on 2007-05-07
It looks like it:
```
-rwxr-xr-x 1 root root   55384 2007-03-14 17:44 /usr/bin/apt-cache
-rwxr-xr-x 1 root root   18504 2007-03-14 17:44 /usr/bin/apt-cdrom
-rwxr-xr-x 1 root root    9236 2007-03-14 17:44 /usr/bin/apt-config
-rwxr-xr-x 1 root root   21124 2007-03-14 17:44 /usr/bin/apt-extracttemplates
-rwxr-xr-x 1 root root  199160 2007-03-14 17:44 /usr/bin/apt-ftparchive
-rwxr-xr-x 1 root root  137676 2007-03-14 17:44 /usr/bin/apt-get
-rwxr-xr-x 1 root root 2572976 2007-02-26 15:51 /usr/bin/aptitude
-rwxr-xr-x 1 root root    2230 2007-03-14 17:44 /usr/bin/apt-key
-rwxr-xr-x 1 root root    2162 2007-03-14 17:44 /usr/bin/apt-mark
-rwxr-xr-x 1 root root   27544 2007-03-14 17:44 /usr/bin/apt-sortpkgs

```

This makes it even weirder..

---

### Post by ionel on 2007-05-07
I had the same problem and I fix that by changing  in /etc/fstab UID numbers with device name 
before
```
# <file system> <mount point>   <type>       <options>                       <dump>  <pass>
proc            /proc             proc        defaults                         0       0
UID="numbers"       /                 ext3        defaults,errors=remount-ro       0       1
```
after

```
# <file system> <mount point>   <type>       <options>                       <dump>  <pass>
proc            /proc             proc        defaults                         0       0
/dev/sda1       /                 ext3        defaults,errors=remount-ro       0       1

```

---

### Post by Huwawa on 2007-05-07
Thanks! That solved that one. But now I have another issue.. :( 
I get a blank screen with a blinking underscore.:confused: 
Do you have any idea about this?

---

