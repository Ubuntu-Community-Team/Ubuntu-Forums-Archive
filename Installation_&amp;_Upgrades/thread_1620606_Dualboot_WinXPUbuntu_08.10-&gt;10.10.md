---
title: "Dualboot WinXP/Ubuntu 08.10-&gt;10.10"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by UBUminJ on 2010-11-13
Hello.
I need a little bit of assistance.

I had hoped a new install of 10.10 would be a bit easier, like telling the installation routine
"erase Ubuntu 08.10 and replace it with Ubuntu 10.10"

but it only offers to erase the full disk
or install it alongside the other OS
or manually

I thought I choose the alongside option but there I have now several partitions 
sda1 (fat16); sda2 (ntfs); sda5 (the old Ubuntu); sda? (linuxswap) and sda3 (fat32)

I don't know how to proceed: I guess I have to delete sda5 and then click add ?
Then I have to point the boot to sda1?

But then I get the message "no root file is defined".
???

Thanks
Michael

---

### Post by UBUminJ on 2010-11-14
I checked with sfdisk -l - and there seem to be an error (I cannot figure out the meaning, despite searching the web)


Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0
```

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+      8       9-     72261   de  Dell Utility
/dev/sda2   *      9   17960   17952  144199440    7  HPFS/NTFS
/dev/sda3      60370   60800     431    3462007+  db  CP/M / CTOS / ...
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda4      17961   60369   42409  340650292+   5  Extended
/dev/sda5      17961+  59143   41183- 330802416   83  Linux
/dev/sda6      59144+  60369    1226-   9847813+  82  Linux swap / Solaris
```

To do a clean install of Ubuntu 10.10, is it recommended to first delete sda3, 4, 5 and 6 and then install Ubuntu 10.10 ? 

Thank you for any help (hints or links).

Michael

---

### Post by bradbury on 2010-11-14
I did this upgrade (8->10) yesterday.  The trick is to attempt to record the specific partitions where Ubuntu is installed (e.g. sda3 -> /boot, sda5 -> / (root), etc.) then boot the 10.10 Install CD.  Select the Install option, then the "Advanced" partitioning option.  Then it will bring up a list of current partitions (similar to fdisk).  You have to select/highlight the Linux partitions, right click and tell it where you want them mounted during the install -- e.g. /boot, /, /usr, /home, etc).  The problem is that the install process doesn't make it clear that you have to select the Advanced install and associate the hardware devices with mount points.  [A more advanced install would find the old root partition and look in /etc/fstab...]

After that continue with the install process.  It may give you a message about needing to delete "system" directories on /boot but that is ok.  The install proceeds as "normal" overwriting old binaries with the upgraded binaries (mostly /bin, /usr/bin, /etc, /lib, /usr/lib, etc.) with no reformatting (so any non-system data should be preserved.  I think some care is taken to preserve configuration specific files (e.g. password) but I'm not sure how far this extends (e.g. squid, apache, etc. configurations).

Now, BE FORWARNED. IMO, 10.10 is a VERY problematic upgrade.  I've gotten core dumps/aborts from X (seg violations) because Ubuntu is using the problematic 1.9.0 driver and multiple Gnome utilities/components have problems (because the Gnome developers have not bothered to test 2.32 upgrades back to the level of configurations that are from Ubuntu 8.0.  You will get situations of being able to login to old user accounts once but never again.  Many errors present in the X-session errors file and problems with X aborting and gdm switching VTs for re-invocations of X subsequently.  New users may be OK but the only way I've found to work with old users is to completely remove .gconf and reconfigure the desktop.  Even that may have some problems.  The Intel i810 driver is also problematic as it looks like the KMS features lose the ability to switch to VT1-4 for a "straight" console display.  Buyer Beware!

---

### Post by wilee-nilee on 2010-11-14
@bradbury some of you explanation is well fud but thats okay your trying.;) This was your experience no one else's.

OP take a screen shot of gparted and post it if all you want to do is remove 8.10 and put in 10.10 the screen shot will be more helpful.;)

---

### Post by matt_symes on 2010-11-14
Hi

Might i also suggest creating a dedicated partition for your home directory on this _fresh_ install. I can help alot with future upgrades. I take it you have run the live CD to check compatibility?

Kind Regards

---

