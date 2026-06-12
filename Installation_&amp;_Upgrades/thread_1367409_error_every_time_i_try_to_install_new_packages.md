---
title: "error every time i try to install new packages"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by coloradolover on 2009-12-29
just installed ubuntu 9.10 on a compaq evo n610c laptop .. working out all the issues, 


one 

everytime i try to install a new package from the package manager i get the error

flash installer was the first try that this came up .. then tryed a few others and got the same error 


E: linux-image-2.6.31-16-generic: subprocess installed post-installation script returned error exit status 1
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured



two 

cant get wireless to work , tried the ' hardware drivers' and it says im not running an proprietary drivers 

i have a d-link airplus dwl-650 + wifi card

---

### Post by PlankEyeWilly on 2009-12-29
I am having similar issues with apt-get dist-upgrade:

user@ubuntu:/var/cache/apt$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.31-16-generic (2.6.31-16.53) ...
Internal Error: Could not find image (/boot/vmlinuz-2.6.31-16-generic)
dpkg: error processing linux-image-2.6.31-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up nvidia-185-kernel-source (185.18.36-0ubuntu9) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing nvidia-185-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.31-16-generic
 nvidia-185-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@ubuntu:/var/cache/apt$ 

Any ideas?

---

### Post by avtolle on 2009-12-29
Are either of you utilizing a separate boot partition that may, for whatever reason, i.e., nearly full? ```
df -h
```at the command line to check status of HDD partitions mounted on Ubuntu boot as to size and free space.

---

### Post by PlankEyeWilly on 2009-12-29
I am not.  This is a fresh install, and everything is on one partition.  Before I started getting this error I was trying to "activate" the NVIDIA drivers, but the laptop crashed during the install.

I have tried removing the files from cache, but that didnt make any difference either.

Thanks!

---

### Post by coloradolover on 2009-12-29
same here this is a fresh install .. trying to install compiz and same thing happen

i used a 30g hard drive full install ..

---

### Post by avtolle on 2009-12-29
Thought compiz was installed by default. 

Obviously, there was a problem with the kernel upgrade for both of you. Try, from the terminal, ```
sudo dpkg --configure -a
```and post back with any error messages.

---

### Post by PlankEyeWilly on 2009-12-29
user@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for user: 
user@ubuntu:~$

---

### Post by coloradolover on 2009-12-29
jay@jay-laptop:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.31-16-generic (2.6.31-16.53) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.31-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-16-generic; however:
  Package linux-image-2.6.31-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.16.29); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.31-16-generic
 linux-image-generic
 linux-generic

---

### Post by PlankEyeWilly on 2009-12-29
Mine originally had similar issues until I cleared the cache folder andeleted the files /boot/

---

### Post by coloradolover on 2009-12-29
how did you do that ? im lost here ..dont even know what that error meant

---

### Post by PlankEyeWilly on 2009-12-29
This is how i removed the downloaded files from cache, however it didnt really fix anything

```
cd /var/cache/apt/archives/
sudo rm *

```

---

### Post by PlankEyeWilly on 2009-12-29
OK.  I think I may have figured this out.  Bear with me, because I dont really know the "best" way to do things, but this seems to have fixed my issues.

First off I opened a terminal window and change my director to:
/var/lib/dpkg/info

then i looked for the files that I was getting the errors about.  In my case it was 'linux-headers-2.6.31-16 nvidia-settings linux-image-2.6.31-16-generic'. Doing an ls I looked for files with those names

```
ls | grep 2.6.31-16
ls | grp nvidia
```

I noticed that there were a few diff files for each problematic packagem, so I removed all of the files in question with the following:

```
sudo rm *2.6.31-16*
sudo rm nvidia-settings
```

When I ran apt-get dist-upgrade the errors were not there, but it also did not redownload the packges.  I had to do the following command to removed the package files, you would have to replace these package names with the ones you are experiencing trouble with.

```
sudo apt-get remove --purge linux-headers-2.6.31-16 nvidia-settings linux-image-2.6.31-16-generic

```

 and then this to install them

```
sudo apt-get -f install linux-headers-2.6.31-16 nvidia-settings linux-image-2.6.31-16-generic
```

So far everything seems to be ok.  Let me know how it goes for you.

--
Tommy

---

### Post by coloradolover on 2009-12-29
i didnt get past the first step... it gives me an error trying to get into that diretory

---

### Post by PlankEyeWilly on 2009-12-29
What error did you get?

What is your output from this:
```
cd /var/lib/dpkg/
ls
```

---

### Post by Cluster-Karl on 2009-12-31
PlankEyeWilly.

tnx alot, your advice cured the same bugs I encountered.
I wish u all a pleasant 2010.

---

### Post by Lytspeed on 2010-05-07
**PlankEyeWilly**

Thanks for your posts.  They helped me solve a similar problem with 2.16.31-14 kernel errors.

:KS

---

