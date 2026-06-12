---
title: "Dual Boot: Win 10 and Kubuntu"
date: 2015-08-03
forum: Installation &amp; Upgrades
---

### Post by nostal on 2015-08-03
Hey, I'm new here. I have messed around with linux before (on other computers or in a vm) but I decided that I wanted to do a dual boot setup. I have looked at plenty of tutorials and during installation most show the "Boot alongside Windows" or something. However, I just upgraded to windows 10 and I dont see that option when in the installer. Is there anything special I need to do? Should I wait till its more supported or should I make partitions? Thanks alot!

---

### Post by oldfred on 2015-08-03
Is your system UEFI or BIOS?
Have you turned off fast startup or always on hibernation in Windows.
Or did you shrink Windows with its disk managment and not reboot immediately so it could run chkdsk?

       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

Post this from live installer in live mode, terminal.
sudo parted -l

---

### Post by nostal on 2015-08-03
My system is in BIOS (I think so, no cofiguration option within shift restart in windows and I can boot into bios from my bios button on motherboard). 
I have to turn off quick boot to even boot from a disc, usb, or configure boot order. 
I have not attempted to shrink windows with disk management.

It gave no install along windows option, just went straight to partition editor

---

### Post by oldfred on 2015-08-03
Need details, post 
sudo parted -l

Usually best to shrink Windows using Windows disk management to make unallocated space on drive.
Have you used all 4 primary partitions? Above request will show if that is an issue.

---

### Post by nostal on 2015-08-03
[ATTACH=CONFIG]263615[/ATTACH]
This is what my disk management window looks like

---

### Post by oldfred on 2015-08-04
Is this a 3TB drive?
And Windows is in BIOS boot mode? Windows only boots in BIOS mode from MBR drives.
Windows only boots from gpt partitioned drives with UEFI.
And 3TB drives must be gpt partitioned. So some systems force MBR(msdos) onto a 3TB drive but make it a 2TB drive or use non-standard sector sizes.

Is you system BIOS only? 

       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by nostal on 2015-08-04
Sorry but I am very inexperienced in this matter. I'm pretty sure its 3tb but only uses 2tb for windows.
In my windows > panther > setupact.log it says my system uses BIOS.
In the properties of my hdd it says the partition style is mbr.

---

### Post by nostal on 2015-08-04
I tried installing Ubuntu instead. I was given the option to install along windows but I got this error:
[ATTACH=CONFIG]263617[/ATTACH]

---

### Post by nostal on 2015-08-04
Should I just shrink my C drive volume down by however much I want for ubuntu then install? Would this fix the problem?

---

### Post by oldfred on 2015-08-04
If MBR, then that may work. Try to see if you can use gparted to create two partitions, one ext4 that you will use for / (root) and one for swap about 2 or 4GB. If you want separate /home you can create that also. You can also create a shared NTFS data partition but cannot select that during install, but have to add it later.

If you partition in advance you have to use Something Else and choose (change button) the partition you created for / as /, format ext4. It will auto find swap.
Screen shots with lots of detail as Something Else is a bit more than just click and auto install.
       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

            Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)

    
But Linux is a big more particular that drive is partitioned correctly. Windows does all sorts of things incorrectly and still works, probably intentional.

---

