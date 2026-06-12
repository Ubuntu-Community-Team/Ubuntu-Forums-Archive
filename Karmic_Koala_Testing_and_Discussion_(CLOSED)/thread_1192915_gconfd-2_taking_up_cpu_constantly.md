---
title: "gconfd-2 taking up cpu constantly"
date: 2009-06-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yoasif on 2009-06-20
Anyone notice that gconfd-2 is taking up 10-15% of the cpu constantly, never stopping?

I'm on a laptop that likes to die when it gets too hot, and this is causing my laptop to get hot -- i'm afraid it's going to shut off unexpectedly. 

any ideas what the issue might be?

---

### Post by mbeichorn on 2009-06-22
I can confirm this problem on my Thinkpad X61t. It registers as 10% all of the time, but stopping it results in cpu idle going from 60% to 8%.

---

### Post by mbeichorn on 2009-06-22
Filed bug report, please append more data or just click this affects me too.
[https://bugs.launchpad.net/ubuntu/+bug/390733](https://bugs.launchpad.net/ubuntu/+bug/390733)

---

### Post by ronacc on 2009-06-22
just for info I am not seeing this on my 64bit desktop .

---

### Post by scradock on 2009-06-22
> **ronacc said:**
> just for info I am not seeing this on my 64bit desktop .
Confirm this observation on AMD64/64-bit system - gconfd-2 is running at 0% cpu utilisation.

---

### Post by mbeichorn on 2009-06-22
I just updated and rebooted, the problem is continuing in Karmic Alpha 2 amd64 Kernel 2.6.30-9-generic. I wonder if this is caused by a something constantly calling gconfd-2, as this is required to launch many gnome programs.

---

### Post by jerrylamos on 2009-06-22
Not quite sure how you're measuring % cpu.  If I start System Monitor it says the system monitor itself is using 10% of the cpu, everything else it shows is zero...

Jerry

---

### Post by celticbhoy on 2009-06-22
Sitting at 0% on my PC

---

### Post by Starks on 2009-06-22
0%

Linux kingfisher 2.6.30-9-generic #10kms5-Ubuntu SMP Sun Jun 14 12:45:52 UTC 2009 i686 GNU/Linux

---

### Post by ronacc on 2009-06-22
system-monitor is itself a resource hog , top is much easier on resources and sorts the output by resource usage , highest at the top of the list .

---

### Post by mbeichorn on 2009-06-22
results are consistent in System Monitor and powertop. System monitor reports 10% cpu usage for gconfd-2. With it on and the computer idle cpu utilisation is 60% or more. When I stop the process it goes to less then 10%. I know that the process is used to some launch gnome apps so it is possible that something is broken and calling it in a loop. Nevertheless there have been other users with the problem, and the effect is massive.

---

### Post by JMFTheVCI on 2009-07-29
I am seeing this as well. Karmic Alpha 3. Htop shows gconfd-2 running at least 20% CPU with X taking up another 10%
My Htop load average is 45% on a system that is just sitting idle.
Not good!

---

### Post by jfernyhough on 2009-07-29
When I'm running Metacity with no Compositing gconfd and X are where they should be - at or around 0%. If I do a 
$ compiz --replace 
then both gconfd and X up themselves to 10-20% (30-40% total).

It's not very useful.

---

### Post by MacUntu on 2009-07-29
Known bug: [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/389686](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/389686)

---

### Post by Tompalaz on 2009-09-04
gconfd-2 take from 50~70% of my CPU.
> 2.6.31-9-generic #29-Ubuntu SMP Sun Aug 30 17:39:26 UTC 2009 x86_64 GNU/Linux

> tomas@MacintoshLinux:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu karmic (development branch)
Release:	9.10
Codename:	karmic

Like the bug report say. If I kille metacity then gconfd-2 go to sleep.

---

### Post by TaTaE on 2009-09-05
Same here. It takes about 10-20% of CPU, according to top.

---

