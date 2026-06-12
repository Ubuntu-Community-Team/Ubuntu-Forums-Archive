---
title: "[SOLVED] upgrade problem because of lack of space on disk '/boot'"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by sanford55 on 2008-09-06
I dual boot xp and ubuntu on two machines.  The upgrade to 8.04 went fine on one machine, but failed on the other.  When I try to upgrade, it starts, but when it gets to the place where it says "Setting new software channels, calculating the changes" it stops and it says 

"The upgrade aborts now. The upgrade needs a total of 31.5M free space on disk '/boot'. Please free at least an additional 30.5M of disk space on'/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."  

I empty trash and use the 'sudo apt-get clean' command but it does not help.  I do not know much about ubuntu (though I have been using it for a while).  I checked the boot file, which I assume the message referred to and it has the following in it.  

abi-2.6.22-14-generic initrd.img-2.6.22-15-generic
abi-2.6.22-15-generic lost+found
config-2.6.22-14-generic memtest86+.bin
config-2.6.22-15-generic System.map-2.6.22-14-generic
grub System.map-2.6.22-15-generic
initrd.img-2.6.22-14-generic vmlinuz-2.6.22-14-generic
initrd.img-2.6.22-14-generic.bak vmlinuz-2.6.22-15-generic

Am I supposed to remove some of this?  Why?  There is plenty of room on the partition and I did not have to do anything like this on my other machine even though, I thought, I had installed ubuntu the same way.  Some one suggested that the boot section of ubuntu installed differently on the two machines.  Maybe so, but that does not tell me what to do.  Is there a way to fix this?  Also, is it possible to just put ubuntu live cd into my cd-drive and install over the old installation from that?  Ubuntu has given me few problems till now and I would like to get it to work again.    Thanks in advance for your help.

---

### Post by iaculallad on 2008-09-06
On your terminal:

```
sudo rm /boot/*.bak
```

Then try, re-upgrading...

Or you could post whatever displays when you issue the terminal command below:

```
df -h
```

---

### Post by cdtech on 2008-09-06
the command "df -H" will tell what space is available on your install. You may need to resize your partition using the Live CD "gparted" so that you can support more than one or even two kernel images.

---

### Post by sanford55 on 2008-09-15
Hi, hope someone reads this.  I had to leave town and just got back.  I first posted some time ago.  

I tried sudo rm /boot/*.bak and it did not help.  Here is the output from df-h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              12G  3.6G  7.4G  33% /
varrun                378M  216K  378M   1% /var/run
varlock               378M     0  378M   0% /var/lock
udev                  378M   72K  378M   1% /dev
devshm                378M     0  378M   0% /dev/shm
lrm                   378M   34M  345M   9% /lib/modules/2.6.22-15-generic/volatile
/dev/sda2              30M   21M  7.9M  72% /boot

I do not know much about Linux, but does this say that I boot from a separate partition, sda2, with only 30M?  Is it supposed to be like that? Looks like that is the problem I suppose.  Anything I can do? Oh one other thing, I hope there is a way to fix this without using the Live Cd as one person mentioned since my cd-rom just died and my department may not be able to afford a repair for a while, sigh! 
Thanks again for any help.  Sanford

---

### Post by linuxonbute on 2008-09-15
> **sanford55 said:**
> Hi, hope someone reads this.  I had to leave town and just got back.  I first posted some time ago.  

I tried sudo rm /boot/*.bak and it did not help.  Here is the output from df-h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              12G  3.6G  7.4G  33% /
varrun                378M  216K  378M   1% /var/run
varlock               378M     0  378M   0% /var/lock
udev                  378M   72K  378M   1% /dev
devshm                378M     0  378M   0% /dev/shm
lrm                   378M   34M  345M   9% /lib/modules/2.6.22-15-generic/volatile
/dev/sda2              30M   21M  7.9M  72% /boot

I do not know much about Linux, but does this say that I boot from a separate partition, sda2, with only 30M?  Is it supposed to be like that? Looks like that is the problem I suppose.  Anything I can do? Oh one other thing, I hope there is a way to fix this without using the Live Cd as one person mentioned since my cd-rom just died and my department may not be able to afford a repair for a while, sigh! 
Thanks again for any help.  Sanford

Post the output from cat /etc/fstab

Linux has a root ( / ) partition and everything is seen below that.

By carefully doing some work you should be able to :

1/ create a new directory ( say newboot )

2/ copy all files from /boot to it.

3/ rename /boot to /oldboot

4/ rename newboot to boot

5/ edit /etc/fstab 

6/ reboot 

7/ try your install again.

Assuming I have got this right you should be up and running.

Just in case I have gone wrong somewhere I would wait until a few have read this update to your post :p

---

### Post by sanford55 on 2008-09-17
Hi, thanks for the reply.  I have a few questions before I try the suggested move.  I do not know much about this.  First, is there a best place to put the "newboot" directory?  Second, you mention editing /etc/fstab, but I am not sure what changes to make.  Is this the file that tells the computer where the boot files are?  What changes am I to make?   Finally, I just got my cd-ROM to work.  Is it possible to simply reinstall Linux over the old one with the live CD rather than working with the old intallation?  

You requested the output from /etc/fstab.  Here it is, though I am not sure what any of it means!  Thanks again, Sanford

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=a1f41064-8d51-4885-b716-8f250a394836 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=70a89e17-c79a-4bf6-8cf8-0e7537d11d6b /boot           ext2    defaults        0       2
# /dev/sda1
UUID=0634C4E434C4D837 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=744c1d6e-2d98-4bcc-89bb-e7380b793214 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by mrand on 2009-09-19
> **sanford55 said:**
> I dual boot xp and ubuntu on two machines.  The upgrade to 8.04 went fine on one machine, but failed on the other.  When I try to upgrade, it starts, but when it gets to the place where it says "Setting new software channels, calculating the changes" it stops and it says 

"The upgrade aborts now. The upgrade needs a total of 31.5M free space on disk '/boot'. Please free at least an additional 30.5M of disk space on'/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."  

I empty trash and use the 'sudo apt-get clean' command but it does not help.  I do not know much about ubuntu (though I have been using it for a while).  I checked the boot file, which I assume the message referred to and it has the following in it.  

abi-2.6.22-14-generic initrd.img-2.6.22-15-generic
abi-2.6.22-15-generic lost+found
config-2.6.22-14-generic memtest86+.bin
config-2.6.22-15-generic System.map-2.6.22-14-generic
grub System.map-2.6.22-15-generic
initrd.img-2.6.22-14-generic vmlinuz-2.6.22-14-generic
initrd.img-2.6.22-14-generic.bak vmlinuz-2.6.22-15-generic

Am I supposed to remove some of this?  Why?  There is plenty of room on the partition and I did not have to do anything like this on my other machine even though, I thought, I had installed ubuntu the same way.  Some one suggested that the boot section of ubuntu installed differently on the two machines.  Maybe so, but that does not tell me what to do.  Is there a way to fix this?  Also, is it possible to just put ubuntu live cd into my cd-drive and install over the old installation from that?  Ubuntu has given me few problems till now and I would like to get it to work again.    Thanks in advance for your help.

Old thread, but for anyone looking for an answer to this:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/104337/comments/28](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/104337/comments/28) says:

It looks like you removed the images from the filesystem, but not the kernel packages. Please use synaptic to remove the no longer used kernels (make sure to keep the one you are currently using :)

[INDENT]Marc[/INDENT]

---

### Post by sivasankarigovind on 2010-08-06
The upgrade needs a total of 496M free space on disk '/'. Please free at least an additional 440M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean' 
sankari@sankari-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda9             2.3G  2.2G   55M  98% /
tmpfs                 498M     0  498M   0% /lib/init/rw
varrun                498M  104K  498M   1% /var/run
varlock               498M     0  498M   0% /var/lock
udev                  498M  160K  498M   1% /dev
tmpfs                 498M  536K  497M   1% /dev/shm
lrm                   498M  2.4M  495M   1% /lib/modules/2.6.28-11-generic/volatile


how to solve this problem

---

