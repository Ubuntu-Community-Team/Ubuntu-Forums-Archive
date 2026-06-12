---
title: "Ubuntu installation on a HP laptop"
date: 2016-06-03
forum: Installation &amp; Upgrades
---

### Post by marco139 on 2016-06-03
I have a HP laptop with Windows 7 (which I have recently updated to Windows 10).
I want to dual-boot with Ubuntu, but when I try to install it (with a DVD), the installation procedure never ends.
I had the same problem with Fedora (In particular, in that case, it stopped at boot loader installation. There were no error messages: it just went forever)

---

### Post by Frogs Hair on 2016-06-03
Hello and Welcome

What partitions do you have and did you overwrite the Win 7 recovery partition ?  I also have an HP and upgrading to Win 10 without a clean installation post upgrade leaves the Win 7 factory recovery partition in place and usable. I also had to remove the HP Tools partition to dual boot , but you would have had to remove those to upgrade to win 10 anyway.

---

### Post by marco139 on 2016-06-04
This is the disk situation:
[IMG]http://s33.postimg.org/yid1nyu5p/disk_mngt.png[/IMG]

---

### Post by Frogs Hair on 2016-06-04
Just an FYI ,if you do a factory reset on that computer it will re-load windows 7  and not 10. Your table is much different than mine and I think it's because MS gives the option go back to WIN 7 for a specified period of time, this is different from your factory reset.

 My model had some hardware and software incompatibilities with Win 10 . After  3 tries I used the factory reset and dual booted with Win 7 . I also had nothing labeled OEM Partition. I wrote of a post upgrade clean installation of windows 10 . With caution, some users have done this only after the device is identified on the MS severs you may also need to know how to get the code for your OEM loaded Windows and there are articles on how to do it.

What this does, is gives Win 10 the entire drive and makes the dual boot process much simpler, but you would lose any chance of using a factory reset.

---

### Post by marco139 on 2016-06-04
But I don't understand why I can't install Ubuntu if I maintain the disks like they are now...

---

### Post by Frogs Hair on 2016-06-04
My Hp would not dual boot with only four disk volumes thus the need remove the Hp tools. You have seven including the Unallocated space and I think that is why the Linux installers aren't working properly.

---

### Post by marco139 on 2016-07-07
This is the new situation. It still does not work because of the same problem.
[IMG]https://s31.postimg.org/rxq1zl0gb/Capture.png[/IMG]

---

