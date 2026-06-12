---
title: "Odd issue with Hibernate on Windows 10 after installing Grub"
date: 2017-06-27
forum: Installation &amp; Upgrades
---

### Post by egandt on 2017-06-27
Before installing Grub (EFI) everything worked and Hibernate was not a problem, after installing Grub and Ubuntu 16.04 (using EFI), if I hibernate Windows 10, on resume it sayst teh system partition is corrupt and run chkdsk, then deletes the Hibernation file and boot cleanly.   I have fastboot disabled for this system, as I know that is an issue, or has been for me with Linux in teh past. 
Now at no time during this did I access Ubuntu I simply went select windows bootloader in grub -> Windows 10 (open a browser) -> hibernate -> resume -> select Windows bootloader -> system system partition corrupt -> run chkdsk -> delete hibernation file -> clean Windows 10 boot.  Before Grub the process was smooth   boot->Windows 10 (open a browser) -> hibernate -> resume_>windows (browser still open), so I know the issue is related to grub, but how can I fix it, I do not see why Grub is corrupting the System Partition, unless it simply writes to it as part of loading the boot menu and Windows considers that to be an issue, again any suggestion on how to resolve this?

Thanks,
ERIC

---

### Post by Bucky Ball on 2017-06-27
If you are hibernating Windows and restarting, then I doubt grub can access the drive and maybe that is why you're getting issues. Hibernating Windows locks the drive to any other OS. Hibernating Windows is NOT shutting down Windows, it is putting it to sleep, so not sure I would expect to see grub after that in any case.

When you boot to Windows and restart WITHOUT putting Windows into hibernate, does everything work as expected?

---

### Post by oldfred on 2017-06-27
How to correctly turn of fast start up & hibernation:
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)

---

