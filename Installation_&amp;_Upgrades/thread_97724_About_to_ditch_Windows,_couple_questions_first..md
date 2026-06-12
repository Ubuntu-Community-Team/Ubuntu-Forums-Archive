---
title: "About to ditch Windows, couple questions first."
date: 2005-12-01
forum: Installation &amp; Upgrades
---

### Post by siorai on 2005-12-01
I think I'm finally at a point to actually nuke my Windows partitions once and for all. I just have a couple questions on the best way to do it though. Right now, I have two harddrives in my box. IDE1 Master is a 120GB drive with Windows on it. SATA1 Master is a 300GB drive with Ubuntu on it. Is it possible to just take out the 120GB and not even touch my Ubuntu install? I'd love to not have to reinstall it again right now... If so, what do I have to do in regards to GRUB and whatnot?

Also, right now I just did the basic Ubuntu install where it does all the partitioning for you. Should I just bit the bullet, reinstall, and do the partitioning myself? If so, what would be the best scheme for a system with a gig of ram? I know I'll need to have a 30Gb FAT partition for swapping files with other boxes on my network, but other than that, I'm not sure about what's needed for /, /boot, /swap, etc.

---

### Post by earobinson on 2005-12-01
you should be able to take the hdd out and just dont boot to the windows one, you could edit the grub file, i think its in /boot/grub/menu.lst not on my linux box

best set up depends on what you do, I have a gig or ram and 2 gig of swap space (but it never gets used) so really i dont need it i just like to have it, It all comes down to what apps your going to run and if your going to run any apps that need a lot of memmory

edit for correct grub path /boot/grub/menu.lst

---

### Post by bwog on 2005-12-01
You can just format the windows disk. I would put the fat32 partition there. I use 6gb / (root), 1gb swap, and the rest home on a 200 gb sata disk. 

I dont know where grub is, but you may have reinstall it if it is on the windows disk (chapter 8 in the offical starter guide).

Personally, I am leaving windows on the machine (games) on a separate disk.

How is your ubuntu disk partitioned now? Perhaps there is no reason to reinstall.

---

### Post by aysiu on 2005-12-01
Is Grub installed to the MBR?

If so, and you already have Ubuntu installed, there's no need to reinstall. Just delete the Windows entry from /boot/grub/menu.lst and use GParted to reformat the former Windows drive as Ext3 and create a mount point for it.

If Grub isn't on the MBR, you can [install it to the MBR.](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by earobinson on 2005-12-01
I assumed that the OP wanted to take the hdd out to put in another computer, but yes you can also format the windows hdd

---

### Post by siorai on 2005-12-01
Yes, Grub is in the MBR. I'm probably just going to take that disc right out seeing as how I think that 300GB should be more than plenty for awhile.

So looking through that thread, (thanks aysiu), it looks like I should be able to yank out the 120GB, and do the following:

1. Boot with my Gentoo Live CD
2. Get a root shell
3. Make a folder -> mkdir /mnt/ubuntu
4. Check the Ubuntu partition -> fdisk -l (Mine should be /dev/sda1)
5. Mount the root partition of Ubuntu -> mount -t ext3 /dev/sda1 /mnt/ubuntu
6. Chroot the mounted partition -> chroot /mnt/ubuntu
7. Restore Grub / the initial MBR -> grub-install /dev/sda
8. Exit the shell
9. Reboot

This would mean I wouldn't have to reinstall which would be preferable. 

I would think that my paritioning is fine as it is. I'm just wondering if there's an advantage as such to setting it up yourself. Like if Ubuntu sets up the partitions in a very basic way or something.

---

