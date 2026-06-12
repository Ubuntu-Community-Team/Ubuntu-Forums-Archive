---
title: "Ubuntu 9.10 64bit ...GRUB.....Multiboot"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by RajeshSharma on 2010-03-08
Hey All ,
 
On my HP-Laptop Core-2 Duo , i m using Windows Vista 32bit and Ubuntu 8.10 Desktop 32bit .Both are installed within laptop internal hard disk space.
 
Recent upgrade of ram to 4gb and want to use few high cpu and ram consuming applications forced me to try my hands on Ubuntu 9.10 Desktop 64 bit OS.
I used an external hard drive -USB for ubuntu9.10 installation.
Ubuntu 9.10 works well for me except that it took over control of GRUB-Bootloader which was earlier taken care by Ubuntu 8.10 (32bit).
 
I cannot keep my USB HardDisk to be connected with my laptop and cant carry it with me everywhere . When i remove USB hard drive and as Grub is Ubuntu 9.10 which didnt find boot files .It directs me to grubeditor>
 
and  i m stuck with it as i cant use my Windows Vista or Ubuntu 8.10 in the absence of my USB Hard Disk .
 
Is there any way to use earlier version of GRUB -which is ubuntu 8.10 ????

---

### Post by oldfred on 2010-03-08
You needed to set the external to boot first so grub2 was installed on the external. Then when the external is not plugged in the internal boots. We just need to install grub 2 to the external, grub legacy to the internal and reset BIOS

Since you can boot you should not need the livecD instrucitons. But I would make sure I had another way to boot LiveCD or USB key install.

Must be from external that has grub2:
reinstall from working system - first find Ubuntu drive, external may not be sdb: 
sudo fdisk -l 
if it's "/dev/sdb"  then just run: 
sudo grub-install /dev/sdb 
If that returns any errors run: 
sudo grub-install --recheck /dev/sdab
Then: 
sudo update-grub

Set BIOS to boot from external & reboot.

Must be from internal that has grub legacy:
this should also find your internal to let you choose to boot it. It should be hd0 but check to make sure.
#reset grub boot
sudo grub
find /boot/grub/stage1 #you will get a response such as  (hd0,5)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition  or root (hd0,5)
setup (hd0)

---

### Post by kamallneet on 2010-03-08
As oldfred mentioned, you need to setup grub from the 32 bit ubuntu. In that menu.lst, you can add an entry for the 64-bit Ubuntu also, so that you can choose among them at boot time. And you should still be able to boot to OSs on the internal hard disk when the external disk is not plugged in.
Btw, it's not that hard to use grub command line too :)

---

