---
title: "Dual Boot from 2 hard drives?"
date: 2013-07-08
forum: Installation &amp; Upgrades
---

### Post by Langney on 2013-07-08
Hello. I'm just wondering if anyone could help me regarding this matter. I've dual booted before on a  single hard drive but I'm wondering how i would go about dual booting from 2 seperate hard drives as I'm going to be using one of them for Winedows 7 and the other for Ubuntu 12.04. Trouble is i'm a real noob when it comes to manually setting things up in G-parted. I'm just wondering If anyone has a guide or a link to an Idiot proof guide so I can Install Ubuntu onto my other hard drive without borking everything.

Thank you In advance

Langney

---

### Post by ajgreeny on 2013-07-08
Install windows first onto the first disk.

When you install ubuntu choose "Something else" at partitioning stage and then you will get the option to install the bootloader (grub) to the disk of your choosing.  You should choose the same disk as ubuntu is installed to, making sure grub goes onto the root of the device, ie, /dev/sdb and not to /dev/sdb1 or other numbered partition.

Now at boot time if you have the first disk as priority device the machine will boot straight to windows, as that disk will have the windows bootloader system.  If you give the second disk boot priority, the grub menu should appear giving you the option of ubuntu or windows.

I am trying to find an up-to-date installation instruction website with pictures to help, but at the moment I can't find one; perhaps you will have more luck.

---

### Post by Mark Phelps on 2013-07-08
I generally recommend having only one disk connected when you install an OS.  While it's not necessary, it prevents the situation where you accidentally write boot loader files to the wrong disk -- and then have repair to do to get that other OS booting again.

IF only the "Ubuntu drive" is connected during the install, there is no risk of writing GRUB to the wrong drive.

After Ubuntu installation, do the following:
1) Reconnect the "windows drive"
2) Boot -- but from the "Ubuntu drive"
3) Open a terminal and enter "sudo update-grub".  This will regenerate the GRUB config file, adding an entry for Windows.
4) When you reboot, you should get a GRUB menu allowing to choose either OS.

---

### Post by Langney on 2013-07-08
Thanks guys for the tips. I'm going to try both methods. Fingers crossed :D

---

### Post by oldfred on 2013-07-08
A couple of links one gui and the other now text mode with alternative install which is not now available with the newest versions of Ubuntu. But install process is essentially the same with all version or modes.

 Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer which is not available on newest versions. 
Different versions have slight difference in install screens but process is the same. And gui versions are not really a lot different.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by Langney on 2013-07-16
Hi guys. Sorry about the long delay as I had to get my computer a new heatsink and Fan. All Is working as Intended. I can now dualboot with two hard drives. Thanks all who helped with this matter :)

---

### Post by cogset on 2013-07-16
I'm late but,if this is of any help,I have a cumbersome setup with two disks,one is a windows/Ubuntu dual boot,the other one is a triple boot with Ubuntu and two Mint versions:I was convinced that only one of the disks was actually controlling the boot procedure,then I've found that in reality the disk which had the priority in the Bios was obviously the one from which the system booted,but I could choose the boot device sequence with F8 (in case of my motherboard) and therefore boot from the other one as well.

Which is to say,the first reply is spot on:since you're actually planning to install "only" two operating systems,each on his own disk,probably the easiest way would be to set the priority for the windows disk,which will boot automatically and never see the Ubuntu installation,and manually alter the boot sequence when you want to boot from the second drive,which will present you with the choice to start either windows or Ubuntu.
It could obviously be the other way around,if you wish so:in reality,there are many ways to thinker with Grub-as long as you don't overwrite the windows MBR,Grub will start pretty much anything...I've done some experiments (some not entirely on purpose,may I add) and I've never been left with an unbootable system ;)

---

