---
title: "Why USB drive is to be formatted using NTFS when it is to be made bootable"
date: 2013-04-09
forum: Installation &amp; Upgrades
---

### Post by linuxday on 2013-04-09
I have decided to install Ubuntu as the second OS on my PC to get started with Linux. I attempted to make USB drive bootable by following the guidelines mentioned in all the linux forums and also copied the Ubuntu files on to the USB drive. When the system boots, it threw an error that 'BOOTMGR is missing'. On researching, I understood it could be due to the USB drive not being made bootable properly or due to incompatible system types (32 bit or 64 bit). I rule out the later possibility as my system is 64-bit and I downloaded 64-bit flavor of Ubuntu.

I now suspect the issue could be only due to USB drive not being made bootable properly. I formatted the USB drive using NTFS, and also tried using tools like UNetbootin but to no help :( I am still trying to figure out other culprits causing BOOTMGR issue, but am struck at understanding why is that the USB drive is to be formatted only using NTFS but not the default FAT-32?

Your answers will be great helpful. Thanks in advance

---

### Post by fantab on 2013-04-09
What tool did you use to make the USB bootable? Official Instructions are [HERE]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows").
Try another USB if you can.

---

### Post by oldfred on 2013-04-10
Are you trying to create a liveCD version or a full install to your flash drive. But either way you do not install with NTFS formatting as that is Windows. The bootmgr missing is a Windows error as the NTFS partition boot sector is looking for Windows to boot. Windows does not boot from external devices anyway.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

If you want to have space on a full install for shared Windows data, you may want a NTFS partition first as Windows only sees the first partition, but you have to install Ubuntu into Linux partitions. This only works for larger flash drives.

---

### Post by C.S.Cameron on 2013-04-10
Use Startup Disk Creator from the Live CD or Unetbootin to install to make a Live USB.
Filesystem type should be FAT32.

---

### Post by linuxday on 2013-04-11
Thanks for your answers. Now it makes sense to me why file system should be FAT32. I formatted USB stick using FAT32 and used Unetbootin to install Ubuntu.

Well, now how do I mark this thread as SOLVED?:confused:

---

### Post by N3XU5 on 2013-04-11
Use the windows partition manager, and format it to fat32. Use Unetbootin to make a live/download ubuntu usb.

---

