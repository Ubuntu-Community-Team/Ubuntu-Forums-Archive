---
title: "Installing Ubuntu on a seperate HDD, how do I do this?"
date: 2015-05-08
forum: Installation &amp; Upgrades
---

### Post by petter2 on 2015-05-08
**[SIZE=4]Hello![/SIZE]**

First of all I want to say, I'm not new to Linux or Ubuntu in general, but I've never tried what I currently want to do.

When I've installed Ubuntu in the past, I'd always install it over Windows (Thus deleting Windows). This time, I'd like to install Ubuntu on a seperate HDD from Windows 8.1, so that I can dual boot.

The problem is, I've never done this before. I've searched the internet, and while there are plenty of guides I have to admit that I'm kind of scared to follow them, because they aren't guides for my specific situation.

[SIZE=4][B]My situation
[/B][SIZE=2]
So this is my situation:

SSD 60GB
- Windows 8.1 

HDD 1TB
- Partition 1 900GB - Storage. Google Drive, music, games etc.
- Partition 2 100GB - This is the partition I want to install Ubuntu to.
[/SIZE][/SIZE]
[B][SIZE=4]What I need help with[/SIZE]
[SIZE=2]
[/SIZE][/B][SIZE=2]So, I've read some tutorials, and they all talk about GRUB, and having to repair my Ubuntu installation and such things. I have no idea what any of this means, or why I have to do this. I'm honestly just scared of screwing up my Windows installation, and I really don't want my 900GB partition (With a lot of important files) to be wiped.

So, how do I install Ubuntu on partition 2, and set it up so that I can choose between either booting Windows 8.1 or Ubuntu at startup (Without messing up either Windows and partition 1) ?[/SIZE][SIZE=4][SIZE=2]

[B][SIZE=4]Relevant information

[/SIZE][/B]Ubuntu version: [/SIZE][/SIZE]Ubuntu 14.04.2 LTS
[SIZE=4][SIZE=2]Method of installation: Bootable USB memory stick ([/SIZE][/SIZE]I am able to run Ubuntu as a live cd from my memory stick.)[SIZE=4][SIZE=2]
Current OS: Windows 8.1


[/SIZE][SIZE=2]If I can give you guys any information to make it easier to help me, please ask! I'd appreciate any help that I can get [/SIZE][/SIZE]O:)[SIZE=4][SIZE=2]

I am not too good at the Linux terminal, but I have a lot of experience with Windows Powershell and CMD. I know that this doesn't translate to Linux, but I'm comfortable with using a CLI.[/SIZE]

**WIFI USB ADAPTER EDIT:**

[SIZE=2]If you came here from Google searching for how to fix your wifi usb adapter, scroll further down for the solution.[/SIZE]
[/SIZE]

---

### Post by oldfred on 2015-05-08
Older BIOS or new UEFI?

If BIOS you must install grub2's boot loader to the hard drive and set BIOS to boot from sdb. Grub will let you choose Windows or Ubuntu if you have Windows fast-startup off.

If UEFI, grub installs boot files into efi partition that Windows is already using. There are separate folders so no conflict, but some systems have modified UEFI to make it difficult for Linux. But we have ways.

Either way best to use Something Else. That is the only install option that gives you a choice on where to install grub2's boot loader. You want sdb if BIOS. If UEFI it just defaults.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)


 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
      
 Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

    
Any of the install examples about shrinking Windows then do not apply, but you still need Windows 8's fast startup off.

---

### Post by petter2 on 2015-05-08
Hi.

It's BIOS, not UEFI.

I assume that the "Installing Ubuntu to a Specific Partition ("Something Else"):" part from [this link]("https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29") is what I should go for then?

I'm a little bit confused, but I'll try to explain my thought process.

> 
[COLOR=#333333][FONT=Ubuntu]On a system with multiple drives and OS's, the user can preserve the original bootloader by installing GRUB 2 on another drive. To accomplish this:[/FONT][/COLOR]

[LIST]
[*=left]specify the disk (eg /dev/sdX, not /dev/sdaXY) not currently used to boot the system for the bootloader location.
[*=left]After the installation is complete, change the boot order (via BIOS setup) so that the disk to which the GRUB information was written is the one booted first.
[*=left]If the user wishes to restore booting with the original bootloader, change the boot order back to the original drive.
[/LIST]


So let's say that Windows is installed on sda1 (Sorry if I get this wrong, I don't understand the Linux way of naming disks and partitions).

My HDD is then named sdb, and sdb will be split in two. Partition 1, where my files are and partition 2, where I want to install Ubuntu. These will be named sdb1 and sdb2?

So all I have to do to accomplish my goal is to install Ubuntu to sdb2, then change the boot order in the BIOS?

---

### Post by oldfred on 2015-05-08
Yes. But check which drive is sda and sdb, that often depends more on which SATA port in motherboard is used. If concerned from live installer, use dash or icon in upper left for terminal or 
 Get a terminal by <ctrl_+alt+F1> & back to gui with ctrl alt f7
And post this to show drives & partitions:
sudo parted -l

Best to test live installer in live mode just to confirm that everything works ok.

But normal Linux installs also include another partition swap.
But if you have lots of RAM, you may not need swap or much swap. I normally suggest at least 2GB if you have 4GB of RAM or more. Very old rule was 2X RAM and if you want to hibernate which is  not recommened if dual booting, the swap needs to be equal to RAM in GiB not GB or about 10% more in GB.
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by petter2 on 2015-05-09
Reporting back.

It was a lot easier than I thought it would be.

I just found the partition that I had created for Ubuntu. It was called sdbX (I don't remember the number).

I used [this guide]("http://www.tecmint.com/ubuntu-14-04-installation-guide/") for installation. Whenever I turn on my computer, it boots into grub and I get to choose between Ubuntu and Windows 8.1.

The only problem I've encountered is that my USB wireless adapter's connection is really bad. The speed is horrible, and it constantly disconnects me from the internet. This is when using Ubuntu.

I have no idea why this happens, but I've googled this as well. It seems that the default driver for my adapter is kind of bad. I'll be editing this comment if I find a solution. The adapter is called "Realtek RTL8188EU WirelesS LAN 802.11n USB 2.0 Network" in the Windows device manager.

Thanks for helping! O:)

EDIT:

I found the solution for fixing the wifi issue [here]("https://www.kubuntuforums.net/showthread.php?64211-TP-link-WN725N-nano-usb-driver-installation-problem&p=345276&viewfull=1#post345276").

In case that link gets deleted, here's a cut out:

> SOLVED:

This is the process:


From this page:


[http://www.ubuntuask.com/q/answers-tp-link-wn725n-unable-to-get-drivers-to-work-with-13-04-after-upgrade-worked-o-377470.html](http://www.ubuntuask.com/q/answers-tp-link-wn725n-unable-to-get-drivers-to-work-with-13-04-after-upgrade-worked-o-377470.html)


The instructions set which worked for Kubuntu 13.04 is as follows:


Download this zip and "extract here" using Ark (or utility of your choice) into your home directory:


[https://github.com/lwfinger/rtl8188eu/archive/master.zip](https://github.com/lwfinger/rtl8188eu/archive/master.zip)

This will create a set of directories in /home/your-name/rtl8188eu-master
From your home directory, execute:


Code:
cd rtl8188eu-master
sudo make
sudo make install
sudo modprobe 8188eu
The driver should now be active and visible to NetworkManager

Remember to reboot after doing this.

If the files above are removed, PM me on the forums. I have them stored.

---

