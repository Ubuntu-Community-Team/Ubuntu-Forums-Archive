---
title: "Won't Load After Hardware Upgrade"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by bryder2162 on 2008-06-03
Need a little help here.  I have Ubuntu 7.10 AMD 64 installed in a separate partition on my hard drive.  The PC usually boots to Windows XP...well last night I did an upgrade to my computer.  The major difference being the motherboard...which in turn will change the network device.  XP booted and allowed me to install new drivers, etc., but now when I go to boot Ubuntu it just sits there with no hard drive activity.  I took the almost two hours to download the alternate version of 8.04 this morning thinking I could just upgrade my system.  Well, there is NO upgrade option on the main menu.  I have some important email settings and other files saved in the Ubuntu partition and DON'T want to lose them with a fresh install.

Thanks!

---

### Post by bryder2162 on 2008-06-03
Someone help please!!!  I have ubuntu 7.10 and can't access it.  I've downloaded the alternate CD for my computer which supposedly will allow me to upgrade to 8.04.  There is NO upgrade option on the install menu...just Install and Restore.  Do I use Restore???  I have to access my Linux install (dual boot system) for important email, etc.

---

### Post by overdrank on 2008-06-03
> **bryder2162 said:**
> Someone help please!!!  I have ubuntu 7.10 and can't access it.  I've downloaded the alternate CD for my computer which supposedly will allow me to upgrade to 8.04.  There is NO upgrade option on the install menu...just Install and Restore.  Do I use Restore???  I have to access my Linux install (dual boot system) for important email, etc.

HI and on your other issue
[http://ubuntuforums.org/showthread.php?p=5106561#post5106561](http://ubuntuforums.org/showthread.php?p=5106561#post5106561)
Are you able to boot into recovery mode, which is usually the second choice from the grub?

---

### Post by aysiu on 2008-06-03
You don't upgrade by *booting* the Alternate CD.

You upgrade by booting into your regular installation and then *inserting* the Alternate CD.

From the Ubuntu website: > Upgrading using the alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1.

      Download and burn the alternate installation CD.
   2.

      Insert it into your CD-ROM drive.
   3.

      A dialog will be displayed offering you the opportunity to upgrade using that CD.
   4.

      Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

```
gksu "sh /cdrom/cdromupgrade"
```

Or in Kubuntu run the following command using Alt+F2:

```
kdesu "sh /cdrom/cdromupgrade"
```
 **Edit**: Wait. Are you not able to boot into 7.04 at all? Why are you trying to upgrade, then? Your top priority should be getting 7.04 bootable!

---

### Post by aysiu on 2008-06-03
FS-Driver should help you access your Ubuntu partition from Windows:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by bryder2162 on 2008-06-03
To answer both questions...NO...I can't boot into 7.10 anymore...not even recovery mode.  I did a hardware upgrade on my computer and Ubuntu won't work now.:(

---

### Post by aysiu on 2008-06-03
All right. Let's get the priority straight here, then:

1. Get your important documents

2. See if we can get Ubuntu bootable

3. Upgrade

I've already posted in your other thread about #1.

---

### Post by bryder2162 on 2008-06-03
So, this Windows software will allow me to access all the files on Linux???...such as email??? and other saved items?

---

### Post by Slim Odds on 2008-06-03
> **bryder2162 said:**
> So, this Windows software will allow me to access all the files on Linux???...such as email??? and other saved items?

For access, you should be able to just boot the LiveCD and mount the partition(s).

---

### Post by bryder2162 on 2008-06-03
I installed that utility that allowed me to mount my Linux drives on Windows...I can now access at least the documents I had saved..but not any email.  I was using Evolution.  Any idea how to access those files.

2.  Make Ubuntu bootable again????  Can't start in recovery mode nor normal mode...that is why I was trying to use the 8.04 CD to upgrade with via booting my computer from it.  I tried the 7.10 alternate CD to boot with in hopes of repairing Ubuntu, but it gets stuck at one point and won't do anything afterwards.  My hard drive and master CD drive are SATA.  My new motherboard uses the nForce 570/550 chipset and has a nVdidia 8000 series graphic card.

---

### Post by aysiu on 2008-06-03
I've merged these two threads so we can streamline the help a little here.

Your Evolution email should be stored in /home/*username*/.evolution

Note that directories and files beginning with a . are hidden directories and files, so be sure to enable a view that let's you see hidden files and folders.

---

### Post by bryder2162 on 2008-06-04
Thanks...I now have access to a much of Evolution files which I assume can be read with Notepad.  What about getting my Ubuntu working????

---

