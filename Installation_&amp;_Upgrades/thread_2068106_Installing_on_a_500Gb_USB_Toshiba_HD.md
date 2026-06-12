---
title: "Installing on a 500Gb USB Toshiba HD"
date: 2012-10-08
forum: Installation &amp; Upgrades
---

### Post by TGamel on 2012-10-08
It has been since version 9 that I have used Ubuntu; not because of it's shortcomings. Personially I believe Linux is a far superior OS than windows. However there are some software packages that I simply have to run in Windows such as Adobe Premiere Pro and After Effects.  
 

 Previously I have partioned my hardrive and ran a dual boot system from one drive. Eventually I needed the hardrive space as we all know Windows is a pig and finally had to go back to windows on my i7. I have kept Ubuntu on my older AMD triple core as a Linux only machine. Now that hardrives have become so inexpensive I have purchased a 500Gb Toshiba USB portable drive and would like to install Ubuntu from a live DVD to this drive so that I can use it on both my i7 desktop and my i5 laptop simply by carrying the hardrive from computer to computer.
 

 As long as both systems are set to boot off the USB first, I believe that I can run Linux without having to boot into windows or using a dual boot loader. I guess my question is has anyone done this (I am sure many people have) and is the install procedure any different from a Live DVD than a regular install?  
 

 My thinking is that If I installed Ubuntu to the Toshiba external drive using the whole drive for Ubuntu and both computers would boot from the USB port first that I could use Ubuntu on both of my machines without any problems. I have searched the forums on installation procedures regarding this but have not found any real answers.
 

 Thanks,
 

 Todd

---

### Post by oldfred on 2012-10-08
You set system to boot from USB first and internal second. Grub loads and gives a choice of Ubuntu or Windows from internal. If external is not plugged in, then BIOS defaults to the internal drive.

You mention i7, is Windows booting in UEFI or BIOS mode? That may complicate it some if UEFI. But either should work.

If only Ubuntu on external you can use gpt partitioning on external whether UEFI or BIOS, but Windows only boots from internal drives and only from gpt partitioned drives if booting in UEFI mode. Windows in BIOS boot can read data from gpt NTFS formated partitions. 

Either way you have to use manual install as that is the only one that lets you choose where to install boot loader if in BIOS mode. And if in UEFI you have to boot 64bit install in UEFI mode to get it to install in UEFI mode.

We can give better details if we know your internal drive partitioning. Post this from liveCD.

sudo parted /dev/sda unit s print

---

### Post by TGamel on 2012-10-17
I had to use two different sets of install instructions to get the external drive working, but seems to boot fine on the laptop as long as it remains plugged in. If you disconnect the drive and boot into windows, then the next time you must plug in the drive and hit the 'ESC' key to boot back off the external which stays active untill disconnected.

So far I have used this configuration on both my laptop i5 w/8Gb memory and my desktop i7 w/8Gb memory. I actually think it works better on the laptop. Sometimes on the desktop, the response time seems to lag. Will continue to work on it, but happy so far.

Todd

---

### Post by oldfred on 2012-10-17
Glad you got it working. 

If you want to document how system is configured you can run the BootInfo report from Boot-Repair. I actually run the Bootinfoscript which is part of BootInfo report as part of every rsync backup, just to have current configuration documented. 

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

