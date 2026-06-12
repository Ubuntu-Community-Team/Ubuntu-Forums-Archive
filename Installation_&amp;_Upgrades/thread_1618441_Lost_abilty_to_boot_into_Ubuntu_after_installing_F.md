---
title: "Lost abilty to boot into Ubuntu after installing Fedora on another partition"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by IanWood on 2010-11-10
Hi all,

I hope someone can help me.

I wanted to experiment with Fedora 14.

The machine has Windows XP and Ubuntu 9.10.

Before today when I turned the machine on there was a black screen with many Linux kernals to choose from and Windows.

I created another v for Fedora and installed it on there - the Ubuntu root partition is still there. 

When I boot now, there is a blue Fedora screen with just it and Windows. 

To make matters worse Fedora doesn't work with my graphics card, unlike Ubuntu does...

What do I need to change to be able to boot into Ubuntu again and how do I do it?

Thanks in advance,

Ian

---

### Post by Zimmer on 2010-11-10
If you have not overwritten the Ubuntu partition then it looks like Fedora has installed its own bootloader (GRUB or LILO not sure which it uses) to the MBR of your disk.

It should be possible to re install GRUB2 using Ubuntu live CD . GRUB2 has the ability to look for and find all OS's on the disk and then put them in the opening GRUB menu at boot...

See the info here
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

[https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2](https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2)
and maybe
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by IanWood on 2010-11-10
Thanks Zimmer for your quick reply.

So after I boot using the Live CD which command should I run? Sorry if this is obvious but I find this whole thing very confusing indeed. 

I would like to get Fedora and Ubuntu working, but if its very tricky I wouldn't mind deleting the partition I put it on.

Thanks again,

Ian

---

### Post by Zimmer on 2010-11-11
I have copied and pasted what I think is the relevant section from my second link above:


There may be times when a user needs to either move or reinstall a GRUB 2 installation. GRUB 2 needs to be reinstalled when a user is presented with a blank screen with only the word "GRUB", no prompt, and no ability to enter commands. This often happens when the MBR of the booting device is altered and GRUB 2 is removed, such as when Windows is installed after Ubuntu. Additionally, if a user cannot boot into an operating system at all, even using the rescue mode mode, a complete reinstallation of GRUB 2 may be necessary. 

Reinstalling from LiveCD

If a reinstall becomes necessary follow these instructions. The method requires booting from a LiveCD (Ubuntu 9.10, Karmic Koala or later version).

SIMPLEST - Copy GRUB 2 Files from the LiveCD

This is a quick and simple method of restoring a broken system's GRUB 2 files. The terminal is used for entering commands and the user must know the device name/partition of the installed system (sda1, sdb5, etc). The problem partition is located and mounted from the LiveCD. The files are then copied from the LiveCD libraries to the proper locations and MBR. It requires the least steps and fewer command line entries than the following methods. 
Boot to the LiveCD Desktop (Ubuntu 9.10 or later). 

Open a terminal by selecting Applications, Accessories, Terminal from the menu bar. 

Determine the partition with the Ubuntu installation. The fdisk option "-l" is a lowercase "L". 
sudo fdisk -l
If the user isn't sure of the partition, look for one of the appropriate size or formatting. 

Running sudo blkid may provide more information to help locate the proper partition, especially if the partitions are labeled. The device/drive is designated by sdX, with X being the device designation. sda is the first device, sdb is the second, etc. For most users the MBR will be installed to sda, the first drive on their system. The partition is designated by the Y. The first partition is 1, the second is 2. Note the devices and partitions are counted differently. 
Mount the partition containing the Ubuntu installation. 
sudo mount /dev/sdXY /mnt

Example: sudo mount /dev/sda1 Note: If the user has a separate /boot partition, this must be mounted to /mnt/boot Note: If the user has a separate /home partition, this must be mounted to /mnt/home. Encrypted home partitions should work. 

Run the grub-install command as described below. This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device. 
sudo grub-install --root-directory=/mnt/ /dev/sdX

Example: sudo grub-install --root-directory=/mnt/ /dev/sda 

Reboot (without the CD !)
(I think it should go straight to the Ubuntu installation without showing the GRUB menu )

Open a Terminal as before and...
Refresh the GRUB 2 menu with      sudo update-grub

When you next Boot the Grub menu should contain the entries for your Windows OS, Ubuntu and (maybe) Fedora (which may work, depending how Fedora recognised the drive when it installed: I say this as I have had a problem with a Mepis install in this way.)

---

### Post by IanWood on 2010-11-11
Thanks again Zimmer - appreciate your help.

I managed to find this [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) and used it to get my boot loader working again to use Ubuntu - but not Fedora (which didn't work anyway).

I will look into your instructions when I want to boot into Fedora too.

The whole reason I wanted to change was because a few times Xorg goes to 100% and the machine is effectvly unusable. Having read the readme for my Matrox driver I may just need to reinstall it each time a kernel chances...

Maybe I could upgrade to 10.04 for a newer install, but that's another question....

So happy now that I can use Ubuntu and don't need to use Doze :)

Ian

---

### Post by oldfred on 2010-11-11
If you run this the osprober should find Fedora and add it to our boot options.
```

sudo update-grub
```

---

### Post by Zimmer on 2010-11-12
> **IanWood said:**
> Thanks again Zimmer - appreciate your help.

....

Maybe I could upgrade to 10.04 for a newer install, but that's another question....

So happy now that I can use Ubuntu and don't need to use Doze :)

Ian

If you want a suggestion as to how to move to 10.04 this is what I would do. (stress on 'I' ).

Use a live CD to install 10.04 fresh onto the partition you have the dead Fedora on :) (two birds with one stone..)

When you get to that part on the install that installs GRUB use the 'Advanced' button hidden at the base of the GUI window and install it to the specific partition you are installing to ( sdaX) and NOT sda , NOT to the MBR.
Then go back to boot up 9.04 , and in the terminal  sudo update-grub  in order to add the new install to the bottom of the GRUB menu.


If you have sufficient disk space, create a partition just to save your personal data files to (instead of storing important stuff in a /home directory).(TIP: add DISKMOUNTER to your GNOME Panel)

This has the effect of being able to use either install of Ubuntu ( or any other Linux you may put on a 3rd partition) but have a common place to access for data storage .. so when you next want to wipe an install your personal data is not on the partition you are overwriting (and , yes , I have read all about having a separate /home partition, but I prefer this as being LESS complex to administer IMO)
 
and also it is easier to write an  rsync command for that data partition to copy it to an external back up...

One last thing...when wanting to copy files from one location to another in Nautilus, have you tried F3 to bring up a second pane for the destination location? Only discovered this recently (after nearly 6 years of Linux!) by reading the Ubuntu guide :)

---

