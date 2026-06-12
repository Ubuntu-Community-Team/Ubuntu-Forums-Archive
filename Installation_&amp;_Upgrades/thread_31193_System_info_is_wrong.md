---
title: "System info is wrong"
date: 2005-05-02
forum: Installation &amp; Upgrades
---

### Post by Insanely on 2005-05-02
Can someone please help me out with my problem here.

I was reading through the Ubuntu guide at the following thread which tells you how to display your system information:
[http://www.ubuntuforums.org/showthread.php?t=29300](http://www.ubuntuforums.org/showthread.php?t=29300)

Here is my output:

sudo head /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 4
model name      : AMD Athlon(tm) 64 Processor 3200+
stepping        : 8
cpu MHz         : 797.948
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no

Can this be correct. 797Mhz is just not 2Ghz. 

I also discovered:

head /proc/meminfo
MemTotal:       906660 kB
MemFree:        168960 kB
Buffers:         53100 kB
Cached:         472904 kB
SwapCached:         88 kB
Active:         455396 kB
Inactive:       235744 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       906660 kB

I have 1024MB (1GB) of RAM.

I have noticed the computer has been sluggish. I am using the i386 version of Ubuntu.

uname -a
Linux 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux

 Thanks for any advice.

---

### Post by nocturn on 2005-05-02
Regarding the CPU speed, this can be correct is CPU scaling is active.  This slow your CPU down when not using it to save power.

Put the system on a load, does it still give the same value?

---

### Post by gunnyman on 2005-05-02
You need the 686 kernel.  It's available in synaptic.
I don't know about the processor detection, but the 386 kernel has  a 900 meg memory limit.

---

### Post by Insanely on 2005-05-02
Thank you for getting back to me.

I was unsure of what I should do to simulate load so i compiled an application

sudo head /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 4
model name      : AMD Athlon(tm) 64 Processor 3200+
stepping        : 8
cpu MHz         : 797.948
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no


Unfortunately I got the same results.

---

### Post by Insanely on 2005-05-02
[QUOTE=gunnyman]You need the 686 kernel.  It's available in synaptic.
I don't know about the processor detection, but the 386 kernel has  a 900 meg memory limit.[/QUOTE]


Ok. I will give it a go. Cheers.

---

### Post by Xerampelinae on 2005-05-02
Is it using cpu scaling?  Try

```

watch cat /proc/cpuinfo

```

Then do something processor intensive and see if it goes up to its full speed.


Edit: I guess I shouldn't start a post, then get distracted and walk away, only to come back 10 minutes later and finish it... :\

---

### Post by Insanely on 2005-05-02
I am in a bit of trouble here. I don't know what went wrong!

I am booted up into windows atm. I installed the kernel-2.6-10 686 image. I then proceeded to boot up my machine from the new kernel. On boot I was told that the superblock on reiserfs could not be found. (Btw my system was reiserfs on /)

I then tried booting back into my 386 kernel and got the same message. I tried mounting it read write and running fsck.reiserfs --fix-fixable. This did not work. I also tried --rebuild and --rebuild-tree non would work. Just kept telling me that the super block cannot be found!

I can't boot into my ubuntu! What did I do wrong?
Do I have to reinstall? Should I use athlon-64 installation disks?


BTW: That watch command is tops.

---

### Post by arbearce on 2005-05-02
Check out this post for infomation on changing cpu scaling [http://ubuntuforums.org/showthread.php?t=21370](http://ubuntuforums.org/showthread.php?t=21370)

---

### Post by Insanely on 2005-05-02
[QUOTE=arbearce]Check out this post for infomation on changing cpu scaling [http://ubuntuforums.org/showthread.php?t=21370](http://ubuntuforums.org/showthread.php?t=21370)[/QUOTE]
Cheers. I will give:

sudo apt-get remove powernowd (it's not a laptop)

I just have to get my ubuntu back up and running :(

---

### Post by Insanely on 2005-05-02
Anyone got any tips to get my system back up?

Should I be using ext3 instead of reiserfs?

Should I be using the amd_64 installation of ubuntu?

How did I break my system?

---

### Post by Insanely on 2005-05-04
Ok. I fixed it. For all those who want to know!

1. I reinstalled Ubuntu.

2. I updated to kernel 2.6.10-5-686 from 386 version. This fixes the wrong memory size. (thankyou gunnyman)

3. I ran the following commands: (thankyou arbearce)

 sudo invoke-rc.d powernowd stop

 sudo head /proc/cpuinfo
 processor       : 0
 vendor_id       : AuthenticAMD
 cpu family      : 15 
 model           : 4
 model name      : AMD Athlon(tm) 64 Processor 3200+
 stepping        : 8
 cpu MHz         : 1994.883
 cache size      : 1024 KB
 fdiv_bug        : no
 hlt_bug         : no


4.Sweet. I am back to 2GHz from 800MHz and it's very noticable! All I have to do now is make sure that service does not start on boot.
 
 sudo update-rc.d -f powernowd remove
 update-rc.d: /etc/init.d/powernowd exists during rc.d purge (continuing)
 Removing any system startup links for /etc/init.d/powernowd ...
   /etc/rc0.d/K20powernowd
   /etc/rc1.d/K20powernowd
   /etc/rc2.d/S20powernowd
   /etc/rc3.d/S20powernowd
   /etc/rc4.d/S20powernowd
   /etc/rc5.d/S20powernowd
   /etc/rc6.d/K20powernowd

Thanks to everyone for their support on this issue.

---

