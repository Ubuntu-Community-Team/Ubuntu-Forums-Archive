---
title: "Want to bypass GNU Grub after fresh install"
date: 2013-09-20
forum: Installation &amp; Upgrades
---

### Post by WJMRfYt on 2013-09-20
EDIT: The issue seems to be that I can't uninstall 12.04 cleanly. It's displaying that my OS is booting from my HDD, but 13.04 is installed on my SSD (see 4th post). Let me know if you'd like any more info and I'll gladly supply it.

---------
My computer has a small SSD for the operating system and a larger HDD for my files. I had tried to install 12.04 on it but to no avail (because of something involving EFI, I believe), so I installed 13.04 on the SSD and now it works fine. However, I had previously tried to install 12.04 on my HDD and it aborted towards the end - though I believe there are remnants of it still on the disk. Basically, whenever I boot up my computer, it opens up the purple GNU Grub screen and I have to select Ubuntu (or wait 10 seconds) to boot up the system.

I know how to set the screen time to 0 seconds so it isn't as big a problem, but I would rather skip the grub process altogether. As far as I've been able to gather, this process never initiates if it's clear your computer only has one operating system on it (hence why I think the problem is related to the aborted 12.04 install on my HDD). I tried to format my HDD drive, but I still see a brief flash of purple upon startup (and it still takes about 20 seconds to boot on the SSD, which is as long as it took windows to boot).

Any ideas on how to fix this? I have already moved all my data off of this computer so if I need to re-install something to be safe, I am able to. Thank you.

---

### Post by nerdtron on 2013-09-21
If you set the GRUB screen timeout to 0, you'll basically skip the screen. It's just a split second after booting.

---

### Post by grahammechanical on 2013-09-21
Even with one Ubuntu OS installed Grub is still there. It is just that the menu screen does not appear. If you remove Grub your computer will not boot. it needs a boot loader.

How many operating systems were in the Grub boot menu? You have formatted the hard drive but the Grub menu remains the same. That is because you have not re-configured the Grub configuration files.

Boot into Ubuntu on the SSD and in a terminal run

```
sudo update-grub
``` 

The output will show you all the operating systems being detected by Grub OS-prober. It will change the Grub configuration file. And you may find that any listing of the broken 12.04 install on the hard disk is removed.

Regards.

---

### Post by WJMRfYt on 2013-09-21
Gotcha - I understand that the grub is necessary to boot now. Thanks.

Regarding cleaning up the old OS, here's the outputs I got from the terminal:


```
connor@connor-UX32A:~$ sudo update-grub[sudo] password for connor: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found Ubuntu 12.04.3 LTS (12.04) on /dev/sda5
done
connor@connor-UX32A:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring
```

Still a bit confused because the grub does not show a 13.04 (but I am sure I'm running this version). Also I can't seem to find my SSD through my file explorer.. just 2 partitions of my HDD. Here's the fdisk. Perhaps I'm not booting up from the SSD? I have the SSD selected to boot from the bios, though.

```
[COLOR=#000000][FONT=Consolas]connor@connor-UX32A:~$ sudo fdisk -l[/FONT][/COLOR] 
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfffad7d7
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   362156870   181077411+   7  HPFS/NTFS/exFAT
/dev/sda2       362158078   625141759   131491841    5  Extended
/dev/sda5       362158080   616990719   127416320   83  Linux
/dev/sda6       616992768   625141759     4074496   82  Linux swap / Solaris
 
WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.
 
 
Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
 
   Device Boot      Start         End      Blocks   Id  System
[COLOR=#000000][FONT=Consolas]/dev/sdb1               1    62533295    31266647+  ee  GPT[/FONT][/COLOR]
```

---

### Post by WJMRfYt on 2013-09-22
bump; problem still persists. Here's some more info and speculation from someone who is brand new to ubuntu:

1) My HDD is actually partitioned in half (probably during the aborted installation). I had formatted only one of the partitions; not the other. I'll try formatting the other now.
2) The third "device" on my file explorer is something called "Computer". I cannot see its properties so I have no idea if this is my SSD or not. Furthermore, it appears all the programs I've been downloading to my computer have been going to my not-yet-formatted HDD (because it has 2.3GB used). 
3) I want to be able to install commonly used programs (eclipse, chrome) to my SSD, but can't understand how with ubuntu's installation system. 

Thank you.


EDIT: This might be of use (screenshot of disks): [http://i.imgur.com/EHgnnBM.png](http://i.imgur.com/EHgnnBM.png) ; [http://i.imgur.com/V7TSrUr.png](http://i.imgur.com/V7TSrUr.png)

E: I believe I have solved my problem.. I used GParted to format my HDD and now everything seems to work fine.

---

### Post by oldfred on 2013-09-22
It looks like you had mixed MBR(msdos) partitioning on hard drive and gpt on SSD. Better to have both the same.

Windows only boots from gpt partitioned drives with UEFI.
Ubuntu will boot from gpt drives with either UEFI or BIOS/CSM.
Both Windows and Ubuntu boot with BIOS from MBR partitioned drives.

 GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

