---
title: "Lubuntu manual partitioning"
date: 2021-01-14
forum: Installation &amp; Upgrades
---

### Post by icewizard8029 on 2021-01-14
I am trying to install lubuntu 20.04.1 with a usb to my new acer aspire model N19C1 laptop using this manual - [https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html) . It came with windows installed, but I want to completely erase windows and only use lubuntu on this computer. At the partitioning step, the only option that shows is the manual partitioning option. It is also showing that my system was started with an EFI boot environment and my device has an MBR partition table. After choosing manual partitioning I selected "new partition table" and chose GUID partition table (I don't know if I should've chose GUID or master boot record). Then I selected the partition and selected create, and now I'm shown a window with a file system option, a mount point option, and flags, but I don't know what I should select for any of these so that I can properly install lubuntu. [ATTACH=CONFIG]287741[/ATTACH][ATTACH=CONFIG]287742[/ATTACH]

---

### Post by oldfred on 2021-01-14
Please do not create duplicate threads.
You did change this one to Solved, but this is same issue?
[https://ubuntuforums.org/showthread.php?t=2456574](https://ubuntuforums.org/showthread.php?t=2456574)

---

### Post by icewizard8029 on 2021-01-14
I think this is a different issue. In the last thread I was originally trying to install lubuntu 18.04 because I couldn't install 20.04, but a user helped me and now I'm able to install 20.04, but I'm confused on how to get through this partitioning step. In the last thread I didn't see any partition, but now I do. Should I just continue asking in the last thread instead of this one?

---

### Post by GhX6GZMB on 2021-01-14
Your screenshots look strange. From where did you get your Lubuntu 20.04.1 .ISO image? Hopefully from lubuntu.me.

A normal install should run something like:

Booting from USB/DVD (black screen for some time), then:
Select language, you'll land on a "DOS-like" window where you can select "Start Lubuntu". It's a good idea to press F3 and select the keyboard layout first.

This will start the live boot, and after some minutes you'll land on the Lubuntu desktop.

Did you get this far?

---

### Post by icewizard8029 on 2021-01-14
I downloaded the ISO file today from lubuntu.me/downloads and the sha256sum matches their given sha256sum (0727253098c998c0b7b7963326690419710cdce2479472ca7cfe7adda7a31174). 

The boot/install process so far has looked pretty much how you're describing it. After The lubuntu desktop opened I selected the "Install Lubuntu 20.02 LTS" file but now I'm stuck on this partitioning step.[ATTACH=CONFIG]287745[/ATTACH][ATTACH=CONFIG]287746[/ATTACH]

---

### Post by GhX6GZMB on 2021-01-14
OK, looks good, you've landed in the right place and your install is running.

[SIZE=1]But I see an issue, which I don't really know how to solve. Your USB-stick is /dev/sda which it should NOT be.
/dev/sda is your future main harddisk, which is now blocked by your stick.

How was the stick formatted before the .ISO was installed? It should be FAT32.
Using Rufus and choosing only the default settings usually works.[/SIZE]

EDIT!!! Scratch this. I tried my own installer, you're fine.

---

### Post by grahammechanical on 2021-01-14
It is best to choose GUID partition table (GPT) even if our motherboard is BIOS and not UEFI. With MBR partitioning there is a limit to the number of partitions that we can have and a workaround that we have to do to have more than that limit. With GPT the limit has been expanded to be effectively limitless. For the ordinary user that is.

I cannot understand why you did not get the option to Erase Disc and Install Lubuntu. With the manual install option we have to select partitions, give them a mount point and a file system. We have to choose where the Grub boot loader is installed. You have yet to create partitions.

If you want to use the Manual option then I suggest that you use GParted to create a GPT partitioning system for that drive and then create the partitions you want/need. You need a boot partition; a root partition; and it makes sense to have a /home partition and even a partition for Data. You may need a Swap partition. 

With the partitions already created you then need to tell the installer which partition is what by giving it a mount point from the drop down menu. And also a file system.

Regards

P.S. I am thinking that the USB flash drive (/dev/sda) is the USB memory stick that you are loading the Lubuntu live session from. Click the down arrow to the right of the panel and see if it shows your hard drive.

---

### Post by icewizard8029 on 2021-01-14
I used Unetbootin to add the ISO to this usb. I'll remove the files and try Rufus to see if that changes anything. Before I installed the 20.04 iso onto this usb another os iso was installed on this usb and I removed those files before adding the 20.04 iso file to it. The partitions page on the lubuntu 20.04 installation window says the usb has a FAT32 file system

---

### Post by GhX6GZMB on 2021-01-14
No, stop.
You're absolutely fine. Now you just need to define your partitions manually.

I suggest 30 GB for /dev/sda1 with mount point / formatted.
The rest of the drive you can partition as you like: /dev/sda2, /dev/sda3 etc., but they all need to formatted and given a mount point. /home is mandatory, of course :)

Sorry, sorry that I created confusion in my earlier post.

---

### Post by oldfred on 2021-01-14
I have not installed Lubuntu, but it looks like you only are showing the USB drive. 
Do you see a larger drive than the 16GB(14.9) drive?

On my system flash drives are often promoted to sda and old sda becomes sdb etc.

---

### Post by icewizard8029 on 2021-01-14
> Click the down arrow to the right of the panel and see if it shows your hard drive. All I see listed is my 14.9 GiB usb. It doesn't show my hard drive.

---

### Post by GhX6GZMB on 2021-01-14
> **oldfred said:**
> I have not installed Lubuntu, but it looks like you only are showing the USB drive. 


It's all OK. Selecting "Manual Partitioning" will show the full harddisk and allow partitioning and mount point selection.

---

### Post by icewizard8029 on 2021-01-14
> I suggest 30 GB for /dev/sda1 with mount point / formatted.
The rest of the drive you can partition as you like: /dev/sda2, /dev/sda3 etc., but they all need to formatted.
I tried making a partition the a / mount point and 30 GB, but that takes up all the memory and I can't make any other mount points. I think this is because the only storage device is my usb and not my computers. 

> Do you see a larger drive than the 16GB(14.9) drive? No, this is the only storage device showing.[ATTACH=CONFIG]287747[/ATTACH]

---

### Post by GhX6GZMB on 2021-01-14
> **icewizard8029 said:**
> All I see listed is my 14.9 GiB usb. It doesn't show my hard drive.

Just tick the circle next to "Manual Partitioning" and move on. Click "New partition table".

---

### Post by icewizard8029 on 2021-01-14
> Just tick the circle next to "Manual Partitioning" and move on. Click "New partition table".
I did that but my full hard disk never shows, all I'm getting is my usb. This is what is shown after I select the circle for manual partitioning: 


\[ATTACH=CONFIG]287748[/ATTACH]

---

### Post by GhX6GZMB on 2021-01-14
Wow!
I'm completely stumped. Your BIOS/EFI is hiding your hard disk from the world, somehow?

You'll need to go back to that point. A complete new one for me. I understand your frustration.

An idea could be to reenable secure boot (not fast boot) just to see what happens (far out, I know...).

---

### Post by yancek on 2021-01-14
If clicking the down arrow to the right of where you see sda doesn't show your other drive(s) and you have windows 8/10 installed most likely situation is you left windows hibernated so boot it and turn off hibernation.

---

### Post by GhX6GZMB on 2021-01-14
I put on my thinking hat.
Could it be that your harddisk has password protection? I don't mean OS or BIOS, but HW password? This is the new fad for keeping users from playing around.
Please check the documentation.

---

### Post by oldfred on 2021-01-14
Did you look at the posts I linked to in your first thread?

Have you changed drives to AHCI?
Have you turned off Windows fast start up?
Did you update UEFI and  SSD firmware if SSD?
More info in link below in my signature.

---

### Post by icewizard8029 on 2021-01-14
> An idea could be to reenable secure boot (not fast boot) just to see what happens (far out, I know...). I tried and nothing changed. 

> left windows hibernated so boot it and turn off hibernation. I disabled hibernation but still have the same issue. 

> Could it be that your harddisk has password protection? I had to set a password on it when I turned off safe mode in the BIOS. I removed the password but I'm still getting the same problem. 

> [INDENT]                     Did you look at the posts I linked to in your first thread?

Have you changed drives to AHCI?
Have you turned off Windows fast start up?
Did you update UEFI and  SSD firmware if SSD?
More info in link below in my signature.                 [/INDENT]
            
                         

I couldn't find anything in the posts you linked from the first thread that looked related enough. 
I changed SATA to AHCL but the issue hasn't changed. Fast start up is turned off but nothing has changed. I haven't updated the UEFI and I don't have an SSD, I have an HDD. Should I update the HDD? I'll look through the link in your signature and see if anything helps. In similar posts to this its reccomended to change UEFI to legacy mode, but my computer isn't showing that option in BIOS.

---

### Post by yancek on 2021-01-15
On newer Acer machines with windows 10 preinstalled, you need to set a supervisor password in the BIOS firmware and enable trust to install anything other than windows.  Have you done that and do you have windows 10?

---

### Post by oldfred on 2021-01-15
Did you go thru the link with 35 steps. Lot more detail on an install specific for a Acer machine.
Issues are most common by brand, then by whether AMD or Intel based.
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

Do not turn on legacy/BIOS/CSM mode.
Old suggestions on BIOS mode perhaps working are more for old or early implementations of UEFI by vendors. But UEFI update to newest available from vendor and newer versions of Linux solve most of those issues. 

A few vendors have unique settings like Acer's "trust" setting required for ubuntu entry in UEFI once installed.


Another Acer install tutorial:
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire A515-54G Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI
[https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected](https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected)

---

### Post by icewizard8029 on 2021-01-15
>                               [INDENT]                     On newer Acer machines with windows 10 preinstalled, you need to  set a supervisor password in the BIOS firmware and enable trust to  install anything other than windows.  Have you done that and do you have  windows 10?                 [/INDENT]
            
                         
 Yes, I've tried that and got nothing.


After  trying to install lubuntu for several hours and finding out that the Acer brand  seems to generally have problems with installing ubuntu/linux I don't  think its worth pursuing any farther. It's too much trouble so I'm  returning this laptop and buying one that wont give me so much trouble  just for changing the operating system. I don't recommend any  ubuntu/linux users ever buy from Acer. 

Thanks to everyone that tried helping, I really appreciate it.

---

### Post by oldfred on 2021-01-15
It may just be the model you have?

ACER sf514 laptop UEFI Class 3
[https://unix.stackexchange.com/questions/615603/in-uefi-class-3-how-install-centos-8](https://unix.stackexchange.com/questions/615603/in-uefi-class-3-how-install-centos-8)
Acer Swift 5 (2019) ctrl-s  in UEFI required to be able to change to AHCI mode.
[https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown](https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown)
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire A515-54G Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI
[https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected](https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected)
acer predator helios 300 PH 315-51 i5 8th gen nouveau.modeset=0
[https://askubuntu.com/questions/1118751/has-anyone-successfully-dual-booted-ubuntu-18-04-lts-on-their-acer-predator-heli](https://askubuntu.com/questions/1118751/has-anyone-successfully-dual-booted-ubuntu-18-04-lts-on-their-acer-predator-heli)
Acer Predator Helios 300 Boot into system, update, reboot then install drivers.
[https://askubuntu.com/questions/1194761/how-to-install-nvidia-geforce-gtx-1050-ti-drivers-for-ubuntu-18-04-03-lts-on-ace](https://askubuntu.com/questions/1194761/how-to-install-nvidia-geforce-gtx-1050-ti-drivers-for-ubuntu-18-04-03-lts-on-ace)
Acer Aspire 7 A715-71G NVE not seen Boot parameter: nvme_core.default_ps_max_latency_us=200 
[https://ubuntuforums.org/showthread.php?t=2429323](https://ubuntuforums.org/showthread.php?t=2429323)
Ace

---

### Post by GhX6GZMB on 2021-01-15
> **icewizard8029 said:**
> It's too much trouble so I'm  returning this laptop and buying one that wont give me so much trouble  just for changing the operating system. I don't recommend any  ubuntu/linux users ever buy from Acer. 


If you have that option, great! Good luck.

---

