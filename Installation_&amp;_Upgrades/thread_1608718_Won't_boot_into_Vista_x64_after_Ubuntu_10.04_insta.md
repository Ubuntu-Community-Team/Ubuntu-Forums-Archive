---
title: "Won't boot into Vista x64 after Ubuntu 10.04 install"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by WhyCali on 2010-10-29
I'm new to Linux.

I installed Ubuntu 10.04/32-bit desktop on a system with a working Vista x64 installation.  I had problems installing Ubuntu.  I tried wubi, which didn't work at all... just booted right into Vista with no ubuntu boot option.  I tried doing a full Ubuntu install, and it never gave me the "install side by side" option.  Finally, I shrunk my Vistax64 boot partition to give some room for Ubuntu.  Ultimately, I installed Ubuntu 10.04/32-bit desktop.  I had to use the "Manully create partitions" option during installation, and created an ext4 root  partition and a swap partition.  The Ubuntu install worked but now I'm unable to boot into Vista x64.

After the Ubuntu 10.04 / 32-bit desktop install, the Grub2 boot loader came up.  It boots into Ubuntu just fine, but when I select Vista I get a very fast blue screen, then it reboots.  I tried "last known good" on the vista boot, didn't work  I tried a safe mode vista boot, but get the blue screen right after it loads the "crcdisk.sys" file.

Please help me boot into Vista...

Mike

---

### Post by drs305 on 2010-10-29
Your situation sounds similar to the problem that occurs when Grub is installed to the Windows partition. See if this site helps:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

If not, please run the boot info script and post the contents of the RESULTS.txt. The scirpt will show is your system's boot information and help us determine what's happening with your system:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by WhyCali on 2010-10-29
Thanks for the quick reply.  I'm trying to follow the directions from the first link you sent and I'm lost at:
[FONT=monospace]
[/FONT]```
Fifth   screen:  Select the Windows system partition  and choose "boot"
```The fifth's screen looks like this:

```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition                  Start        End    Size in sectors
 1 P W2K Dynamic/SFS          0   1  1     0  32 32       1985
 2 * Windows RE(store)        0  32 33   195 239 44    3145728
 3 P W2K Dynamic/SFS        195 239 45 18021  31 50  286361592
 4 E extended             18021  31 57 19457  53 52   23070722
 5 L Linux                18021  31 59 18892 151 11   14000128
   X extended             18892 151 12 19457  53 52    9070592
 6 L Linux Swap           18892 183 44 19457  53 52    9068544

[  Type  ]  [Image Creation]  [  Quit  ]
              Change type, this setting will not be saved on disk


```So, I'm not sure which is the Windows system partition (I know it's about 149 GB) and there doesn't appear to be a "boot" option to select.

What should I do at this step?

Thanks!

---

### Post by drs305 on 2010-10-29
> **WhyCali said:**
> So, I'm not sure which is the Windows system partition (I know it's about 149 GB) and there doesn't appear to be a "boot" option to select.

What should I do at this step?

Thanks!

This post will just have to serve as a bump for someone. I'm not familiar with how Windows sets up the boot and system partitions any longer. I see the boot flag is on #2 but your main Windows partition looks like it's #3. 
I can't be sure which one should be selected in this case. 

You can wait for a Windows user to chime in here or run the boot info script. The top of the results should indicate if Grub2 is installed on a partition, and which partition it is. You would note whichever partition it is and select it in Testdisk. I would suspect it will be either 2 or 3.

As for the "boot" issue, when you select the NTFS partition the "boot" option will appear at the bottom of the test disk screen.

---

### Post by bcbc on 2010-10-29
You can repair the boot sector on any ntfs partition. If I recall correctly, testdisk will tell you if there is an available backup bootsector that differs. You can also run [bootinfoscript]("http://bootinfoscript.sourceforge.net") and it will tell you if grub has been installed to any of your ntfs bootsectors (and choose the affected ones).

Did you use the windows disk management to shrink the partition or the ubuntu installer? The installer is known to cause issues.
In which case, you're probably going to need a windows repair CD.

---

