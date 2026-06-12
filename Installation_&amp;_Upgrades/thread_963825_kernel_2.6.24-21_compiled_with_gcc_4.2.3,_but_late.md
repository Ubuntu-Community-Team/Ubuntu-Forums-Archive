---
title: "kernel 2.6.24-21 compiled with gcc 4.2.3, but latest stable gcc is 4.2.4"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by mykmelez on 2008-10-30
I'm running Ubuntu 8.04 with all recommended updates.

I recently applied the kernel update from 2.6.24-19 to 2.6.24-21, but when I try to reinstall VMware tools (I'm running Ubuntu in a VM on VMware Fusion 2), the installer complains that my kernel was built with gcc 4.2.3, while I have gcc 4.2.4 installed on the system.

I got both the kernel and gcc from the standard Ubuntu stable package repository.  Is it an Ubuntu bug that the latest available kernel was compiled with a different version of gcc than the latest available gcc?

And would it be problematic to reinstall VMware tools, which compiles kernel modules, using the newer version of gcc?  The tools installer strongly discourages it.

(Note: the gcc package reports its version as 4:4.2.3-1ubuntu6, but the gcc-4.2 package reports its version as 4.2.4-1ubuntu3.)

---

### Post by scotty64 on 2008-11-01
> **mykmelez said:**
> I'm running Ubuntu 8.04 with all recommended updates.

I recently applied the kernel update from 2.6.24-19 to 2.6.24-21, but when I try to reinstall VMware tools (I'm running Ubuntu in a VM on VMware Fusion 2), the installer complains that my kernel was built with gcc 4.2.3, while I have gcc 4.2.4 installed on the system.

I got both the kernel and gcc from the standard Ubuntu stable package repository.  Is it an Ubuntu bug that the latest available kernel was compiled with a different version of gcc than the latest available gcc?

And would it be problematic to reinstall VMware tools, which compiles kernel modules, using the newer version of gcc?  The tools installer strongly discourages it.

(Note: the gcc package reports its version as 4:4.2.3-1ubuntu6, but the gcc-4.2 package reports its version as 4.2.4-1ubuntu3.)

same problem here. The odd thing is that my laptop did not do any upgrade to 4.2.4, while the VM got this odd gcc today. And I do not now how to downgrade to the 4.2.3 version.

---

### Post by fractl on 2008-11-08
I've been trying to reinstall vmplayer on my upgraded Hardy Heron install (kernel = 2.6.24-21), and I get a related message:
```

Your kernel was built with "gcc" version "4.2.3", while you are
 trying to use "/usr/bin/gcc" version "4.2.4". This configuration
is not recommended and VMware Player may crash if you'll continue. 
Please try to use exactly same compiler as one used for building 
your kernel. Do you want to go with compiler "/usr/bin/gcc" 
version "4.2.4" anyway? [no] 
```

Choosing to override the suggested [no] appears to work on the face of it, but actually doesn't do much.  Every time I try to run vmplayer, I get the message:
```
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

```
And if I do that it leads me back to the first message.  How do people resolve this sort of thing? :confused:

Julie

---

### Post by shuki on 2008-11-13
i also having the same problem.
i just install a fresh copy of ubuntu, and tried to install the VMware server, but i've got same messages as my previous friends...

how do i downgrade to version 4.2.3 for a clean installation of VMware.

thanks.

---

### Post by iancairns on 2008-11-13
I upgraded VMware two days ago from 1.0.6 to 1.0.8 and configured ignoring the compiler mismatch. It's since been running continuously with no problems. YMMV but it seems to have worked for me.

   Ian

---

### Post by untill on 2008-11-17
Same problem here, with VMware Server 1.0.7 build-108231.

I suspect, however, that the changes ain't that big for an upgrade from 4.2.3 to 4.2.4, so I continued with a yes on the compilation question, which eventually succeeded. The VM works like a charm. \\:D/

---

### Post by yrrej on 2008-11-17
> **mykmelez said:**
> I'm running Ubuntu 8.04 with all recommended updates.

I recently applied the kernel update from 2.6.24-19 to 2.6.24-21, but when I try to reinstall VMware tools (I'm running Ubuntu in a VM on VMware Fusion 2), the installer complains that my kernel was built with gcc 4.2.3, while I have gcc 4.2.4 installed on the system.

I got both the kernel and gcc from the standard Ubuntu stable package repository.  Is it an Ubuntu bug that the latest available kernel was compiled with a different version of gcc than the latest available gcc?

And would it be problematic to reinstall VMware tools, which compiles kernel modules, using the newer version of gcc?  The tools installer strongly discourages it.

(Note: the gcc package reports its version as 4:4.2.3-1ubuntu6, but the gcc-4.2 package reports its version as 4.2.4-1ubuntu3.)

Sigh,

I have the same problem...I tried the compile of VMWare Tools ignoring the warning...
The compile failed and the old tools where gone.

I had a 2 week old backup that I used to replace the munged ubuntu vm and I decided
*not* to try updating  the Tools.

The old tools seem to be working...

I am running Ubuntu 8.04-1 under Fusion 2.1 on a Mac Book Pro.

I asked for assistance in how to revert back to an earlier version of gcc. ( A bit later
in the day than this thread) but have not received any responses...

Jerry

---

### Post by mykmelez on 2008-11-17
I decided to try compiling the tools anyway, and so far so good.  It's been about a week, and I haven't noticed additional instability.  gnome-terminal crashed a few times after the change, but it hasn't crashed again for days, so that may be unrelated.

---

### Post by tk471 on 2008-11-27
After reading this thread, I decided as well to go with the gcc 4.2.4.  I agree, so far seems to be running OK!

---

### Post by dfeathers on 2008-11-27
_How to downgrade from gcc-4.2.4 to gcc-4.2.3_

[LIST=1]
[*]Start Synaptic Package Manager
[*]'Search' for "gcc" (and you should find your installed version, 4.2.4-1ubuntu3)
[*]Click on "gcc-4.2" to highlight that package
[*]In the 'Package' menu, select 'Force Version ...'
[*]In the resulting dialog, select '4.2.3-2ubuntu7 (hardy)'
[*]Complete the package install using the forced version
[/LIST]

NOTE 1: I have **not** tried the above steps myself.

NOTE 2: I built the vmware-tools with gcc-4.2.4 and so far have had no difficulties.

---

### Post by red_oranda on 2008-11-27
```
Your kernel was built with "gcc" version "4.2.3", while you are
 trying to use "/usr/bin/gcc" version "4.2.4". This configuration
is not recommended and VMware Player may crash if you'll continue. 
Please try to use exactly same compiler as one used for building 
your kernel. Do you want to go with compiler "/usr/bin/gcc" 
version "4.2.4" anyway? [no] yes 
```

it works :)

---

### Post by fistcar on 2008-12-01
I ignored the compiler version error and said yes. Vmware is back up and running for me YMMV.

---

### Post by jhetrick62 on 2008-12-01
I agree, I ignored the warning also and answered "yes" and it worked.  When I attempted to "force package" to the older version, Synaptic complained that the resulting package was broken, so it would not perform the downgrade.

Jeff

---

### Post by demon55 on 2008-12-02
I have am having the same problem but when choosing the yes option I get this.

Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and 
VMware Player may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.2.4" anyway? [no] yes

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-22-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.24-22-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-22-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
In file included from include/asm/bitops.h:2,
                 from /tmp/vmware-config0/vmmon-only/./include/vcpuset.h:74,
                 from /tmp/vmware-config0/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config0/vmmon-only/common/vmx86.h:18,
                 from /tmp/vmware-config0/vmmon-only/common/hostif.h:18,
                 from /tmp/vmware-config0/vmmon-only/common/cpuid.c:14:
include/asm/bitops_32.h:9:2: error: #error only <linux/bitops.h> can be included directly
make[2]: *** [/tmp/vmware-config0/vmmon-only/common/cpuid.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


Any help would be much appreciated!

---

### Post by butteryak on 2008-12-30
I get the same error as "DEMON55"  anyone have any ideas?

thanks!

---

### Post by butteryak on 2008-12-30
nevermind.....I just found this,  got it working!

[http://www.nalinmakar.com/2008/05/05/vmware-player-on-ubuntu-804-hardy-heron/](http://www.nalinmakar.com/2008/05/05/vmware-player-on-ubuntu-804-hardy-heron/)

---

### Post by derekshaw on 2009-01-01
> **dfeathers said:**
> _How to downgrade from gcc-4.2.4 to gcc-4.2.3_

[LIST=1]
[*]Start Synaptic Package Manager
[*]'Search' for "gcc" (and you should find your installed version, 4.2.4-1ubuntu3)
[*]Click on "gcc-4.2" to highlight that package
[*]In the 'Package' menu, select 'Force Version ...'
[*]In the resulting dialog, select '4.2.3-2ubuntu7 (hardy)'
[*]Complete the package install using the forced version
[/LIST]

NOTE 1: I have **not** tried the above steps myself.


I tried this (and several variations thereon) and it does not work.

---

### Post by derekshaw on 2009-01-01
> **butteryak said:**
> I get the same error as "DEMON55"  anyone have any ideas?

thanks!

> **butteryak said:**
> nevermind.....I just found this,  got it working!

[http://www.nalinmakar.com/2008/05/05/vmware-player-on-ubuntu-804-hardy-heron/](http://www.nalinmakar.com/2008/05/05/vmware-player-on-ubuntu-804-hardy-heron/)

a far better solution in my experience is to get the new vmware player, currently at 2.5.1
[http://www.vmware.com/download/player/](http://www.vmware.com/download/player/)

---

### Post by prog101 on 2009-02-19
I too ignored the compiler version error and said yes. It works well for me.

---

