---
title: "Vmware Server 1.0.7 on new kernel 2.6.27-2"
date: 2008-08-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by daverab on 2008-08-30
Anyone having sucess running Vmware Server on the newest Ibex kernel? Normally with kernel updates I can just run the config.pl and get it up and running, but with this latest version (besides major nvidia driver issues) I can't get the vmmon kernel module to build.

Also, let me know if you know a way to get it working.

---

### Post by wilbur.harvey on 2008-08-31
Vmware Server 2.0 RC2, as well as the Vmware Workstation Beta v6.5 doesn't seem to work with the 2.6.27 kernel.
Hopefully someone will find a solution soon.

---

### Post by daverab on 2008-09-01
Yeah. I've tried Server 1.0.7 and Player 2.0.6 to no avail.

I have a feeling the change from 26 to 27 kernel wise is fairly big. Either that or they haven't tweaked the new kernel enough.

I've gone back to using the previous kernel, 2.6.26-5, and both vmware player and server works like it should and builds perfectly fine.

I know there's been a bug report filed by someone else as a general "This doesn't build" notification, so we'll see what happens. I just figure it's a bit too early in the 27 test and tweak process to rely on it.

---

### Post by reames on 2008-09-02
I've done some digging on this one.  Apparently the vmmon kernel module makes use of a deprecated API (kernel_thread) that was finally removed from 2.6.27.

There has been a note in "Documentation/feature-removal-schedule.txt" (kernel source tree) since 2.6.24 (at least).

    What: remove EXPORT_SYMBOL(kernel_thread)
    When: August 2006
    Files: arch/*/kernel/*_ksyms.c
    Check: kernel_thread
    Why: kernel_thread is a low-level implementation detail. Drivers should
    use the <linux/kthread.h> API instead which shields them from
    implementation details and provides a higherlevel interface that
    prevents bugs and code duplication
    Who: Christoph Hellwig <hch@lst.de>

The fun occurs when you realize that kthread uses task handles and kernel_thread uses PID's... which are used internally in the VMXLinuxState struct.

---

### Post by tmahmood on 2008-09-02
Anyone find a way to fix this? I've already edited the vmmon modules a little that solves 2 compilation error ... but there are one more 

and any-any patch does not works

---

### Post by reames on 2008-09-04
FYI, I threw something together here:

[https://bugs.launchpad.net/ubuntu/+bug/263837/comments/6](https://bugs.launchpad.net/ubuntu/+bug/263837/comments/6)

---

### Post by wilbur.harvey on 2008-09-06
The new VirtualBox [http://www.virtualbox.org/](http://www.virtualbox.org/) works fine with my Intrepid and kernel 2.6.27-2 (x64)

In addition, my special USB devices work which I was not able to make work with VMware.

The graphics performance of scrolling high resolution screens (2048x1536) seems better than in VMware.

I have only been using it for a day, and using VMware for several years, but VirtualBox seems to be a much better solution.

It is very easy to install and setup.

---

### Post by ntetreau on 2008-09-07
> **reames said:**
> FYI, I threw something together here:

[https://bugs.launchpad.net/ubuntu/+bug/263837/comments/6](https://bugs.launchpad.net/ubuntu/+bug/263837/comments/6)

Thanks reames for the patch, it doesn't apply cleanly on Wmware workstation 6.0.5 with this output:

```
patching file include/compat_semaphore.h
patching file include/x86paging.h
patching file linux/driver.c
Hunk #1 succeeded at 395 with fuzz 2 (offset -27 lines).
Hunk #2 succeeded at 1043 (offset -43 lines).
patching file linux/driver.h
Hunk #1 succeeded at 131 with fuzz 2 (offset 35 lines).
patching file linux/hostif.c
Hunk #7 succeeded at 2136 (offset 11 lines).
Hunk #8 succeeded at 3359 (offset -14 lines).
Hunk #9 succeeded at 3485 (offset -14 lines).
Hunk #10 succeeded at 3516 (offset -14 lines).
Hunk #11 FAILED at 3539.
Hunk #12 succeeded at 3651 (offset -14 lines).
Hunk #13 FAILED at 3663.
2 out of 13 hunks FAILED -- saving rejects to file linux/hostif.c.rej
patching file linux/vmhost.h
patching file linux/vmmonInt.h

```

with config failing at:

```
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
/tmp/vmware-config0/vmmon-only/linux/driver.c:171: error: unknown field &#8216;nopage&#8217; specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:172: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:175: error: unknown field &#8216;nopage&#8217; specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:176: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function &#8216;LinuxDriverPoll&#8217;:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1080: error: &#8216;VMXLinuxState&#8217; has no member named &#8216;fastClockThread&#8217;
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-2-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

```

I know you do not mean to update or support your patch, but nay help will be very appreciated!

As for virtualbox, it doesn't yes support iphone USB unfortunately, which is the reason why I use vmware...
Nic

---

### Post by reames on 2008-09-08
Can you get me a copy of your hostif.c and hostif.c.rej files?

---

### Post by ntetreau on 2008-09-11
> **reames said:**
> Can you get me a copy of your hostif.c and hostif.c.rej files?

I certainly, here they are!

---

### Post by SpUpUz on 2008-09-29
version 2.0 of vmware server released and now working ... only have a big problem using keyboard on the console -.- :|

---

### Post by azelter on 2008-10-10
Server 2 does indeed work. I am hoping a patch becomes available to make server 1 work though as I much prefer it.

---

### Post by billenbois on 2008-10-22
for vmware server 1  and workstation 5.5
(from the bug report)

[http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627](http://www.insecure.ws/2008/10/20/vmware-specific-specific-55x-and-kernel-2627)

---

### Post by azelter on 2008-10-22
Thanks very much for posting that billenbois. Worked fine and now I don't have to use sever 2.0 which I really do not like.

---

### Post by aldeby on 2008-10-24
VMware-Workstation-6.5.0-118166.x86_64.bundle
 and 
VMware-Workstation-6.5.0-118166.i386.bundle

versions are stated to be working fine with new linux 2.6.27 kernel.

Download those updated versions!

---

