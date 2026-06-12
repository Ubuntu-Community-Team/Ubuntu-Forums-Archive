---
title: "100% CPU load by kswapd0 since upgrade to 15.10"
date: 2015-10-31
forum: Installation &amp; Upgrades
---

### Post by mtl-0 on 2015-10-31
Hi,


since upgrading my homeserver (Xbubuntu 15.04 x64) to Xubuntu 15.10 kswapd0 produces 100% cpu load. I helped that I set vm.swappiness = 0, but since yesterday I also get 100% cpu load when vm.swappiness set to 0. Using a higher value doesn't help either.
The server has 3GB of RAM and a 5GB swap file.


This didn't happen ever on Xubuntu 14.04., Xubuntu 14.10. or Xubuntu 15.04.

Anyone got a clue?

[COLOR=#000000][FONT=Liberation Sans]
[ATTACH=CONFIG]265294[/ATTACH][/FONT][/COLOR]

---

### Post by vuo on 2015-10-31
I second this.

Same scenario except for using `zram-config` for swap: As soon as swap is used `kswapd0` uses up one CPU core's performance. Sometimes it's disappearing when closing a program like Firefox that caused swapping.

Configuration changes haven't resulted in any improvements. Large games are almost unplayable. Changing niceness of `kswapd0` is just slightly soothing to not have the system choking.

---

### Post by vuo on 2015-11-10
This solved it for me now:
> There’s also quite a common problem with *kswapd0* hogging CPU on the C720. I was able to get rid of this problem by setting *transparent_hugepage* to *madvise*. To do so, add this to **/etc/rc.local**:

[FONT=Courier New]echo madvise > /sys/kernel/mm/transparent_hugepage/enabled[/FONT]
from [https://www.reddit.com/r/chrubuntu/comments/3ru04q/help_kernel_process_kswapd0_randomly_consuming/cwshnf2]("https://www.reddit.com/r/chrubuntu/comments/3ru04q/help_kernel_process_kswapd0_randomly_consuming/cwshnf2") respectively [https://blogs.fsfe.org/the_unconventional/2014/04/20/c720-ubuntu/](https://blogs.fsfe.org/the_unconventional/2014/04/20/c720-ubuntu/)

I also had to disable all custom [FONT=Courier New]vm.*[/FONT] settings in [FONT=Courier New]/etc/sysctl.conf[/FONT]. With this the system works well again now.


I believe this issue has been introduced through the 4.2 kernel included in the Xubuntu upgrade. (This didn't occur with Ubuntu's 3.x and mainline kernels 4.0-4.1 before.)

I also noticed Xfce4's *Power Manager Plugin* at times consumed up to 300 MiB resident memory and switched to using the *Indicator Plugin* equivalent feature for this.

---

### Post by mtl-0 on 2015-12-30
> **vuo said:**
> This solved it for me now:

from [https://www.reddit.com/r/chrubuntu/comments/3ru04q/help_kernel_process_kswapd0_randomly_consuming/cwshnf2](https://www.reddit.com/r/chrubuntu/comments/3ru04q/help_kernel_process_kswapd0_randomly_consuming/cwshnf2) respectively [https://blogs.fsfe.org/the_unconventional/2014/04/20/c720-ubuntu/](https://blogs.fsfe.org/the_unconventional/2014/04/20/c720-ubuntu/)

I also had to disable all custom [FONT=Courier New]vm.*[/FONT] settings in [FONT=Courier New]/etc/sysctl.conf[/FONT]. With this the system works well again now.


I believe this issue has been introduced through the 4.2 kernel included in the Xubuntu upgrade. (This didn't occur with Ubuntu's 3.x and mainline kernels 4.0-4.1 before.)

I also noticed Xfce4's *Power Manager Plugin* at times consumed up to 300 MiB resident memory and switched to using the *Indicator Plugin* equivalent feature for this.

Thanks for the answer. Sadly this didnt fix it for me. Still 100% cpu load, even with no SWAP attached.

---

### Post by zeroepoch on 2016-02-19
Thank you so much!!!  I tried commenting out my one option "vm.swapiness" in /etc/sysctl.conf but that made no difference.  Running that command during normal operation didn't help.  Although adding the command you mentioned to /etc/rc.d/rc.local (on Fedora 22) and rebooting did solve the problem.  Now kswapd0 uses almost 0% CPU.  I also had to disable tracker to get the rest of my idle CPU back but that's a GNOME 3 specific issue.  Now my c720 launches firefox much faster.

---

### Post by sistoviejo on 2016-10-24
Is this the same as this other thread? [https://ubuntuforums.org/showthread.php?t=2338503&highlight=kswapd0](https://ubuntuforums.org/showthread.php?t=2338503&highlight=kswapd0)

---

### Post by oldos2er on 2016-10-24
Not exactly, this thread was about 15.10, not 16.04. 15.10 is EOL, so putting this one to bed.

---

