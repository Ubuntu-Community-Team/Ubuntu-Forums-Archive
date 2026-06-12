---
title: "grub rescue (error no such device)"
date: 2013-02-28
forum: Installation &amp; Upgrades
---

### Post by sixcorners on 2013-02-28
[http://pastebin.com/syFC8248](http://pastebin.com/syFC8248) grub.cfg
[http://pastebin.com/BD3MR3uK](http://pastebin.com/BD3MR3uK) blkid
[http://pastebin.com/VjFHUSFJ](http://pastebin.com/VjFHUSFJ) fdisk -l

error: no such device: e4ae1f64-039b-491f-832e-aa5fcfb110bf.
grub rescue> 
grub rescue> set
prefix=(hd0)/boot/grub
root=hd0
grub rescue> ls
(hd0) (hd1) (hd1,gpt6) (hd1,gpt5) (hd1,gpt4) (hd1,gpt3) (hd1,gpt2) (hd1,gpt1)
grub rescue> ls .
error: unknown filesystem.
grub rescue> 

It's a fresh 12.10 amd64 ubuntu install. I shrunk the ntfs partition on the 2nd disk from windows then chose for ubuntu to install itself alongside Windows 8.
Edit: This is a desktop that was purchased in 2007.

---

### Post by fdrake on 2013-02-28
follow this tutorial to fix grub. You will need an USB/cd install
[http://theguyonthe3rdfloor.wordpress.com/2013/02/28/how-to-install-grub-2/](http://theguyonthe3rdfloor.wordpress.com/2013/02/28/how-to-install-grub-2/)

---

### Post by sixcorners on 2013-02-28
> **fdrake said:**
> follow this tutorial to fix grub. You will need an USB/cd install
[http://theguyonthe3rdfloor.wordpress.com/2013/02/28/how-to-install-grub-2/](http://theguyonthe3rdfloor.wordpress.com/2013/02/28/how-to-install-grub-2/)

> ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="System Reserved" UUID="3414C87914C8401A" TYPE="ntfs" 
/dev/sda2: UUID="A8B2CC20B2CBF13C" TYPE="ntfs" 
/dev/sdb2: UUID="BA0C5C7A0C5C341B" TYPE="ntfs" 
/dev/sdb4: UUID="e4ae1f64-039b-491f-832e-aa5fcfb110bf" TYPE="ext4" 
/dev/sdb6: UUID="2df992db-3d72-45f2-b1f9-27053b683bdb" TYPE="swap" 
/dev/sr0: LABEL="Ubuntu 12.10 amd64" TYPE="iso9660" 
root@ubuntu:~# mount /dev/sdb4 /mnt
root@ubuntu:~# grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
root@ubuntu:~# reboot

Still have the same problem. I also can't get into recovery mode.

---

### Post by oldfred on 2013-02-28
Do you have a very large / (root) partition? We have seen users have issues with grub not being able to find all the files when they are far apart on drive. I normally suggest  a 25GB / partition with the rest as /home or even better as data partition(s). It looks like you already have NTFS as data partitions in addition to your Windows system partition which you should set at read only to avoid issues.

You can realtively quick test my suggestion by using gparted and shrinking / to less than 100GB. About 50% of those I suggest this to have it work. The rest either reinstall with different partitioning and/or add a 200 to 500MB /boot partition near the beginning of the drive.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by fdrake on 2013-02-28
try to chroot in /sda4 and run as update-grub
just after those commands:
```

chroot /mnt
mount -o rw,remount / 
update-grub

```

---

### Post by sixcorners on 2013-03-01
I fixed it by creating a /boot partition on the first disk where grub was.
Still kind of surprised that a simple dual boot install would leave my system like that.
Thanks for the help anyway.
If the forums didn't go down, that advice about creating a dedicated boot partition would have solved it.
Should I still post my boot info? Should I be trying to get this fixed in one of these projects? Seems like this shouldn't have happened in the first place.

Edit: Also I don't see an option to mark this thing as solved under Thread Tools...

---

