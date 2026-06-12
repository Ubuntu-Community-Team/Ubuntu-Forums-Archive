---
title: "Dpkg makes my Linux frozen"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by mulanee on 2008-11-03
Hi,

When I launch my update manager , I get a lot of items to update.
But If I launch the update process , I get ```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```
I try to launch dpkg --configure -a , but some seconds after , my hard disk play always the same thing and my PC becomes frozen.
I need to switch OFF .
I can't reinstall dpkg because it needs itself.
Here is my df:
```
Sys. de fich.           1K-blocs       Occupé Disponible Capacité Monté sur
/dev/sda1              5083680   4029860    795580  84% /
varrun                  192764       224    192540   1% /var/run
varlock                 192764         0    192764   0% /var/lock
udev                    192764        68    192696   1% /dev
devshm                  192764         0    192764   0% /dev/shm
/dev/sda3              9116560   5644656   3008832  66% /home
/dev/sdf1            488264768 206414080 281850688  43% /media/LaCie

```

I run xubuntu 8.04.1

Thanks for your next help , with simple words please.

---

### Post by Pumalite on 2008-11-03
Post the output of:
sudo dpkg --configure -a

---

### Post by mulanee on 2008-11-04
I don't have the output ; I remember it's only one or two lines , talking about depmod without any error message , just ...nothing.After some hours , I stop the power.
Here is my last dpkg.log:
```
2008-11-01 12:54:27 startup packages configure
2008-11-01 12:54:28 configure libdbus-1-3 1.1.20-1ubuntu3.1 1.1.20-1ubuntu3.1
2008-11-01 12:54:28 status unpacked libdbus-1-3 1.1.20-1ubuntu3.1
2008-11-01 12:54:28 status half-configured libdbus-1-3 1.1.20-1ubuntu3.1
2008-11-01 12:54:28 status installed libdbus-1-3 1.1.20-1ubuntu3.1
2008-11-01 12:54:28 status triggers-pending libc6 2.7-10ubuntu4
2008-11-01 12:54:29 configure linux-headers-2.6.24-21 2.6.24-21.42 2.6.24-21.42
2008-11-01 12:54:29 status unpacked linux-headers-2.6.24-21 2.6.24-21.42
2008-11-01 12:54:29 status half-configured linux-headers-2.6.24-21 2.6.24-21.42
2008-11-01 12:54:29 status installed linux-headers-2.6.24-21 2.6.24-21.42
2008-11-01 12:54:29 configure jockey-common 0.3.3-0ubuntu8.1 0.3.3-0ubuntu8.1
2008-11-01 12:54:29 status unpacked jockey-common 0.3.3-0ubuntu8.1
2008-11-01 12:54:29 status half-configured jockey-common 0.3.3-0ubuntu8.1
2008-11-01 12:54:40 status installed jockey-common 0.3.3-0ubuntu8.1
2008-11-01 12:54:41 configure cupsys-common 1.3.7-1ubuntu3.1 1.3.7-1ubuntu3.1
2008-11-01 12:54:41 status unpacked cupsys-common 1.3.7-1ubuntu3.1
2008-11-01 12:54:41 status half-configured cupsys-common 1.3.7-1ubuntu3.1
2008-11-01 12:54:41 status installed cupsys-common 1.3.7-1ubuntu3.1
2008-11-01 12:54:41 configure hal-info 20081001-0ubuntu1~hardy1 20081001-0ubuntu1~hardy1
2008-11-01 12:54:41 status unpacked hal-info 20081001-0ubuntu1~hardy1
2008-11-01 12:54:41 status half-configured hal-info 20081001-0ubuntu1~hardy1
2008-11-01 12:54:41 status installed hal-info 20081001-0ubuntu1~hardy1
2008-11-01 12:54:41 configure dbus 1.1.20-1ubuntu3.1 1.1.20-1ubuntu3.1
2008-11-01 12:54:41 status unpacked dbus 1.1.20-1ubuntu3.1
2008-11-01 12:54:41 status unpacked dbus 1.1.20-1ubuntu3.1
2008-11-01 12:54:41 status unpacked dbus 1.1.20-1ubuntu3.1
2008-11-01 12:54:41 status unpacked dbus 1.1.20-1ubuntu3.1
2008-11-01 12:54:41 status unpacked dbus 1.1.20-1ubuntu3.1
2008-11-01 12:54:41 status half-configured dbus 1.1.20-1ubuntu3.1
2008-11-01 12:54:47 status installed dbus 1.1.20-1ubuntu3.1
2008-11-01 12:54:47 configure linux-libc-dev 2.6.24-21.42 2.6.24-21.42
2008-11-01 12:54:47 status unpacked linux-libc-dev 2.6.24-21.42
2008-11-01 12:54:47 status half-configured linux-libc-dev 2.6.24-21.42
2008-11-01 12:54:47 status installed linux-libc-dev 2.6.24-21.42
2008-11-01 12:54:47 configure linux-headers-2.6.24-21-generic 2.6.24-21.42 2.6.24-21.42
2008-11-01 12:54:47 status unpacked linux-headers-2.6.24-21-generic 2.6.24-21.42
2008-11-01 12:54:48 status half-configured linux-headers-2.6.24-21-generic 2.6.24-21.42
2008-11-01 12:54:48 status installed linux-headers-2.6.24-21-generic 2.6.24-21.42
2008-11-01 12:54:48 configure linux-image-2.6.24-21-generic 2.6.24-21.42 2.6.24-21.42
2008-11-01 12:54:48 status half-configured linux-image-2.6.24-21-generic 2.6.24-21.42
2008-11-01 13:06:32 startup packages configure
2008-11-01 13:06:32 configure linux-image-2.6.24-21-generic 2.6.24-21.42 2.6.24-21.42
2008-11-01 13:06:32 status half-configured linux-image-2.6.24-21-generic 2.6.24-21.42
2008-11-03 07:34:06 startup packages configure
2008-11-03 07:34:06 configure linux-image-2.6.24-21-generic 2.6.24-21.42 2.6.24-21.42
2008-11-03 07:34:07 status half-configured linux-image-2.6.24-21-generic 2.6.24-21.42
```

---

### Post by Pumalite on 2008-11-04
Post:
uname -a

---

### Post by mulanee on 2008-11-08
> Linux box 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux


Thank you for help

---

### Post by Pumalite on 2008-11-08
sudeo apt-get -f install
sudeo apt-get update
sudo apt-get dist-upgrade

---

### Post by mulanee on 2008-11-08
This is the problem:I can't apt-get:
```
root@box:~# sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

```

---

### Post by mulanee on 2008-11-10
Any idea?

I don't believe the ultimate choice is to format and reinstall as windows..?

Or is it?

---

### Post by Pumalite on 2008-11-10
Run:
sudo dpkg --configure -a
And then, the rest of the commands I gave you.

---

### Post by mulanee on 2008-11-10
> Run:
sudo dpkg --configure -a
When I do that , I lose the hand , system becomes frozen , hours after I need to switch off

---

### Post by Pumalite on 2008-11-10
Check the status of dpkg in /var/lib/dpkg/status
Report back.

---

### Post by mulanee on 2008-11-11
Here it is:
[http://www.ebgy.freesurf.fr/tempo/status.htm]("http://www.ebgy.freesurf.fr/tempo/status.htm")

---

### Post by mulanee on 2008-11-14
Any idea apart format and reinstall?

Thank you

---

### Post by mulanee on 2008-11-14
This is what I get in console , without x session:
> ata1.00 status:{DRDY err} error:{UNC}
exception Emask 0x0 action 0x0 SErr 0x0 action 0x0
BMDA stat 0x25
cmd c8/00:08:8f:77:5d/00:00:00:00:00/e0 tag0 dma 4056

Any idea?

---

### Post by batty_whol on 2008-11-14
I've got similar issues after the same upgrade on an AMD64 Dual Core with 4 SATA drives.

Sounds like we may both be having a hard disk failure.

See 
[http://ubuntuforums.org/showthread.php?p=6110341#post6110341](http://ubuntuforums.org/showthread.php?p=6110341#post6110341)

batty

---

### Post by mulanee on 2008-11-14
I've got no boot issue.
I will try to boot on a live cd and to chkdsk the HD.

---

### Post by batty_whol on 2008-11-14
On scanning disks - some suggestions (some plagerised from psusi - ta!)
Replace sdX with the name of your disks e.g. hda or sda.
Replace # with partition number e.g hda1 or sda1

fsck will run a file system check. Must be run against the device that the file system is mounted on, but not when the filesystem is mounted.
fsck /dev/sdX#                          Run this command against each partition.
fsck /dev/sdX# -y                       Only use this one if you are getting lots of
                                        errors from the previous one. It will answer
                                        yes to all of the questions.

smartctl provides info on disc, and can run tests.
smartctl -a /dev/sdX                    Run this command against each disk.
smartctl -t long /dev/sdX               Run this command against each disk
smartctl -l selftest /dev/sdX           I believe this command gets the output from the
                                        previous one.

badblocks will look for badblocks
badblocks -v /dev/sdx                   These may take a long time (hours if your
or                                      discs are 100's of Gb.
badblocks -v /dev/sdX# 

to fix any badblocks use
e2fsck -vc /dev/sdX#

I hope this helps.
Anyone else feel free to add in other suggestions.

batty

---

### Post by batty_whol on 2008-11-15
Actually, ignore the badblocks suggestions.

Just run
e2fsck -vc /dev/sdX# -y

It's much quicker, and it will add the badblocks to a list at the same time.

---

### Post by mulanee on 2008-11-15
How to umount , sda1 file (system) and sda3 are shown as "in use"?

I can't smartctl because I don't have the packet and I can't apt-get

---

### Post by batty_whol on 2008-11-15
Do you have a live Linux CD to boot from? The original Ubuntu CD / DVD will do for this.

Put the CD in, reboot, if there is an option for a boot menu, select that an choose boot from CD/DVD.

When you have booted from CD you will be in a very basic linux system. 
From here none of your discs will be mounted, and therefore can be checked.

If you haven't got smartctl, then use the command
apt-get install smartctl 
(I think smartctl is the package, it may be smartmon).

Hope this helps

---

### Post by mulanee on 2008-11-15
Ok,I will boot on xubuntu 8.10 live CD I own.

I can't apt-get because I get the "dpkg --configure -a" of the death

---

### Post by batty_whol on 2008-11-15
If you have booted from a CD, then there shouldn't be a problem with running apt-get (as long as there is space to install stuff - i.e. on the ramdisk). Don't forget you will not be running from the (currently) broken xubuntu install, but from the (should be) ok CD version of it.

---

