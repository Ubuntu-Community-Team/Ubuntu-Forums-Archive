---
title: "Linux taken over dual boot hard disk and wont let go :("
date: 2013-09-27
forum: Installation &amp; Upgrades
---

### Post by Crinkle on 2013-09-27
Hello there, Linux was looking lovely till this happened. I changed a few partitions on my dual boot disk, and now trying to boot from that disk brings up some sort of "invalid filesystem- grub rescue" command prompt. Knowing of course, that grub is something to do with linux, I deleted the linux partitions, so it would just load windows. However it's still giving that error message. 

Has ubuntu corrupted my windows installation as well? :(

---

### Post by Mark Phelps on 2013-09-27
when you installed ubuntu, you installed GRUB as well, most likely, to the MBR.  Removing the Linux partition did not reset the MBR.  So now, your PC is still booting from GRUB, but since it can't find the Ubuntu partition, the boot fails.

You can repair this from a Windows install DVD or Windows repair CD.

If you have neither of these, you can purchase an ISO image of the one you need from the following link: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")  Use another PC to burn that ISO to a CD, boot your PC from it, and run Startup Repair three times, that's right, three times.

---

### Post by Crinkle on 2013-09-27
Thanks for the help! I actually managed to "solve" this another way. I just reinstalled ubuntu. Even though it brings up the GRUB menu to choose windows or Linux, the windows partition is fully loading, so undamaged. Phew!

---

### Post by oldfred on 2013-09-27
While your Ubuntu install flash drive or DVD will work as a Linux repair tool, there just are certain repairs for Windows that can only be made from Windows. Make a Windows repair CD or flash drive now while Windows is working. It may save a lot of grief later.

 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

