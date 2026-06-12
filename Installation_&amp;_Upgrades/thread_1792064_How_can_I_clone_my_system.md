---
title: "How can I clone my system?"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by darthpenguin on 2011-06-27
Hey guys. I'm looking for a way to clone my system. I don't want my home folder backed up. I just want an iso I can burn to a cd or boot off a USB that would install Ubuntu plus all the software and settings from the source system. I don't just want a list of currently installed apps for apt-get to download because I've already installed them on one machine and there is no sense downloading them over again and using up my bandwidth. not to mention software compiled from source and third party ppa's. Plus I have gone through the trouble of removing stuff like Unity and Evolution. I don't want to have to remove them every time I install Ubuntu. Basically, I have a heavily customized Ubuntu 11.04 install that I want to replicate on multiple machines.

I tried remastersys but the iso it created wouldn't boot in VirtualBox for testing.

Any ideas? Thanks. (^_^)

---

### Post by Jahid65 on 2011-06-27
if you have 2 separate partition for root & homr, then you can try[ fsarchiver.]("http://www.fsarchiver.org/QuickStart") it is good for if you  backup & restore only to your pc

Other option is clonezilla or ubuntu customization kit.

---

### Post by darthpenguin on 2011-06-27
Ubuntu customization kit looks like it's just for languages or something. What about fsarchiver? I have a 2 GB /boot partition and a 10 GB / (root) partition. Can I backup both those partitions in a single archive? How do I restore it? Do I need to partition the destination drive with gparted or something first?

Once I restore an image or archive will the machine boot or will I need to rebuild grub? I imagine I'll need to change the hostname? Anything else I should change?

---

### Post by Jahid65 on 2011-06-28
> **darthpenguin said:**
> Ubuntu customization kit looks like it's just for languages or something. What about fsarchiver? I have a 2 GB /boot partition and a 10 GB / (root) partition. Can I backup both those partitions in a single archive? How do I restore it? Do I need to partition the destination drive with gparted or something first?

you can archive more than one partition in one file. see the link given on my 1st post.
 you can restore on the same partition (better) or different. just make sure that the uncompressed file doesn't go beyond your partition.

You can also archive several filesystems in a single archive file:

```


fsarchiver savefs /media/backup/gentoo-rootfs.fsa /dev/sda1 /dev/sda2 
```You can also restore both the first and the second filesystem in the same time: (numbers 0 and 1) 



```
fsarchiver restfs /media/backup/archive-multple-filesystems.fsa id=0,dest=/dev/sda1 id=1,dest=/dev/sdb1 
```In terminal type
> fsarchiver --helpYou will find many example....

if you want to use tar method then see this [thread]("http://ubuntuforums.org/showthread.php?t=35087&highlight=backup")

Explains what is happening.

Only thing to note is ...

don't 

sudo su
to gain root user..

Instead ...

cd /
then 

```
sudo tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/media --exclude=/sys /
``` use media instead of mnt.
sudo'ing to root is not the way to do most things, issue the sudo before the command you wish to execute as 'root user'.

The above thread, tho' long & involved, will introduce you to the lay out of files in your machine.

Have fun.


 

You have to use live cd (System Rescue CD) which contains fsarchiver or another distro installed in your pc & have fsarchiver. 
When you work on any partition make sure that partition is **unmounted**.


> Once I restore an image or archive will the machine boot or will I need  to rebuild grub? I imagine I'll need to change the hostname? Anything  else I should change?yes need to restore grub in case of root or boot partition.

---

### Post by darthpenguin on 2011-07-01
Thanks, the tar method seems like the best one to use. I've used tar before to backup and restore a system but I have never restored a backup to a different hdd or different machine. My current hdd is setup with swap, /boot, /, and /home partitions. Do I need to manually format/partition the destination HDD before restoring the backup? I do not want to backup the /home directory. Would I be able to login as root once the backup is restored? How would I create a new user?

I tried this last night and the machine wouldn't boot. I get the grub rescue> prompt. I tried suggestions from many forums with no luck. How do I restore/rebuild grub after I restore the backup? (keep in mind, this is grub2 on ubuntu 11.04)

Sorry for all the questions. I'm still learning.

---

### Post by Jahid65 on 2011-08-05
[SIZE=5][COLOR=red]How to restore the Ubuntu grub bootloader in 11.04[/COLOR][/SIZE]

First you need to find out what your drives are called. You can do this by going to a terminal and typing:

```
sudo fdisk -l 
```You will get something like this:

[IMG]http://img196.imageshack.us/img196/713/svr8xil.jpg[/IMG]
From that you need to find the device name of your Ubuntu drive, something like &#8220;/dev/sda5&#8243;.
 So, still in the terminal, type:
     ```
sudo mkdir /media/sda5
``````
sudo mount /dev/sda5 /media/sda5 
```And then, to reinstall the grub: 

```
sudo grub-install --boot-directory=/media/sda5/boot /dev/sda5
```Push enter and you&#8217;re done! Of course you need to replace &#8220;/dev/sda5&#8243; and &#8220;/dev/sda&#8221; with what you found in the fdisk output.

[LIST]
[*]Reboot
[*]Refresh the GRUB 2 menu with sudo update-grub
[/LIST]
for more info go [here]("https://help.ubuntu.com/community/Grub2#Methods%20of%20Reinstalling")

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by YesWeCan on 2011-08-05
You will need to edit /etc/fstab on each new installation in order to correct the partition names and UUIDs.

---

