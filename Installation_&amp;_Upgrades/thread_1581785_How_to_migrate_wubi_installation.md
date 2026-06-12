---
title: "How to migrate wubi installation?"
date: 2010-09-25
forum: Installation &amp; Upgrades
---

### Post by andreasbuykx on 2010-09-25
Hi all, I am a very happy user of Ubuntu 10.04 installed by Wubi on my company laptop. Now my company wants me to replace my laptop. Since the wubi installation is just a file on the windows file system, I hope it is easy to move my current wubi installation to my new laptop. Can someone tell me how to do this?

thanks
Andreas

---

### Post by sikander3786 on 2010-09-25
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

A very nice guide is there.

---

### Post by sanderd17 on 2010-09-25
Before you can use that guide, you'll have to have the different partitions. The best way to do so is to install ubuntu the normal way and overwrite it with that guide afterwards.

---

### Post by bcbc on 2010-09-25
You can generally just install wubi on the new laptop and then copy the old root.disk over the new one. But...

1. Make sure it's the same release
2. Edit the grub menu item the first time you boot:
It is highly likely that the partition may be different. Change all instances of (hdX,Y) to the new partition and /dev/sdaY as well. Also, the "search --xxx" line refers to a UUID, so you'll need to delete that. 
3. After booting run "sudo update-grub" to update the grub menu.

To edit the grub menu hit 'e', edit and then CTRL+X to boot.
To identify the partition, use "ls" and then "ls (hd0,Y)/ubuntu" to find the correct partition. The Y in the device /dev/sdaY matches the Y in (hd0,Y). Usually it's the first hard drive 0 and a (in /dev/sdaY), but if you're on (hd1,Y) then use /dev/sdbY).

Possible complications: if you have a custom hardware driver installed it could cause issues. Remove prior to copying. 
If you have issues with the new hardware and ubuntu (e.g. booting a live CD then you may need some additional workarounds).

PS you don't have to do the 2nd part of the wubi install on the new machine - where you reboot the first time and you get the 'slide show'. If you want to skip this part, then also copy the swap.disk (along with the root.disk) so that it's set up correctly.

---

### Post by Praveen30 on 2010-09-25
> **andreasbuykx said:**
> Hi all, I am a very happy user of Ubuntu 10.04 installed by Wubi on my company laptop. Now my company wants me to replace my laptop. Since the wubi installation is just a file on the windows file system, I hope it is easy to move my current wubi installation to my new laptop. Can someone tell me how to do this?

thanks
Andreas

follow this for standalone installation--

[http://tricksfind.blogspot.com/2010/09/ubuntu-install-linux-quick-and-easy.html](http://tricksfind.blogspot.com/2010/09/ubuntu-install-linux-quick-and-easy.html)

---

### Post by andreasbuykx on 2010-10-13
The moment of truth has come:  I have a shiny brand new Toshiba Tecra S11-13G with Windows7 installed on it. I downloaded a wubi installer (installing Ubuntu 10.04). Now I'd like to migrate my backed up disk files. These files have Ubuntu 10.04, but my original wubi was for 8.04. It has a disks/boot/grub directory with 
[INDENT]default
device.map
grubenv
menu.lst
[/INDENT]int it

I already tried copying my old root.disk, scratch.disk and home.disk over the c:\ubuntu\disks and the files into the (empty) boot/grub directory, but that didn't work. Rebooting got me a grub> prompt but I couldn't find out what to do, looking in the earlier posts of this thread. 

Do I have to get a wubi for 8.04 and try again?

Thanks for your advice!

Andreas

---

### Post by bcbc on 2010-10-13
> **andreasbuykx said:**
> The moment of truth has come:  I have a shiny brand new Toshiba Tecra S11-13G with Windows7 installed on it. I downloaded a wubi installer (installing Ubuntu 10.04). Now I'd like to migrate my backed up disk files. These files have Ubuntu 10.04, but my original wubi was for 8.04. It has a disks/boot/grub directory with 
[INDENT]default
device.map
grubenv
menu.lst
[/INDENT]int it

I already tried copying my old root.disk, scratch.disk and home.disk over the c:\ubuntu\disks and the files into the (empty) boot/grub directory, but that didn't work. Rebooting got me a grub> prompt but I couldn't find out what to do, looking in the earlier posts of this thread. 

Do I have to get a wubi for 8.04 and try again?

Thanks for your advice!

Andreas

With 8.04 all the boot files are in the \ubuntu\disks\boot directory - not on root.disk. so yes you need the same version and you need to copy the boot directory as well. There should be some kernel and initrd files as well.
8.04 uses grub-legacy and 9.10 onwards uses grub2, so you need to stick with legacy.

---

### Post by andreasbuykx on 2010-10-13
Tried to run wubi 8.04, but the installer aborts early during the download process, and Windows7 reports that wubi 8.04 isn't compatible with Win7... 

Is there a next move, or should I consider running the latest, installing my data (which I backed up separately, luckily) and giving up on migrating my root.disk, home.disk and scratch.disk. 

Would it be possible to migrate only my home.disk?

---

### Post by bcbc on 2010-10-13
> **andreasbuykx said:**
> Tried to run wubi 8.04, but the installer aborts early during the download process, and Windows7 reports that wubi 8.04 isn't compatible with Win7... 

Is there a next move, or should I consider running the latest, installing my data (which I backed up separately, luckily) and giving up on migrating my root.disk, home.disk and scratch.disk. 

Would it be possible to migrate only my home.disk?

You should be able to do that... install the latest wubi, copy in home.disk. Backup the /home on the root.disk, edit fstab and then reboot.

```
sudo mv /home /homebackup
gksu gedit /etc/fstab

```
add line 
```
/host/ubuntu/disks/home.disk /home               ext3    loop 0       2
```


Reboot. Or maybe you can just run "sudo mount -a".


PS or read this, maybe it will allow you to run 9.04 wubi.exe: [http://www.sevenforums.com/tutorials/316-compatibility-mode.html](http://www.sevenforums.com/tutorials/316-compatibility-mode.html)

---

### Post by andreasbuykx on 2010-10-14
@bcbc Thanks for the compatibility mode tip. Unfortunately it didn't work either. Each time the installer stops after renaming the MD5SUMS-metalink.gpg file to MD5SUMS-metalink.asc, while attempting to download it seems. The Ubuntu Setup error popup reads: 'The download was interrupted with the error: ', without giving the error...

Any other suggestions? Otherwise I'll have to abandon my backed up wubi 8.04 and turn to installing 10.04 and migrating my home.disk.

---

### Post by bcbc on 2010-10-14
> **andreasbuykx said:**
> @bcbc Thanks for the compatibility mode tip. Unfortunately it didn't work either. Each time the installer stops after renaming the MD5SUMS-metalink.gpg file to MD5SUMS-metalink.asc, while attempting to download it seems. The Ubuntu Setup error popup reads: 'The download was interrupted with the error: ', without giving the error...

Any other suggestions? Otherwise I'll have to abandon my backed up wubi 8.04 and turn to installing 10.04 and migrating my home.disk.
Are you installing from a cd? If you supply the command line option *--skipmd5check* that should prevent it from trying to download the MD5 metalink...  see if that works or you get some other issue.

---

### Post by andreasbuykx on 2010-10-14
I install from an installer on my harddisk. Tried to use the --skipmd5check by running the installer from the command line, but that didn't work either. The same error occurred.

---

### Post by bcbc on 2010-10-14
> **andreasbuykx said:**
> I install from an installer on my harddisk. Tried to use the --skipmd5check by running the installer from the command line, but that didn't work either. The same error occurred.
In that case you should be running the wubi.exe with the downloaded 8.04 .iso image in the same folder.

You need to run as administrator and allow pyrun.exe access to the firewall. (These are just basic things that could give errors and I'm sure don't apply to you). 

I don't really know of a good reason why 8.04 shouldn't install on win7. Unless maybe you have some unsupported feature - encrypted disks, raid whatever.

---

