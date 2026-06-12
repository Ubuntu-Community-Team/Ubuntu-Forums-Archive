---
title: "Boot Repair won't work: 'File system repair requires to unmount partitions' loops"
date: 2014-01-26
forum: Installation &amp; Upgrades
---

### Post by cpt.mayhem on 2014-01-26
I am in the process of installing ubuntu on a Windows 8 machine. I have followed the instructions here: [http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)

I have got to the stage where I am applying Boot Repair's recommended fix.

The problem I keep encountering is that Boot Repair keeps giving the message "Filesystem repair requires to unmount partitions. Please close all your programs. Then close this window." the only program that I have opened is boot repair. This message reappears after dismissing.

I have got to the ubuntu install by rebooting from Windows 8, opting to load from the device "ubuntu". This is the only way I can get into my ubuntu installation.

Here is my boot repair BootInfo summary: [http://paste.ubuntu.com/6820834/](http://paste.ubuntu.com/6820834/)

---

### Post by grahammechanical on 2014-01-26
Are you running boot repair from inside Ubuntu? Ubuntu is on a mounted partition and Boot Repair cannot unmount the parttition to do its stuff because that would break the loaded Ubuntu Session. This is my guess.

I suggest that to use Boot Repair to repair what is wrong we need to run Boot Repair from a Ubuntu live session. We may need to install it first.

Regards.

---

### Post by oldfred on 2014-01-26
It looks like you originally installed Ubuntu in BIOS boot mode as you have grub in protective MBR.
But you now have grub in efi partition for UEFI boot.

Since a Dell do not run the backup & rename Windows files option. Dell's boot from UEFI without the rename. The rename is only for systems that have modified UEFI to only boot Windows.

But you modified Windows system reserved partition from unformatted to ext4? It must be unformatted and you may later have issues with Windows as it needs that space for serial numbers and hidden data. Part of the errors on type issues Boot-Repair is reporting.

       Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

Use gparted and change sda2 back to unformatted. Make sure flag still has msftres set.

It looks like you should be able to boot ubuntu from UEFI, and Windows from UEFI or from grub menu. 
There is a bug in grub that if you turn secure boot on, you cannot boot Windows from grub menu.

Is this a Dell like the first link you have?
Many similar issues.
      
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[URL="https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z"]https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z

[/URL]
 Dell Inspiron 3521
[URL="http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html"]http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html
      [/URL]
 Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)

    [URL="http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html"]

[/URL]

[URL="https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z"]
[/URL]

---

