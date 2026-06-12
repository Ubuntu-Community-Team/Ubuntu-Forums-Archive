---
title: "Ubuntu Karmic livecd does not detect harddrive."
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by zzzisgood on 2009-11-23
Hi there,
I came across some issues here when upgrading my server from Jaunty to Karmic. The current problem is that Ubuntu Live CD does not detect my Hard Drives. Therefore I can neigher fix the faulty Karmic I installed on the disk earlier(upgraded from a working Januty), nor install a fresh Karmic from scrach.

Here is a brief history of how I got to this point.

Everything started when I tried to upgrade ubuntu from Jaunty to Karmic.

The upgrade finished with no error prompted, but when reboot, problems emerged. The first issue was 

1) Boot failed with error message "**One or more of the mounts listed in /etc/fstab cannot yet be mounted**",  it stopped at one   hard disk that contain /home. After patiently waiting , it reached the recovery shell, pressing ctrl +D ended up the same. Apparently one hard disk that contain /home did not mount.  Then I tried solutions from :[http://creativeinstantia.blogspot.com/2009/11/upgrade-to-karmic-koala-kubuntu-910.html](http://creativeinstantia.blogspot.com/2009/11/upgrade-to-karmic-koala-kubuntu-910.html), and
[http://ubuntuforums.org/showthread.php?t=1318593&page=1](http://ubuntuforums.org/showthread.php?t=1318593&page=1)

change UUID  in fstab and dpkg --configure -a did not work ,  I then commented out mount /home disk and tried to skip it, I created another user in /temphome, rebooted, get the same error, but this time stopped at swap disk. 

2) Checked  fstab again, It did not use UUID for SWAP, so I thought I might tweak it to UUID instead 
Then I tried [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/474720](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/474720)

> 1) get the uuid of your swap partition
 sudo blkid
 example:
/dev/sda1: UUID="d4c3f800-f968-4445-bc32-3151051b1064" TYPE="swap"
 2) edit initramfs:
 sudo gedit /etc/initramfs-tools/conf.d/resume
 so:
 RESUME=UUID=d4c3f800-f968-4445-bc32-3151051b1064
 *** without " " ****
 save and exit.
 3) sudo update-initramfs -k all -u
 4) reboot :)
3)


3)  However, after rebooting I got another error "udevadm trigger is not permitted while udev is unconfigured",  perhaps the SWAP cannot be loaded at all.
> udevadm trigger is not permitted while udev is unconfigured.1
udevadm settle is not permitted while udev is unconfigured.
svgalib: Cannot open /dev/mem.
Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/byuuid/a46dd7c7-2caa-4fce-8941-95892956b121 does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)

Enter 'help' for a list of built-in commands.



What does this imply? I have no idea.

4) Googled an entry at  [https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654](https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654) , attempted to try the solution 
> The solution is to use a live-CD to mount the system (or boot from a completely separate installation), mount the failed OS partition(s), and complete the update process: e.g.
 sudo -i
 # create a target mount point
mkdir /mnt/target
 # mount root
mount /dev/sda8 /mnt/target
# mount boot
mount /dev/sda9 /mnt/target/boot
 # into Jaunty
chroot /mnt/target/
 # update
dpkg --configure -a
 # done
exit
 #unmount
umount /mnt/target/boot
umount /mnt/target


5) However, after downloading and burning a Karmic live cd, it firstly  failed to boot and halt with keyboard indicators flashing, changed another keyboard, successfully logged in. not sure why though, the original keyboards worked with normal boot, but not live cd.

6) After I logged in to Ubuntu from Live CD,  I  cannot see the harddisk at all.

 sudo fdisk -l returns nothing. 

well, I am stuck again. Is there any other solution to 3)? What does it mean?  I cannot find one on the net except 4). 

Wondering if anyone has similar issues,  and how did you solve them? Everything was perfect for upgrade of previous versions on this machine, from fiesty to jaunty, but not this time. 

Anyway, please help if you have any thoughts and experience.
Thanks

---

### Post by zzzisgood on 2009-11-24
Since I cannot find a  way to fix the exiting Karmic on the hard disk,  I attempt to install a fresh one from live CD. However, reinstalling does not work so far, it  failed to recognize my hard disk. The installation wizard  stopped after  Prepare Partition page, which showed no disk/partition at all. click on Forward would prompt "No root file system: No root file system is defined, please correct this from the partitioning menu."  I tried different boot options, still not working.

What's involved to detect and load a hard disk upon booting? Can I do it manually?

Can anyone suggest what  I  should do to proceed, I am totally stuck now

---

### Post by dhavalbbhatt on 2009-11-24
> **zzzisgood said:**
> Now I attempt install Karmic from live CD, but it still failed to recognize my hard disk. The installation wizard  stopped after  Prepare Partition page, which showed no disk/partition at all. click forward would prompt No root file system: No root file sytem is defined, please correct this from the partitioning menu. 

Can anyone suggest what  I  should do to proceed, I am totally stuck now

Can you boot using LiveCD? If you can, then boot into the LiveCD environment. In the LiveCD environment, go to System - Administration - Synaptic

Once in Synaptic, search for "dmraid" and mark the first two dmraid packages for complete removal. This method worked for me.

---

### Post by zzzisgood on 2009-11-24
Thanks for your reply. but NO, removing dmraid does not work for me,  Ubuntu still cannot detect the harddrive.

And another thing is the issue of Keyboard comes back again from time to time. Sometimes Live CD cannot boot, and halt after choosing language. The keyboard has both Caps Lock and Scroll Lock lights constantly flashing, and the screen is blank with no display.

 I tried Intrepid Live CD again, which can detect the HD with no problem. I am starting to think maybe it's better idea to downgrade to Intrepid or Jaunty , just to get the machine work again.  Since I don't seem to be able to solve the issue of upgrading after struggling for two days.

Any suggestion?

---

### Post by zzzisgood on 2009-11-25
It is funny, I can no longer boot into Karmic LIveCD now. Everytime the system halt after I chose language using the keyboard, then nothing happened on screen afterward, except the keyboard indicator flashing. What's going on here????? What makes it so hard to get into Karmic?

---

### Post by wilee-nilee on 2009-11-25
I would assume a gparted cd would be a good start it may detect the HD, and if your is just trying to do a fresh install this may be a method.

---

### Post by zzzisgood on 2009-11-25
I don't quite understand the purpose of using gparted cd.  even if it can detect the HDDs, which I belive still exist as I can see them using Intrepid Live CD, does it ensure that Karmic recogonises them afterwards?   Plus, Karmic Live CD does not work any more somehow even after changing to keyboards. How do I run/install Karmic then? Should I try alternative CD? 

It looks like downgrading to Jaunty is my best option now, although I am reluctant to do it, since I will lose all configs/settings. 

Anybody out there who can help????

---

### Post by dhavalbbhatt on 2009-11-25
Another solution may be to use the alternate installation CD. It is CLI based, but does the job fine, and provides additional options.

---

### Post by zzzisgood on 2009-11-25
Thanks , I am thinking to try the alternative CD. 

However, The problem I was trying to fix in step 3) of the origninal post looks like a long lasting kernel bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/33269?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/33269?comments=all)
[and]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/33269?comments=all")
[ https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/47768]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/33269?comments=all")

Therefore, I have the impression that it's not going to be easy to get around. I might end up with having to reinstall Jaunty then. Bugger.

But hang on, how about the Karmic LiveCD issue (odd halting problem and  HDD issue?), Does anyone sense them as related bugs as well?

---

### Post by BubbaQ on 2009-11-25
Same here.  After doing a kernel upgrade on Karmic, I get the following message and the system will not boot from there:
```

udevadm trigger is not permitted while udev is unconfigured.5
udevadm settle is not permitted while udev is unconfigured
 
 svgalib: can not open /dev/mem
 
 Gave up waiting for root device. Common problems:
   - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - check root= (did the suystem wait for the right device?)
 - Missing modules ( cat /proc/modules; ls /dev )
 
 ALERT! /dev/disk/by-uuid/45f75601-96f0-47fd-9117-340289c12a12- does not exist. Dropping to a shell!
 
 BusyBox c1.13.3...
```

---

### Post by wilee-nilee on 2009-11-25
> **zzzisgood said:**
> I don't quite understand the purpose of using gparted cd.  even if it can detect the HDDs, which I belive still exist as I can see them using Intrepid Live CD, does it ensure that Karmic recogonises them afterwards?   Plus, Karmic Live CD does not work any more somehow even after changing to keyboards. How do I run/install Karmic then? Should I try alternative CD? 

It looks like downgrading to Jaunty is my best option now, although I am reluctant to do it, since I will lose all configs/settings. 

Anybody out there who can help????

I have no experience with a server environment, so I probably shouldn't be commenting at all, but I had found that under a occasional situation that gparted was effective where the built in partition manager and partition recognizing was ineffective.

---

