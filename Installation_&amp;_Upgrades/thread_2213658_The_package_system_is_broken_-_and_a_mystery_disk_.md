---
title: "The package system is broken - and a mystery disk space shortage"
date: 2014-03-27
forum: Installation &amp; Upgrades
---

### Post by Sapient_Fridge on 2014-03-27
I've been using Ubuntu on and off in a virtual machine for a couple of years now (vmware, on Windows) for a bit of perl and image processing, but I'm not a heavy Linux user.  

Every now and then I run the update manager, and that has always worked up to now.  The problem is that last time I updated it said "The package system is broken". Ouch. 

The "Details" say:

The following packages have unmet dependencies:

linux-headers-generic: Depends: linux-headers-3.2.0-60-generic but it is not installed
linux-headers-generic-pae: Depends: linux-headers-3.2.0-60-generic-pae but it is not installed

I've tried doing this:

sudo apt-get clean
sudo apt-get update
sudo apt-get install -f

and get this output from the last of the above:

```

sapient@oranges:/$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-41-generic-pae linux-headers-3.2.0-41 linux-headers-3.2.0-41-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.2.0-60-generic linux-headers-3.2.0-60-generic-pae
The following NEW packages will be installed:
  linux-headers-3.2.0-60-generic linux-headers-3.2.0-60-generic-pae
0 upgraded, 2 newly installed, 0 to remove and 25 not upgraded.
3 not fully installed or removed.
Need to get 0 B/1,955 kB of archives.
After this operation, 22.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 1237385 files and directories currently installed.)
Unpacking linux-headers-3.2.0-60-generic (from .../linux-headers-3.2.0-60-generic_3.2.0-60.91_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-60-generic_3.2.0-60.91_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-60-generic/include/config/hid/acrux.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-60-generic/include/config/hid/acrux.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-60-generic-pae (from .../linux-headers-3.2.0-60-generic-pae_3.2.0-60.91_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-60-generic-pae_3.2.0-60.91_i386.deb (--unpack):
 error creating directory `./usr/src/linux-headers-3.2.0-60-generic-pae/include/config/hid': No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-60-generic_3.2.0-60.91_i386.deb
 /var/cache/apt/archives/linux-headers-3.2.0-60-generic-pae_3.2.0-60.91_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The obvious thing there is that something has run out of disk space.  The problem is that I can't work out what.  There seems to be lots of space:

```

df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        20G   12G  6.3G  66% /
udev            494M  4.0K  494M   1% /dev
tmpfs           201M  764K  200M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            501M  288K  501M   1% /run/shm

```

As a double check I created a 160M file under /usr/src and it worked fine.  

I'm at a loss as to what's going on. The system is working fine but I don't like not being able to update it any more, and I'm loathe to start again with a fresh installation as getting mySQL and apache configured was a real pain.  

I don't have any software from non-official repositories, or at least not as far as I remember.  This vm is pretty old, but updated on a regular basis to keep it current.

Anyone got any ideas?  What am I missing?

Cheers,
Sapient Fridge

---

### Post by westie457 on 2014-03-27
Welcome to the Forum.

You probably have run out of inodes, so before this gets too technical can you post the output of ```
sudo df -i
```

If you have run out of inodes do you have a lot of small files somewhere?

---

### Post by ibjsb4 on 2014-03-27
Do what it said.

```
sudo apt-get autoremove
```

Then update

---

### Post by Sapient_Fridge on 2014-03-27
sudo fdisk -i says "fdisk: invalid option -- 'i'"

but thanks for the hint:

```

sapient@oranges:/$ df -i
Filesystem      Inodes   IUsed  IFree IUse% Mounted on
/dev/sda1      1277952 1272026   5926  100% /
udev            126374     460 125914    1% /dev
tmpfs           128197     370 127827    1% /run
none            128197       4 128193    1% /run/lock
none            128197       7 128190    1% /run/shm

```

Looks like you are spot on with the inodes!  Any ideas on how to sort that out?

---

### Post by Sapient_Fridge on 2014-03-27
I've tried "sudo apt-get autoremove" it just told me to use 'apt-get -f install' to correct the unmet dependencies...

It looks like it's an inode problem.

---

### Post by ibjsb4 on 2014-03-27
Try step #6

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

### Post by westie457 on 2014-03-27
Sorry for the rubbish command, have edited it.

The suggested command from apt to run 'sudo apt-get autoremove' will free up some inodes, maybe even enough to complete the updates. However you will quickly use up the free inodes.

Let us see how many old kernels you have. ```
ls /usr/src
```

---

### Post by Sapient_Fridge on 2014-03-27
> **ibjsb4 said:**
> Try step #6

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

I think you have found the problem.  I have a vast number of old packages.  This is an old system which has been running for some years!

```

sapient@oranges:~$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9]
linux-headers-3.2.0-24
linux-headers-3.2.0-24-generic
linux-headers-3.2.0-24-generic-pae
linux-headers-3.2.0-25
linux-headers-3.2.0-25-generic
linux-headers-3.2.0-25-generic-pae
linux-headers-3.2.0-26
linux-headers-3.2.0-26-generic
linux-headers-3.2.0-26-generic-pae
linux-headers-3.2.0-27
linux-headers-3.2.0-27-generic
linux-headers-3.2.0-27-generic-pae
linux-headers-3.2.0-29
linux-headers-3.2.0-29-generic
linux-headers-3.2.0-29-generic-pae
linux-headers-3.2.0-30
linux-headers-3.2.0-30-generic
linux-headers-3.2.0-30-generic-pae
linux-headers-3.2.0-31
linux-headers-3.2.0-31-generic
linux-headers-3.2.0-31-generic-pae
linux-headers-3.2.0-32
linux-headers-3.2.0-32-generic
linux-headers-3.2.0-32-generic-pae
linux-headers-3.2.0-33
linux-headers-3.2.0-33-generic
linux-headers-3.2.0-33-generic-pae
linux-headers-3.2.0-34
linux-headers-3.2.0-34-generic
linux-headers-3.2.0-34-generic-pae
linux-headers-3.2.0-35
linux-headers-3.2.0-35-generic
linux-headers-3.2.0-35-generic-pae
linux-headers-3.2.0-36
linux-headers-3.2.0-36-generic
linux-headers-3.2.0-36-generic-pae
linux-headers-3.2.0-37
linux-headers-3.2.0-37-generic
linux-headers-3.2.0-37-generic-pae
linux-headers-3.2.0-38
linux-headers-3.2.0-38-generic
linux-headers-3.2.0-38-generic-pae
linux-headers-3.2.0-39
linux-headers-3.2.0-39-generic
linux-headers-3.2.0-39-generic-pae
linux-headers-3.2.0-40
linux-headers-3.2.0-40-generic
linux-headers-3.2.0-40-generic-pae
linux-headers-3.2.0-41
linux-headers-3.2.0-41-generic
linux-headers-3.2.0-41-generic-pae
linux-headers-3.2.0-43
linux-headers-3.2.0-43-generic
linux-headers-3.2.0-43-generic-pae
linux-headers-3.2.0-44
linux-headers-3.2.0-44-generic
linux-headers-3.2.0-44-generic-pae
linux-headers-3.2.0-45
linux-headers-3.2.0-45-generic
linux-headers-3.2.0-45-generic-pae
linux-headers-3.2.0-49
linux-headers-3.2.0-49-generic
linux-headers-3.2.0-49-generic-pae
linux-headers-3.2.0-51
linux-headers-3.2.0-51-generic
linux-headers-3.2.0-51-generic-pae
linux-headers-3.2.0-52
linux-headers-3.2.0-52-generic
linux-headers-3.2.0-52-generic-pae
linux-headers-3.2.0-53
linux-headers-3.2.0-53-generic
linux-headers-3.2.0-53-generic-pae
linux-headers-3.2.0-54
linux-headers-3.2.0-54-generic
linux-headers-3.2.0-54-generic-pae
linux-headers-3.2.0-55
linux-headers-3.2.0-55-generic
linux-headers-3.2.0-55-generic-pae
linux-headers-3.2.0-56
linux-headers-3.2.0-56-generic
linux-headers-3.2.0-56-generic-pae
linux-headers-3.2.0-57
linux-headers-3.2.0-57-generic
linux-headers-3.2.0-57-generic-pae
linux-headers-3.2.0-58
linux-headers-3.2.0-58-generic
linux-headers-3.2.0-58-generic-pae
linux-headers-3.2.0-59
linux-headers-3.2.0-59-generic
linux-headers-3.2.0-59-generic-pae
linux-image-2.6.38-11-generic
linux-image-3.0.0-17-generic
linux-image-3.2.0-24-generic
linux-image-3.2.0-25-generic
linux-image-3.2.0-26-generic
linux-image-3.2.0-27-generic
linux-image-3.2.0-29-generic
linux-image-3.2.0-30-generic
linux-image-3.2.0-31-generic
linux-image-3.2.0-32-generic
linux-image-3.2.0-33-generic
linux-image-3.2.0-34-generic
linux-image-3.2.0-35-generic
linux-image-3.2.0-36-generic
linux-image-3.2.0-37-generic
linux-image-3.2.0-38-generic
linux-image-3.2.0-39-generic
linux-image-3.2.0-40-generic
linux-image-3.2.0-41-generic
linux-image-3.2.0-43-generic
linux-image-3.2.0-44-generic
linux-image-3.2.0-45-generic
linux-image-3.2.0-49-generic
linux-image-3.2.0-51-generic
linux-image-3.2.0-52-generic
linux-image-3.2.0-53-generic
linux-image-3.2.0-54-generic
linux-image-3.2.0-55-generic
linux-image-3.2.0-56-generic
linux-image-3.2.0-57-generic
linux-image-3.2.0-58-generic
linux-image-3.2.0-59-generic

```

The only problem is that I need to fix the package system in order to remove the unused packages in order to get my inodes back.  Spot the problem:

```

sapient@oranges:~$ dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get -y purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-generic : Depends: linux-headers-3.2.0-60-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-60-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Rats.  I'll have a hunt around to see if I can find something else to delete.

---

### Post by ibjsb4 on 2014-03-27
Try removing just one

```
sudo apt-get remove --purge linux-headers-3.2.0-24 linux-headers-3.2.0-24-generic linux-headers-3.2.0-24-generic-pae
```

---

### Post by westie457 on 2014-03-27
This post has a workable solution. [http://ubuntuforums.org/showthread.php?t=2206534&p=12937031#post12937031](http://ubuntuforums.org/showthread.php?t=2206534&p=12937031#post12937031)

Change the given numbers to match the ones you have.

Then run 'sudo apt-get autoclean' to possibly remove some files that get left behind.

And as a precaution at the end run 'sudo update-grub

---

### Post by Sapient_Fridge on 2014-03-27
> **ibjsb4 said:**
> Try removing just one

```
sudo apt-get remove --purge linux-headers-3.2.0-24 linux-headers-3.2.0-24-generic linux-headers-3.2.0-24-generic-pae
```

Nope, same problem :( 

I've deleted several thousand files now (.e.g. thumbnails) but it doesn't seem to make any difference.

---

### Post by ibjsb4 on 2014-03-27
And post #10?

---

### Post by Sapient_Fridge on 2014-03-27
The combination of the "rm" suggestion from this page: [http://ubuntuforums.org/showthread.php?t=2206534&page=2&p=12937031#post12937031](http://ubuntuforums.org/showthread.php?t=2206534&page=2&p=12937031#post12937031)

Released enough inodes to allow the command from here to work: [http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

Package manager now working again.  Hurrah!  Thanks for all the help!

---

### Post by ibjsb4 on 2014-03-27
And welcome to the forums :)

---

