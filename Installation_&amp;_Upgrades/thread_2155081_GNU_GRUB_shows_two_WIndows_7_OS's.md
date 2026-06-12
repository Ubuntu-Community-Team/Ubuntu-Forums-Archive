---
title: "GNU GRUB shows two WIndows 7 OS's"
date: 2013-06-17
forum: Installation &amp; Upgrades
---

### Post by chockopocko on 2013-06-17
A while back, I was wanting to uninstall Ubuntu 12.10 and install Xubuntu 13.04 on my dual-boot system, which also has Windows 7. However, for some reason I was unable to burn a Windows 7 Recovery Disc that would allow me to restore the MBR upon deleting GRUB, and I searched online for a guide that would tell me how to restore it. I used EasyBCD, ([http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)), which purports to restore the MBR, after deleting the Ubuntu partition on my hard drive. 

However, when I rebooted my system, Windows would not start up, with a notification saying there was a fatal error in booting up and that I had to use a recovery disc. I was able to get a copy eventually, and after restoring the MBR, I booted into Windows to notice two things were changed: under msconfig > Boot Options, "Windows 7 (recovered)" was shown, and a "System Reserved" partition showed up under My Computer. 

After installing Xubuntu 13.04, I also noticed that there were now two Windows 7 options shown on GRUB:

Windows 7 (loader) (/dev/sda1)
Windows 7 (loader) (/dev/sda2)

I believe /sda1 is the System Reserved partition, as when I boot into it there is a screen that allows me to go to either "Windows 7" or "Microsoft Windows 7." Both of them allow me to boot into Windows. The second option (/dev/sda2) boots straight into Windows.

I'd like to know how I can remove /dev/sda1 from my GRUB screen, as I tried to install BURG, but the two Windows options was irritating. I have tried using GParted to make /dev/sda1 a hidden partition, and while for some reason the System Reserved partition doesn't show up under My Computer in Windows 7 anymore, it still shows up in GRUB. I haven't been able to tackle this problem until now due to school.

Any help would be very much appreciated! Thanks. :)

---

### Post by darkod on 2013-06-17
The System Reserved partition holds win7 boot files. If for some reason, during your MBR repair the repaired files were put on sda2 (the win7 OS partition), now you have a situation with sda1 with "older" boot files, and sda2 with the newer ones.

Grub detects boot files, not actual OSs, and it lets you know what it found. So, as long as you have boot files on sda1, it will show as "another" win7 option.

If you are sure you can boot your win7 directly with the sda2 option in grub, it should be safe to delete all files on sda1, and run update-grub afterwards. That should leave only one win7 option in the menu, the sda2.

---

### Post by oldfred on 2013-06-17
I believe the sda1 partition also has Microsoft recovery console or f8 to get to repairs. If you boot directly to sda2 that may not work. Many do install Windows to just one partition without the separate boot partition. The main reason for the separate boot partition was so you could encrypt the main partition as the boot files could not be encrypted.

Best to have recovery on separate CD or flash drive.
       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by chockopocko on 2013-06-22
Thanks darkod and oldfred! I've booted many times to /dev/sda2, and it works completely fine. I formated /dev/sda1, applied sudo update-grub, and it worked.

Cheers!

---

### Post by Mark Phelps on 2013-06-23
Have you successfully booted into Win7 since you reformatted sda1? 

The typical reason for two Win7 entries in GRUB is that in pre-loaded Win7 systems, there are Win7 boot loader files in one partition, and Win7 system files in a second partition.  OS-Prober sees both partitions as containing Win7 -- which they do, it's just that each one contains different pieces of Win7.  If you remove the first partition, you can't boot into Win7 anymore because the boot loader is gone; if you remove the second, you can't use Win7 anymore because the system files are gone.

---

