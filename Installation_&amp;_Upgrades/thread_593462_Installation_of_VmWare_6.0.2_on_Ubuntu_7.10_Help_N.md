---
title: "Installation of VmWare 6.0.2 on Ubuntu 7.10 Help Needed!!!"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by empeker on 2007-10-27
Hello Everyone!!

I'm trying to install VMware 6.0.2 Workstation on my Ubuntu 7.10. Have 2.6.22.14 Kernel.

So far, I found some patches, but did not work till now. 

Anybody out there, to help me to install VmWare.

Thx.
:KS

---

### Post by FredB on 2007-10-27
> **empeker said:**
> Hello Everyone!!

I'm trying to install VMware 6.0.2 Workstation on my Ubuntu 7.10. Have 2.6.22.14 Kernel.

So far, I found some patches, but did not work till now. 

Anybody out there, to help me to install VmWare.

Thx.
:KS

I am using this version of VMWare with Ubuntu 7.10 AMD64. Applied no patch. Just installed build-essential and xinetd.

Install works after that without problem.

What's happening ?

---

### Post by BaarLaar on 2007-10-27
I have the same problem. I have installed all but the VMWARE-INSTALL.PL doesnot run..

---

### Post by FredB on 2007-10-27
Try in a console :

```
sudo ./vmware-install.pl
```

What happens ?

---

### Post by empeker on 2007-10-27
FredB

Thx for your replies.

I've installed build-essentials xinetd before.

Here is the output of when vmware-config.pl runs after installation 

[COLOR="Red"]What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.22-14-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
/tmp/vmware-config0/vmmon-only/Makefile:90: *** Inappropriate build environment: you wanted to use gcc version 4.1.3 while kernel attempts to use gcc version 3.3.6.
/tmp/vmware-config0/vmmon-only/Makefile:92: *** For proper build you'll have to replace gcc -m32 with symbolic link to /usr/bin/gcc-4.1.  Stop.
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
[/COLOR]

---

### Post by FredB on 2007-10-28
?????

Looks like a conflict between two gcc versions.

What gcc version are you using.

What does gcc -v say ?

I'm kinda lost here !

---

### Post by BaarLaar on 2007-10-28
> **FredB said:**
> Try in a console :

```
sudo ./vmware-install.pl
```

What happens ?

Thanks, i will try tonight. I am now at work. I will let you know

---

### Post by BaarLaar on 2007-10-28
> **BaarLaar said:**
> Thanks, i will try tonight. I am now at work. I will let you know

Ok, it worked. I have installed the app and it is working fine. My fault was that I tried without the "./", or at least that is what they mentioned in another forum.

Why is this?

(I am a newbie in Linux)

---

