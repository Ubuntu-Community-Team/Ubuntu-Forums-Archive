---
title: "[SOLVED] Dual boot grub issue"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by Licurgo on 2007-09-28
Hi:
I have 2 HD and yesterday I installed Gentoo in HDA while Ubuntu 7.04 is in HDB
But something terrible happened and I cant upload Ubuntu, I tried the help document RecoveringUbuntuAfterInstallingWindows in which I modified the Grub:

Sudo grub
find /boot/grub/stage1
"hd0,2
hd1,0"
root (hd1,0) "Enter"
setup (hd1,0) "Enter"
quit

But for some reason only starts the hd0 (with gentoo) and no the hd1 with Ubuntu

The report of the command sudo fdisk -lu is:
Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1              63      208844      104391   83  Linux
/dev/hdc2          208845     2136644      963900   82  Linux swap / Solaris
/dev/hdc3         2136645   312576704   155220030   83  Linux

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *          63   387889424   193944681   83  Linux
/dev/hdd2       387889425   390716864     1413720    5  Extended
/dev/hdd5       387889488   390716864     1413688+  82  Linux swap / Solaris
Comment: hdc is gentoo and hdd is Ubuntu

The report of the menu.lst of the first disk is:

default 0
timeout 30
splashimage=(hd0,2)/boot/grub/splash.xpm.gz
title=Gentoo Linux
root (hd0,2)
kernel /boot/kernel-genkernel-x86-2.6.19-gentoo-r5 root=/dev/ram0 init=/linuxrc ramdisk=8192 real_root=/dev/hdc3 grub
initrd /boot/initramfs-genkernel-x86-2.6.19-gentoo-r5

HELP PZ
:lolflag:

---

### Post by Pumalite on 2007-09-28
Post: 
sudo /boot/grub/menu.lst

---

### Post by SpiritIsReality on 2007-09-28
howdy

there's maybe other tutorials around that explain chainloading easier, but I used this one.
[http://www.justlinux.com/forum/showthread.php?threadid=147959](http://www.justlinux.com/forum/showthread.php?threadid=147959)

beginner here, but it looks sort of like you have 
-gentoo grub in (hd0)  mbr
-ubuntu grub installed to it's own root partition
-no chainloader in gentoo menu.lst to give you a choice to boot to ubuntu 

a guess on my part would be to make a back up copy of your gentoo menu.lst
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup (there's a space between lst and /boot/grub/menu.lst.backup
add a chainloader entry for ubuntu like so, under the other os heading. in gentoo /boot/grub/menu.lst
title.................... ubuntu 7.04 (on /dev/hdd1)
root................... (hd1,0)
chainloader....... +1
savedefault
(don't put the dots in, use two tab keys to get the space between title and ubuntu)

save the file, reboot. Hopefully you see ubuntu on the menu. and if I read your partitions right,
if you select ubuntu with the arrow keys when gentoo grub menu appears, and press
enter, you should then see ubuntu grub menu.
good idea in ubuntu /boot/grub/menu.lst to comment out the hiddenmenu like so
#hiddenmenu

hopefully I haven't missed something real important, except it is kind of curious that
your hard drives are hdc and hdd. usually that's for the cdrom drives. usually the hard
drives are hda hdb
I think you have your hard drives on the slave ide, or they are plugged onto 3 and 4 sata?
well let me know where I messed up here. I'm not really competent to be giving advice
about something I know so little about.

Pumalite ...howdy, let me know if you think I've messed up..thanks

trails

---

### Post by logos34 on 2007-09-29
fmat's suggestion is the easiest I think, just add a chainloader boot entry for ubuntu to Gentoo menu.lst--you've already installed grub to the bootsector of ubuntu root partition (which is required, afaik). Or use the [configfile]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") format.

Unless, of course, you would rather use ubuntu's own grub, in which case you would reinstall grub almost exactly like you did with this difference:

**setup (hd0)** -->sends grub to mbr

Your drives hdc and hdd are actually your secondary IDE channel master and slave, so you should swap the cables on the mobo so that the hard disks are connected to the primary channel and the cdrom as secondary master.

---

### Post by SpiritIsReality on 2007-09-29
logos ...thanks

---

### Post by Licurgo on 2007-10-01
Hi guys:
The Saturday was a CAOS for some reason I couldn't open an OO date base and I couldn't install the printer, startin with the liveCD, remember I couldn't initiate it from the hard drive.
So I changesd the bus cable as was suggested by fmal and by logos34.
then I made a new installetion and the program itself made the entry for gentoo and fortunatetly everything is going OK
Thanks a lot guys
:guitar:

---

