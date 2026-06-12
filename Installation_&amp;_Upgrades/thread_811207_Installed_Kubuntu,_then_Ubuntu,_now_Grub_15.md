---
title: "Installed Kubuntu, then Ubuntu, now Grub 15"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by bigric on 2008-05-28
So here's what I've done to get myself a grub error 15 at boot:

1.  I had XP installed on the system.
2.  I installed Kubuntu 8.04, using the installer to resize the XP partition.  I had no problems with the boot manager that it installed.
3.  I decided I'd prefer Ubuntu, so I used its installer to reformat the partition that Kubuntu was on and installed.  I believe my first problem was leaving the "install bootloader" box checked at this point.

After the Ubuntu install I rebooted to a grub 15 error.  After reading lots of these threads I think I've got some of the relevant information ready by booting to the Ubuntu install CD:

sda1 is my Dell utility partition (48 MB)
sda2 is my XP partition (60 GB)
sda3 is the Dell media partition (3.4 GB)
sda4 shows Extended (12 GB, not sure where this came from)
sda5 shows Linux (12 GB, what I set up for Linux)
sda6 is swap (600 MB)

/boot/grub/menu.lst doesn't exist

This is on my laptop so there's only one SATA hard drive installed.

What do I need to do to get a boot menu set up so that I can select XP or Ubuntu?  Are there now two boot managers installed?

I'm pretty green with linux so please spell out what I need to do.  Thanks!

---

### Post by Pumalite on 2008-05-28
Boot your Live CD and post from the Terminal:
sudo fdisk -l

---

### Post by iaculallad on 2008-05-28
What about giving this command on your terminal:

Code:

```
cat /boot/grub/device.map
```

Does it show you something?

---

### Post by bigric on 2008-05-28
Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        7504    60227685    7  HPFS/NTFS
/dev/sda3            9116        9545     3453975   db  CP/M / CTOS / ...
/dev/sda4            7505        9115    12940357+   5  Extended
/dev/sda5            7505        9041    12345921   83  Linux
/dev/sda6            9042        9115      594373+  82  Linux swap / Solaris



cat /boot/grub/device.map gives:  no such file or directory

---

### Post by confused57 on 2008-05-28
Try reinstalling grub, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by bigric on 2008-05-28
> **confused57 said:**
> Try reinstalling grub, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Thanks.  Just tried that and got an error 15 when I did find /boot/grub/stage1.  I also tried the workaround of mounting my Ubuntu partition as /mnt/root but that was also a nogo.

Interestingly, after mounting /dev/sda5 as /mnt/root I get nothing when I ls /mnt/root.  Is it possible that something went very wrong with my install and I just need to reinstall?

---

### Post by confused57 on 2008-05-29
> **bigric said:**
> Thanks.  Just tried that and got an error 15 when I did find /boot/grub/stage1.  I also tried the workaround of mounting my Ubuntu partition as /mnt/root but that was also a nogo.

Interestingly, after mounting /dev/sda5 as /mnt/root I get nothing when I ls /mnt/root.  Is it possible that something went very wrong with my install and I just need to reinstall?
It would probably be quicker & easier just to reinstall Ubuntu, installing grub to (hd0), which is the default location(mbr).

---

### Post by bigric on 2008-05-29
OK, the second install attempt gave an IO error at 60%.  I ran a check on the install CD, and naturally, it failed.  I'm redownloading and burning right now, so hopefully I'll have better results this evening.  Thanks for everybody's help.  Now I have something to do during the commercials on Lost tonight.

---

### Post by Topsiho on 2008-05-29
I react to:

sda1 is my Dell utility partition (48 MB)
sda2 is my XP partition (60 GB)
sda3 is the Dell media partition (3.4 GB)
sda4 shows Extended (12 GB, not sure where this came from)
sda5 shows Linux (12 GB, what I set up for Linux)
sda6 is swap (600 MB)

You have sda5 and sda6, which are logical partitions, which have to reside within an extended partition, which is sda4. So that is where sda4 comes from :), it is a repository for partitions sda5, 6, etc.

Next: As sda5 and 6 together are 12,6 GB, sda4 must be 12,6 GB or larger.

Then: You do not need to install Kubuntu and Ubuntu separately, as you would with Ubuntu and, let us say, Fedora or Suse or Mandriva, for which you would have to prepare separate (logical) partitions.

You need only to first install one (Let's say Kubuntu), and after that you install ubuntu-desktop from Synaptic, or in a console (sudo apt-get ubuntu-desktop). It only takes some time for a lot has to be downloaded and after that veryfied, installed and configured.

If you can't get Grub reinstalled from the above advice, please install Kubuntu again, and after that Ubuntu as I described.

It's nice to know that (most or all) Gnome programs work in Kubuntu and same for KDE-programs in Ubuntu. Gnome and KDE are both great, and have their own advantages and disadvantages. I prefer KDE however for the KDE-translations (Dutch) are much better :)

Topsiho

---

