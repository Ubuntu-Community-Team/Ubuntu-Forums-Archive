---
title: "Issue with Dual Booting"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by Salgat on 2006-09-08
Unfortunately it seems as though nearly every guide I google is about installing Ubuntu after you install Windows, and when I tried  GAG(seems to only support EXT2?) it didn't recognize the Ubuntu partition.  My question is, with GParted or another program, when I convert a partition to EXT2 from EXT3, will everything be intact(Im guessing no?), and also, if not, how do I setup dual boot for XP and Windows(Ubuntu was installed first).  And please don't tell me to reinstall Ubuntu, thats a last resort and is something I can do on my own, the whole point of this post is to avoid that.  Thanks for any help!

---

### Post by raldz on 2006-09-08
Just install Windows.. then after installing Windows, you will have to reinstall GRUB (the bootloader).. to reinstall GRUB, do this:

1. Insert the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. type: "find /boot/grub/stage1"
5. Type "root (hd0,6)", or whatever is the result from number 4 
6. Type "setup (hd0)", ot whatever your harddisk number is, this will install GRUB in the MBR.
7. Quit grub by typing "quit".
8. Reboot.

---

### Post by zxee on 2006-09-08
If you have a partition for windows you can just install windows to it.
If you need to create a partition I think gparted will allow you to change types or take a look at cfdisk.You can look at your partitions with cfdisk or fdisk -l from a terminal. 
After you install windows (since it overwrites the mbr) you will need to use the ubuntu live cd and reinstall grub-which if it works the way it suppose to will set up for dual booting windows.
Check out the official ubuntu grub guide here: [https://help.ubuntu.com/community/SystemAdministration#head-2f326435bdb2aef79861d039744b03887dfa3dfd](https://help.ubuntu.com/community/SystemAdministration#head-2f326435bdb2aef79861d039744b03887dfa3dfd)

---

### Post by Herman on 2006-09-08
> Unfortunately it seems as though nearly every guide I google is about installing Ubuntu after you install Windows, and when I tried GAG(seems to only support EXT2?) it didn't recognize the Ubuntu partition. My question is, with GParted or another program, when I convert a partition to EXT2 from EXT3, will everything be intact(Im guessing no?), and also, if not, how do I setup dual boot for XP and Windows(Ubuntu was installed first). And please don't tell me to reinstall Ubuntu, thats a last resort and is something I can do on my own, the whole point of this post is to avoid that. Thanks for any help! GAG supports ext3 without a problem. Ext3 is  essentially the same as ext2, but with 'journalling' added, so if a power failure occurs, or you shut down your computer wrong, it is less likely that you will lose data and incur serious filesystem damage.

You do not need to convert your operating system to ext2 in order to use GAG Boot Manager. 

GAG Boot Manager is a boot manager though, not a boot loader. (As we all know, a manager's job is to delegate responsibility, not to do all the actual work). SO to use GAG Boot Manager to boot Linux, you need a boot manager like Grub or Lilo installed to the first sector of your Ubuntu or Linux distro's partition. Many people like GAG Boot Manager, because it is graphical and quick to reconfigure, and is 'operating system independant', being installed in the MBR and in the first track of the hard disk.
Here's more information on how to use GAG Boot Manager for booting Ubuntu, [Click Here]("http://users.bigpond.net.au/hermanzone/p12.htm")

The other posters are correct if you want to continue to use Grub. Grub is  more than just a boot loader, it is also a boot manager too, and is even really a miniature operating system in its own right. For more info on Grub, [Click Here]("http://users.bigpond.net.au/hermanzone/p15.htm").

I agree with raldz.
If you want to install Grub to your Ubuntu partition so you can boot with GAG Boot Manager, you do the same as raldz explained, but change step 6 slighlty,
6. Type "setup (hdx,y)", 'x' being whatever your harddisk and 'y' being whatever your Linux partition numbers are, this will install GRUB to the first sector of your partition.

I also agree with xzee, GParted is the best partitioner to use if you need to  resize your Ubuntu partition and make room for Windows. [GParted LiveCD]("http://gparted.sourceforge.net/") version 0.3-1 is now available featuring new 'move' support for Linux partitions. GParted Live CD is fully compatable with Linux operating systems and bootloaders.

Regards, Herman :D

---

