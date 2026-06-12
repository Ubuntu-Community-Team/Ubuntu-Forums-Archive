---
title: "[Solved] 18.04.3 LTS installation crashes from USB flash drive"
date: 2020-02-10
forum: Installation &amp; Upgrades
---

### Post by pickelhaupt on 2020-02-10
I'm trying to install Ubuntu 18.04.3 LTS (dual boot alongside Win10) on my new laptop MSI GS65 Stealth. The laptop is a 9th gen i9 equipped with Nvidia RTX2060 GPU and 16 GB Ram (dual channel). 

 I have Win10 on an ADATA XPG8200 Pro 1TB and intend to have Ubuntu on a Samsung 970 EVO Plus 1TB so the two OS will be on two separate ssd's. 

I have done the necessary preparations (i.e. disable Secure Boot and disable Fast Boot and set boot order in BIOS) and created an ISO USB flash drive in Ubuntu (on my old computer) using this tutorial [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview) 


**Now to my problem: **
It boots the USB drive fine but when I go into the installation procedure Ubuntu crashes. In the option "Install Ubuntu alongside Windows" it recognizes the Samsung ssd as target for installation but when I click proceed the installer crashes and the GUI disappears and just a lot of error messages in a Terminal/TTY screen. It is similar to this bug report [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1767594](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1767594) but I don't know if it's applicable to my system.
 
I get to make the partitions in the "advanced" installation option (Something Else) but since the whole Samsung drive will be dedicated to Ubuntu I thought that the Ubuntu installer could decide. Besides, I'm unsure about the swap partition vs swap file question...

I've read many bug reports on Nvidia GPU drivers causing trouble in 18.04. Could this be one of those?
I've tried to redo the flash drive installation also using Rufus but it makes no difference. Could it be the USB flash drive or USB drivers? The laptop has one USB-C 3.2 gen 2, two USB-A 3.2 gen 1 and one USB-A 3.2 gen 2. 

Any ideas on how to proceed?

---

### Post by dragonfly41 on 2020-02-10
When I last installed Ubuntu on an external SSD I first used "Try Ubuntu" in LiveUSB and ran GParted so that I could predefine SSD partitions.

My setup has SSD with a first partition /dev/sdb1 500MB as EFI partition.
Then I have Ubuntu in /dev/sdb2
I leave more than 10% unallocated as per advice I have read on SSD provisioning.
Check if you need to update firmware.

[P.S.] I always use the "try something else" option.

---

### Post by P-I H on 2020-02-10
This is how I mostly install when I have 2 ssd:s and install in UEFI mode.

First I boot the usb and selects "Try Ubuntu" and use Disks to check the system and I also starts Firefox to verify that the network is available.

Then I start the installation and selects "Normal installation", "Download updates while installing Ubuntu" and "Install third-party software for graphics and WI-FI hardware and additional media formats"

Next I selects "Erase disk and install Ubuntu". When there are several disks you are able to select the disk to use. Be sure to select the wanted disk.

Grub will be installed in the first disk sda or nvme0n1. In case W10 is installed on the first disk grub will be installed in the W10 boot record.

---

### Post by yancek on 2020-02-10
First thing I would suggest is to read the pages at the link below which contains the official documentation on dual booting windows 10 and Ubuntu UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The link you posted discusses a problem with an upgrade of Ubuntu and problems with the internet connection?  You also refer to error messages but posted none and I don't see any on the page you linked to.  If you are doing an EFI install, you would be much better off using the manual install method (referred to as Something Else in Ubuntu).  If you are not familiar with it, do some research.  If you are having problems already, don't choose the option to install additional software unless you are connected to the internet and have a fast and reliable connection.   You also do not indicate if windows is EFI.  If you want windows and Ubuntu separated and they are both EFI, you need to create an EFI partition on the SSD on which to install Ubuntu.  THe Ubuntu Grub will still probably install the EFI files to the EFI partition on the windows drive but they can be copied to the correct drive.  Simplest solution to this problem is disconnect the windows drive before beginning the Ubuntu install or turn it off or disable it in the BIOS if you can.  THe nthen Ubuntu EFI files will be written to the Ubuntu SSD.

Seems like a very new computer so the software needed may not be available yet.  Also, it could be Nvidia so posting some of the actual error information would be useful.

---

### Post by oldfred on 2020-02-10
Have you updated UEFI and SSD firmware? 
I updated my Samsung M2 drive using a bootable ISO from Samsung, not sure if it works with an external drive or not.

MSI GS65  Boot parameter: modprobe.blacklist=nouveau 
[https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions](https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions)
MSI GE63 Update UEFI then acpi=off not required
[https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues](https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues) & 
[https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off](https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off)

If SSD is external, you must partition in advance if you want it to boot on its own. The issue is Ubuntu's Ubiquity installer that only installs grub to first drive usually sda or first NVMe drive. You want grub on your SSD  not the Windows drive's ESP.
You can either reinstall grub manually or with Boot-Repair or unmount incorrect ESP and mount correct one in middle of install. And then edit fstab with correct ESP UUID after install.
Posted work around to manually unmount & mount correct ESP during install #23 & #26
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

---

### Post by pickelhaupt on 2020-02-10
I thank you for your replies and links. Even though I've used Ubuntu for years I'm an no more than intermediate user, as it were. 

Both ssd drives are internal i.e. installed on the motherboard. The installation program identifies them as nvme0n1 (Win10) and nvme1n1 (Ubuntu target disk). 

I think I've found a clue to solving my problem here: [https://medium.com/@carlosero/making-ubuntu-18-04-work-on-msi-gs65-8re-9818f4d9dc9d](https://medium.com/@carlosero/making-ubuntu-18-04-work-on-msi-gs65-8re-9818f4d9dc9d) in the part called "Installing Ubuntu. It seems very similar to the link concerning MSI GS65 Boot parameter link above. I will try it tomorrow after work.

[SIZE=3][FONT=medium-content-serif-font]*"There&#8217;s one thing you need to do, otherwise it will freeze at a random point during the installation. Just before booting from the USB, on the menu, select &#8220;Install Ubuntu&#8221; and press &#8220;e&#8221;, then on the line that reads &#8220;linux /cas/vmlinuz&#8221;, just before the &#8220;quiet splash &#8212; -&#8221;, write &#8220;nomodeset&#8221;, then press &#8220;F10&#8221; to run."*[/FONT][/SIZE]

---

### Post by dustyt on 2020-02-11
You should select "do something else" on the screen where you are selecting "install alongside windows 10"

Once you get there you can select the free space on your other hard disk, create your swap partition, / partition, /home partition... etc, lay it out however you want.

AND you can also select which drive you want to install the grub bootloader. I would personally install it on that drive. Then you can select which drive you want to boot first. If that one, it will have grub and you can chose which OS you want to boot. 

This will allow you to later select your windows disk to boot should something happen to Ubuntu or Grub... you can still boot windows because that drives boot partion won't be bothered, and vice-versa... windows won't mess up grub and your ubuntu boot.

I used to have a desktop set up this way with a bunch of operating systems. I was just saying a couple of times lately that I wish laptops had multiple drive bays. Is this something you did custom, or did it come with 2 drive bays????

---

### Post by dragonfly41 on 2020-02-11
> **dustyt said:**
> I was just saying a couple of times lately that I wish laptops had multiple drive bays. Is this something you did custom, or did it come with 2 drive bays????

Adding to my earlier post I now place my bootable Ubuntu SSD in an external docking bay via USB 3..

[https://www.startech.com/uk/HDD/Docking/2-bay-usb-3-1-gen-2-sata-dock~SDOCK2U313](https://www.startech.com/uk/HDD/Docking/2-bay-usb-3-1-gen-2-sata-dock~SDOCK2U313)

I also read one tip while searching around that if there is no internal docking bay, SSD might be installed internally (in PC towers not laptops) just using velcro tape!.
But I prefer the external docking station. It arrived with unexpected extra connector cables and connectors to allow very old (IDE) drives to be connected for extracting old archives.

P.S. [a portable SSD for laptops here.]("https://www.techradar.com/uk/reviews/crucial-x8-1tb-portable-ssd")

---

### Post by pickelhaupt on 2020-02-11
This laptop motherboard has 2 ssd m.2/nvme bays. From factory it has only one nvme ssd installed so I had to buy an nvme ssd, open the laptop and install it in the vacant ssd m.2/nvme bay. 

> **dustyt said:**
> 

I used to have a desktop set up this way with a bunch of operating systems. I was just saying a couple of times lately that I wish laptops had multiple drive bays. Is this something you did custom, or did it come with 2 drive bays????

---

### Post by pickelhaupt on 2020-02-13
Well, I think I found the problem. 
The ISO image 18.04.3 LTS (downloaded from [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)) crashed and produced a stack pile of error messages (SQUASHFS error) after installation started and when searching for these error messages I found the very good advice to checksum the downloaded ISO image ([https://askubuntu.com/questions/993407/is-verifying-isos-downloaded-from-the-official-website-worthwhile/993409#993409](https://askubuntu.com/questions/993407/is-verifying-isos-downloaded-from-the-official-website-worthwhile/993409#993409)). I also found the 18.04.4 LTS (at [http://releases.ubuntu.com/bionic/](http://releases.ubuntu.com/bionic/)) and performed a md5sums check the downloaded image before burning it to the USB flash drive.

After that it was a cake walk. I did not have to modify Grub setup parameters with *nomodeset* before *quiet spash* or *modprobe.blacklist=nouveau* after *quiet splash*. Also, partitioning in the installation manager was no problem (1. EFI 2. Swap 3. /(root) 4. /home). Only thing I had to do after install was to change boot order in UEFI/Bios to Ubuntu instead of Windows in order to get the Grub start up menu when booting. The default graphics driver after install is xorg, not nvidia. It can be a can of worms getting nvidia drivers to work sometimes but hopefully I will get it to work.

I'll mark this thread as "Solved"

---

### Post by P-I H on 2020-02-13
With the terminal command "inxi -Fz" you are able to get a list of your hardware.
With an Nvidia gpu the graphics device driver is either Nvidia or Nouveau. Xorg is the Display server. The alternative to Xorg is Wayland, but I think there are problems to use wayland together with an Nvidia GPU.

---

### Post by pickelhaupt on 2020-02-13
Again the installation went smooth. Latest nvidia-440 driver installed. [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) 

The only glitch is the system program crash report that greets me after logging in after boot. Similar to this [https://itsfoss.com/how-to-fix-system-program-problem-detected-ubuntu/](https://itsfoss.com/how-to-fix-system-program-problem-detected-ubuntu/)

My crash log looks like this:
```
karl@karl-GS65-Stealth-9SE:~$ ls -l /var/crash/
totalt 22920
-rw-r----- 1 gdm whoopsie 23466701 feb 12 23:27 _usr_bin_gnome-shell.121.crash
```

It's from yesterday so no new crash today. Just the pop-up

---

### Post by mörgæs on 2020-02-14
Thanks for an attempt at marking the thread solved. Better though to use Thread Tools.

---

