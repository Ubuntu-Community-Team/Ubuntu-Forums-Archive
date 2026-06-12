---
title: "Disk partionining and grub"
date: 2011-12-17
forum: Installation &amp; Upgrades
---

### Post by deepakdeshp on 2011-12-17
I need to shrink some partitions, and delete some other. I have 2 disks in my desktop and the layout of the first one is as follows:-

Partition                      SIze
/dev/sda                     Unallocated
sda2                            Linux partition
swap

Extended partition        It has partition nos8,5,6,9,7
sda1                             Linux partition,

I am planning to remove partition 8 and partition 2. How will it affect the grub? WHat steps do I need to follow so that all systems boot from    the respective partitions.
I will use Clonezill for this purpose.

---

### Post by mikewhatever on 2011-12-17
Depends. If Grub is installed on one of the partitions you are going to remove, it will get removed as well, and you'll get an unbootable system, which is easily remedied by reinstalling Grub from CD/USB. Make sure you have one of those ready. It's also a good idea to look up a howto on reinstalling Grub on a OS that you wish to retain.

PS: Clonezilla is probably not the tool for repartitioning. I suppose you meant Gparted.

---

### Post by Rex Bouwense on 2011-12-17
If you could post a screen shot of Gparted, it might give us a better idea of what you are trying to do.  After reading your post twice, I'm still not sure of your set up.

---

### Post by deepakdeshp on 2011-12-17
The screenshot is attached. 

I will be using clonezilla for restoring the image and some other tool loike gparted to manage the partitions.

I have installed the grub on both my disks ,sda and sdb. When I installed Mint12 , I am getting hsync and vsync error on monitor and dont see the first grub boot screen. When I hit enter it takes the first OS to boot, mint 12 and goes ahead. 

The layout is:-

Partition               OS
a1                     Suse LTES 11
a5                     Nagios  9.04 Ubuntu server
a7                     Edubuntu 9.04 desktop
b5                     Mint9
b7                     Ubuntu 10.04 server
b6                      Mint12[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]

b1 is the 2nd disk whose pic I have attached


Is it possible to install WIndows XP or 7 on the 1st partition now and later re-create the grub which will recognize WIndows and all the above Linux versions while booting?

---

### Post by fantab on 2011-12-18
The Screen-Shot you've use is from Disk Utility tool and it does not tell us much?

install GParted: ***sudo apt-get install gparted*** , and post the screen shot.

Also tell us Which grubs (from which distros) you have installed on both your Hard Disks?

---

### Post by deepakdeshp on 2011-12-20
The screen shots with gparted are attached. 
I have grub from Ubuntu 9.04 , ubuntu 10.04 and Mint 12. That should be grub and grub 2.0 / The last OS to install was mint 12 and when I installed it, I installed grub2 on sda and sdb.

Since installing grub 2 from mint 12  am seeing***" vertical sync and horizontal sync out of range***" message when I boot my machine. When I hit "enter " it does boot the first os in the grub menu. I need to solve this problem too. Any help will be much appreciated.

---

### Post by Hakunka-Matata on 2011-12-21
Throw caution to the wind, just like in Washington DC.  
Do the massaging of the HDD(s) and then update grub.  See what happens, maybe nothing.


A.K.A.  "Just hit Enter"

---

### Post by deepakdeshp on 2011-12-21
Update grub from mint once more or from one of the ubuntu distros?

So What I understand is I boot one of the **ubuntu distros**, massage the disks  and run update grub. Because the mint grub gave the hsync vsync problem while the Ubuntu distro workd fine untill overwritten by the mint grub..

---

### Post by emmomalick on 2011-12-21
Use Gparted to re-arrange your Disks Partitions. and then update your Grub if needed 

```
sudo update-grub
```

---

### Post by deepakdeshp on 2011-12-26
I updated grub with*** update-grub*** command and it worked fine. It has detected the existing systems and accordingly created the grub on the partition from which I ran the command
The grub is created on the partition frm which I ran ***update-grub***.

I have multiple disks as shown in the attachments in the previous posts. I   need that the grub should be re-built on the other disks also and if I boot from the other disks, it should show me the latest installed os 

information. I am attaching the grub,cfg, I had to rename it as grubcfg.txt. This grub, when it loads, the first opening  sreen gives me error "Hsync and Vsync out of order." How do I handle this? Should I comment out some lines from the code?

---

### Post by oldfred on 2011-12-26
By looking at your grub.cfg you can tell which install is next and just hit down arrow to get to another install. I have hit down arrow before menu appears but after BIOS and it remembers it and works to change boot item.
Not sure about video issue. I might try comparing one that works from Ubuntu and the one from Mint. Possibly something in gfxmode?

You can only have one grub in the MBR and that is the one that controls booting. It should be the one you will use the most, but is Ubuntu's grub works, then I would install it to the MBR and use it to boot.

If you can get into Ubuntu, you can just reinstall grub from inside the system. You then do not need a liveCD to reinstall grub.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

You may need to run the dpkg on all your other installs, so a major update to grub does not reinstall it to the MBR. I think unchooseing all drives makes it not reinstall.

Besides liveCDs I like to have several repairCD/USB bootable versions. Then I know I can get into one or the other of my installs.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by deepakdeshp on 2011-12-27
Thank you Oldfred for your detailed reply. I had seen the entries in grub.cfg and was hitting "Enter" key a number of times  to boot the distro I wanted.

I did #**update-grub /dev/sda** after booting from sda5 but the grub I am getting is the same as the entries in /boot/grub/menu.lst as this is grub1 on Ubuntu 9.04. When I update grub after booting from sda5, it only scans entries on sda srive and creates the menu. It doesnt scan sdb and sdc which have different distros. Is there any way to refresh the grub entries on /dev/sda which should contain all the distros from sdb and sdc too.

---

### Post by oldfred on 2011-12-27
The MBR only has one boot loader. All the others are not used unless you configure for chainloading. Updating the other grub menus will not change the menu you boot from.

Generally I prefer grub2 from Ubuntu, but I know it best. The os-prober in Ubuntu's grub2 is very good at finding other systems and adding menu items to boot them. Grub legacy was not very good at finding other systems as we usually had to manually add boot stanzas.

You have to do the grub install commands or the dpkg command to reinstall grub2's boot loader to the MBR from whichever install you want to be the one in control.

---

