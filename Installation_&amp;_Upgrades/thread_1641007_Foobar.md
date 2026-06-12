---
title: "Foobar?"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by Odyssey1942 on 2010-12-08
I shut down my Ubuntu 10.04 (recently upgraded from 9.04 to 9.10 to 10.04) and moved it to another location with a different monitor, keyboard, mouse.

When I booted, a screen came up stating:

> The disk drive for /mnt/foobar is not ready yet or not present.
Continue to wait; or press S to skip mounting or M for manual recovery

Have googled without finding an answer.

Whatzit?

---

### Post by Odyssey1942 on 2010-12-08
Further to the issue, I tried M to manually recover. It went to the shell and said it was starting a recovery routine, then immediately reverted to the prompt with no feedback. I exited the shell and it went back to the warning message, so this time I pressed S to skip. It seemed to start normally.

I used Chrome for awhile and then attempted to start Firefox. Instead of starting, Firefox threw up a message:

> Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.I continued and it crashed and threw up a Mozilla Crash Reporter.

I tried to uninstall FF and reinstall but no improvement.

I restarted the computer again and again attempted to start FF with the same result. Then attempted to start Chrome but it would not start.

So re-started the computer again (beginning to sound like a Windows problem?) and this time started Chrome which started normally. Made no further attempt to start FF as by now I know what is going to happen.

Do I reinstall 10.04, or what other action?

---

### Post by Odyssey1942 on 2010-12-09
Am I in the wrong forum?

---

### Post by uRock on 2010-12-09
Have you tried booting the recovery kernel and letting it fix broken packages?

---

### Post by Odyssey1942 on 2010-12-09
uRock, Thanks for yours.

I am pretty new at this. How would I accomplish this?

---

### Post by uRock on 2010-12-09
If you are dual dooting the select the kernel listed with Recovery beside it. If you aren't dual booting then you will have to hit Esc when your system first starts booting to get into the grub menu.

---

### Post by Odyssey1942 on 2010-12-09
There were actually 2 kernels with recovery beside and I chose the first one. It went through some stuff mentioning that it could not find apparmor files, continued then stalled with the last two lines being:

/dev/sda6: clean, 168652/610800 files, 987483/2441872 blocks
/dev/sda5: clean, 23070/2449408 files, 7040886/9765504 blocks

with the cursor blinking under the beginning of the last line. It has been stalled there for at least 10 mins. Is it doing something, or frozen?

Do I need to restart?

Thanks.

---

### Post by Odyssey1942 on 2010-12-09
Wanting to get on with this, I reinstalled 10.04 in a new partition. It boots up well now with no error messages, but because (I guess) I installed to a new partition, I somehow did not wind up with it finding my existing /home partition.

I think it is possible to mount the old /home so that the new install will automatically mount it each time it boots, but I have no idea how. Any guidance appreciated.

Would it be easier to reinstall and tick the right boxes so that the new install knows to look for the existing /home, and if so, how to do this?

Thanks.

---

### Post by uRock on 2010-12-09
If you created the same screen name and password, then mounting the old /home should be no problem. Simply click on the places menu, then click the corresponding Filesystem that you want to mount.

---

### Post by oldfred on 2010-12-10
You still have to add it to fstab. You can look at the fstab of your old install and copy the entry.

You only have to do the last steps:
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

