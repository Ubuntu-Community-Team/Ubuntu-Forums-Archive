---
title: "VMware server 2 on Ubuntu server 10.04"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by kgb_hc on 2011-06-02
Hi,
I have been trying to install VMware server for a few days now,  following various guides and using different patching solutions. But no  matter what I try, I always get some error message at the end. Right now  I get the error message described below.

I'm using the latest Ubuntu server LTS, 10.04.2, with Kernel  2.6.32-31-generic on x86_64. Trying to install VMWare server  2.0.2-203138. 

```
You have VMware Server archive:
        VMware-server-2.0.2-203138.x86_64.tar.gz
Checking for needed packages on Ubuntu
You do have the linux-headers-2.6.32-31-generic package...
You do have the build-essential package...
You do have the patch package...
Extracting the contents of VMware-server-2.0.2-203138.x86_64.tar.gz
Found .tar file for vmci module
Found .tar file for vmnet module
Found .tar file for vmmon module
Found .tar file for vsock module
Extracting .tar files in order to apply the patch...
Untarring /home/vm/vmware_server_package//vmware-server-distrib/lib/modules/source/vmci.tar
Untarring /home/vm/vmware_server_package//vmware-server-distrib/lib/modules/source/vmnet.tar
Untarring /home/vm/vmware_server_package//vmware-server-distrib/lib/modules/source/vmmon.tar
Untarring /home/vm/vmware_server_package//vmware-server-distrib/lib/modules/source/vsock.tar
Testing patch...
Creating some simlinks for the newer kernels...
ln: creating symbolic link `/usr/src/linux-headers-2.6.32-31-generic/include/linux/autoconf.h': File exists
ln: creating symbolic link `/usr/src/linux-headers-2.6.32-31-generic/include/linux/utsrelease.h': File exists
Applying patch...
Preparing new tar file for vmci module
Preparing new tar file for vmnet module
Preparing new tar file for vmmon module
Preparing new tar file for vsock module
Checking that the compiling will succeed...
Trying to compile vmci module to see if it works
Performing make in /home/vm/vmware_server_package//vmware-server-distrib/lib/modules/source/vmci-only
Using 2.6.x kernel build system.
Trying to compile vmnet module to see if it works
Performing make in /home/vm/vmware_server_package//vmware-server-distrib/lib/modules/source/vmnet-only
Using 2.6.x kernel build system.
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121:  warning: data definition has no type or storage class
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121:  warning: type defaults to âintâ in declaration of âDEFINE_SEMAPHOREâ
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/driver.c:121:  warning: parameter names (without types) in function declaration
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:82:  warning: type defaults to âintâ in declaration of âDEFINE_SEMAPHOREâ
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:82:  warning: parameter names (without types) in function declaration
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:  In function âVNetFilter_HandleUserCallâ:
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089:  error: âfilterIoctlSemâ undeclared (first use in this function)
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089:  error: (Each undeclared identifier is reported only once
/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089:  error: for each function it appears in.)
make[2]: *** [/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only/filter.o] Error 1
make[1]: *** [_module_/home/vm/vmware_server_package/vmware-server-distrib/lib/modules/source/vmnet-only] Error 2
make: *** [vmnet.ko] Error 2
There is a problem compiling the vmnet module after it was patched.  :(
```I'm using the same script and patch as this guy did:


> **karhukuoma said:**
> I'm using  raducotescu-vmware-server-linux-2.6.3x-kernel-f271f27.tar.gz with  updated vmware-server-2.0.2-203138-update.patch from this thread. What  could I've missed?

**Update**
##########
This has been fixed like this:
```

sudo su -
goto /usr/src/linux-headers-2.6.38-9-generic/include/linux
cat ../generated/utsrelease.h >> version.h
ln -s ../generated/autoconf.h

```kudos to [thingy@vmware-communities]("http://communities.vmware.com/message/1684660#1684660")

Also, a lot of guides tell me to use files in the   /usr/src/linux-headers-2.6.32-31-generic/generated/ directory but I   don't have that directory at all. 

Anyone have any ideas?

Thanks in advance!

---

### Post by kgb_hc on 2011-06-03
No one has any ideas? 



On a side note, why is my kernel 2.6.32-31-generic and not 2.6.32-31-server..?

---

### Post by anton7811 on 2011-06-06
I have the same issue.

I fixed patch for filter.c

FROM:
```

diff -Naurx '*.o' -x '*.cmd' -x '*.ko' '-x*.tar' '-x*.mod.c' vmware-server-distrib//lib/modules/source/vmnet-only/filter.c vmware-working//lib/modules/source/vmnet-only/filter.c
--- vmware-server-distrib//lib/modules/source/vmnet-only/filter.c   2009-10-20 18:43:25.000000000 -0700
+++ vmware-working//lib/modules/source/vmnet-only/filter.c  2011-05-01 16:44:33.485416859 -0700
@@ -76,7 +76,11 @@
 RuleSet *activeRule = NULL;   /* actual rule set for filter callback to use */

 /* locks to protect against concurrent accesses. */
-static DECLARE_MUTEX(filterIoctlSem);   /* serialize ioctl()s from user space. */
+//#if !defined(CONFIG_PREEMPT_RT)
+//static DECLARE_MUTEX(filterIoctlSem);   /* serialize ioctl()s from user space. */
+//#else
+static DEFINE_SEMAPHORE(filterIoctlSem);   /* serialize ioctl()s from user space. */
+//#endif
 /*
  * user/netfilter hook concurrency lock.
  * This spinlock doesn't scale well if/when in the future the netfilter

```TO(deleted comments for define):
```

diff -Naurx '*.o' -x '*.cmd' -x '*.ko' '-x*.tar' '-x*.mod.c' vmware-server-distrib//lib/modules/source/vmnet-only/filter.c vmware-working//lib/modules/source/vmnet-only/filter.c
--- vmware-server-distrib//lib/modules/source/vmnet-only/filter.c   2009-10-20 18:43:25.000000000 -0700
+++ vmware-working//lib/modules/source/vmnet-only/filter.c  2011-05-01 16:44:33.485416859 -0700
@@ -76,7 +76,11 @@
 RuleSet *activeRule = NULL;   /* actual rule set for filter callback to use */

 /* locks to protect against concurrent accesses. */
-static DECLARE_MUTEX(filterIoctlSem);   /* serialize ioctl()s from user space. */
+#if !defined(CONFIG_PREEMPT_RT)
+static DECLARE_MUTEX(filterIoctlSem);   /* serialize ioctl()s from user space. */
+#else
+static DEFINE_SEMAPHORE(filterIoctlSem);   /* serialize ioctl()s from user space. */
+#endif
 /*
  * user/netfilter hook concurrency lock.
  * This spinlock doesn't scale well if/when in the future the netfilter


```So installation continued until this:
```

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmnet-only'
make -C /lib/modules/2.6.32-32-preempt/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-32-preempt'
  CC [M]  /tmp/vmware-config1/vmnet-only/driver.o
/tmp/vmware-config1/vmnet-only/driver.c:121: warning: data definition has no type or storage class
/tmp/vmware-config1/vmnet-only/driver.c:121: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;DEFINE_SEMAPHORE&#8217;
/tmp/vmware-config1/vmnet-only/driver.c:121: warning: parameter names (without types) in function declaration
  CC [M]  /tmp/vmware-config1/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config1/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config1/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config1/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config1/vmnet-only/filter.o
  CC [M]  /tmp/vmware-config1/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config1/vmnet-only/smac_compat.o
  CC [M]  /tmp/vmware-config1/vmnet-only/smac.o
  CC [M]  /tmp/vmware-config1/vmnet-only/vnetEvent.o
  CC [M]  /tmp/vmware-config1/vmnet-only/vnetUserListener.o
  LD [M]  /tmp/vmware-config1/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "vnetStructureSemaphore" [/tmp/vmware-config1/vmnet-only/vmnet.ko] undefined!
  CC      /tmp/vmware-config1/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config1/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-32-preempt'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config1/vmnet-only'
Unable to make a vmnet module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config1/vmnet.o': -1 Unknown symbol in module
There is probably a slight difference in the kernel configuration between the 
set of C header files you specified and your running kernel.  You may want to 
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.


```Does anyone has any idea?

---

### Post by aznnico on 2011-06-15
*bump* I'm hoping for a solution as well.

---

### Post by earthgecko on 2011-06-21
**<SOLVED>** for me...

```
/usr/local/vmware-server/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: âfilterIoctlSemâ undeclared (first use in this function)
/usr/local/vmware-server/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: (Each undeclared identifier is reported only once
/usr/local/vmware-server/vmware-server-distrib/lib/modules/source/vmnet-only/filter.c:1089: error: for each function it appears in.)
make[2]: *** [/usr/local/vmware-server/vmware-server-distrib/lib/modules/source/vmnet-only/filter.o] Error 1
make[1]: *** [_module_/usr/local/vmware-server/vmware-server-distrib/lib/modules/source/vmnet-only] Error 2
make: *** [vmnet.ko] Error 2
There is a problem compiling the vmnet module after it was patched. :(
```

After encountering the same problem and following lots of different forum suggestions, etc I managed to mix and match up some of the varying methods and patch in place without @raducotescu's script.

However I recommend first trying ....

```
apt-get --reinstall install linux-headers-`uname -r`
```

And THEN use **release-1.5 NOT THE LATEST** and instructions as per [http://radu.cotescu.com/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/](http://radu.cotescu.com/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/) with the script.

If that does not work, then try the patch in place mashup - [http://www.of-networks.co.uk/miscellaneous/vmware-server-2.0.2-ubuntu-howto-with-vmnet.ko-error](http://www.of-networks.co.uk/miscellaneous/vmware-server-2.0.2-ubuntu-howto-with-vmnet.ko-error)

Hopefully that will help someone.

---

