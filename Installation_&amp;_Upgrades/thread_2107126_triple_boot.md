---
title: "triple boot"
date: 2013-01-21
forum: Installation &amp; Upgrades
---

### Post by nervynewman on 2013-01-21
I have Windows 7 and now Ubuntu 12.10 on separate drives(ssd and hdd). If I want to add Windows 8 to another ssd on the last SATA 3 port, will the Windows 8 bootmgr overwrite GRUB2? If so, what's my best option to take for a multi-boot?

---

### Post by presence1960 on 2013-01-21
> **nervynewman said:**
> I have Windows 7 and now Ubuntu 12.10 on separate drives(ssd and hdd). If I want to add Windows 8 to another ssd on the last SATA 3 port, will the Windows 8 bootmgr overwrite GRUB2? If so, what's my best option to take for a multi-boot?

If you areinstalling a new SSD for windows 8 installation then make that SSD first disk to boot in BIOS. Then install the Windows 8 OS. After installation make sure Windows 8 boots properly. Then you can change the disk with GRUB 2 on it back to the first disk to boot in BIOS. Boot into ubuntu and run in terminal ```
sudo update-grub
``` This should add windows 8 to your GRUB list.

If you fail to change the new SSD to first disk to boot in BIOS then the Windows installer will write it's bootloader to whatever the first disk is in the boot order in BIOS, effectively overwriting what is on the MBR of that disk.

Or if you aren't confident enough you can always open your case and disconnect the other two disks from the mobo. Install windows 8 and then reattach the other two disks to mobo. Boot into ubuntu and run in terminal ```
sudo update-grub
``` GRUB should detect your windows 8 installation and add it to the list of OSs to boot.

---

### Post by Mark Phelps on 2013-01-21
If the Win8 installer "sees" Win7, it will most likely overwrite the Win7 boot loader files with Win8 files.  While this will not remove the ability to boot into Win7, what it will do, when you update grub, is produce a Windows login screen, from which you will then have to select either Win7 or Win8.

If you want to be able to use GRUB to select either Win7 or Win8 directly, then do NOT have the Win7 "drive" connected when you install Win8.  The os_prober will find BOTH OSs when it runs and will then write two entries into the GRUB config file -- one for each OS.

---

### Post by presence1960 on 2013-01-21
I may be wrong, but I believe if Windows 7 is on a different disk than Windows 8 the windows 8 installer will not combine the boot into one function.

Either way if the OP removes the windows 7 disk when installing windows 8 he won't have to tell us who is correct!?!?...LOL ;):)

---

### Post by Lightning Dragon on 2013-01-21
It shouldn't overwrite anything if it is on a separate HDD. You should be brought to a boot screen with a list of selections to pick from. I currently boot from Windows 7, Ubuntu 12.04, Linux Mint and Kubuntu without any problems. Although I did install each and everyone of them while the others were disconnected just to be safe.

---

### Post by oldfred on 2013-01-21
Windows seems to be a little smarter than grub. Grub always installs to sda, Windows seems to put boot files  & MBR in drive that is set as boot drive in BIOS usually sda.

We have seen several users with Windows 7 installed to sdb, they then install Ubuntu to sda and cannot boot as they overwrote the hidden in Windows 100MBR boot partition on sda. The assumption is that sda was the boot drive in BIOS or the boot partition would have been on sdb.

So I think the answer is not just where boot flag is but also which drive is set as boot drive in BIOS.

Again disconnecting drive will guarantee none of us know the correct answer for sure. Unless you would like to install several times. :)

---

### Post by presence1960 on 2013-01-21
> **oldfred said:**
> Windows seems to be a little smarter than grub. Grub always installs to sda, Windows seems to put boot files  & MBR in drive that is set as boot drive in BIOS usually sda.

We have seen several users with Windows 7 installed to sdb, they then install Ubuntu to sda and cannot boot as they overwrote the hidden in Windows 100MBR boot partition on sda. The assumption is that sda was the boot drive in BIOS or the boot partition would have been on sdb.

So I think the answer is not just where boot flag is but also which drive is set as boot drive in BIOS.

Again disconnecting drive will guarantee none of us know the correct answer for sure. Unless you would like to install several times. :)

Nice oldfred. I have had multiple windows installations set up on different hard disks. I have never had the bootloaders combined because as you noted I always set the disk that I am installing windows to as first boot disk in BIOS. Once the install is finished I put the disk with GRUB in MBR as first boot disk, boot into Ubuntu and run sudo update-grub. I then was able to boot each windows install from GRUB directly. Actually I learned this trick from you I believe because you always used to say you keep Windows on one disk and linux on another.

---

### Post by oldfred on 2013-01-22
@presence1960
> Actually I learned this trick from you I believe because you always used  to say you keep Windows on one disk and linux on another.

Huh?! I have said that but later on?
I thought I learned all my booting info from you and .meierfra when I first started posting in the forum. :)

---

### Post by presence1960 on 2013-01-22
> **oldfred said:**
> @presence1960


Huh?! I have said that but later on?
I thought I learned all my booting info from you and .meierfra when I first started posting in the forum. :)

Possible. Going back a few years. All I know is you and meierfra are very good company to be in.

I regret somewhat that I don't currently have the time to be as active in here as I once was. My daughter is now 10 years old. I am a single dad. I work full time and my computer business that I operate from my home has also picked up. So I am very busy. My daughter is very good on computers. She has a desktop I built running a tr-boot of Windows 8, Windows 7 and Ubuntu 12.04. In school for the last 4 years she uses Mac. She has basic knowledge of hardware, better than a lot of adults. 

I hope you are well oldfred. You just brought me back to "the good ole days" in here. :)

---

