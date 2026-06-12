---
title: "Problem with boot-repair"
date: 2017-06-11
forum: Installation &amp; Upgrades
---

### Post by kkhoury on 2017-06-11
Hi,

I increased the size of my unbuntu partitions by:
1. reducing windows partition
2. move unallocated space (move partitions..)
3. increase size of ubuntu partitions

I tried to fix grub using boot-repair (recommended repair) but there were errors.

Boot info follows:
[https://paste2.org/BJvI7CfM](https://paste2.org/BJvI7CfM)

At present I cannot boot on ubuntu.

Any ideas on how to fix it?

Thanks in advance!

---

### Post by deadflowr on 2017-06-11
*Thread moved to **Installation & Upgrades**.*

---

### Post by oldfred on 2017-06-11
Errors all seem related to some required unformatted partitions that then it complains about.
What model Lenovo, they seem to have a lot of models.

Can you boot directly from UEFI boot menu?
Is Windows booting?
Did Ubuntu boot ok before?

Did you run chkdsk on Windows immediately after resizing it? And did you only use Windows tools to shrink NTFS partition & reboot for the chkdsk.
Then use gparted for Linux partition changes?

A lot of Lenovo systems do not like to boot the Ubuntu UEFI entry.
 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715) 

Boot-Repair should do the renamw with 'Use the standard EFI file' in advanced options. 
 Rename bootx64.efi for fallback or hard drive default entry.
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

But you may need to add an UEFI boot menu item for booting the bootx64.efi entry.
sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'  -d /dev/sdX -p Y
      sdX is drive, Y is efi partition  
If ESP is sda2 like yours:
sudo efibootmgr -c -g  -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/sda -p 2

---

### Post by kkhoury on 2017-06-12
Thanks for your reply [COLOR=#000000]oldfred!

It is an IdeaPad flex 14 (model name: 20308)

It came with windows 8 that got upgraded to windows 10.

At the moment I can boot only on windows (I think it has to do with not moving the windows partition - just resized it). Before the resize and move Ubuntu was working.

So as to resize the windows partition I used gparted form an Ubuntu live usb. I used the same in order to move the unallocated space and resize the ubuntu partitions.

Regarding the UEFI, i have disabled it in the past because I had to use an nvidia graphics driver on ubuntu. 

Up to now I am using grub for booting/

Thanks in advance

[/COLOR]

---

### Post by oldfred on 2017-06-12
With Windows 8 or 10,you have to make sure Windows fast start up or hibernation is off.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

While gparted often works with Windows better to use Windows to shrink NTFS partitions and reboot immediately so it can run chkdsk. The fast start/hibernation & chkdsk make it possible that repairs become difficult.
You probably have to directly boot Windows from UEFI boot menu and use f8 to get into repair console.

You should turn of UEFI Secure boot, but not use Legacy boot to install Ubuntu. You still want Ubuntu in UEFI boot mode.

And many brands/models violate UEFI standard that says NOT to use description as part of boot. And only valid description is "Windows Boot Manager". But the fallback or hard drive boot entries usually work for those systems.

Some other Ideapads, but not same model. But issues are still often common.

 Lenovo Y700 Ideapad Windows 10 & Ubuntu SSD & HDD
[http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html](http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html) 

Some of the older Ideapads were 32 bit UEFI with no BIOS/CSM boot mode or UEFI class 3 devices.

---

