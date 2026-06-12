---
title: "Upgrate to Fiesty Crashed - Now Can't Boot"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by awells527 on 2007-07-06
Greetings, I ran the upgrade on my Ubuntu server today and it froze.  I'm not sure really why, but now, I can't even boot to recovery mode.  It says something like "Alert: /dev/hda2 not found, dropping to shell", except, it's not the normal shell prompt with some sort of 'init' prompt.  I know my drive is found because I'm in the live CD right now, and all my files are there.  Is there a way to repair my filesystem to continue the upgrade, or am I going to have to pull off my files and do a fresh install?

Although it does function as a file/web server, ubuntu-desktop is installed, so I upgraded the GUI way.  I am comfortable in the shell, so if that's all I get until it's upgraded, that's fine.

Thanks for any advice.

---

### Post by confused57 on 2007-07-07
> **awells527 said:**
> Greetings, I ran the upgrade on my Ubuntu server today and it froze.  I'm not sure really why, but now, I can't even boot to recovery mode.  It says something like "Alert: /dev/hda2 not found, dropping to shell", except, it's not the normal shell prompt with some sort of 'init' prompt.  I know my drive is found because I'm in the live CD right now, and all my files are there.  Is there a way to repair my filesystem to continue the upgrade, or am I going to have to pull off my files and do a fresh install?

Although it does function as a file/web server, ubuntu-desktop is installed, so I upgraded the GUI way.  I am comfortable in the shell, so if that's all I get until it's upgraded, that's fine.

Thanks for any advice.
It might be that the Feisty kernel is recognizing your hard drive as sda, instead of hda...if you're getting a grub boot menu, try highlighting your Ubuntu entry, press "e", then try changing your kernel root to /dev/sda2, then press "b" to boot...I don't know if this is your problem or not, but worth a try.

---

### Post by awells527 on 2007-07-07
Still no luck.  It hangs at this line: 

> Begin: Waiting for root file system...

Here is an image of what the output is.  I figured connecting the digital camera to my desktop would be quicker and more accurate than typing. :)

---

### Post by confused57 on 2007-07-07
> **awells527 said:**
> Still no luck.  It hangs at this line: 



Here is an image of what the output is.  I figured connecting the digital camera to my desktop would be quicker and more accurate than typing. :)
You might want to post the output of:
```
sudo fdisk -l
```
-l is a small "L"

You can mount your root partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
you might want to check your /etc/fstab & /boot/grub/menu.lst...you're probably aware that Feisty uses root UUID's in the menu.lst kernel line.  Is /dev/hda2 your root partition?
I'm not sure if you can chroot into your root partition and resume the upgrade or not...give   me a few minutes & I'll see if I get together some instructions for doing this.

Added:  Have you seen this method for manually upgrading to Feisty?:
[https://help.ubuntu.com/community/FeistyUpgradesManual](https://help.ubuntu.com/community/FeistyUpgradesManual)

If you want to try chrooting into your Ubuntu, this may or may not work:
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda2 /mnt/ubuntu
sudo mount -t proc none /mnt/ubuntu/proc
sudo mount -o bind /dev /mnt/ubuntu/dev
sudo chroot /mnt/ubuntu /bin/bash
```
you'll have to substitute your root partition for /dev/hda2...then you might be able to run these commands to finish the upgrade:
```
sudo apt-get -f install
sudo dpkg --configure -a
```

If you'll note, at the bottom of the link I provided, it mentions running the upgrade again:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

You may be able to get your system upgraded without chrooting into your Ubuntu...these directions may not even work, but at least it's something to try if nothing else does.

---

### Post by awells527 on 2007-07-07
Here is the fdisk info:

> Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          25      200781   83  Linux
/dev/hda2              26       24130   193623412+  83  Linux
/dev/hda3           24131       24321     1534207+  82  Linux swap / Solaris

I will go through the other directions and see what happens.  Thank you very much for providing that information.

EDIT: Forgot to mention - /dev/hda1 is /boot; /dev/hda2 is everything else

---

### Post by confused57 on 2007-07-07
> **awells527 said:**
> Here is the fdisk info:



I will go through the other directions and see what happens.  Thank you very much for providing that information.

EDIT: Forgot to mention - /dev/hda1 is /boot; /dev/hda2 is everything else
If you chrooted, you'd probably have to mount your /boot, also:
```
sudo mkdir /mnt/ubuntu/boot
sudo mount /dev/hda1 /mnt/ubuntu/boot
```

Don't try chrooting(yet)...Here's something else you might try, using the live cd, run the command:
```
blkid
```
then mount your root partition, using the instructions in the link, then compare your UUID's in /etc/fstab with the results of "blkid"...I know that Edgy uses UUID's in fstab, but /dev/hda2 in the menu.lst kernel root...this may not work with Feisty.  You might want to change your kernel root to UUID, for example "root=UUID=enter UUID here from blkid"...or possibly change your fstab to /dev/hda2.  I would suggest using UUID in both fstab & menu.lst, since Feisty may recognize your partitions as /dev/sda2.
I don't know, I'm just fumbling and throwing out ideas for you to try.

---

### Post by awells527 on 2007-07-07
It looks like that the /dev/hda / UUID could be the problem, but it fixed itself when I chrooted into the system, which I never knew was possible, so I learned something. :D

It turns out that the chroot option was the way to go.  I was able to repair the broken dependencies and finish the upgrade.  Thank you all for your help and tips!

---

### Post by confused57 on 2007-07-08
> **awells527 said:**
> It looks like that the /dev/hda / UUID could be the problem, but it fixed itself when I chrooted into the system, which I never knew was possible, so I learned something. :D

It turns out that the chroot option was the way to go.  I was able to repair the broken dependencies and finish the upgrade.  Thank you all for your help and tips!

Good job getting your upgrade completed...glad it worked.  I picked up a little about chrooting by installing Gentoo and Linux From Scratch, both of which I've since removed, but it was definitely a learning experience.

---

