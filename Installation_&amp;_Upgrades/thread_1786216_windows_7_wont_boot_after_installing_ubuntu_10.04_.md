---
title: "windows 7 wont boot after installing ubuntu 10.04 on external hard drive"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by Barastrix187 on 2011-06-19
i just loaded ubuntu onto my 500gb external hard drive but now when i start up my laptop without the external plugged in it says "error : device not found : "error code" grub rescue:". when i boot with the external plugged in it brings me to my boot options and windows 7 is there and boots just fine and the external is no longer needed to run from there. i looked at the partition manager on ubuntu and it says there is one OS on each drive so i know i didnt accidentally dual install. PLEASE HELP :(

---

### Post by mac67 on 2011-06-19
Hi,

I know your problem, but I am not sure I know the solution for your trouble.

The problem is: whenever you install or update or upgrade Linux, grub gets updated too and gets control of all OS.

So, what you should have done is installing Ubuntu (or anything else) on  an external HD **after** removing the internal HD.

If you had only Windows on the internal HD, I do not know how to solve your problem.
If you had also Ubuntu on the internal HD, then connect the external HD, boot the internal Linux, open a terminal and write "sudo dpkg reconfigure grub-pc". Then say Ok to everything. But then you have lost the grub on the external HD.

Sorry for not being of much help.

---

### Post by flemur13013 on 2011-06-19
It sounds like you DID do a dual install and that the grub boot sector is on the removable disk, and it points to the grub portion on the Win7 disk that'll boot windows - it acted like you had two HDs installed on the computer. (IMHO the ubuntu installer is very hard to use - you can tell because there's SO MANY posts about it causing problems).

To get windows to boot normally without the external drive, run [I][I]bootrec.exe (sort of a pain - you need W7 install or repair CD/DVD):
[http://windows7themes.net/how-to-fix-mbr-in-windows-7.html](http://windows7themes.net/how-to-fix-mbr-in-windows-7.html)
[/I]
[I]Do you want to install ubuntu as if it's on a USB stick (or the original DVD), and select which system to boot  via the BIOS boot options?  



[/I][/I]

---

### Post by YesWeCan on 2011-06-19
> **Barastrix187 said:**
> i just loaded ubuntu onto my 500gb external hard drive but now when i start up my laptop without the external plugged in it says "error : device not found : "error code" grub rescue:". when i boot with the external plugged in it brings me to my boot options and windows 7 is there and boots just fine and the external is no longer needed to run from there. i looked at the partition manager on ubuntu and it says there is one OS on each drive so i know i didnt accidentally dual install. PLEASE HELP :(

This is IMO a problem with the Ubuntu Installer because it defaults to putting the Ubuntu boot-loader MBR (Grub) on your first hard drive (sda) rather than putting it on the drive you are installing Ubuntu on (your external USB).

The issue is that Grub requires files inside your Ubuntu partition in order to work at all. When you remove the USB those files are not available. What you want is when the USB is connected you boot a Grub on it and when it is not connected you boot a standard MBR on the Windows drive.

What you need to do is:
1) Install Grub MBR to your USB drive.
Boot into Ubuntu and in a terminal run
[COLOR="Navy"]sudo fdisk -l[/COLOR]
to list your drives. Find the drive name of the USB drive. It will be something like sdb. Your Windows drive will probably be sda. Then reinstall Grub using the USB drive name
[COLOR="Navy"]sudo grub-install /dev/sdb[/COLOR]

2) Reinstate the standard MBR on your Windows drive so Windows will boot when the USB is not connected
either
a) boot off a Windows CD and run the fixmbr utility
or
b) boot off a Ubuntu live CD and in a terminal run
[COLOR="Navy"]sudo apt-get install lilo[/COLOR]  (ignore all warnings)
[COLOR="Navy"]sudo lilo -M /dev/sda mbr[/COLOR]  (assuming sda is your Windows drive)


Having done this, you should be able to use your bios to either boot the USB to get the Grub menu or boot the Windows drive to go straight into Windows.
:)

---

### Post by gpse01 on 2012-03-04
Thank you YesWeCan!!

I ended up using part B. I think the main problem was that I had been running one HD one Sata and one IDE. Ubuntu was installed on IDE. When I unplugged SATA I had no bootup issues. When both had been plugged in I would get the Grub Rescue on bootup.

---

