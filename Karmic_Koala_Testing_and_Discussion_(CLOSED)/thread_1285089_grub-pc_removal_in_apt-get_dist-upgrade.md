---
title: "grub-pc removal in apt-get dist-upgrade"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by whoop on 2009-10-07
Has anybody else gotten a grub-pc to be removed in apt-get dist-upgrade? I got this for a 64 bit karmic and not for a 32 bit one.....
Logically I am hesitant to run the command :-p

---

### Post by kansasnoob on 2009-10-07
Just FYI 'grub-pc' is grub2, whereas 'grub' is legacy grub.

So are you using grub2 or legacy grub?

The output of:

```
grub-install -v
```

will tell you. 0.97 is legacy grub and 1.97 is grub2.

---

### Post by whoop on 2009-10-07
I am using grub2, but dist-upgrade outputs:
```

Calculating upgrade... Done
The following packages will be REMOVED:
  grub-pc
The following packages will be upgraded:
  grub-common
1 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 1,243kB of archives.
After this operation, 1,892kB disk space will be freed.
Do you want to continue [Y/n]? 

```
atm, on one machine while I am not getting this on other machines...

Removing grub-pc seems dangerous, so I was just wondering if anybody else is experiencing this...

---

### Post by kansasnoob on 2009-10-07
It sounds dangerous to me too!

Just to satisfy my curiosity would you post the output of:

```
grub-install -v
```

and also:

```
ls ~ /boot/grub
```

---

### Post by whoop on 2009-10-07
```

:~$ grub-install -v
grub-install (GNU GRUB 1.97~beta3)

```

---

### Post by whoop on 2009-10-07
Strange... I found out that grub was still installed on my machine... Although I thought it would have been removed by upgrade-from-grub-legacy
After I removed it in synaptic, dist-upgrade reports

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  grub-common grub-pc
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,739kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 

```
Allot less terrifying...

---

### Post by kansasnoob on 2009-10-07
Just doing some reading and I guess that's happened to others also:

[http://ubuntuforums.org/showthread.php?t=1284884](http://ubuntuforums.org/showthread.php?t=1284884)

I'm currently using legacy grub as part of an experiment, but I noticed that "grub" was updated yesterday (it broke the functionality of startupmanager w/legacy grub).

Normally an "update" shouldn't randomly "install" conflicting packages, so I'm thinking "bug"!

---

### Post by rex4u on 2009-10-07
> **whoop said:**
> 
Removing grub-pc seems dangerous, so I was just wondering if anybody else is experiencing this...

Wait for some time and don't hit Upgrade button. It cleaned my Grub2 and I had to reinstall.
Just wait for some time...

---

### Post by whoop on 2009-10-07
Well I did it anyway, with a workaround... Looks to me like a bug so I reported it:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/445653](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/445653)

---

### Post by kansasnoob on 2009-10-07
> **rex4u said:**
> Wait for some time and don't hit Upgrade button. It cleaned my Grub2 and I had to reinstall.
Just wait for some time...

**[COLOR="Red"]Note: I've made many changes to this post preparing for a HowTo![/COLOR]**

You had to reinstall Karmic?

Seldom necessary, you can just mount and chroot the broken *buntu from a Live CD and then use apt to reinstall parts and pieces (in this case 'grub-pc') or apt-get update, apt-get upgrade, etc.

***Note: the commands below are just a string of commands connected by "space&&space" but if one part of the string fails it stops the whole process so if you encounter any failure message look at the list of individual commands below!***

Of course you must first know what partition you want to mount, in this example I'm using sda3:

```
sudo mount /dev/sda3 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

It may be a good idea to run "lsb_release -a" to be certain you mounted the correct partition!

[B]Note: In Karmic and Lucid only you may also need to run:

```
dpkg-divert --local --rename --add /sbin/initctl
```

and:

```
ln -s /bin/true /sbin/initctl
```

The reason is explained here for Karmic:

[http://www.ubuntu.com/getubuntu/releasenotes/910#Upstart%20jobs%20cannot%20be%20run%20in%20a%20chroot](http://www.ubuntu.com/getubuntu/releasenotes/910#Upstart%20jobs%20cannot%20be%20run%20in%20a%20chroot)[/B]

And here again for Lucid:

[http://www.ubuntu.com/getubuntu/releasenotes/1004#Upstart%20jobs%20cannot%20be%20run%20in%20a%20chroot](http://www.ubuntu.com/getubuntu/releasenotes/1004#Upstart%20jobs%20cannot%20be%20run%20in%20a%20chroot)

Then run whatever commands needed - no sudo needed.

When done exit the chroot and unmount (this applies to all versions):

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

As mentioned above these are the individual commands (no code tags to preserve space):

MOUNT:
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt

REMEMBER: exit

UNMOUNT:
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

Example:

> lance@lance-desktop:~$ sudo mount /dev/sda3 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
[sudo] password for lance: 
root@lance-desktop:/# dpkg-divert --local --rename --add /sbin/initctl && ln -s /bin/true /sbin/initctl
Adding `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@lance-desktop:/# [B]lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu lucid (development branch)
Release:	10.04
Codename:	lucid[/B]
root@lance-desktop:/# exit
exit
lance@lance-desktop:~$ sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
lance@lance-desktop:~$ 


In bold you can see I checked to be sure I'd mounted the root partition of my Lucid install from running those commands in my Karmic install. Works the same way from a Live CD.

Neat huh?

---

