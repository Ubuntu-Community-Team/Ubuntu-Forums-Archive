---
title: "Ubuntu fails to load after install and shutdown"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by mxreader on 2006-08-31
Please help a newbie, Ubuntu fails to boot after install and a complete system shutdown.

I got XP on IDE drive and Ubuntu on SATA drive.  I installed using a DVD-RW drive off a liveCD.

I messed around going back and forth between Ubuntu and XP fine, the last use was on XP after trying to find a solution to my wireless problem with Ubuntu, called it a night so shut down the PC.  Next day Ubuntu fails to boot. XP is running fine.

Grub comes up fine and Ubuntu tries to boot but after a quick splash screen, it goes to black with white writing:

Booting 'Ubuntu, kernel 2.6.15.23-386
root (hd1,0)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.15.23-386 root=/dev/sda1 ro quiet splash
(other stuff here....)
mount: mounting /dev/sda1 on /root failed:Invalid argument
(other stuff here...)
takes me to a # prompt.

I think its related to other posts here about "mounting root file system" bug.... but the instructions to the workarounds are not descriptive enough for a newbie like me.

I am thinking of re-installing and then perhaps try to get at files like fstab and menu.1st as the said workarounds didnt explain how to get from a liveCD to the installed files to edit them.   How to mount the partitions from a liveCD? what commmands? these are not explained.

Hope someone can help.

---

### Post by craig552 on 2006-08-31
Assuming your trying to mount the partition hda1 using you live CD... 
You can use the following command to mount it in to the folder /mnt/
```
sudo mount -t ext3 /dev/hda1 /mnt
```
Then you can open menu.lst using
```
sudo gedit /mnt/boot/grub/menu.lst
```
and fstab using
```
sudo gedit /mnt/etc/fstab
```

If you're using Kubuntu, swap **gedit **for **kate**.
If your working without the GUI, swap **gedit **for **nano**

---

### Post by austin on 2006-08-31
an example if you have ext3 (default in ubuntu)

sudo mkdir /mnt/sda1
sudo mount -t ext3 /dev/sda1 /mnt/sda1
sudo cd /mnt/sda1

go to the files you want to edit with        cd
list directories with        ls
edit files with                    vi

---

### Post by mxreader on 2006-08-31
I hope someone still may have an answer to fix the problem.

However, thank you both for at least giving me some line commands to try out.

Austin, why is it that we have to mkdir first?  should the mnt directory be there already or not?  I guess I can check this out using the GUI file explorer.

Presumably by booting liveCD I am mkdir a virtual directory mnt from which the real HDD is mounted?

---

