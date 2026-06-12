---
title: "Install Ubuntu on a Win7 PC"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by jmcdonnell1947 on 2010-08-21
Hi,
 
I am looking for some reassurance on whether my installation plan will work. I have a new PC with two SATA drives. I have installed Win7 Pro on the first hard drive. I also installed the OSL2000 boot manager and it works OK. I want to install Ubuntu 9.04 on the second drive without impacting the Win7 setup.
 
My plan is to disconnect the Win7 drive and install Ubuntu stand-alone on the second drive. After testing the Ubuntu installation, I want to reconnect the Win7 drive. Hopefully the OSL2000 boot manager will place it into the boot menu and that will be the end of it.
 
I am concerned that Linux may become confused if the device names change. I am also afraid that Ubuntu might write something to the boot record of the first drive without first asking permission. I do not know at this time what the bios and/or Ubuntu will do regarding /dev/sda versus /dev/sdb. I am hoping that Ubuntu will utilize only UUID to identify the hardware and not be concerned about changes in the sda/sdb area.
 
Shoud I be confident or concerned?
 
Thanks, John

---

### Post by user_linux08 on 2010-08-21
John,
While I don't have an advise how to install onto 2 separate HDs. I also have Windows 7, & Ubuntu 10.04 installed on the same HD, with separate partitions.

Just be VERY CAREFUL When you start the installation of Ubuntu. Just read and follow the instructions for the specific location onto which you want Ubuntu installed. I always select the 3rd option "let me select", and instruct it to install on a separate partition. (you may have to partition HD before that with .ext3 or .ext4 format). 

After you finished the installation, LINUX will install GRUB2 onto your HD, such that, it will provide the option when you boot up, to select between Ubuntu (1st option), and windows (2nd option).
Mine works flawlessly.

---

### Post by cazador31 on 2010-08-21
I Have windows 7 and I installed Lucid on a second harddrive. Follow the prompts and you will see where you put it in the drive you want from a drop down menu. It's working great for me

Also I never unplugged my default harddrive and all went well

---

### Post by jmcdonnell1947 on 2010-08-25
I want to report back on the installation. It basically worked out as planned. Ubuntu installed OK on a logical drive in the extended partition of the second physical disk. Upon reconnection of the Windows drive and system reboot, Linux appeared as a selection in the OSL2000 boot manager menu. Ubuntu would not boot, however. I had to select "MBR Hard Disk 2" from the OSL2000 menu. Then Ubuntu started and everything ran normally.
 
I have been running Linux on and off for quite a few years, going back to the days when I had to manually configure and compile the kernel. At that time I could not even use modules. Everything was compiled directly into the kernel. More than once I needed to modify device driver code in order to get the IRQ and memory selections required for my particular hardware.
 
One thing that I do remember fondly is the old LILO boot loader. During the last stage of Linux configuration, there was a nice choice presented - MBR versus Linux partition. I was not given such a choice during the Ubuntu installation. It qujietly set up the boot on the MBR. I found some information online regarding how to manipulate things in order to boot from other than the MBR, but none of the suggestions worked. Because Ubuntu is running fine, it's really no big deal. But it would have been nice if the installer would have at least asked a question instead of simply presuming to know what is best for the user.

---

### Post by techxcell on 2010-08-25
The Ubuntu installer INCLUDES the option to select the installation of grub onto your chosen drive and partition!

The last screen of Ubiquity (just before it starts copying files) which shows all the options you selected has a button labeled "Advanced" at the lower right corner. You can tell ubiquity where and even if you want to install a bootloader.

---

### Post by jmcdonnell1947 on 2010-08-25
Yes. I did discover this at a later point of time. But I will offer the opinioon that it could be made a little more prominent. The old LILO selection was "in your face". 
 
Is it possible to jump right to the boot loader part of the installation process?

---

### Post by oldfred on 2010-08-25
This runs something like the installer and you should run it to choose sdb (or whatever your drive is). Grub has a nasty habit of just installing to sda. 

Grub2 does not like to be installed to a partition and there is very little reason to install it to a partition. It will complain about blocklists which are less reliable, but you can force it to install. On initial install it does not seem to complain but will on updates.

If you have set BIOS to boot grub2 from the Ubuntu drive and you can boot windows you are all set.

---

### Post by jmcdonnell1947 on 2010-09-01
I want to thank everybody who contributed to my post.  I have always had more faith in community support than in vendor websites.

I installed grub2 in the Linux partition which is a logical drive in the extended partition of the second hard disk which is sdb.  Grub2 is also somehow installed in the MBR of sdb.  This is a good thing because although a Linux selection does appear in the OSL2000 boot manager menu, Linux will not boot when selected.  Linux will however boot from the "Second Hard Disk MBR" menu selection of OSL2000.  Yes, I know I could avoid all of the confusion if I simply accepted grub2 as my boot manager instead of clinging to OSL2000.  But that's beside the point and I am willing to move along and accept the present setup.

After a successful installation of Linux 9.10, I immediately upgraded to 10.04.  Upon first boot, I had no gui.  This was due to the fact that my Radeon HD 5670 was no longer recognized as it was in 9.10.  I had to reboot in terminal mode and manually create a xorg.conf file with a VESA device.  After that the gui was operational and I downloaded and installed the ATI Catalyst software which provided the desired screen resolution et al.

Additionally, my HP Laserjet 1505n was no longer functioning in 10.04 as it did in 9.10.  I found a foo2zjs.tar.gz download on the web which corrected the issue.

Finally, I had to jump through quite a few hoops to get my Creative X-Fi sound card to operate.  After going down several dead end paths, I downloaded and installed the very latest ALSA drivers which seemed to do the trick.  I think that the HD sound features of the Radeon 5670 card were causing some kind of conflict with the X-Fi during the Creative driver installation process (which I never was able to completel and which I subsequently abandoned).

The bottom line - Ubuntu 10.04 is up and running without issues.  All hardware is funtioning as it should.

One minor annoyance - my system clock jumped ahead four hours when I booted back to Windows.  This was fixed by changing UTC=yes to UTC=no in /etc/default/rcS.

---

