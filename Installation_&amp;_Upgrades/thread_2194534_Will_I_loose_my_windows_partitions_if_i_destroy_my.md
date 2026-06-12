---
title: "Will I loose my windows partitions if i destroy my boatloader?"
date: 2013-12-19
forum: Installation &amp; Upgrades
---

### Post by Dospanes on 2013-12-19
Hello Community!

Just a quick question:

I have a friend who uses 3 Windows on three diffrent partitions. on Another Partition he wanted to install Ubuntu but he rather would stick to the Windows Bootloader beacause he is afraid of maybe loosing his windows partitions if he screws up something and the ubuntu bootloader gets destroid. I'm not tooo expirienced with this so I wanted to ask somebody with more expirience. 

So my idea was that acutally he is not in danger of loosing anything because with the Ubuntu Live-CD you can always reinstall the bootloader and recover the relevant partitions for booting from the old configuration file. Is that right? Also I thought that you can always just put in the Windows Installation CD and he will again find the "lost" partitions, right?

So actually no danger for data loss, right? I just wanted to check with you guys. thx in advance.

---

### Post by Mark Phelps on 2013-12-19
Sorry, but there is ALWAYS danger for data loss -- which is why we encourage backups before partitioning.

When you install Ubuntu, it will also try to install GRUB -- so it can boot. IF you're not careful, presuming the hard drive is MBR formatted, Linux will overwrite that and put an entry to GRUB in it.  To restore access to Windows, you will then have to boot into Ubuntu, open a terminal, and enter "sudo update-grub".  That will regenerate the GRUB  config file and should then add an entry for Windows.   But ... and this is important ... it will add ONE entry for Windows, not three.  When you then select that, you will get a Window OS menu from which you will then have to select which Windows to use.

The Windows boot loader can NOT boot Linux OSs. NeoSmart Technologies makes a product know as EasyBCD which will allow you to add an entry to the Windows boot loader for Linux.  It then installs GRUB4DOS -- a GRUB version that installs on Windows filesystems and will run inside Windows.  That will then allow you to boot into Ubuntu from the Windows OS menu.  But ... you have to add that yourself.

---

### Post by Dospanes on 2013-12-21
Thanks for your reply. I thought of installing GRUB yes. My question is though is more general. I justed wanted to know if there is a way to find the old Windows partitions if Grub someday fails...

---

### Post by Hakunka-Matata on 2013-12-21
Yes, you can view windows partitions from within a running Ubuntu installation.  They are available to view via Ubuntus File Browser, Nautilus.  The windows partitions will be listed and you can open them without knowing the password if there is one.  That is a general statement, if a windows data partition is encrypted, that may not be possible, I don't know.

---

### Post by oldfred on 2013-12-21
Boot-Repair can reinstall a Windows type boot loader to the MBR. That only boots the one install with the boot flag that has all the boot files for all the installs.

Best to copy boot files and do a repair so every install that is in a primary partition can be booted. But only partition with boot flag is bootable with Windows. Grub does not use boot flag.

       To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words Vista but applies to all versions of Window in MBR(msdos) installs (not UEFI).
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

