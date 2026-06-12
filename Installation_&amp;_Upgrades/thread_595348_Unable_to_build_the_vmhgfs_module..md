---
title: "Unable to build the vmhgfs module."
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by iXneonXi on 2007-10-28
Please help me install vmhgfs.
Windows XP Pro host running VMWare Workstation 6.0.2.
Xubuntu 7.10  guest.

I have already run vmware-install.pl
This is the result of: sudo vmware-config-tools.pl 

```

Trying to find a suitable vmhgfs module for your running kernel.

None of the pre-built vmhgfs modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmhgfs module for
your system (you need to have a C compiler installed on your system)? [yes] 
Extracting the sources of the vmhgfs module.

Building the vmhgfs module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmhgfs-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config2/vmhgfs-only/backdoor.o
  CC [M]  /tmp/vmware-config2/vmhgfs-only/backdoorGcc32.o
  CC [M]  /tmp/vmware-config2/vmhgfs-only/bdhandler.o
  CC [M]  /tmp/vmware-config2/vmhgfs-only/cpName.o
  CC [M]  /tmp/vmware-config2/vmhgfs-only/cpNameLinux.o
  CC [M]  /tmp/vmware-config2/vmhgfs-only/cpNameLite.o
  CC [M]  /tmp/vmware-config2/vmhgfs-only/dbllnklst.o
  CC [M]  /tmp/vmware-config2/vmhgfs-only/dentry.o
  CC [M]  /tmp/vmware-config2/vmhgfs-only/dir.o
  CC [M]  /tmp/vmware-config2/vmhgfs-only/eventManager.o
  CC [M]  /tmp/vmware-config2/vmhgfs-only/file.o
  CC [M]  /tmp/vmware-config2/vmhgfs-only/filesystem.o
/tmp/vmware-config2/vmhgfs-only/filesystem.c: In function ‘HgfsInitFileSystem’:
/tmp/vmware-config2/vmhgfs-only/filesystem.c:582: error: too few arguments to function ‘kmem_cache_create’
/tmp/vmware-config2/vmhgfs-only/filesystem.c:593: error: too few arguments to function ‘kmem_cache_create’
make[2]: *** [/tmp/vmware-config2/vmhgfs-only/filesystem.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmhgfs-only'
Unable to build the vmhgfs module.

The filesystem driver (vmhgfs module) is used only for the shared folder 
feature. The rest of the software provided by VMware Tools is designed to work 
independently of this feature.
If you wish to have the shared folders feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ] 


```

---

### Post by aNyBosZ on 2007-12-08
Instalación VmwareTools 6.0.2.59824 Ubuntu Desktop 7.10
------------------------------------------------------------------------
Bug fixed:

  CC [M]  /tmp/vmware-config3/vmhgfs-only/filesystem.o
/tmp/vmware-config3/vmhgfs-only/filesystem.c: En la función ‘HgfsInitFileSystem’:
/tmp/vmware-config3/vmhgfs-only/filesystem.c:582: error: muy pocos argumentos para la función ‘kmem_cache_create’
/tmp/vmware-config3/vmhgfs-only/filesystem.c:593: error: muy pocos argumentos para la función ‘kmem_cache_create’
make[2]: *** [/tmp/vmware-config3/vmhgfs-only/filesystem.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmhgfs-only] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [vmhgfs.ko] Error 2
make: se sale del directorio `/tmp/vmware-config3/vmhgfs-only'
Unable to build the vmhgfs module.


Software necesario
- sudo aptitude install build-essential linux-headers-$(uname -r)

vmwaretools
- cd /tmp
- tar -xzvf VMwareTools-6.0.2-59824.tar.gz
- cd vmware-tools-distrib/lib/modules/source
- cp vmhgfs.tar vmhgfs.tar.old
- tar xvf vmhgfs.tar
- cd vmhgfs-only
- chmod 644 compat_slab.h
- vi compat_slab.h
	Search->	#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 6, 22) || defined(VMW_KMEMCR_HAS_DTOR)
	Fix-> 	#if LINUX_VERSION_CODE <= KERNEL_VERSION(2, 6, 22) || defined(VMW_KMEMCR_HAS_DTOR)
	Save Chages
- chmod 444 compat_slab.h
- cd ..
- rm vmhgfs.tar
- tar cvf vmhgfs.tar vmhgfs-only
- cd /tmp/vmware-tools-distrib
- sudo ./vmware-install.pl

Enjoy!! 

--- by aNyBosZ ---

---

### Post by mhowellaz on 2008-01-05
Thank you, this fixed it for me. Perfect.

---

### Post by ambarishmalpani on 2008-01-07
Great instructions! Thank you so much!

I am particularly impressed by how precise you were about copying the tarball, then
making changes.....

Thanks again!
Regards,
Ambarish

---

### Post by frossm on 2008-01-20
Thank you so much aNyBosZ!

I was poking around and not really getting anywhere.  Much appreciated.

Frosty

---

### Post by elbowgeek on 2008-01-21
Many thanks for this info.  I got to the point at which I'm supposed to edit the file named compat_slab.h, but my directory doesn't seem to have that one.  It's got compat_version.h, but that seems to list mainly very kernels.  

Any ideas would be appreciated.

Many thanks

Dennis

---

### Post by aws.python.enthusiast on 2008-01-26
I am having a similar similar but not identical issue.

Have installed Ubuntu-7.10 as a VM under VMWare Server 1.0.4 build 56528.

While installing the VMWare tools, I too have a problem with the vmhgfs module.  However, the compile failure, in my case is in:

vmhgfs-only/driver.c:835:  In function HgfsInitializeNode - struct inode has no member named 'u'

When I follow the above steps, I do not find a compat_slab.h at all.  Instead I have a compact_sched.h and compat_version.h neither of which have any reference to the 2.6 kernel.

What am I missing here ??

---

### Post by elbowgeek on 2008-01-26
I struggled with this too.  I believe the _sched.h is the correct one.  I can only guess that it may have been changed by VMWare.

Best of luck with the installation

---

### Post by aws.python.enthusiast on 2008-01-26
But the compat_sched.h does not even reference the 2.6 kernel.

Can you post the changes you made ?

---

### Post by elbowgeek on 2008-01-26
Will do - I'm back at the computer on which I have the VM, so I'll get back atcha in a bit.

Cheers

---

### Post by aws.python.enthusiast on 2008-01-26
Never mind, I found the answer.  Take a look at the following article as it describes the issue I faced as well as the resolution

[http://kamilkisiel.blogspot.com/2007/11/installing-vmware-tools-on-kernel-2622.html](http://kamilkisiel.blogspot.com/2007/11/installing-vmware-tools-on-kernel-2622.html)

---

### Post by tallsandwich on 2008-02-15
Also works good for Ubuntu 64 server running on VMware 6 on Vista 32 on Dual Core Intel.

Thanks!

---

### Post by PS8 on 2008-03-08
Works like a charm. Thanks a Bunch. I somehow got another error (theme went very basic blue from the lovely red) in deamon tools but I guess a restart would solve it.

---

