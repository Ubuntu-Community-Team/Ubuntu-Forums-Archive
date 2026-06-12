---
title: "GRUB Boot 2nd HD Problem"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by parsimony on 2008-01-18
I've installed Ubuntu on a 2nd hard drive SATA (and left first SATA with windows untouched) - but I can't get it to boot.

I've put GRUB on this 2nd HD and the entry is

root(hd1,0)

but I can't seem to get it to boot - it keeps on saying

error 17 - cannot mount...

Any ideas, thanks

---

### Post by Pumalite on 2008-01-18
If you have XP, I'd use Gparted live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php), resize the XP partition, install Ubuntu in that space, save the other drive for storage or a 'separate /home', intall Grub to MBR and you should have no problems.

---

### Post by c0met on 2008-01-18
Boot into Ubuntu go the URL below
[URL="http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp"]
http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp[/URL]

About 1/3 of the way down the web-page is a heading "Reinstall GRUB to the MBR". Follow the instructions from there onwards and you will be able to restore your system.

[COLOR="Blue"][B][U]BACKGROUND INFO
[/U][/B][/COLOR]You probably know all this, but just in case you don't, here is some information on hard drive codes

sda1 = scsi drive 1 (that is, a) and partition 1
sdb2 = scsi drive 2 (that is, b) and partition 2

(NOTE: hda1, etc, is also used instead of sda1; it essentially means the same thing)

(hd0,1) = (first hard drive, partition 2)
(hd1,0) = (second hard drive, partition 1)

(NOTE that the numbers are 1 less than what drive or partition they indicate. Whether or not Ubuntu shows sda or hda, Grub always uses (hd) :)

Lastly, using the above,
If XP is on your first disk and on the first parition, this will be (hd0,0) and if Ubuntu is on your second drive, first partition, this will be (hd1,0)

---

### Post by mastro59 on 2008-01-18
I have similar issue even if different topics ae involved. I hope someone can help me too.
The problem is always error 21,  grub can't find where the to start booting.
Here is my HW config.

Boot disc 250Gbye Sata samsung with WinXp on removable tray
spare disk 500Gbyte Sata Hitachi on removable tray

2x200 Sata WD configured in RAID 0 used as general storage device. ( I know Ubuntu does not like Raid disks)

In order to avoid the problems with a dual boot (I'm glad I did this) I have removed the WinXP boot HD and started Ubuntu 7.04 live DVD, installed linux on the 500Gbyte mounted as sdc, recognized by the OS as SCSI3, marked in grub as root(hd2,0)(missed any other name?), .Everything looks fine, reboot error 21. The problem is that I get a grub error even if I remove sdc, which means for me that the loader has been installed,  on the first SCSI driver ,the first one of the raid 0. Fortunately the drivers data are still accessable under XP, and I can boot in WinXP (plug in the samnsung HD), but I can't get any further. and these are my questions:
Why has the loader been written on this HD and not on sdc? Is there a way I can install Ubuntu on SDC, boot from this driver and use the Raid 0 as read only resource? SO far the only solution I can see is to get rid of the Raid0, but I hope there is a way to make it work. By the way I was able to read the data on the Raid0 disk, but after the Ubuntu installtion it is shown as avaible device (378 Gbyte) but can't be mounted.
Any suggestion is well appreciated
Thanks
Mastro59

---

### Post by Pumalite on 2008-01-18
Have you read this?:
[http://lists.alioth.debian.org/pipermail/utnubu-discuss/2006-May/000472.html](http://lists.alioth.debian.org/pipermail/utnubu-discuss/2006-May/000472.html)
Look for Fake Raid How-to Ubuntu Community Documentation too. (in google) (sorry I'm at my Apple Laptop)

---

### Post by dabl on 2008-01-18
Here's a great reference for working with Grub:

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

:)

---

### Post by mastro59 on 2008-01-18
the links provided are usefull and confirm my fear, the live DVD seems to include the Raid 0 support (I was able to read my files on the Raid array), but is not doing the same during installation or during the HD boot. So the next step will be to be able to make the system boot from sdc and then add dmraid.
I will try reinstalling grub on the sdc HD, and will see if this helps

Cheers
Mastro59

---

### Post by c0met on 2008-01-19
Hi Mastro,

Another little program that you might like to try is called SuperGRUB. It's pretty good at fixing boot problems. Download a bootable ISO for the program from the below URL. Burn this to a CD and then boot your system from this CD. It will give you options for...

    * making your win(dows) drive bootable
    * making your linux drive bootable
    * setting your system up for a dual boot

If you have Windows on one drive and Linux on the other, then you simply need to choose the dual boot option and it will setup the Grub menu for you so that you can select which operating system to boot into.

This is a great little program to have on hand. It's got me out of a few tight spots. You can download the ISO from

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by mastro59 on 2008-01-19
I will try supergrub as well, sound an interesting program.ù
In the mean time I have solved the issue, do not know why it works, but it does. 
Have installed Ububtu on SDC (hd2,0)
at boot error21
in Bios I changed the RAID controller to IDE (GA-X38 mother board GRaid controller)
boot with live DVD
from terminal I did these commands:
  sudo grub
  find /boot/grub/stage1   
    it  returned (hd2,0)
  root (hd2,0)   //(this will set the root on third HD first partiton)
  setup (hd2)   //this will install grub on third HD

reboot 
this time grub starts, but still not right,  I get a menu prompt, where I can edit the boot command, and guess what it is correct at ( HD2,0) but here grub can not find anything there. The reason is that at boot the boot disk is the first one, for ubuntu installer is the 3rd one. Why? I have no idea, most likelly a problem with bios and ide drivers. In any case I can boot following the grub menu ( press e for edit, and b for boot)
Once I am in Ubuntu I  have to redo the grub installation:
from terminal I did these commands:
  sudo grub
  find /boot/grub/stage1   
    it  returned (hd2,0)
  root (hd0,0)   
  setup (hd0)   
  sudo gedit  /boot/grum/menu.lst
here have to change all occurences of  HD2,0 to HD0,0 

in bios I have changed back IDE controller to RAID. So in WIndows I have a RAID disk (376 Gbyte) which I see in Linux, but can't mount. 
Now I can boot from Linux and WinXP, simply choosing the boot disk, and without having grub on the Windows disk. 
Even linux now is giving me the correct HD order, boot disk is hda and the 2 raids are hdb and hdc.

If someone has a clue of this, please let me know, I'm curios. 

I only have 2 little problems to solve. RAID support and remove gub from first DIsk of the raid0 array. If I remove both Ubuntu and WInXP disk I do not get the usual message NO BOOT DISK FOUND, but grub error 21....so grub is there, even after format and raid rebuild !!
Does anyone know how to remove grub from a disk? Should I use FDISK on this HD? 

Cheers 
Mastro59

If I leave t

---

### Post by Pumalite on 2008-01-19
T think to remove Grb from a Raid Array ia a little more complicated, but see if reading this helps you:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by mastro59 on 2008-01-19
I have seen that Howto, really well done. I will try installing DMRAID and may be this will help.
Unfortunatelly I can't find anythign that tells me how to get rid of the grub in the MBR.
I'm tempted to do that with FDISK...can try at the command prompt of windows...but not sure if this will affect the MBR of the WIndows boot disk instead.

---

