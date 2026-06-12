---
title: "Windows XP not loading and its partition can't be mounted after ubuntu install"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by DwightRGV on 2008-01-30
I installed Ubuntu (7.10) and in the install selected for the hard drive to be partitioned for a dual boot.  After the install, Grub loads Ubuntu, and it works fine.

When I selected Windows XP the first time, checkdisk ran.  I cannot remember the exact 'areas' it checked, I know the first was files - which were ok, then the second group was fine, and the third (I think titled security) had some errors.  It finished and restarted the computer.

When I select Windows XP after that, I see the normal 'Startup' in the upper left, quickly followed by the 'We apologize...' and the menu to choose safe mode, etc.  Choosing to start Windows normally, gives me the normal Windows XP splash screen, and then the computer restarts (back to Grub). Choosing safe mode, I get a scrolling set of files and then the computer restarts back to Grub.

In Ubuntu, if I try to mount the partition Windows is in I get a 'Cannot mount vollume' error.  The details include....$LogFile indicates unclean shutdown (0,1) Failed to mount '/dev/sda1':Operation not supported Mount is denied because NTFS is marked to be in use...' it provides two options, first from windows to shut it down cleanly (can't do that), and second ...'If you don't have Windows then you can use the 'force' option for       your own responsibility. For example type on the command line:         mount -t nfs-3g/dev/sda1/media/disk -o force      or add the option to the relevant row in the /etc/fstab file....'  (I didn't try either of these options).

This is what I get from fdisk.
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9241    74228301    7  HPFS/NTFS
/dev/sda2           12136       12161      208845   88  Linux plaintext
/dev/sda3            9242       12009    22233960   83  Linux
/dev/sda4           12010       12135     1012095    5  Extended
/dev/sda5           12010       12135     1012063+  82  Linux swap / Solaris


So, is there any hope in getting windows and that partition to work? I couldn't find a issue like this (at least close enough for me to know it was the same problem).

Thanks for any help that can be offered!

---

### Post by Craigus on 2008-01-30
Boot from your XP Cd and do a repair install.

You'll have to reinstall grub after that. A forum search will readily locate threads dealing with that.

---

### Post by erginemr on 2008-01-30
+1 to Windows CD and repair install, and then fix Grub (MBR).

If it doesn't work, try "testdisk" from under Ubuntu, which can be used to repair your NTFS partition:
```
sudo aptitude install testdisk
```

---

### Post by DwightRGV on 2008-01-31
Can I use a XP Pro cd (full version) to repair my XP home (only have OEM version of that...and no repair option)?

---

### Post by erginemr on 2008-01-31
As far as I can remember, you start with a regular install, and when the time comes, Windows Installer recognizes that there is an existing installation on the hard drive and passes onto the repair mode. There should be an option for a "Recovery Console", if there is such an option in your OEM CD and if you can boot into that, you can issue "chkdsk C:" command to fix your Windows partition.

Alternative to the above and "testdisk" (which, I know, has been a savior for quite a few Ubuntu forum users), you may download the GParted Live CD, which has the capability of checking and fixing your NTFS drives as well:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Craigus on 2008-01-31
Have a read here:

[http://www.michaelstevenstech.com/XPrepairinstall.htm]("http://www.michaelstevenstech.com/XPrepairinstall.htm")

---

### Post by DwightRGV on 2008-01-31
Just wanted to say thanks again to both of you..  I read through a bunch of threads and sites, and decided to try using chkdisk, before doing a repair.  It worked. So now I can get my regular work done while getting up to speed on Ubuntu. :)

---

### Post by erginemr on 2008-02-01
Great! We are very glad that you solved your problem. Keep up the good work and have fun with Ubuntu! ):P

---

### Post by Craigus on 2008-02-01
Indeed we are :)

---

