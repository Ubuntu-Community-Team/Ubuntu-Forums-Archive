---
title: "Anybody get vmware server running on karmic?"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by whoop on 2009-10-02
I get error when trying to run
```

sudo vmware-config.pl

```


Error:
```

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.31-11-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-11-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:31:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config0/vmmon-only/./include/vmware.h:38,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:99:
/tmp/vmware-config0/vmmon-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config0/vmmon-only/./include/vcpuset.h:103,
                 from /tmp/vmware-config0/vmmon-only/./include/modulecall.h:37,
                 from /tmp/vmware-config0/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:101:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:460:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:551:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:640:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:729:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:816:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:903:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:986:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1069:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1313:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1796:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config0/vmmon-only/./include/vm_asm_x86_64.h:39,
                 from /tmp/vmware-config0/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:103:
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h:486:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h:779:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h:820:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h:922:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config0/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:103:
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86_64.h:56:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:119:
/tmp/vmware-config0/vmmon-only/./common/hostif.h:53:7: warning: "WINNT_DDK" is not defined
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriverSyncCallOnEachCPU’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1423: error: too many arguments to function ‘smp_call_function’
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘euid’
/tmp/vmware-config0/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config0/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘fsuid’
/tmp/vmware-config0/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config0/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘egid’
/tmp/vmware-config0/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config0/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘fsgid’
/tmp/vmware-config0/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config0/vmmon-only/linux/driver.c:2007: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-11-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.

```

---

### Post by dmatrix on 2009-10-02
Virtualbox works good and in headless mode can replace vmware server.

---

### Post by carnagex420x on 2009-10-02
Im pretty sure you are using the wrong command for the install is all, what version are you using? vmware-config is executed by the vmware installer after the binaries are installed to build the kernel devices.

---

### Post by jms-ubuntu-en on 2009-10-02
I have same problem. Vmware was running fine in jaunty and after update to karmic there are obvoiusly no kernel modules available.

Trying to start vmware manually:
```
$ sudo /etc/init.d/vmware start
VMware Server is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/local/bin/vmware-config.pl.

```
and after running /usr/local/bin/vmware-config.pl as suggested I got same errors as whoop...

---

### Post by carnagex420x on 2009-10-02
Did you try a fresh install? If so it might not work with the running kernel for some reason. It is in testing too, I'll give it a try.

---

### Post by whoop on 2009-10-02
> **carnagex420x said:**
> Im pretty sure you are using the wrong command for the install is all, what version are you using? vmware-config is executed by the vmware installer after the binaries are installed to build the kernel devices.

I am not trying to install, I am trying to run. Had it running in jaunty after upgrade to karmic it stopped working. I always run vmware-config.pl after a kernel change, but this time it doesn't work...

---

### Post by carnagex420x on 2009-10-02
I can not get tools built in Karmic either. The problem is the running kernel. I'll try an earlier one

---

### Post by carnagex420x on 2009-10-02
tools wont build on 2.6.30-2 or on 2.6.31-11.

---

### Post by Wistful on 2009-10-03
[http://communities.vmware.com/thread/233294](http://communities.vmware.com/thread/233294)

The first post there says he managed to install it with kernel 2.6.31-10-generic and after having the issue stated there he solved it running a command.

EDIT: The How-To in the symbolik's blog(link in the post below) works fine for me.

---

### Post by carnagex420x on 2009-10-03
I followed the trail from the forum post and found this How-To:
[http://symbolik.wordpress.com/2009/09/21/howto-64-bit-kernel-2-6-31-and-vmware-server-2-0-1/](http://symbolik.wordpress.com/2009/09/21/howto-64-bit-kernel-2-6-31-and-vmware-server-2-0-1/)

Which links to another couple threads that actually have the "vmware-server.2.0.1_x64-modules-2.6.30.4-fix.patch":
[http://communities.vmware.com/thread/215985?start=15&tstart=0](http://communities.vmware.com/thread/215985?start=15&tstart=0)  -  newer
and
[http://communities.vmware.com/thread/221724?start=0&tstart=0](http://communities.vmware.com/thread/221724?start=0&tstart=0)  -  older

The patch consists of a .sh script and the .patch file to be applied. The 2 fixes are posted in the previous threads as attachments.

---

### Post by whoop on 2009-10-03
Aight, got it up and running again. Although running vmware-config.pl after applying the patch gave me a buck-load of warnings:


This one about a 1000 times (although it was mostly in the same header file).
```

/tmp/vmware-config1/vmnet-only/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined

```
And then this:
```

insserv: warning: script 'S01linux-restricted-modules-common' missing LSB tags and overrides
insserv: warning: script 'K20acpi-support' missing LSB tags and overrides
insserv: warning: current stop runlevel(s) (0 2 3 5 6) of script `vmware' overwrites defaults (0 6).
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites defaults (empty).
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwrites defaults (empty).
insserv: script vmware-autostart: service VMware already provided!
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: warning: script 'linux-restricted-modules-common' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: warning: current stop runlevel(s) (1) of script `policykit' overwrites defaults (empty).
insserv: warning: script 'usplash-down' missing LSB tags and overrides
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountnfs.sh' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `wpa-ifupdown' overwrites defaults (empty).
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: warning: script 'gdm' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: warning: script 'hal' missing LSB tags and overrides
insserv: warning: script 'usplash' missing LSB tags and overrides
insserv: script vmware-core: service VMware already provided!
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: script vmware-mgmt: service VMware already provided!
insserv: There is a loop between service rsyslog and hwclock if stopped
insserv:  loop involving service hwclock at depth 4
insserv:  loop involving service sysklogd at depth 3
insserv: There is a loop between service hwclock and sysklogd if started
insserv:  loop involving service sysklogd at depth 3
insserv:  loop involving service hwclock at depth 2
insserv:  loop involving service rsyslog at depth 1
insserv: There is a loop between service hwclock and sysklogd if stopped
insserv:  loop involving service rsyslog at depth 5
insserv: exiting without changing boot order!
In which directory do you want to keep your virtual machine files? 

```
But it's running....

---

### Post by carnagex420x on 2009-10-03
Good stuff!

---

### Post by carnagex420x on 2009-10-07
Was this 32 or 64 bit BTW?

---

### Post by boban on 2009-10-07
> **whoop said:**
> Aight, got it up and running again. Although running vmware-config.pl after applying the patch gave me a buck-load of warnings:



I had one more issue. I had to convert the script for patching with dos2unix command. And now it works like a charm...

---

### Post by whoop on 2009-10-07
> **carnagex420x said:**
> was this 32 or 64 bit btw?
64

---

### Post by whoop on 2009-10-07
> **boban said:**
> I had one more issue. I had to convert the script for patching with dos2unix command. And now it works like a charm...

Yeah me too... B.t.w. did you encounter all those warnings I got (look at my post above)?

---

### Post by zachtib on 2009-10-07
If you're trying to run VMware Server 1.x on a desktop system, I'd suggest you try the new VMware Player 3.0 RC: [http://communities.vmware.com/community/beta/player](http://communities.vmware.com/community/beta/player)

It's been overhauled with the ability to create and modify virtual machines to be more of a "Workstation-Lite"

VMware Server 1.x is pretty old at this point, and chances are you'll run into more issues as Ubuntu moves along.

---

### Post by whoop on 2009-10-07
> **zachtib said:**
> If you're trying to run VMware Server 1.x on a desktop system, I'd suggest you try the new VMware Player 3.0 RC: [http://communities.vmware.com/community/beta/player](http://communities.vmware.com/community/beta/player)

It's been overhauled with the ability to create and modify virtual machines to be more of a "Workstation-Lite"

VMware Server 1.x is pretty old at this point, and chances are you'll run into more issues as Ubuntu moves along.

Where using vmware server 2.0.1

---

### Post by zachtib on 2009-10-07
> **whoop said:**
> Where using vmware server 2.0.1

are you running it on a headless system, then?

---

### Post by whoop on 2009-10-07
> **zachtib said:**
> are you running it on a headless system, then?

yes

---

### Post by zachtib on 2009-10-07
> **whoop said:**
> yes

ah, carry on then ;)

I just still see a lot of people running Server 1.x in order to get something along the lines of Workstation functionality for free

---

### Post by bribera on 2009-10-27
FYI, once I got server running (xubuntu, x86_64) I encountered the GTK mouse grab/ungrab issues described (and fixed!) here:

[http://ubuntuforums.org/showthread.php?p=8177063](http://ubuntuforums.org/showthread.php?p=8177063)

---

### Post by carnagex420x on 2009-10-28
nice. i still cant get tools installed thou.

---

