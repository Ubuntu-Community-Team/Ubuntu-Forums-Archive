---
title: "Installing over existing format"
date: 2012-08-28
forum: Installation &amp; Upgrades
---

### Post by coolecho on 2012-08-28
During install is there an option to format the drive? I have an XP SP3 NTFS formatted drive that I will essentially wipe or format clean and install Ubuntu. What type of filesystem does Ubuntu use? Thanks.

---

### Post by oldfred on 2012-08-28
Welcome to the forums.

Linux can use many formats, but not any Windows ones. The standard is ext4.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited and if total less than about 30GB just use / not separate /home.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

---

### Post by micahpage on 2012-08-28
yes. There will be an option to format the partiion/drive upon install of the OS. 
Normally people now do ext4 file system

---

### Post by coolecho on 2012-08-29
I'm installing on a desktop with 300GB drive. 
I started the installation just to see the disk options in the install and exited out.
I will probably partition for root, swap and home and have a partition for windows.
Thanks.

---

### Post by oldfred on 2012-08-29
If you want a partition for Windows it prefers the first. It has to be a primary NTFS partition (sda1 thru sda4) and have the boot flag.

---

### Post by coolecho on 2012-09-05
Hello,

I installed Win XP SP3 first into 150GB partition of a 300GB drive. I then installed Ubuntu 12.04.1 that I made into a bootable CD. Ubuntu knew windows was on the drive already a came up with a dialog with I think 3 options. 
1. was install alongside Win XP, 
2. was wipe out all partitions and install fresh Ubuntu, 
3. I think was install manually. 
I selected number 1 and was expecting to see a partitioning dialog come up at some point, but it never did.
It fully completed and came up to the desktop, and it was saying it needed to reboot.
I assume it did the partitioning by itself and perhaps I should have selected option 3.
But when it rebooted it has an error. It stops on reboot: "Searching for boot record from IDE-0", "error: no such partition". It stops at the prompt: "grub rescue>"

I have no idea why it can't find the boot record. I am also thinking that I'd like to remove the Ubuntu partition and start over trying to do the partitioning myself.
What might be the reason it didn't start up properly? Is there a way to start over without restarting from scratch by reinstalling windows?  

Thanks! :confused:

---

### Post by oldfred on 2012-09-05
That sounds more like a BIOS error not either grub nor Windows.

Post link to BootInfo report from liveCD:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by coolecho on 2012-09-08
I did have a problem with that computer. I decided to try another computer so I moved the hard drive to the other computer and was planning on booting the Ubuntu CD and delete the partition and start over. I can't boot the CD now at all. I select the CD in the BIOS for boot. It only comes up with a GNU GRUB Menu. I assume there is a utility perhaps fdisk to run from the command line? 


Update:
The CD drive was set as secondary (slave) with no master is why it wouldn't boot. 
I don't know Ubuntu fdisk so I just booted the Ubuntu drive as secondary drive in windows and used windows to delete all partitions. 
Now to start over...

---

### Post by coolecho on 2012-12-05
I decided to go with a External USB 500GB drive to have Windows 7 and Ubuntu dual boot, with Windows 7 installed first. I went through trouble installing Windows 7 and getting it to boot from the laptop boot options. I have Windows 7 on 1st partition 230GB active primary, 2nd partition 100GB primary, and 3rd 135GB primary. I was intending on installing Ubuntu onto the 2nd partition. I read the article "How to dual boot Windows XP and Linux (XP installed first) -- the step-by-step guide with screenshots". It seems to say that Ubuntu will install alongside Windows in the same partition. Is this true? Can it be installed into it's own partition and dual boot along with windows? Thanks.

---

### Post by oldfred on 2012-12-05
Windows will not boot from an external drive. It is licensed (and checks) to be used only on one computer.

So are you installing Windows on internal drive and Ubuntu on external?

Ubuntu has a version called wubi that can be used by new users to test and see if they like Ubunutu. It installs into the NTFS Windows partition and uses the Windows boot loader. It then is easily uninstalled as it is just a file. But not intended for long term and is not a true partitioned dual boot. Any issues in the NTFS partition may prevent or break wubi.

Some install examples
       Install options, Do not use erase entire drive unless that is really what you want.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by coolecho on 2012-12-05
Windows 7 is successfully installed and booting from my 500GB USB drive just as if it was an internal drive, and is partitioned as stated above. It's only used on this one laptop. I just hit F12 boot options to boot it. As I mentioned, I want to install Ubuntu on it as well and have dual boot. I would not be interested in Wubi; as I started out this post I am using this as learning Ubuntu and ended up learning alot just from installing windows onto USB. 
Thank You.

---

### Post by coolecho on 2012-12-05
It is booting successfully into Windows 7 from this external USB drive, I just hit F12 to get boot menu to boot it. This USB drive is only used with this laptop. I would not be interested in Wubi. As I started out this post I was doing this to learn Ubuntu, however I learned alot on installing Windows 7 onto external USB drive. I'll make an image backup of this drive asap, and will proceed with installing Ubuntu onto it to see how it goes. Thanks for the links.

---

### Post by oldfred on 2012-12-06
System was up & down as they were doing some maintenance today. 

Post this so we can  see what partitions you have. Run from terminal in liveCD/flash drive or an install.

sudo fdisk -lu

click in liveCD to mount Windows partition(s).

df -h

---

### Post by coolecho on 2012-12-06
I was able to boot the Ubuntu DVD and the custom partition section of  the install I was able to partition the WD elements USB drive.  
[ATTACH]228286[/ATTACH]
I tried  to follow the preceding suggestion here I have root 15GB and boot 1GB  setup.
[ATTACH]228287[/ATTACH]
But when I got to select a swap I didn't see the option. 
[ATTACH]228288[/ATTACH]
I only see: /,  /boot, /home, /tmp, /usr, /var, /srv, /opt, /usr/local ! So which one is  swap? I exited out discontinuing the install.
Thank You.

---

### Post by oldfred on 2012-12-06
Swap is unformatted, so by selecting a format did it exclude swap? Found example, swap is under the format choices. 

I have not created swap for eons & I always have partitioned in advance with gparted from either Ubuntu liveCD or gparted liveCD.

See screen shot on page 2
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

---

### Post by coolecho on 2012-12-06
I got it all done. From The article I found that swap is a pull down option. So I went thru the whole Ubuntu 12.10  install perfect. Rebooted to the F12 options selected USB and it came up with Ubuntu boot menu. Ubuntu is 1st choice and Windows is last, sda1 (since I installed Win 7 first.) Ubuntu boots ok and Windows boots ok! Wala!

---

