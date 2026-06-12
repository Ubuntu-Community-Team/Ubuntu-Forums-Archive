---
title: "Installing Ubuntu on USB flash drive?"
date: 2013-08-11
forum: Installation &amp; Upgrades
---

### Post by peter1897 on 2013-08-11
I am new to Linux and i want to learn how to install Ubuntu on USB drive. I mean i want Ubuntu to work on the usb drive as i have installed it on my hard disk, not to make installation usb for Ubuntu. I found this program but i am not sure if this is what i need - pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/

Can someone tell me how to install Ubuntu on USB or point me to some good tutorial? I have Windows 7 installed on my laptop.  

Thanks!

---

### Post by oldfred on 2013-08-11
There is the live flash drive which is the installer. You can add persistence to save some data but that is not a full install. The installers like pendrive or unetbootin are extracting the ISO and making a flash drive you can use to install to a hard drive or another flash drive.

       Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

You need two flash drives. One can be smaller as the installer version only need 2GB but ususaly overwrite entire flash drive. A full install needs 8GB flash drive as a minimum but you can go as large as you want. I did find a new USB3 flash drive to be faster even with my USB2 ports on my old system.

      
 Full install - C.S.Cameron post #2
[http://ubuntuforums.org/showthread.php?t=2116798](http://ubuntuforums.org/showthread.php?t=2116798)
Full install of 12.04 to 64GB USB device C.S.Cameron post #3
[http://ubuntuforums.org/showthread.php?t=2092077](http://ubuntuforums.org/showthread.php?t=2092077)


 HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)

Actual install to another flash drive is not really different than any install to a second hard drive. You really need to use Something Else or manual install to create partitions. But only manul install gives the option on where to install the grub2 boot loader and you want it on the flash drive. All other choices will just install to sda, or (usually) your internal drive. And then you can only boot internal drive with flash drive plugged in. You can fix that but better to install correctly first time.

      
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

### Post by peter1897 on 2013-08-11
Thanks for the information!
What can i do to extend the live of the usb drive, because i guess when i install Ubuntu on it will waste faster because of the heavier write/read process?

---

### Post by ubfan1 on 2013-08-11
Take a look at [http://www.systemateka.com/usbboot.html](http://www.systemateka.com/usbboot.html) for some optimizations on USB sticks.  Basically, align the partitions to match the erase-block size, and move as much into ram as possible.

---

### Post by oldfred on 2013-08-11
I used ext4, but turned journal off. On a smaller system journal is less important, and there are some advantages of ext4 over ext2 as I understand it. Shows sdb1, but use correct drive & partition.
 sudo tune2fs -O ^has_journal /dev/sdb1


I just used gparted which now starts at sector 2048.

I also added noatime to fstab, so then timestamp of every access of a file is not written back to flash drive.

---

