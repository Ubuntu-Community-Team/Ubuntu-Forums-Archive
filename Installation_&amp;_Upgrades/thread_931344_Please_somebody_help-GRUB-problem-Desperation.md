---
title: "Please somebody help-GRUB-problem-Desperation"
date: 2008-09-27
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-09-27
First I am terribly sorry that I am sending 2 mails about the same topic, I want to guive more explanation of my problem.
 
I was browsing the programming/talk forum of ubuntu, and my browser freezed, I had to stop the computer manually to get out of the frozing browser, I use dual booting with Vista.after that I can't get into ubuntu desktop, when I restarted the computer it come automatically into grub and stop there,before it continuous to ubuntu desktop, when I use Esc I se a place where I can reboot, halt, and more, what can I do get into ubuntu desktop ? I am very desperate for a solution.
 
tks

---

### Post by Pumalite on 2008-09-27
What programs have you installed lately; before this occured?

---

### Post by hoboy on 2008-09-27
> **Pumalite said:**
> What programs have you installed lately; before this occured?

I just run Update Manager, and didn't pay attention to what has been installed specificaly

---

### Post by Pumalite on 2008-09-27
Get into Recovery Mode and use 'xfix'

---

### Post by Pumalite on 2008-09-27
If it doesn't work; you can run this from a CLI:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by hoboy on 2008-09-27
I can't get into recovery mode.

I always land in 
find /ubuntu/disk/boot/grub/menut.lst
find /ubuntu/install/boot/grub/menut.lst
fint /menu.list
find /grub/menut.list
commandeline
reboot
halt
when I hit commandline, I land into grub>
I am using dual booting vista is working fine.

---

### Post by Pumalite on 2008-09-27
Boot your Live CD and post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by caljohnsmith on 2008-09-27
From that output you posted, it looks like you are actually using Wubi and not a true dual boot setup. When you installed Ubuntu, did you install Ubuntu to its own partition by clicking on the installer program on the Ubuntu Live CD desktop, or did you use the "Install Ubuntu" option from the main menu of the Ubuntu Live CD? If you chose the latter, that would have used Wubi to install Ubuntu inside your Windows.

If you can boot your Ubuntu Live CD, open a terminal (Applications > Accessories > Terminal), and type:
```
sudo fdisk -l
```
And post the output please.

---

### Post by hoboy on 2008-09-27
I hope that I have understood your question
I have put ubuntu cd in the computer then launch ubuntu from their.
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb9193ca0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976771071   488384512    7  HPFS/NTFS
ubuntu@ubuntu:~$ 
I can not run the second command
ubuntu@ubuntu:~$ cat/boot/grub/menu.list
bash: cat/boot/grub/menu.list: No such file or directory
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-09-27
OK, definitely looks like you used Wubi. Try this from the Live CD terminal:
```
sudo mount /dev/sda1 /mnt
ls -lR /mnt/ubuntu/disks
sudo fsck -y /mnt/ubuntu/disks/root.disk
```
Please post the output of the above commands.

---

### Post by hoboy on 2008-09-27
Very true I have sued Wupi to install ubuntu, vista was installed first.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9193ca0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384512    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by hoboy on 2008-09-27
Here is 

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
fuse: mount failed: Device or resource busy
ubuntu@ubuntu:~$ ls -lR /mnt/ubuntu/disks
ls: cannot access /mnt/ubuntu/disks: No such file or directory
ubuntu@ubuntu:~$ sudo fsck -y /mnt/ubuntu/disks/root.disk

---

### Post by hoboy on 2008-09-27
ubuntu@ubuntu:~$ sudo mount /dev/ sdal/mnt
mount: mount point sdal/mnt does not exist
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-09-27
On start up, can you still boot into Vista? Because it looks like you need to boot into Vista and then restart, so that Vista can have a "clean" shutdown. That is what is probably preventing you from mounting the Vista partition per the instructions I gave in my last post.

---

### Post by hoboy on 2008-09-27
Sorry guys this is not my area.

ubuntu@ubuntu:~$ sudo mount /dev/sdal/mnt
mount: can't find /dev/sdal/mnt in /etc/fstab or /etc/mtab

---

### Post by hoboy on 2008-09-27
ubuntu@ubuntu:~$ sudo fsck -y /mnt/ubuntu/disk/root.disk
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: No such file or directory while trying to open /mnt/ubuntu/disk/root.disk

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$

---

### Post by hoboy on 2008-09-27
Is anybody out there ? i am still struggling with my problems.

---

### Post by meierfra. on 2008-09-27
Did you see post 14?

---

### Post by hoboy on 2008-09-27
> **meierfra. said:**
> Did you see post 14?

It can be that I misunderstand you on post 14, my understanding was that I should restart vista, I have done that, that hasn't help.
Could please explain in detail what do you mean I should do in post 14 ?

---

