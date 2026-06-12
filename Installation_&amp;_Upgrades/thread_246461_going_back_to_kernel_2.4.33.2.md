---
title: "going back to kernel 2.4.33.2"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by 3SV on 2006-08-29
Hi,

I have some problems on an amd pc. Ubuntu doesn't run good, but suse and fedora have the same problem. The PC hangs complete after a random time, i can only move my mouse when that happens en can't restart X or going to another console. Num lock gives no reaction at that time, i can only reset my box. I was trying different things but without success.
 
I have found that Damn small linux is running very well on that pc but i can't use that small distro for daily use. Because everything is going bad except damn small linux with kernel 2.4.x i want to install kernel 2.4.x into ubuntu. 

I have to compile the kernel by myself because the kernel is no longer available in the ubuntu repositories. I was trying to do that with the guide on [http://www.ubuntuforums.org/showthread.php?t=217657]("http://www.ubuntuforums.org/showthread.php?t=217657") made for installing kernel 2.6.17.7 but with replacing 2.6.17.7 with 2.4.33.2.
But this won't work i get  “error# error Sorry, your GCC is to recent for kernel 2.4.” I don't know witch version of GCC i need for installing a 2.4 kernel and don't know how to install an older version of GCC in general.

Can somebody help me with a good link of explanation on howto install an old kernel?

Thanks in advance.

---

### Post by helmet on 2006-08-31
you can change which gcc you are using

do 'cd /usr/bin' and all the gcc are in there. i don't know which one you are using/ the one you need but it might be 3.4 or 3.3 or even 2.95. just apt-get the needed version, and change the link in /usr/bin to point to the right one. 'update-alternatives gcc' might do the trick too but i've never tried it...

---

### Post by 3SV on 2006-09-04
OK, thank you for the help. I have changed that link and indeed that was solving the problem. 
I can now compile and install the kernel but I can't start with it. I got a Kernel panic immediately after starting the bootprocess.
I also compiled the newest version of the kernel from kernel.org and with that one I can boot, but I have problems with the new kernel like said in my previous post.

The error that I get when I boot with my self compiled 2.4.33.2 kernel:

kmod: failed to exec /sbin/modpobe -s -k ide-disk, errno = 2
Kernel panic: VFS : Unable to mount - root fs on 03:01

Wat is going wrong? 

thanks.

---

### Post by rick_1010 on 2006-09-30
I am in the process of doing the same thing that you are doing, I am changing to a 2.4.26 kernel because I need this to run OpenMosix (a clustering software) as that is the latest kernel for which there is a stable version of OpenMosix.

I will post the solution if I can figure it out, I was having the same problem with gcc but hopefully this will fix it for me.

---

### Post by rick_1010 on 2006-09-30
I just found this thread: [http://www.ubuntuforums.org/showthread.php?t=210320&highlight=suffix+operands+invalid+%60mov%27](http://www.ubuntuforums.org/showthread.php?t=210320&highlight=suffix+operands+invalid+%60mov%27) which deals with the same issue

---

