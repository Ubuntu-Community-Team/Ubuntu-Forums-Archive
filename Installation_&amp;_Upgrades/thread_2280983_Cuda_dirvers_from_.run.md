---
title: "Cuda dirvers from .run"
date: 2015-06-03
forum: Installation &amp; Upgrades
---

### Post by abraxas334 on 2015-06-03
The problem is the following. I want to install the CUDA driver 340 and CUDA toolkit v. 6.5 (there is a reason for not using 7.0) on a Ubuntu machine running 14.04. The machine has been upgraded to 14.04 from 12.04. 
When I try and run:
```

sudo bash cuda_6.5.14_linux_64.run

```

The installer starts fine, but eventually will break off and give me an install error log. Looking at the log, I find the following reason for the failure. 

*"The compiler used to compile the kernel (gcc 4.6) does not exactly match the current compiler (gcc 4.8).  The Linux 2.6 kernel module loader rejects kernel modules built with a version of gcc that does not exactly match that of the compiler used to build the running kernel."*

So I think understand what is going on and I checked my gcc version. It is gcc 4.8, so I used alternatives in this way that I have two gcc options
```

  Selection    Path              Priority   Status
------------------------------------------------------------
* 0            /usr/bin/gcc-4.8   2         auto mode
  1            /usr/bin/gcc-4.6   1         manual mode
  2            /usr/bin/gcc-4.8   2         manual mode

```
Now when I switch to version 4.6 I get the error that the installer cannot locate the kernel source. I don't really know what to do with that information. 

So instead I had a little look at my kernel.
```

:~$ uname -a
Linux machine5 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```
This tells me that I am still running the Kernel from the 12.04? Why was the kernel not updated to 14.04.2 kernel? I have another machine where I have done fresh install which gives me the following output:
```

Linux machine1 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```
On this machine I didn't have any problems with the CUDA toolkit installation using the runscript.
Then I thought maybe I can update the kernel and I tried to install the following package:
```

sudo apt-get install linux-image-generic-lts-utopic

```
after that I rebooted, and the filesystem rebooted into read only mode. After a second reboot it booted fine, but I ended up with the same old kernel as before. I don't really understand what is going, on or how to fix it. Ideally I would like to update to a more recent kernel but I would also be happy to just be able to run the script. Using .deb packages for the installation is not possible unfortunately.

---

