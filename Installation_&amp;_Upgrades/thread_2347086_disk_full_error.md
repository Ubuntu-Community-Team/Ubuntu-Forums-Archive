---
title: "disk full error"
date: 2016-12-21
forum: Installation &amp; Upgrades
---

### Post by gfat2016 on 2016-12-21
Hello, 
i want to do updates but it seems like my disk is full, I tried sudo apt-get install -f but it gave me the following output:   
[http://paste.ubuntu.com/23664944/](http://paste.ubuntu.com/23664944/)

df gives this output :
[http://paste.ubuntu.com/23664953/](http://paste.ubuntu.com/23664953/)

sudo fdisk -l gives this:
[http://paste.ubuntu.com/23664960/](http://paste.ubuntu.com/23664960/)

ls /usr/src output :
[http://paste.ubuntu.com/23664964/](http://paste.ubuntu.com/23664964/)


help please !

---

### Post by papibe on 2016-12-21
Hi gfat2016.

The root partition is getting full, but it seems to be some space. I wonder if there are inodes available.

Could you post the output of these 2 commands:
```
df -h

df -hi
```
Regards.

---

### Post by oldfred on 2016-12-21
Did you run the suggested:

sudo apt autoremove


And you have a lot of very old kernels. Is this an upgrade, that you had not housecleaned before upgrade?
The old kernels may not even be in dpkg anymore. But always best to removes with dpkg if possible as you have not just kernel, but .deb and other files that get removed normally when correctly housecleaned.

I used to use synaptic but with 16.04, it will keep only two kernels if you run the autoremove or have auto updates set to on.
 Determine your current kernel:
uname -a
-s is similate so you can review first:
sudo apt-get -s autoremove
sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521) 

      
 Use dpkg -S to see which .dkms files were not placed by the package manager
dpkg -S /full/path/to/file
Only use rm on files not in dpkg 
   kernel house clean
/usr/src/*
[http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this](http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this) 
   dpkg -S /lib/modules | sed s/:.\*//
uname --kernel-release
 Did you also check /var/cache/apt/archives? You may have the old .deb's taking up space.
 /var/cache/apt/archives

---

### Post by gfat2016 on 2016-12-21
```
df -h 
```
output : 
```

Filesystem      Size  Used Avail Use% Mounted on
udev            1,9G     0  1,9G   0% /dev
tmpfs           384M   12M  373M   3% /run
/dev/sda5        20G   16G  3,3G  83% /
tmpfs           1,9G  3,1M  1,9G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           1,9G     0  1,9G   0% /sys/fs/cgroup
/dev/sda6       133G   44G   83G  35% /home
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           384M  108K  383M   1% /run/user/1001 
```


```
 df -hi
```
output 
```

Filesystem     Inodes IUsed IFree IUse% Mounted on
udev             474K   582  474K    1% /dev
tmpfs            479K   854  479K    1% /run
/dev/sda5        1,3M  1,3M  2,6K  100% /
tmpfs            479K    17  479K    1% /dev/shm
tmpfs            479K     6  479K    1% /run/lock
tmpfs            479K    18  479K    1% /sys/fs/cgroup
/dev/sda6        8,5M   80K  8,4M    1% /home
cgmfs            479K    14  479K    1% /run/cgmanager/fs
tmpfs            479K    45  479K    1% /run/user/1001 
```


Regards

---

### Post by DuckHook on 2016-12-21
Yup. You were out of *inodes*. Since some space appears to have been freed up between first and latest posts, I assume that you deleted some files. Please answer *oldfred*'s question: did you run autoremove?

Now try rebooting and afterward run:```
df -hi
```

---

### Post by papibe on 2016-12-21
Yes, out of inodes as DuckHook mentioned it.

I don't think you'll be able to run any apt or dpkg command, because you can't create temp files.

The way I've solved it in the past is to delete headers manually (see [here]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1089195")). The key is select non used, old headers. For instance:
```
$ uname -a
Linux vaughan 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

$ cd /usr/src

$ ls -1
linux-headers-4.4.0-34
linux-headers-4.4.0-34-generic
linux-headers-4.4.0-36
linux-headers-4.4.0-36-generic
linux-headers-4.4.0-38
linux-headers-4.4.0-38-generic
linux-headers-4.4.0-43
linux-headers-4.4.0-43-generic
linux-headers-4.4.0-51
linux-headers-4.4.0-51-generic
linux-headers-4.4.0-57
linux-headers-4.4.0-57-generic

```
Then in my case, yours might be different, I'm using 4.4.0-57-generic, so I 'can'. without mayor consequences, delete say 34 to 36 (leaving the last 4 headers):
```
sudo rm -rf linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic linux-headers-4.4.0-36 linux-headers-4.4.0-36-generic
```
Once you delete those directories, you should free enough inodes to be able to clean the house:
```
sudo apt-get clean

sudo apt-get autoclean

sudo apt-get autoremove

```

Hope it helps. Let us know how it goes.
Regards.

---

