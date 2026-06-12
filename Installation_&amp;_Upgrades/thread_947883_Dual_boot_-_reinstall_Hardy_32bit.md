---
title: "Dual boot - reinstall Hardy 32bit"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by simonjp on 2008-10-14
I'm hoping someone can help with a problem I've encountered after upgrading to 8.10 using official upgrade method.  First, some info on the current set-up....

One hard disk, 80GB, split into two - 40GB for XP and 38GB for Ubuntu + 2GB for swap.  Dual booting between both no problems.

I originally installed the 64bit version of Hardy (after XP was installed) and all was fine, except my wireless card wouldn't always get detected - even when using the ndis wrapper.  OK, not too worried as simply pulling the USB modem out and back in seemed to correct it...no biggie.

I thought I'd give Intrepid Ibex a blast, so installed that using the Alt+F2 method and the official command line....again, no problems, downloaded and upgraded 8.04 no problems.

Now, graphics and networking aren't working (Onboard nVidia 6150 and nVidia nForce onboard nic).

I'd like to reinstall Hardy 32bit back into the original Ubuntu partition and what I've normally done to reinstall is to start the machine with the XP CD, go into the Recovery Console and fixboot and fixmbr to restore the Windows bootfiles.  This has always worked every time.  I can then delete the Linux partitions and reinstall from the LiveCD....all pretty straightforward.

Now, when I try to boot using the slipstreamed XP CD's (which I know boot as I've tried them on other machines and they start the DOS installation), they hang on the machine that has 8.10 installed on.  They boot initially, the "Press any key to boot from CD" message appears and this starts to boot from the CD, however the blue DOS installation screen never appears - just a blank black screen, and after a short while the CD stops spinning.

So, after all this, it looks like whatever the 8.10 installation has done, Windows doesn't like it as I'm guessing it can't read the disk.  XP starts fine from the boot menu, so still happy about that.

Any ideas anyone where I should go from here?  Can I just re-run the Hardy LiveCD and install over the top of the Ibex install?  Should I just delete the Linux partitions from within Windows and rerun the LiveCD?  I'm nervous about doing these things as I want to avoid having to rebuild the Windows startup files again if possible!

Please, any suggestions?

---

### Post by Pumalite on 2008-10-14
Install Ubuntu 32 bit; go 'Manual' and use the old partitions. You can ignore /swap

---

### Post by caljohnsmith on 2008-10-14
> **simonjp said:**
> 
Any ideas anyone where I should go from here?  Can I just re-run the Hardy LiveCD and install over the top of the Ibex install?  Should I just delete the Linux partitions from within Windows and rerun the LiveCD?  I'm nervous about doing these things as I want to avoid having to rebuild the Windows startup files again if possible!

Please, any suggestions?
Yes, you should be able to just install Hardy over your Intrepid install from the Live CD. But I just want to mention that in many cases I've seen in these forums where a Windows Install CD hangs and doesn't recognize the HDD, it's because the HDD's partition table has problems. It will only take a few minutes to check your HDD's partition table, so I would highly recommend you do it in case there are problems.

First post the output of:
```
sudo fdisk -l
```
Then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

---

### Post by simonjp on 2008-10-16
> **caljohnsmith said:**
> Yes, you should be able to just install Hardy over your Intrepid install from the Live CD. But I just want to mention that in many cases I've seen in these forums where a Windows Install CD hangs and doesn't recognize the HDD, it's because the HDD's partition table has problems. It will only take a few minutes to check your HDD's partition table, so I would highly recommend you do it in case there are problems.

First post the output of:
```
sudo fdisk -l
```

Then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```

After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

Output of fdisk....

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08940894

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5100    40965718+   7  HPFS/NTFS
/dev/sda2            5101        9598    36130185   83  Linux
/dev/sda3            9599        9964     2939895   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc1c3c8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS


Output of testdisk....

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 81 GB / 76 GiB - CHS 9964 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  5099 254 63   81931437

Bad sector count.
 2 P Linux                 5100   0  1  9597 254 63   72260370
 3 P Linux Swap            9598   0  1  9963 254 63    5879790

*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition

Does this help?

---

### Post by caljohnsmith on 2008-10-16
> **simonjp said:**
> 
```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 81 GB / 76 GiB - CHS 9964 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  5099 254 63   81931437

[COLOR="Red"]Bad sector count.[/COLOR]
 2 P Linux                 5100   0  1  9597 254 63   72260370
 3 P Linux Swap            9598   0  1  9963 254 63    5879790

*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition
```

It looks like testdisk found an error with your partition table since it complained about a "bad sector count". I would make sure you have your important file backed up on that HDD, and then rewrite the correct partition table with testdisk. If you want some help with using testdisk to rewrite your partition table, please do the following:
```
sudo testdisk
```
Choose "no log", select HDD and "proceed", "Intel", "Analyze", "proceed", "N" to skip the search for Vista partitions, hit enter, and post the contents of that screen that has "search!" and "write" at the bottom of the screen. Then select "search!" so it does a deeper search, which could take a while. Post the output of that screen too, and we can work from there. :)

---

### Post by simonjp on 2008-10-16
OK, this is the output of the 1st bit of info you wanted....

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 81 GB / 76 GiB - CHS 9964 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  5099 254 63   81931437
 2 P Linux                 5100   0  1  9597 254 63   72260370
 3 P Linux Swap            9598   0  1  9963 254 63    5879790

[  Quit  ]  [Deeper Search]  [ Write  ]
                          Try to find more partitions

Deeper search is running as I type....will post soon :)

---

### Post by simonjp on 2008-10-16
Deeper search.....

TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 81 GB / 76 GiB - CHS 9964 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  5099 254 63   81931437
D HPFS - NTFS              0   1  1  9963 254 63  160071597
D Linux                 1530   0  1  9735 254 63  131829390
D Linux                 1693   1  1  9620 254 63  127363257
D Linux                 5100   0  1  9597 254 63   72260370
D Linux Swap            9598   0  1  9963 254 63    5879790
D Linux Swap            9621   1  1  9963 254 63    5510232
D Linux Swap            9736   0  1  9963 254 63    3662820


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 41 GB / 39 GiB

---

### Post by caljohnsmith on 2008-10-16
> **simonjp said:**
> 
```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 81 GB / 76 GiB - CHS 9964 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  5099 254 63   81931437
 2 P Linux                 5100   0  1  9597 254 63   72260370
 3 P Linux Swap            9598   0  1  9963 254 63    5879790

[  Quit  ]  [Deeper Search]  [ Write  ]
                          Try to find more partitions
```

That screen above that you get before doing the deep search looks like it has all your partitions with the correct start/stop cylinders (when compared to fdisk), so it should be safe to use that to write your partition table. Just retrace your steps to get up to that point, and then select the "Write" above to write your new partition table. Fortunately you have a really simple partition structure, so I don't think you have anything to worry about. After doing that, try booting your Windows XP CD again on that computer and let me know what happens; hopefully it will recongnize your partitions OK this time. But also I wanted to mention about what you said earlier:
[QUOTE=simonjp]I'd like to reinstall Hardy 32bit back into the original Ubuntu partition and what I've normally done to reinstall is to start the machine with the XP CD, go into the Recovery Console and fixboot and fixmbr to restore the Windows bootfiles. This has always worked every time. I can then delete the Linux partitions and reinstall from the LiveCD....all pretty straightforward.[/QUOTE]
You shouldn't have to reinstall the Windows MBR with "fixmbr" from the Windows CD so you can delete the Linux partitions. Just choose the "manual" option in the Ubuntu Live CD installer, and you can tell Ubuntu to install over your old Ubuntu partition (like Pumalite said in post #2). :)

---

### Post by Pumalite on 2008-10-16
See post # 2

---

### Post by simonjp on 2008-10-21
Thanks for the help guys.

I wrote a new partition table and then re-tried the Windows CD but no luck.

I then took the plunge and went for a reinstall of 32-bit Hardy and it installed no problems and retained access to XP.

So, thanks again!

---

