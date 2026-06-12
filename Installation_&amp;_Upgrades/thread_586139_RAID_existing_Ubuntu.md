---
title: "RAID existing Ubuntu"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by tomcatf14 on 2007-10-22
I run mdadm --create /dev/md0 --chunk=64 --level=raid1 --raid-devices=2 /dev/sda1 /dev/sdb1 and it returned the error:-

mdadm: Cannot open /dev/sda1: Device or resource busy
mdadm: create aborted

I am raiding the machine remotely. Do i need to unmount /dev/sda1? sda* is an active disk and primary.

---

### Post by bruban on 2007-10-22
Did you run the mdadm -create command a couple of times?

If so, your system may still have been processing your command. It can take some time to build a raid array.

You can check the progress using:

cat /proc/mdstat


This will show you the status of your arrays.

---

### Post by tomcatf14 on 2007-10-22
```
root@ubuntu:~# mdadm --create --verbose /dev/md0 --level=mirror --raid-devices=2 /dev/sda1 /dev/sdb1
mdadm: Cannot open /dev/sda1: Device or resource busy
mdadm: create aborted
root@ubuntu:~# cat /proc/mdstat 
Personalities : 
unused devices: <none>
root@ubuntu:~# 
```

I guess i need to unmount the active partition. But how to unmount the active partition?

---

### Post by bruban on 2007-10-22
Try booting from the 7.10 Alternate CD and then create your raid array, either using mdadm or by using the appropriate menus during the install process.

This should overcome your mount problem.

You may also want to make sure that your devices are on two different controllers. It will help improve performance with simultaneous writes to your two disks (using raid 1).

Bruce

---

### Post by tomcatf14 on 2007-10-22
> **bruban said:**
> Try booting from the 7.10 Alternate CD and then create your raid array, either using mdadm or by using the appropriate menus during the install process.

This should overcome your mount problem.

You may also want to make sure that your devices are on two different controllers. It will help improve performance with simultaneous writes to your two disks (using raid 1).

Bruce

I want to maintain the current installation. Please give detail guidelines.

---

### Post by tomcatf14 on 2007-10-22
Is it necessary that i do it from single user mode?

---

### Post by bruban on 2007-10-22
It appears from the information that I have that you are trying to create a raid array and that at least one of the disks that you want to put into the array is currently in use.

A simple way of overcoming this is to boot using the Alternate CD (which includes support for mdadm). This will free up your disks and allow you to create the array (while saving your existing install).


Alternatively, you can work through your system to see what is stopping the device from being added to the array. Are you sharing partitions using nfs or samba? This could be causing the problem. Stop the appropriate service and try using mdadm again. 

e.g. to stop nfs server use:

/etc/init.d/nfs-kernel-server stop


I hope this helps.

Bruce

---

### Post by tomcatf14 on 2007-10-22
How do i get the Alternate CD?

---

### Post by tomcatf14 on 2007-10-22
How do i boot up from Alternate CD? I only have the installation CD with me

---

### Post by bruban on 2007-10-22
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Choose your release

under the Download here url, check the box marked:

Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer.


Sorry, I have to run.   Search the Ubuntu site for info on the Alternate CD if you need more info.

Bruce

---

### Post by tomcatf14 on 2007-10-22
downloading alternate cd and will give it a try later.

---

### Post by tomcatf14 on 2007-10-22
I am downloading this; [http://releases.ubuntu.com/dapper/ubuntu-6.06.1-alternate-i386.iso](http://releases.ubuntu.com/dapper/ubuntu-6.06.1-alternate-i386.iso)
Hope it is the correct version.

---

### Post by bruban on 2007-10-22
I just noted that you were downloading Ubuntu 6.06 Alternate.

While this will work with mdadm, you may be better off downloading the latest version, 7.04.

Bruce

---

### Post by bruban on 2007-10-22
sorry, the latest is 7.10

---

### Post by tomcatf14 on 2007-10-22
I have downloaded the Alternate CD, how do i proceed from here?

---

### Post by tomcatf14 on 2007-10-23
How do i boot the OS from CD? There's only option to boot from hard disk and install to harddisk

---

### Post by bruban on 2007-10-23
Boot from the Alternate CD

select Rescue Broken system

after boot, press CTL-ALT-F1 (or F2, F3 etc)

This will bring you to a command line session.


Use mdadm as you were originally intending from the command line.




The other option that I mentioned earlier of setting up your raid array from within the Alternate CD Installer was incorrect. I was confusing this with the Debian installer where this is possible.


Good luck.

Bruce

---

### Post by tomcatf14 on 2007-10-24
I could RAID from Live CD but i can't boot up from on the / raid /dev/md0. It always look for /dev/sda1. I boot up the OS from Live CD, then raid the disks as it is not mounted.

---

### Post by bruban on 2007-10-24
Do you see your raid devices when you type:

```
 cat /proc/mdstat

```


On my box I get something like:

pc# cat /proc/mdstat
Personalities : [raid1] 
   
md0 : active raid1 hda1[0] hdc1[1]
      64128 blocks [2/2] [UU]

=====

What do you get when you type the following:

```
 ps -ef | grep mdadm
```


On my box I get:

pc# ps -ef | grep mdadm
root      5854     1  0 20:25 ?        00:00:00 /sbin/mdadm --monitor --pid-file /var/run/mdadm/monitor.pid --daemonise --scan --syslog

=====

Do you have your raid device mounted at boot, or is it still referring to your old disk configuation?

I have the following extract in my fstab file: 

pc# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

/dev/md0        /boot           ext3    defaults        0       2


=====

Are you able to mount your raid device manually?

Bruce

---

### Post by tomcatf14 on 2007-10-25
Yes, i can see the RAID device and can mount it manually. As i am booting from Live CD, i believe /etc/fstab will refer to the fstab in the CD, rite?

I have a sample RAIDed system and the fstab show the following:-
/dev/md0 / ext3 defaults,errors=remount-ro 0 1
/dev/md1 none swap sw 0 0

---

### Post by bruban on 2007-10-25
As you can mount the raid device manually, change to the /etc directory under the mount and edit the fstab file there to suit your requirements.

If on reboot, your system still does not come up with the raid, it may be that the mdadm package has not been installed. 

To fix it then, you may need to reboot with the LiveCD, mount the raid and chroot into your system on the mounted raid, then use aptitude to install mdadm into the chrooted system.

Bruce

---

