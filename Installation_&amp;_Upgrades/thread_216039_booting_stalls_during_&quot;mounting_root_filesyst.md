---
title: "booting stalls during &quot;mounting root filesystem&quot; -  testing workaround(s)"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by ubuntu_demon on 2006-07-14
**This is regarding the "booting stalls during mounting root filesystem" bug. This thread is for testing workaround(s) only. Everything is on your own risk.**

You can find more information about this bug here :

**booting stalls during "mounting root filesystem"?**
[http://www.ubuntuforums.org/showthread.php?t=197956](http://www.ubuntuforums.org/showthread.php?t=197956)
[http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11](http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11)
[http://www.ubuntuforums.org/showpost.php?p=1098541&postcount=41](http://www.ubuntuforums.org/showpost.php?p=1098541&postcount=41)
[http://www.ubuntuforums.org/showpost.php?p=1231460&postcount=62](http://www.ubuntuforums.org/showpost.php?p=1231460&postcount=62)
[http://ubuntuforums.org/showthread.php?t=212839](http://ubuntuforums.org/showthread.php?t=212839)
[http://www.ubuntuforums.org/showthread.php?t=186115](http://www.ubuntuforums.org/showthread.php?t=186115)
[http://www.ubuntuforums.org/showthread.php?t=208207](http://www.ubuntuforums.org/showthread.php?t=208207)

**WORKAROUND**

[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/69](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/69)

> **Paul Sladen]
For those still wondering said:**
> 

Some additional explanation :

Replace sdX for sda, sdb, sdc, sdd, hda,hdb,hdc,hdd or whatever gparted on the livecd tells you it is.

You have to put the UUID in /boot/grub/menu.1st. For example :

```

title           Ubuntu, kernel 2.6.15-26-686
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-26-686 root=UUID=d4c51a2a-d93f-4dc1-8717-9c3cdb4d41ce ro vga=0×31a
quiet splash
initrd          /boot/initrd.img-2.6.15-25-686
savedefault
boot

```

You probably have to edit your fstab in order for it to use UUID's too. Here's an example fstab (created by an upgrade during edgy) :
[http://www.ubuntuforums.org/showpost.php?p=1301131&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1301131&postcount=1)

**WORKAROUND**

Here is another workarounds (which needs testing) :
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83)

[quote=Scott James Remnant]
Another obvious workaround, for anyone affected ... install the following packages:

[http://archive.ubuntu.com/ubuntu/pool/main/u/udev/libvolumeid0_093-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/libvolumeid0_093-0ubuntu3_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/u/udev/volumeid_093-0ubuntu9_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/volumeid_093-0ubuntu9_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_093-0ubuntu9_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_093-0ubuntu9_i386.deb)

(replace i386 with your architecture if different)



You can post (meaningful) results either on launchpad or in this thread.

---

### Post by markc on 2006-07-16
Not sure if this is "meaningful" or not, probably not, but I am trying to boot up on a 2.6.18-rc1 kernel and am now getting this same error. What is really weird is that I tried this workaround and applied the UUID to my grub entry and it worked the first time I rebooted. However, once rebooted I could not start KDE properly as it hung on restarting sessions. Now, 1/2 an hour later when I go to reboot again I am simply getting the original "Begin: Waiting for root file system ..." again. So the point of this messsage is that this workaround did kind of work for me but now it doesn't.

Why 2.6.18-rc1 ? My hsfmodem requires at least kernel 2.6.16, my Audigy LS card requires at least Alsa 1.0.11 which comes with 2.6.17 and to mount my V3X phone as a USB devices requires a patch to 2.6.18-rc1. For all the time I've wasted trying to get this kernel to work, and I haven't even started on the Nvidia module, I may as well switch back to Gentoo and have KDE 3.5.3, amaroK 1.4.1, Koffice 1.5.3 and a seemless kernel/nvidia upgrade path ](*,)

---

### Post by ronly on 2006-07-16
I've tried that but unfortunately it didn't work. I don't remember the error message precisely but it was along the lines of:
/dev/uuid-(something I don't remember)/(the uuid)
not found

Any news on a new release of dapper?

---

### Post by Kaervek on 2006-07-16
I've been scouring the web (both these forums and #ubuntu) trying to find a solution to the following problem:

I have successfully installed Ubuntu and have been dual-booting with WinXP MCE for a few days now.  However, when I added my other harddrives, Ubuntu would refuse to boot while XP didn't have a problem.  Ubuntu would boot without an issue if the *only* drive installed was the system drive (which has 3 partitions: 1 windows, 1 ubuntu and 1 swap).

I went ahead and edited the bootstring from GRUB with the UUID of my particular device, and things are working great now.  I hope that anybody that runs across the same issue I've had can finally figure things out with your help.

Thanks alot!

---

### Post by markc on 2006-07-17
> **ronly said:**
> I've tried that but unfortunately it didn't work. I don't remember the error message precisely but it was along the lines of:
/dev/uuid-(something I don't remember)/(the uuid)
not found

It's possible then you didn't provide the UUID exactly in this manner, with the double "=" and no spaces in between. Just a long shot.

```
root=UUID=d4c51a2a-d93f-4dc1-8717-9c3cdb4d41ce
```

---

### Post by ajarufe on 2006-07-17
Stalls for 1:15 using UUID which is a slight improvement (1:45 without UUID).  I'm using a Thinkpad T60 and This issue seems to occur only with the newer (post 2.6.15-23) 686 Kernels.

---

### Post by ronly on 2006-07-18
I got it right when I tried with UUID but it didn't work. However, I have gotten booting to work with "acpi=off irqpoll" and disabling legacy USB support in the BIOS. I had already tried that previously but now it all of a sudden worked (the only thing that has changed is my cdrom drive since it broke down and I got a replacement but it seems strange that it affected this, if it did). So right now I'm contemplating whether I should install a new system and set that to always have those options or whether I should wait for a better fix - my current still has dependency problems and quite a few things installed that I don't need so I think that a fresh install is worth the trouble if I can do it safely and will be able to install whatever fixes become available in that later so that those boot options won't be needed anymore. I'm also wondering whether it's possible to enable acpi once you have your system running since I presume that acpi being disabled is the reason why my computer won't power off automatically - it's not that I'm too lazy to press the power button myself but I use it to record TV programmes as well when I'm not at home and would like to be able to set "at (whenever recording has finished) shutdown" to turn it off but that is obviously not possible now.

---

### Post by xicosm on 2006-07-18
Hey all!

I just started with Ubuntu and the first thing I got was this problem.

I tried lots of things that were suggested in another topic and none of them worked for me.

What did work was hitting F6 and putting just "irqpoll" just this in the end of the options and runs great!

---

### Post by John.Michael.Kane on 2006-07-19
ubuntu_demon does this issue affect users who are using just (**one ide-dvd/rw and one sata2 HD**)

---

### Post by ubuntu_demon on 2006-07-20
> **SD-Plissken said:**
> ubuntu_demon does this issue affect users who are using just (**one ide-dvd/rw and one sata2 HD**)
This bug doesn't effect all systems. It probably depends on the combination of hardware in your system.

I have one dvd-rom , one cd-rw and a dvd-rom and the issue affects my system.

---

### Post by Fr@nKy on 2006-07-20
BTW does this still happens on Edgy? (I'm tired of not being able to use Linux, the only UNIX based system that works id *BSD, there's not onle single Linux Distribution I tried that doesn't have this stupid problem.)

---

### Post by Fr@nKy on 2006-07-20
Quote:Originally Posted by Paul Sladen 
For those still wondering; The workaround for this issue involves specifying the partition to boot from by ID, rather than the transient location:

1. Boot a desktop/LiveCD.
2. Run sudo /sbin/dumpe2fs /dev/sdX | grep UUID
3. tell 'grub' or 'lilo' to boot with that ID:

linux ... root=UUID=d4c51a2a-d93f-4dc1-8717-9c3cdb4d41ce

and also adjust this in:

/boot/grub/menu.lst

Ubuntu Demon where to I put this " sudo /sbin/dumpe2fs /dev/sdX | grep UUID " when booting the LiveCD(DesktopCD)??

---

### Post by ubuntu_demon on 2006-07-20
> **Fr@nKy said:**
> Quote:Originally Posted by Paul Sladen 
For those still wondering; The workaround for this issue involves specifying the partition to boot from by ID, rather than the transient location:

1. Boot a desktop/LiveCD.
2. Run sudo /sbin/dumpe2fs /dev/sdX | grep UUID
3. tell 'grub' or 'lilo' to boot with that ID:

linux ... root=UUID=d4c51a2a-d93f-4dc1-8717-9c3cdb4d41ce

and also adjust this in:

/boot/grub/menu.lst

Ubuntu Demon where to I put this " sudo /sbin/dumpe2fs /dev/sdX | grep UUID " when booting the LiveCD(DesktopCD)??

You put the UUID in /boot/grub/menu.1st.

For example :

```

title           Ubuntu, kernel 2.6.15-26-686
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-26-686 root=UUID=d4c51a2a-d93f-4dc1-8717-9c3cdb4d41ce ro vga=0×31a
quiet splash
initrd          /boot/initrd.img-2.6.15-25-686
savedefault
boot

```

I haven't tried the workaround myself yet. Didn't have time yet.

---

### Post by jmbarbier on 2006-07-21
Same symptoms for me, on a noname (microstar i think) laptop (PIV, 1Go ram, only 1 ide HD and 1 ide CD/DVD). 

Tried changing root on grub trick => No difference
Tried using UUID for root => No difference

BUT 
Tried other kernels, and things became better..

Using 2.6.15-26-386 => ALERT! /dev/hda1 does not exist
Using 2.6.15-26-686 instead, or 2.6.15-23-386 made the system work well.
Using 2.6.12-10-386, something segfaults multiple times during boot, and then gives me the ALERT! /dev/hda1... funny : 2.6.12-9-386 is OK..

Bad bug in kernel ????](*,)

---

### Post by ubuntu_demon on 2006-07-26
I editted my first post.

Here's a related thread about UUID's :
[http://www.ubuntuforums.org/showthread.php?t=223182](http://www.ubuntuforums.org/showthread.php?t=223182)

---

### Post by Benjamin_Lebsanft on 2006-07-26
how do I edit my grub entry? My grub doesn't show anything, not the list of the kernels etc. only a blinking "_" but the menu is there but not shown. Recovery mode doesn't work either.

---

### Post by ubuntu_demon on 2006-07-26
> **Benjamin_Lebsanft said:**
> how do I edit my grub entry? My grub doesn't show anything, not the list of the kernels etc. only a blinking "_" but the menu is there but not shown. Recovery mode doesn't work either.
Use a livecd , mount your root partition and :
$sudo gedit /mounteddrive/boot/grub/menu.1st

This thread is about testing workarounds. This is not a thread for support. If you need additional help please use this thread instead :

booting stalls during "mounting root filesystem"
[http://www.ubuntuforums.org/showthread.php?t=186115](http://www.ubuntuforums.org/showthread.php?t=186115)

---

### Post by Azriphale on 2006-07-29
I just tried this with a 2.6.15-26-386 with no change (or maybe the wait got a little longer...)

I am installing the 26-686 kernel to see if it helps then.

---

### Post by Azriphale on 2006-07-29
I installed 2.6.15-26-686 kernel, and it still takes a few minutes to mount the root FS. After waiting for a couple of minutes, i hit ctrl+alt+del to reboot and use the 2.6.15-26-386 kernel again (which suffers from this problem somewhat less - a 20 second wait, for me).

I see no improvement at all. Reverting to /dev/sdaX label in grub and fstab.

---

### Post by ryanmbruce on 2006-08-06
I tried using the workaround you described, but there were a couple problems:

First, dumpe2fs doesn't work on reiserfs(v3).  I don't know an alternative method to get the uuid of my partitions if they are reiserfs. I'm also using LVM, and I'm not sure, but this may be complicating my problem.

To test using an alternative uuid when booting grub, I wrote down all the uuids inside /dev/disk/by-uuid/ and tried each of them in the root=UUID=* part of the kernel boot options.  This didn't seem to fix anything.  Assuming the correct uuid was in that list, and I correctly inserted it into the boot options, shouldn't it mount the root partition?

---

### Post by John.Michael.Kane on 2006-08-06
Those who are still having issues even with using the workaround should include you spec's. theres alot of factors that come into play with this issue as not everyone expriences it. the combinations are endless.

using a 1+1 setup 1-sata 1-ide devices be it dvd/cd/hdd
or
using a 2+2 setup 2-sata 2-ide devices be it 2-sata hdd 1-ide hdd 1-dvd-rw

I would ask anyone trying to test this workaround to use the 1+1 method. **[COLOR="Red"]1-ide dvd-rw with 1-sata hdd[/COLOR]** before trying it with massive amounts of drives.

---

### Post by ryanmbruce on 2006-08-06
I think my problem may be slightly different, but I will continue posting in this thread until I'm sure.

When I try to boot with the default grub string, the root partition will not mount, and I am dropped to a busybox shell.  In this shell, if I do 'ls /dev/disk/by-uuid' there are only two entries, and neither of them are the uuid that is in my grub string.

If I boot using a dapper pre-release live cd and run 'blkid' I can see that the root partition has the same uuid as the entries in my menu.lst.

What is the reason that an entry would not be created in /dev/disk/by-uuid for my root or swap partitions?  It has something to do with LVM.  The following thread seems to be similar to my experience:
[http://www.ubuntuforums.org/showthread.php?t=224904](http://www.ubuntuforums.org/showthread.php?t=224904)

All my drives are ide.  I have two disks, a dvd burner, and a cdrom.  On my primary drive, I am using LVM with separate boot, root, and swap partitions.  On my second drive, I have a single ext3 partition. My root partition is reiserfs, and everything else is ext3(or swap).

[EDIT]
This was an incarnation of the UUID bug afterall, and was fixed by using the work around where you must replace 'root=UUID=*' with  'root=/dev/mapper/Ubuntu-root' in the kernel boot options.

---

### Post by mirak63 on 2006-08-06
I use LVM to and rarely boot on edgy, but it was messed.
edgy changed the grup configuration, and put a path for the kernel that have nothing to with LVM or UUID. It's just wrong.
Even if edgy is a developpement version, that's going to far to commit something that can't even let boot most of the installations. :/

---

### Post by cracker on 2006-08-06
I have found a solution to the issue where the LiveCD stalls at "Mounting root filesystem" and/or "Adding liveCD user". I have tried two different drives. On the older drive, it would hang at mounting root filesystem. I bought two brand new BenQ DVD burners, and found that it hangs at Adding LiveCD user. The solution is to switch to TTY1 as soon as "Mounting Root Filesystem" shows up. The system just hangs if you let it be, but if you switch to TTY1 by pressing Alt+F1 as soon as the text shows up in the semi-graphical mode, the system boots successfully in a normal fasion. I hope this will help someone else.

---

### Post by KenF on 2006-08-12
Some news and a random comment.

1.  News.  I've just read the thread:
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367]("https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367")

Fixes are not going to be moved into dapper.  This means that the "solutions" are:
a.  Workarounds as above.
b.  Downgrade to breezy.
c.  Move to edgy

2.  The scope is not narrow.  Could really turn newbies off of ubuntu.
My hardware isn't special.  My guess is that this will be a continual issue for dapper.  My case:
a.  Upgrade/install dapper.  All is fine.  Great actually!
b.  Buy removable HD.
c.  If removable HD is plugged in before boot.  It won't boot.  If HD is hotplugged ... all is fine.  Minor problem in my case.

While my problem is minor.  This has got to be a PITA for anyone setting up RAID, etc.

3.  I still kind of wonder if my problem isn't more related to:

[http://lkml.org/lkml/2005/12/3/192]("http://lkml.org/lkml/2005/12/3/192")

Any comments on 3?

Thanks,

KenF

---

### Post by ubuntu_demon on 2006-08-12
I had to repartition my harddrive because I removed windows. I decided to keep only my /home partition and reinstall. Now update-grub sees my harddrive also as /dev/hde. So I don't have to edit my /boot/grub/menu.1st anymore after each kernel upgrade.

I also tried the workaround :

> 
sudo /sbin/dumpe2fs /dev/hde | grep UUID
dumpe2fs 1.38 (30-Jun-2005)
/sbin/dumpe2fs: Bad magic number in super-block while trying to open /dev/hde


---

### Post by ubuntu_demon on 2006-08-12
> **KenF said:**
> Some news and a random comment.

1.  News.  I've just read the thread:
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367]("https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367")

Fixes are not going to be moved into dapper.  This means that the "solutions" are:


True. I am waiting a couple of days before announcing this to give people a chance to reply (in the comments on the bug).

> **KenF said:**
> 
a.  Workarounds as above.


Or using other workarounds.

Having problems with installing or upgrading to Dapper? Here are some fixes
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)


> **KenF said:**
> 
b.  Downgrade to breezy.


**DON'T** do this. It's not possible to reliably downgrade. Reinstalling Breezy is ofcourse possible.

> **KenF said:**
> 
c.  Move to edgy


**Don't** use Edgy as a primary desktop. You should at least wait until a RC or beta is available. Edgy Knot 1 and 2 are definetely not suitable for average users since you can lose all your data if you are unlucky.

**Don't use Edgy as your primary (desktop) OS / helping testing**
[http://www.ubuntuforums.org/showthread.php?t=215581](http://www.ubuntuforums.org/showthread.php?t=215581)

---

### Post by WiseSalesman on 2006-08-19
I have this issue with my setup, and I am an absolute Linux newbie. 

System is:
P4 1.7ghz
384 MB ram

On system board:
120GB hdd - Linux Install - primary master
60GB hdd - WinXP Install - primary slave
DVD-RW - Secondary Master
DVD-ROM - Secondary Slave

On a PCI IDE card:
250GB hdd - Data

Ubuntu Dapper boots fine (like now) as long as the IDE adapter (and, consequently, the 250GB hdd) are removed. If they are plugged in and enabled, Ubuntu reads the PCI controller as /hda/, and what should be read as /hda/ (the 120GB hdd) as /hde/. So the dillema is that I can only make the OS work if I slightly cripple my system.

Messing around with the coding and UUIDs seems to be a little beyond me (although i'm willing to give it a shot, eventually), so I was heartened to see that the following was posted in the initial [bug report]("https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/+index"):

> 

Another obvious workaround, for anyone affected ... install the following packages:

[http://archive.ubuntu.com/ubuntu/pool/main/u/udev/libvolumeid0_093-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/libvolumeid0_093-0ubuntu3_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/u/udev/volumeid_093-0ubuntu9_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/volumeid_093-0ubuntu9_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_093-0ubuntu9_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_093-0ubuntu9_i386.deb)

(replace i386 with your architecture if different)


I decided to try this workaround, as it seemed more straight-forward and easy to understand (install a couple packages and you're done?). My problem is that when I download and attempt to install these, the package installer gives me "Error: Dependency not satisfiable: libc6". 

Attempting to install the package manually returns:
> dpkg: dependency problems prevent configuration of libvolumeid0:
 libvolumeid0 depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
dpkg: error processing libvolumeid0 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libvolumeid0


So I downloaded libc6_2.4-1ubuntu9_i386.deb from [here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fglibc%2Flibc6_2.4-1ubuntu9_i386.deb&md5sum=a2d6aa17d6307d0af295a504edff06a2&arch=i386&type=main") and installed it manually, but that just caused Synaptic to tell me my packages were broken, and didn't REALLY fix anything.

Even though Synaptic says my system is completely up-to-date, I've tried reinstalling libc6 and anything with a name similar to libc6. If I can't get support for my PCI card working, I can't use Ubuntu, and am stuck with WinXP.

Uh.... help, please? 

Also - is this the right place for this question? Should I have just created a new thread?

---

### Post by ubuntu_demon on 2006-08-22
Here is another workaround (which needs testing) :
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83)

---

### Post by WiseSalesman on 2006-08-22
> **ubuntu_demon said:**
> Here is another workaround (which needs testing) :
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83)

See my above post for my results when testing this workaround.

---

### Post by John.Michael.Kane on 2006-08-22
So how is this issue playing out for most?

I have a sata drive on order for use with an nvidia NF4 based board.

---

### Post by Cloud[01] on 2006-08-30
Using the workaround of putting the UUID doesn't work.

If before I got an error message like:
```
ALERT! /dev/sda2 does not exist. Dropping to a shell!
```
(/dev/sda1 is swap)

After tryign the workaroung I get:
```
ALERT! /dev/disk/by-uuid/[MY-UUID] does not exist. Dropping to a shell!
```

The UUID btw seems to be impossible to get with:
```
sudo /sbin/dumpe2fs /dev/sda | grep UUID
```

instead with:
```
sudo /sbin/dumpe2fs /dev/sda2 | grep UUID
```
(note: we explicitly point to the / partition and not to the disk itsefl)

Hope my comments are somehow useful to someone, still the problem remains and I'm unable to boot UBUNTU! :(

I'll try edgy, having something buggy but that does boot is better than having something which doesn't boot at all!

-Claudio

---

### Post by mxreader on 2006-08-30
I'm not new to Ubuntu, but still a dummy when it comes to configuring things manually. My system is 1xIDE, 1xSATA and 1xDVD-RW.  XP resides completely on IDE, and I have tried to set up dualboot putting Ubuntu completely on the SATA drive.  I got this problem since the previous version, so for a few months used only XP, with a "stable" new version I thought it should be solved so installed 2.6.15-23-386 (6.0.6 LTS) rebooted between it and XP fine.  Turn off PC and tried to reboot to Ubuntu the next day... same problem as previous version.

After reading what is said here about the workaround... that doesnt work... looks like I will be on XP until the next version of Ubuntu again.

---

### Post by John.Michael.Kane on 2006-08-31
@ubuntu_demon just to update you.

I have just installed a sata hd using 1hd+1dvd drive,and ubuntu installed with no issues.the sata hd is seen as sda1. 

the install was on a biostar tforce 939 with nf410/6100 chipset

Note: I have not tried to install 1-ide hd + sata hd + dvd drive.



@mxreader if you can try installing with only the sata-hd+DVD-RW,and disconnect the ide hd.

---

### Post by Cloud[01] on 2006-09-01
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83)

About this workaround I'm a bit sceptic, .deb linked in the comment are no longer present, still you can find all of them, with a trailing 13 after the name. Ok for that. 

BUT!

Installing these requires LOTS of libraries to be upgraded to versions that would be ready with edgy, so basically, inistalling these packages or installing edgy I think gives the same probability of crash (as Edgy is not yet in beta, as ubuntu_demon pointed out).

BTW: for all of you who would like to try this workaround all you have to do is booting your favourite live distro and chroot to your mounted hard drive containing the installation of choice:

```

mkdir /mnt/ubuntu
mount /dev/sdXY /mnt/ubuntu
chroot /mnt/ubuntu
dpkg -i PACKAGEDOWNLOADED.deb
```

Note: Installing via dpkg doesn't get all the REQUIRED dependencies, so those 3 packages won't work, you would need other dependencies, one way to install them with dependencies:

```

apt-get install 3PACKAGESLISTEDINTHECOMMENT
```

Note2: for this to work you should place edgy repositories in your sources.lst file (/etc/apt/sources.lst) otherwise the packages listed in the comment aren't available

FINALLY: Doing this is not worthwhile (in my opinion) and didn't work for me, I've (as stated in the post above) installed Edgy, and testing, still I would have preferred a *more* stable release, but since I can't get this to work...

ciop ciop

---

### Post by bhowell on 2006-09-01
> **ubuntu_demon said:**
> Here is another workaround (which needs testing) :
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83)


This workaround got me back in action. 

I'm on an AMD64 Gateway laptop with internal IDE disk and DVD.

---

### Post by newrikk on 2006-09-02
Hello, I tried the workaround as explained in the first post, with the UUID in the GRUB menu. My system now mounts the root filesystem without any problem, but it's the only partition that is mounted , even my swap isn't mounted anymore :(  . And I can't get the UUID from my swap partition , maybe there is not any.
really boring ... :frown:

---

### Post by John.Michael.Kane on 2006-09-02
newrikk if you could not get this method to work you may have one of two options. 

Install edgy eft alpha **provided your system is not used for production work**
Or:
Try another distro to see if it works with your hardware at this time.

**Note:** there's is talk that there's a  fix for this in edgy.

---

### Post by Fnx on 2006-09-02
> **ubuntu_demon said:**
> [B]
Some additional explanation :[/B]
Replace sdX for sda, sdb, sdc, sdd, hda,hdb,hdc,hdd or whatever gparted on the livecd tells you it is.
You have to put the UUID in /boot/grub/menu.**l**st. For example :


For me X in hdX had to be replaced by a letter and a figure (number of the partition) like in hda1, hde1.
It is also to be noted that /sbin/dumpe2fs gives UUID only for ext2 or ext3 filesystems. I don't know what to use for reiserfs, fat32 or ntfs.

EDIT: some useful information concerning use of UUID address on  [http://forum.ubuntu-fr.org/viewtopic.php?id=43968](http://forum.ubuntu-fr.org/viewtopic.php?id=43968)

---

### Post by monkey man on 2006-09-03
I, unfortumnatly, could not get the UUID fix to work. My system became unbootable after upgrading from breezy to dapper using update-manager.

I have 1 SATA drive on a Promise controller and one DVD writer as primary master. Same problem as above, re drive assignments, but I have found this is only a problem with kernel images newer than 2.6.15-25-k7. This kernel, and others released before it, work fine. It's only on an upgrade to a newer kernel that this becomes an issue for me.

---

### Post by newrikk on 2006-09-03
> **Fnx said:**
> For me X in hdX had to be replaced by a letter and a figure (number of the partition) like in hda1, hde1.
It is also to be noted that /sbin/dumpe2fs gives UUID only for ext2 or ext3 filesystems. I don't know what to use for reiserfs, fat32 or ntfs.

EDIT: some useful information concerning use of UUID address on  [http://forum.ubuntu-fr.org/viewtopic.php?id=43968](http://forum.ubuntu-fr.org/viewtopic.php?id=43968)

Thank you for the link, worked for both my root partition and swap one, but same problem as you, can't get my windows partitions id. 
but we are on the way , I hope :p  .

---

### Post by newrikk on 2006-09-07
> **newrikk said:**
> Thank you for the link, worked for both my root partition and swap one, but same problem as you, can't get my windows partitions id. 
but we are on the way , I hope :p  .

Finally did it, inverted my two disk controllers so that my linux disk is on the first one,  and put the good informations in my /etc/fstab and modified my /boot/grub/menu.lst. and everything was ok. 8)

A little more detailed explanation : got two sata disks, one dedicated to windows who was on sata controller number 1 , and the other for ubuntu on second controller.
Started having problems with "the mounting root filesystem step", solved it with the link to the french forum given on page 4, for both my root and swap partition. 
BUT my windows partitions were not mounted anymore, and the fdisk command was telling me that my linux disk was /dev/sda , instead of /dev/sdb  as before. so I inverted the two disks and modified grub by clicking "e" on th e grub menu screen. 
If someone wants more details, he can email me at : [email]newrikk974@yahoo.fr[/email].
:mrgreen:

---

### Post by thanosx on 2006-09-08
I had a similar problem installing debian etch. Was was worse is that I couldn't see the hda partitions when I used a knoppix live-cd, so that I could implement the ID solution. I was saved by this post, [http://www.experts-exchange.com/Operating_Systems/Linux/Linux_Administration/Q_21594299.html](http://www.experts-exchange.com/Operating_Systems/Linux/Linux_Administration/Q_21594299.html)
which recommended using testdisk. So I booted knoppix, run testdisk, *important* changed the disk geometry settings (heads=255 not 16), then run Analyze, wrote the partition table back, and the system booted like a charm.

As always, take care when messing with the partitions!!!

Hope this helps!

---

### Post by richo132 on 2006-09-09
I encountered this problem while trying to install Dapper on an IBM Netvista A40.
A number of solutions have been suggested in this post, but have given variable results. It seems that boot stall message is a generic symptom of several possible underlying problems. To test this idea, I used another PC to load a working image of Dapper onto /dev/hda of my Netvista and booted in recovery mode. This gives very detailed diagnostic info to monitor the boot process. I was then able to see that, in my case, the boot process stalled with the message "Checking instruction 'hlt'". Research into this indicates that this is a hardware level test designed to trap some unusual condition(s). However it seems that the test itself can be troublesome. With more research, I discovered that the test can be blocked with the boot option "linux no-hlt". This fixed my problem.
To try this solution,

    * boot from the Dapper live/install CD
    * select menu option "Start or Install Ubuntu"
    * press "F6 Other Options"
    * on "Boot Options" line,
      delete 2 hyphens at the end of the line
      append "linux no-hlt"
    * press enter

Good luck.

---

### Post by CoolkcaH on 2006-10-07
I have this problem with an Adaptec SCSI controller, it stalls on "ACPI PCI Interrupt... GSI 18".

I wanted to install the packages suggested by Scott James Remnant (libvolumeid0 etc) but they need libc6 2.4.1 that is only available for Edgy. How can I install them in Dapper 6.06.1 without breaking anything?

---

### Post by ubuntu_demon on 2006-10-08
If you have this problem it's probably easiest to wait for Edgy and install Edgy.

---

### Post by $teve on 2006-10-09
Hi everyone. firstly I would just like to say that I am by no means an expert and that I would simply like to share my experience of this problem...

I've been running ubuntu since warty and overall I have had few problems. I decided to do a clean install of 6.06 on my second hd (hdb) and all seemed to be alright. The drive was split into 4 partitions; 1 is ext3, 1 is a swap and the other two are vfat (fat32). 

After a few normal re-boots (~5-10) the problem struck! At the grub menu I  select ubuntu and the booting process is fine until it reaches the second line of the GUI which says "Mounting root partition" (I think :???: ). At this point it switches back to the command line interface and reports the following errors: 
mount: Mounting /dev/hdb1 on /root failed: Invalid Argument
...
Traget filesystem doesn't have /sbin/init
...
/bin/sh: cant access tty; job cntrol turned off

(the  '...' in between the lines are just errors which I've ommited because they are consequences of the lines above)

My workaround:
I booted from my ubuntu live cd and I ran "sudo fsck.ext3 -y /dev/hdb1" at the terminal. Running this commnand reports something like: 
"Group descriptors look bad...trying backup blocks"
It takes a few minutes and then reports that the partition has been modified and displays the fragmentation percentage. When I restart the computer (without the live cd) the problem seems to be solved...HOWEVER, after 5 or so reboots I have the same problem and I have to repeat the abve steps.

One thing I have noticed is that each time I repeat these steps it reports  an addition 0.1% of non-contiguous files i.e. first time it said 1.0% non-contiguous files, then the next time I had to repeat these steps it said 1.1% non-contiguous files and so on...

The above is by no means a permenant fix and probably not the most efficeint way of doing it, however at the least it allowed me to access my files which were before inaccessible.  

Hope this is of any help :D

---

### Post by mjunior on 2006-10-21
I tried the workarround, but got some errors...

Still cannot bott from hd..

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo /sbin/dumpe2fs /dev/sdX | grep UUID
dumpe2fs 1.38 (30-Jun-2005)
/sbin/dumpe2fs: No such file or directory while trying to open /dev/sdX
ubuntu@ubuntu:~$ /boot/grub/menu.lst
bash: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# /boot/grub/menu.lst
-bash: /boot/grub/menu.lst: No such file or directory
root@ubuntu:~#

---

### Post by rpradeep on 2006-11-28
I am using a HP visualize X Class 1GHz workstation and Samsung SH-D162C DVDROM.

Firstly My computer halt at mounting root filesystem and refused to go further. Then I changed the Firmware of DVDROM from TS04 to TS01 then it worked after several Buffer I/O error (ie only delayed the booting)

This also make delays in openning the DVD drive when new CD is inserted on Ubuntu desktop (after installation).

Recently I changed back my Firmware and changed the BIOS settings as follows.

In that i changed the IDE for my cdrom setting from AUTO to CDROM
and disabled UDMA.

Now it's working fine for me.

---

### Post by Lemmus on 2007-01-05
I had the version of this bug where the problem was solved by removing usb-devices during startup.

Finally I managed to solve this by turning off BIOS EHCI Hand-off in the USB-menu in the BIOS. All usb-devices still work at full speed, as far as I can tell. Only difference is that they are not mounted before hotplugging-detections, and therefore are not mounted until after mounting of the root system.
I have a ASUS P5N32-SLI Deluxe. Dunno if other BIOS has support for turning of the hand-off.

Really fought a long time on this one :+)))

---

