---
title: "3 Way Boot?"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by archithcr on 2011-04-28
Hello everyone

I have a 1TB Hard drive where I've installed Windows 7 ultimate 64 bit. Since i game a lot, there are a couple of games that don't run on windows 7, i have been thinking of adding another hard drive to my system and install my old copy of XP onto it.

If i buy another 1TB drive and split it into two partitions of 500GB each and dedicate them to XP first and ubuntu next, will GRUB detect my windows 7 installation on the first hard drive and create a 3 way boot?

And installing XP and ubuntu on the 2nd drive shouldn't mess up my 1st windows 7 drive, right?

Would love it if the experts here can help me :)

---

### Post by Edward46 on 2011-04-28
Before linux, I would check to be sure you can install XP and boot from that since this is being installed after Windows 7.  I have read that XP should be installed first when dual booting with Windows 7.  I am not sure if this is still the case with a dedicated second drive.

When you are ready to install linux, you will have the option to install the grub to the drive of your choice.  In this case, the second drive with both XP, linux and boot loader will be booted from first so that the grub will be able to recognize the primary Windows 7 drive.

Like I mentioned above, work on XP and Windows 7 first.

Edward K.

---

### Post by oldfred on 2011-04-28
windows wants to combine boots into one partition as that is the only way it can boot. It literally moves the boot files and modifies boot.ini or the win7 BCD to only have one bootable partition.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by archithcr on 2011-04-29
Hi

Thanks for the replies. That's precisely the problem. I never thought that I would ever need to go back to XP, since 7 is awesome and all.

But some games like Doom 3 and Quake 4 have problems running under 7 64 bit, which is why I wanted to setup a triple boot.

I don't want to remove windows 7, install XP and then reinstall windows 7 :( Which is why i wanted to know if a dedicated second hard drive would be of any use.

---

### Post by Edward46 on 2011-04-29
To install XP on a second drive after Windows 7 to dual boot is not impossible, but since Windows 7 is first, you would have to run a Windows 7 repair operation from your install disk.  From what I have read, the installation of XP could actually overwrite the mbr on the first drive, but even if this is not the case, the old which is XP will not recognize Windows 7 so the repair operation will update the boot loader for Windows 7 to make dual booting possible.  

Adding Linux to create a triple boot process will work.  Do a search for "triple boot"

Edward K.

---

### Post by ssican on 2011-04-29
See this - Illustrated Dual Boot TUTORIAL-: 
DUAL BOOT ON TWO HARD DISKS - Installing Ubuntu in Hard Disk Two:
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

See also the -BIOS PAGE-:
[http://members.iinet.net.au/~herman546/p1.html](http://members.iinet.net.au/~herman546/p1.html)

First install Windows XP , and after install Ubuntu 11.04


I recommend three Hard-Drives. The first Hard Disk Drive for Windows 7. The second Hard Disk Drive for Windows XP (for example 500GB). The Third Hard Disk Drive for UBUNTU 11.04 (for example 500 GB).

With three hard disk drives, there are (3)three possible INDEPENDENT (FIRST BOOT DEVICE) on BIOS.

With (2)two hard disk drives there are (2)two possible INDEPENDENT (FIRST BOOT DEVICE) on BIOS.

Always Ubuntu is the last for install.

On Ubuntu, install STARTUP-MANAGER for control of which operating system will be booted, will be started.
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)


EDIT 1:
See the -Illustrated Dual Boot Site-
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

EDIT 2:
Before installing -Windows XP- go to the BIOS (Turn on the computer and  press DELETE on the keyboard) and in -HARD DISK BOOT PRIORITY- make the chosen hard disk drive of the installation as -FIRST BOOT DEVICE-

EDIT 3:
Before installing -UBUNTU 11.04- go to the BIOS (Turn on the computer and press DELETE on the keyboard) and in -HARD DISK BOOT PRIORITY- make the chosen hard disk drive of the installation as -FIRST BOOT DEVICE-

EDIT 4:
How to enter the BIOS or CMOS SETUP:
[http://www.computerhope.com/issues/ch000192.htm](http://www.computerhope.com/issues/ch000192.htm)

---

