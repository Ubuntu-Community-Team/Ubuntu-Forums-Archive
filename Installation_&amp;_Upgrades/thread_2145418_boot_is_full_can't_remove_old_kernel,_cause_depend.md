---
title: "/boot is full can't remove old kernel, cause dependencies of new failed install"
date: 2013-05-15
forum: Installation &amp; Upgrades
---

### Post by prokop1000 on 2013-05-15
Hello! distupdate failed due dependencies, cause /boot is full!
I found on the forum, how to remove old kernels, but when I want to remove it with purge, remove or autoremove, I got the following error 
```
sudo apt-get autoremove linux-image-2.6.32-28-generic-pae  
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic-pae : Depends: linux-image-3.2.0-41-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

How can I solve the problem ? 
thanks

---

### Post by Bashing-om on 2013-05-15
prokop1000; Hi ! Welcome to the forum >

There are solutions, and then there are solutions. Let's take a look and see why you think you are short of operating head space.
Post back the output of the following terminal command as it is useful for finding out which directories are using all your space...
```
 du -h --max-depth=1 | sort -hr
```

Once operating room is obtained, we can look at the other problems.[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by prokop1000 on 2013-05-15
Hi!

Thanks! 

```
df -h
```
```
Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/xxxxx-root       454G  404G   27G  94% /
udev                          872M  4.0K  872M   1% /dev
tmpfs                         352M   40M  313M  12% /run
none                          5.0M     0  5.0M   0% /run/lock
none                          880M     0  880M   0% /run/shm
cgroup                        880M     0  880M   0% /sys/fs/cgroup
/dev/mapper/xxxxxx_xxxxxxxx1  228M  221M     0 100% /boot
```

The command
```
du -h --max-depth=1 | sort -hr
```
output is:
```
418G    .
403G    ./home
11G     ./var
3.2G    ./usr
1.1G    ./lib
221M    ./boot
39M     ./run
14M     ./etc
9.4M    ./sbin
8.5M    ./bin
2.3M    ./build
436K    ./tmp
204K    ./srv
152K    ./opt
32K     ./root
16K     ./lost+found
8.0K    ./mnt
4.0K    ./selinux
4.0K    ./nonexistent
4.0K    ./media
4.0K    ./dev
4.0K    ./cdrom
0       ./sys
0       ./proc

```
inside /boot
```
du -h --max-depth=1 | sort -hr
```
output is:
```
221M    .4.0M    ./grub
12K     ./lost+found

```

These are the big ones:
```
-rw-r--r-- 1 root root 10955265 Apr 12  2011 initrd.img-2.6.32-28-generic-pae
-rw-r--r-- 1 root root 10990466 Aug  2  2012 initrd.img-2.6.32-41-generic-pae
-rw-r--r-- 1 root root 10990615 Sep  6  2012 initrd.img-2.6.32-42-generic-pae
-rw-r--r-- 1 root root 12775687 Dec 26 01:12 initrd.img-2.6.32-45-generic-pae
-rw-r--r-- 1 root root 17278812 Dec 26 01:29 initrd.img-3.2.0-35-generic-pae
-rw-r--r-- 1 root root 17289527 Feb  4 16:44 initrd.img-3.2.0-36-generic-pae
-rw-r--r-- 1 root root 17288634 Feb  4 17:05 initrd.img-3.2.0-37-generic-pae
-rw-r--r-- 1 root root 17279566 Mar 14 21:54 initrd.img-3.2.0-38-generic-pae
-rw-r--r-- 1 root root 17278603 Apr  5 01:33 initrd.img-3.2.0-39-generic-pae
-rw-r--r-- 1 root root 17320552 Apr  9 02:35 initrd.img-3.2.0-40-generic-pae


```



There are a few linux-image installed:
linux-image-2.6.32-28-generic-pae  linux-image-3.2.0-36-generic-pae
linux-image-2.6.32-41-generic-pae  linux-image-3.2.0-37-generic-pae
linux-image-2.6.32-42-generic-pae  linux-image-3.2.0-38-generic-pae
linux-image-2.6.32-45-generic-pae  linux-image-3.2.0-39-generic-pae
linux-image-3.2.0-35-generic-pae   linux-image-3.2.0-40-generic-pae

I think this might be the problem, am I wrong?

---

### Post by ibjsb4 on 2013-05-15
There are many ways to remove old kernels.  Seems everyone has a pet way to do it :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9)

My pet way is Synaptic Package Manager

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels+synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels+synaptic+package+manager&sa=Search&cof=FORID:9)

---

### Post by Bashing-om on 2013-05-15
prokop1000; Hey.

Yeah, your /boot partition is 100% full. Remove all but the latest 2 images and headers.
Terminal codes:
```

dpkg -l | grep linux-image-
sudo apt-get purge linux-image-2.6.32-{28,41,42,}-generic-pae
sudo apt-get purge linux-headers-2.6.32-{28,41,42,}-generic-pae
```
I would expect there to be many more kernel images/headers than this, remove all of them-less the two latest- using this format.

As you have encrypted file system, I can not really relate as to what is happening in the /root directory - 94% full -> no operating overhead there also - need to do some trimming for sure.
When all done with removals, run terminal command:
```
sudo apt-get --purge autoremove
```[INDENT=2]
regards

[/INDENT]

---

### Post by prokop1000 on 2013-05-23
Thank for the answer, but the problem is, that autoremove will fails cause of the dependency
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-pae : Depends: linux-image-3.2.0-41-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.

```
and not removing the old images. Since images are not removed -f install fails. catch 22

---

### Post by prokop1000 on 2013-05-23
solved it, by moving manually the files /boot/initrd.img-2.*-*-generic-pae to a temp directory, then run apt-get -f install. When it finished with success (since it has space now in /boot), I removed some images I did not move from /boot. After it I moved the files back to /boot from temp and removed it with as well with apt-get.

---

### Post by Bashing-om on 2013-05-25
[COLOR=#000000]prokop1000; Hi ;

I apologize for the delay in my response, focused on getting 13.04 minimal up and working. I have had and continue to have my difficulties.

Your solution is innovative. Shows good thinking on your part; Emphasizing there is more than one way to skin a cat ! I will keep that one in mind for future reference.
Pleased you have resolution. Please mark this thread as solved to aid others seeking a similar solution.
[INDENT=2]
keep on keep'n on <- regards Bashing-om

[/INDENT]


[/COLOR]

---

