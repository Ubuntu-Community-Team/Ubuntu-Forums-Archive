---
title: "Repairing GRUB using Edgy Install CD"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by lucky sevin on 2007-02-11
Right now I'm using the live mode of the 6.10 install cd.  I had installed the Kubuntu-desktop using Synaptic.  On reboot I get an Error 15: File not found.  I'm using a WD 250gb IDE with no other OS on the machine.  There is a slave drive, but there is nothing on it and I haven't mounted it yet.  By reading other threads I've tried several different commands in the terminal:

sudo grub-install /dev/hda (and with /dev/hda1 and hd0)

result:
Could not find device for /boot: Not found or not a block device.

find /boot/grub/stage1

result:
find: /boot/grub/stage1: No such file or directory

Now I'm stumped.  HELP!!

---

### Post by Herman on 2007-02-11
Hello lucky sevin,
From the Gnu Grub Manual,> 15 : File not foundThis error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.                            For example, if you get this error during booting, maybe Grub is telling you it can't find the specified kernel or initrd.img file. Usually this is because of a mistake in editing your menu.lst file, for example, the exact path or name of your kernel or initrd.img contains an error or a typo.
[Super Grub Disk]("http://supergrub.forjamari.linex.org/") can boot your operating system by symlinks to the kernel if you use, from the Main Menu,--> Boot Gnu/Linux and  Other OSes --> Boot Gnu/Linux -->...
                          Boot with Super Grub Disk instead, and then with your operating system running you can check your file and correct your menu entry for Linux.
If you don't want to make a SuperGrubDisk you can also use Grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") to boot your computer with.
The best way would be to do a [**[B]Direct (kernel) Boot**[/B]]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.")

              Once you have it booted up, open your menu.lst file with 'sudo gedit /boot/grub/menu.lst', 
```
sudo gedit /boot/grub/menu.lst
```                          Use the command 'ls /boot' to check for the correct name for your Linux kernel and initrd.img.
```
ls /boot
```                          Copy the correct name from the terminal output to the text file and paste it to avoid typos. Don't forget to save the changes in your menu.lst file before your close it.
              
                          This error can also occur if the files needed to boot with are missing or corrupt in the /boot/grub directory. (But this would be very rare) Refer to             [Grub loading stage1.5]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_loading_stage1.5") for how to completely delete possibly corrupted grub files and restore them again from /sbin/grub. (Only if you have to).

Regards, Herman :)

---

### Post by Herman on 2007-02-11
Well actually, you can use the LiveCD to check for a mistake in your menu.lst and repair it if you want to, here are some instructions for that,
[                           Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")

Do whatever seems the easiest for you. And Good Luck, lucky sevin
Regards, Herman :)

---

