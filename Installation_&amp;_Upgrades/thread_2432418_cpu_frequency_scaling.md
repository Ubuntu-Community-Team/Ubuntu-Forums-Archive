---
title: "cpu frequency scaling"
date: 2019-12-02
forum: Installation &amp; Upgrades
---

### Post by pi3243f on 2019-12-02
Hi,
I downloaded a Xubuntu 19 live iso and installed it on my laptop. It has a 10510U cpu. Frequency scaling does not seem to work. The processor is always on 4 GHz, temperature rises to 66 C due to that and the fan is always on. But ... if I run the live version from the usb, frequency scaling works like a charm. It is mostly low, like 500 MHz. Unless some process runs, than it goes up to around 3.5 GHz. After the process has finished frequency goes down again. Temperature stays low (45 C) and the fan is rarely on.
So ... How do I get this behavior of the live version working in the installed system?
In both cases (live and installed system) there is a /sys/devices/system/cpu/intel_pstate directory present
Does anybody have some hints?
Thanks in advance.

---

### Post by Doug S on 2019-12-02
could you post the contents of the /sys/devices/system/cpu/intel_pstate directory in each case? Example (wait more than 1 minute after boot):

```
doug@goom-i5:~/temp-git-git/k5.4i5$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/intel_pstate/*[/COLOR]
/sys/devices/system/cpu/intel_pstate/max_perf_pct:100
/sys/devices/system/cpu/intel_pstate/min_perf_pct:23
/sys/devices/system/cpu/intel_pstate/no_turbo:0
/sys/devices/system/cpu/intel_pstate/num_pstates:27
/sys/devices/system/cpu/intel_pstate/status:passive
/sys/devices/system/cpu/intel_pstate/turbo_pct:8

```Also post these outputs for each case:
```
doug@goom-i5:~/temp-git-git/k5.4i5$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
intel_cpufreq
intel_cpufreq
intel_cpufreq
intel_cpufreq
doug@goom-i5:~/temp-git-git/k5.4i5$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor[/COLOR]
schedutil
schedutil
schedutil
schedutil

```The kernel command lines for each case:
```
doug@goom-i5:~/temp-git-git/k5.4i5$ [COLOR="#FF0000"]cat /proc/cmdline[/COLOR]
BOOT_IMAGE=/boot/vmlinuz-5.4.0-gg6 root=UUID=8eb53a86-c5d5-4954-b283-5cf8e9c0e640 ro ipv6.disable=1 consoleblank=300 intel_pstate=passive cpuidle_sysfs_switch cpuidle.governor=teo
```
And finally, the kernel version (not a good example because my kernel is custom):```
doug@goom-i5:~/temp-git-git/k5.4i5$ [COLOR="#FF0000"]uname -a[/COLOR]
Linux goom-i5 5.4.0-gg6 #758 SMP PREEMPT Mon Nov 25 17:49:36 PST 2019 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by pi3243f on 2019-12-02
Here is the output from my installed system:
```

~] grep . /sys/devices/system/cpu/intel_pstate/*
/sys/devices/system/cpu/intel_pstate/hwp_dynamic_boost:0
/sys/devices/system/cpu/intel_pstate/max_perf_pct:100
/sys/devices/system/cpu/intel_pstate/min_perf_pct:8
/sys/devices/system/cpu/intel_pstate/no_turbo:0
/sys/devices/system/cpu/intel_pstate/num_pstates:46
/sys/devices/system/cpu/intel_pstate/status:active
/sys/devices/system/cpu/intel_pstate/turbo_pct:68

~] cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate

~] cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
powersave
powersave
powersave
powersave
powersave
powersave
powersave
powersave

~] cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-5.3.0-23-generic root=/dev/mapper/vgxubuntu-root ro silent splash vt.handoff=7

~] uname -a
Linux bto2 5.3.0-23-generic #25-Ubuntu SMP Tue Nov 12 09:22:33 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```

And here is the output from the (very nice and silent) Xubuntu live system:
```

xubuntu@xubuntu:~$ grep . /sys/devices/system/cpu/intel_pstate/*
/sys/devices/system/cpu/intel_pstate/hwp_dynamic_boost:0
/sys/devices/system/cpu/intel_pstate/max_perf_pct:100
/sys/devices/system/cpu/intel_pstate/min_perf_pct:8
/sys/devices/system/cpu/intel_pstate/no_turbo:0
/sys/devices/system/cpu/intel_pstate/num_pstates:46
/sys/devices/system/cpu/intel_pstate/status:active
/sys/devices/system/cpu/intel_pstate/turbo_pct:68

xubuntu@xubuntu:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate

xubuntu@xubuntu:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
powersave
powersave
powersave
powersave
powersave
powersave
powersave
powersave

xubuntu@xubuntu:~$ cat /proc/cmdline
BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/xubuntu.seed quiet splash ---

xubuntu@xubuntu:~$ uname -a
Linux xubuntu 5.3.0-18-generic #19-Ubuntu SMP Tue Oct 8 20:14:06 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by Doug S on 2019-12-02
A difference is the kernel version. So it would be good to try kernel 5.3.0-18-generic on your installed system. I wonder if it is there, but it is just booting the newer one by default. Do you see it on boot? or via dpkg listing. Examples (but where my system has different stuff installed:

```
doug@goom-i5:~/temp-git-git/k5.4i5$ [COLOR="#FF0000"]ls -l /boot/vm*[/COLOR]
lrwxrwxrwx 1 root root       31 Nov 25 15:02 /boot/vmlinuz -> vmlinuz-5.4.0-050400-lowlatency
-rw------- 1 root root 11391736 Oct  9 05:15 /boot/vmlinuz-5.3.0-18-generic
-rw------- 1 root root 11582336 Nov 24 18:01 /boot/vmlinuz-5.4.0-050400-lowlatency
-rw-r--r-- 1 root root  9064384 Nov 25 18:16 /boot/vmlinuz-5.4.0-gg6
-rw-r--r-- 1 root root  9064832 Nov 25 08:41 /boot/vmlinuz-5.4.0-stock
lrwxrwxrwx 1 root root       24 Nov 25 13:50 /boot/vmlinuz.old -> vmlinuz-5.3.0-18-generic

```and```
doug@goom-i5:~/temp-git-git/k5.4i5$ [COLOR="#FF0000"]dpkg -l | grep linux-im[/COLOR]
ii  linux-image-5.3.0-18-generic                 5.3.0-18.19+1                       amd64        Signed kernel image generic
ii  linux-image-5.4.0-gg6                        5.4.0-gg6-758                       amd64        Linux kernel, version 5.4.0-gg6
ii  linux-image-5.4.0-stock                      5.4.0-stock-757                     amd64        Linux kernel, version 5.4.0-stock
ii  linux-image-generic                          5.3.0.18.21                         amd64        Generic Linux kernel image
ii  linux-image-unsigned-5.4.0-050400-lowlatency 5.4.0-050400.201911242031           amd64        Linux kernel image for version 5.4.0 on 64 bit x86 SMP

```Actually, I didn't know there was a 5.3.0-23.

If you do have it, do you know how to make grub visible during boot so that you can select it?

---

### Post by pi3243f on 2019-12-03
Hi, thanks for your help.
I installed kernel 5.3.0-18-generic and reconfigured grub to have a timeout in order to give me a chance to choose another kernel.
Booting my installed system with this kernel worked for the frequency scaling! It behaves as I would like.
But ... now my external monitor connected through HDMI is not recognized and my bluetooth mouse is not recognized. It says there is no bluetooth adapter.
Booting the Xubuntu live system with also the 5.3.0-18-generic kernel has everything working: frequency scaling, external monitor and bluetooth.
I also have a 5.3.0-19-generic kernel installed and booting into that one solves everything: frequency scaling works, HDMI and bluetooth.
Conclusion: I am happy. Except that I now can not profit from newer kernels ...
Are you willing to try to give me some hints to get everything working with the latest kernel or should I wait until a kernel comes out that has everything working again?
I already greatly appreciate your help!

---

### Post by Doug S on 2019-12-03
Glad to hear that you got it working with kernel 5.3.0-19-generic. And thank you for reporting back, as so very many don't.

I think there is a 5.3.0-24-generic in the pipeline. My suggestion at this point is to just wait and try it when it comes out.
Your processor is very new, and some hiccups are not unusual.

If you still have troubles with 5.3.0-24, then try whatever the [mainline kernel]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") is at the time, the purpose being to determine if things are solved upstream then is just a matter of time until they are backported.

---

