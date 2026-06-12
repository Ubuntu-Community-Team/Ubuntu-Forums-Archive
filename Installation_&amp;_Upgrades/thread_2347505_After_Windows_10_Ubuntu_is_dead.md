---
title: "After Windows 10 Ubuntu is dead"
date: 2016-12-26
forum: Installation &amp; Upgrades
---

### Post by MikeCyber on 2016-12-26
Hi
Ubuntu is gone after Windows 10 install. Even to use the network from the install cd, I must shutdown all devices for some minutes.-
I've tried grub update from the install cd. It showed success but no Ubuntu around.
What to do? Many thanks

---

### Post by ajgreeny on 2016-12-26
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by MikeCyber on 2016-12-27
[http://paste2.org/d8Pfyj9n](http://paste2.org/d8Pfyj9n)

Meanwhile I managed to boot with Fedora on my second hd. I have not yet tried to install grub to that disk or my third to not endanger my current boot.
Thanks for your help.

---

### Post by oldfred on 2016-12-27
You still show Windows boot loader in sda.
But you might want to keep that.
Windows 10 has fast boot setting that enables hibernation. And the Linux NTFS driver will not see the NTFS partitions or then grub cannot boot Windows. And Windows updates will probably turn that back on regularly.

You can have grub on any drive and different grubs on different drives to boot different systems. And then when a Windows update prevents grub booting Windows, you can in BIOS directly boot Windows if you still have its boot loader in sda's MBR.
Do not run Boot-Repair's autofix. That installs one grub to all drives. You may want to use advanced mode where you an choose an operating system and then a drive to install boot loader into.

Ubuntu will not see Fedora unless you install Fedora directly to an ext4 partition, or add lvm2 driver and mount the LVM before running sudo update-grub from Ubuntu's install.

---

### Post by MikeCyber on 2016-12-28
So Windows doesn't like grub on the same HD? That's bad for newbies that have only one HD.-
I need Fedora for testing, so I can live with that as soon as I manage to set Ubuntu as default boot.

---

### Post by oldfred on 2016-12-28
With the 35 year old BIOS/MBR configuration, BIOS only boots fro the MBR or first sector on a hard drive. So only one boot loader per drive. Windows is not really designed to multi-boot other than other Windows in BCD.
I typically also have another copy of grub on various flash drives configured to boot my system also.

Grub is designed to boot as many systems as you want. But grub only boots working Windows that is not hibernated and Windows 8 or 10 is now always hibernated with the fast start up on.

New UEFI systems allows many boot loaders in the ESP - efi system partition, so grub & Windows share ESP. But grub still only boots working (not hibernated) Windows.

---

### Post by MikeCyber on 2016-12-29
Before my main HD crash I always booted Windows with ubuntu grub, but I don't remember where I had it installed. Windows update never caused problems to that and windows always booted fine.

What I wanted to point out is that the experience for a new user must be terrible. Grub not working, network only working after removing the power for several minutes.
I don't remember that installation was that bad years ago.

---

### Post by oldfred on 2016-12-29
> I don't remember that installation was that bad years ago. 				

My XP install years ago, and now my Windows 10 always causes issues. But my Windows 10 is primarily Windows 10 only since Comcast will not work with the flash in Linux.

It really is Windows 10 issue & its fast start up. And every major Windows update will probably turn it back on. Always check setting.
Grub only boots working Windows and hibernated is not bootable from grub to protect your data from damage.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by MikeCyber on 2016-12-30
With a fresh Windows 10 install only some days ago, I CANNOT even get grub to appear on the same hd.

---

### Post by yancek on 2016-12-30
> I've tried grub update from the install cd. It showed success but no Ubuntu around.

That will only update Grub on the DVD/usb which will be lost on reboot unless you used a chroot method.

> 
Meanwhile I managed to boot with Fedora on my second hd. I have not yet  tried to install grub to that disk or my third to not endanger my  current boot.

Look at the top of the boot repair output.  It shows Grub code in the MBR of that disk.  It also shows core.img where it should be and "looks          for (,msdos1)/boot/grub2".
That is the Fedora Grub as you can see by the "grub2".  Fedora names the grub directory "grub2", Ubuntu names it "grub".   The Fedora grub.cfg file shows what appear to be correct entries for Fedora, windows 10 and Ubuntu so setting the second 465GB drive with Fedora on it to first boot priority should give you the option to boot any of them.  If they don't boot, post back specifics on what happens when you try.

> With a fresh Windows 10 install only some days ago, I CANNOT even get grub to appear on the same hd.         

As pointed out above, that is because you have windows in the MBR of that drive and although it is possible to add a Linux boot entry to bcdedit in windows, it's not a simple operation.    If you are able to boot to Ubuntu and want it's Grub to boot the system, you need to install the Ubuntu Grub code to the MBR of sda.

---

### Post by MikeCyber on 2017-01-06
> **yancek said:**
> 
As pointed out above, that is because you have windows in the MBR of that drive and although it is possible to add a Linux boot entry to bcdedit in windows, it's not a simple operation.    If you are able to boot to Ubuntu and want it's Grub to boot the system, you need to install the Ubuntu Grub code to the MBR of sda.

After installing Ubuntu I should be simply able to select that drive in bios to boot even with windows on first two partitions? Well it was like this but nowadays alway win10 is booting. bcedit did not work either although it says success.

---

### Post by oldfred on 2017-01-06
Grub only boots working Windows. That is Windows that is not hibernated, nor needing chkdsk, the two biggest issues.

And Windows 8 or 10 uses fast start up which is really just hibernation.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

And with two MBR drives always better to have Windows boot loader in Windows drive and grub boot loader in second drive.

---

