---
title: "Booting from an alternate (pre-existing) partition"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by b_robinson on 2010-03-27
_Problem: _
I can't boot to Windows XP after recently installing Ubuntu (Ubuntu boots fine). The error that comes up (straight after selecting XP) is that it can't find "system32\hall.dll".


_Reason for the problem: _
Ubuntu is looking at the old, corrupted version of XP that I have. The 'real' version is on another partition, for reasons too lengthy to explain. Note: neither of these partitions were touched when installing Ubuntu - I placed Ubuntu in the pre-existing partitions I had setup when installing previous versions of Linux (last was Mandrake 8.)

Now, I can understand why it is looking at the old version, because it is on the first partition of the hard drive, "dev/sda1", the new version is on "dev/sda3" (nomenclature according to Ubuntu, obviously).


_Question:_ 
How do I point the config file to sda3? I have tried setting root to "hd0,3" and "hd3,1" with no luck. Original code is below:

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 5008465808463d6a
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```Any suggestions to fix this would be greatly appreciated!

---

### Post by oldfred on 2010-03-27
It may be best to see your entire configuration.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

Where is your windows boot flag. It should be on the partition that you use to boot. If you did two installs of windows, it combines the boot files into one partition with the boot flag and the second partition is not separately bootable. You may have to run repairs to add the files back if that is the case.

Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)

While it discusses Vista it applies to all versions of windows.
To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by maybeway36 on 2010-03-27
This line:
```
search --no-floppy --fs-uuid --set 5008465808463d6a

```
changes the root to whatever has that UUID. If you want to use the "root" line above it, then this line should be commented out.

---

### Post by b_robinson on 2010-03-28
Thank you very much for your advise, by combining the two I have managed to start the Windows boot sequence, which is then failing further down the line, so a recovery CD will have to be the final answer. Luckily Ubuntu can see both partitions so no data will be lost.

Thanks again!

---

