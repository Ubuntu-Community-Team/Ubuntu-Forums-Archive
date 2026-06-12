---
title: "unable to boot Ubuntu, GTP issue"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by Dragon2012 on 2012-05-30
Hi everyone.
I'm totally new to Linux, I have to mention. I have a netbook - ASUS Eee PC 1215B, with AMD C-60 processor, 4GB RAM, and 320 HDD. I decided to install Ubuntu 11.04 on my netbook. I''ve been fighting with this for a week. Firstly, I have Windows 7 installed and I wanted to install Ubuntu, but after installation Windows 7 was starting normally, it wasn't a system-choosing screen after installation. I've read a lot about restoring GRUB etc., but I couldn't do anything with this, so I deleted all ot the partitions on my HDD and installed only Ubuntu. Now my problem is, that after turning my computer on I have only this information:
```
Reboot and Select proper Boot device or Insert Boot Media in selected Boot devide and press a key
```I've been doing everything due to [http://www.linlap.com/wiki/asus+eee+pc+1215b](http://www.linlap.com/wiki/asus+eee+pc+1215b). Now I can't do anything with this. When I launch Ubuntu Live and type "sudo fdisk -l" I obtain a warning:
```
GPT (GUID Partition Table) detected on 'dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted"
```After typing "sudo blkid" I've got something like this:
[[IMG]http://images41.fotosik.pl/1550/6970fac4026b47d8m.jpg[/IMG]]("http://www.fotosik.pl/showFullSize.php?id=6970fac4026b47d8")
Here -> [http://ubuntuforums.org/showthread.php?t=1744799](http://ubuntuforums.org/showthread.php?t=1744799) it's similar issue, but after installing FixParts on my Ubuntu Live and typing "sudo fixparts /dev/sda" I obtain:
```
FixParts 0.8.4. Loading MBR data from /dev/sda  
This disk appears to be a GPT disk. Use GNU Parted or GPT fdisk on it! 
Exiting!
```What should I do now ? It's problem with this, that sda disk is GPT. How to fix it and change this GPT for something else ?
If I named my topic wrongly please correct me.

---

### Post by kc1di on 2012-05-30
download a copy of gpartd and put it on a flashdrive using unetbootin or similar. boot to it and reconfigure the drive and repartion it.

---

### Post by Dragon2012 on 2012-05-30
I can't boot GParted from a pendrive, I obtain lot of errors like that:
```
cat: can't open '/sys/block/*/removable': No such file of directory

```
and, at the end:
```
BOOT FAILED!
This Debian Live image failed to boot.
Please file a bug(...)

Unable to find a medium containing a live file system
modprobe: module i8042 not found in modules.dep
modprobe: module atkbd not found in modules.dep
[   118.888529] uhci_hcd: USB Universal Host Controller Interface driver
[   118.901839] usbcore: registered new interface driver usbhid
[   118.903906] usbhid: ISB HID core driver

BusyBox v1.19.3 (Debian 1:1.19.3-7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off
(initramfs)
```.

---

### Post by darkod on 2012-05-30
Do you want to replace win7 or to dual boot?

Because right now it doesn't seem that win7 is there.

Boot into live mode again with the cd, open terminal and post the output of:
sudo parted /dev/sda print

---

### Post by Dragon2012 on 2012-05-30
In result, I'd like to have dual boot, but at this moment I don't have Win7 installed, as I wrote before I deleted all of the partitions to install only Ubuntu first and than perchance install Win7 to have a dual boot.

I'm booting with the pendrive, I don't have a tray in the netbook.
Here you have a screenshot after typing "sudo parted -l":
[[IMG]http://images40.fotosik.pl/1599/11b7c7e0291e2daam.jpg[/IMG]]("http://www.fotosik.pl/showFullSize.php?id=11b7c7e0291e2daa")

---

### Post by darkod on 2012-05-30
Who made the GPT table, was it you?

Because unless the machine is using EFI boot, windows won't work on gpt.

If it is using EFI, the dual boot is a bit complicated. It seems the situation is still new and all the issues are not solved.

If you don't use EFI boot (or if the BIOS has an option to disable it), you can create msdos table on the disk and the dual boot should work fine.

But for the combination of EFI + gpt + dual boot I can't give you specific advice since I haven't used any of it.

---

### Post by 2F4U on 2012-05-30
If I am not totally mixing up things, gparted should be available on the Ubuntu liveCD. So instead of running a gparted liveCD you can run the Ubuntu liveCD. From there you can change the partition table from gpt to msdos.

---

### Post by kc1di on 2012-05-30
The problem is that gpt is a partition protection scheme.
You may have to find a dos disc or try to reinstall window temporarily any way here are some of pages that may give you a hint. you've got to get rid of that gpt partition.

[http://www.computerforum.com/163009-how-format-gpt-ntfs.html]("http://www.computerforum.com/163009-how-format-gpt-ntfs.html")

[http://answers.microsoft.com/en-us/windows/forum/windows_vista-windows_install/how-do-i-format-a-drive-to-gpt-on-windows-vista/4031d494-4aaa-48e6-afa3-889f96ee279c]("http://answers.microsoft.com/en-us/windows/forum/windows_vista-windows_install/how-do-i-format-a-drive-to-gpt-on-windows-vista/4031d494-4aaa-48e6-afa3-889f96ee279c")
[http://blog.paulgu.com/windows/delete-gpt-protective-partition/]("http://blog.paulgu.com/windows/delete-gpt-protective-partition/")

---

### Post by ajgreeny on 2012-05-30
> **2F4U said:**
> If I am not totally mixing up things, gparted should be available on the Ubuntu liveCD. So instead of running a gparted liveCD you can run the Ubuntu liveCD. From there you can change the partition table from gpt to msdos.
+1

Keep things simple, and assuming you can boot to the live USB of ubuntu, gparted will indeed be there.  Go to Device > Create partition table.  The default is an msdos table, which is exactly what you want, so do that, then start making new partitions as you want.

If you want to dual boot with Win7, install that first, either to pre-made partitions, or to the whole disk, and if using whole disk you should then shrink it with the Win7 disk management tool to make room for ubuntu.

---

### Post by kc1di on 2012-05-30
> **2F4U said:**
> If I am not totally mixing up things, gparted should be available on the Ubuntu liveCD. So instead of running a gparted liveCD you can run the Ubuntu liveCD. From there you can change the partition table from gpt to msdos.

your not mistaken but the ubuntu live would not boot for him.

---

### Post by Dragon2012 on 2012-05-30
Yes, I can boot Ubuntu live. And I managed to create new msdos partition table. Now, I have all space unallocated. Now, please tell me what should I do now to have dualboot between Win7 and Ubuntu 11.04 - I have 300 GB of space, how to divide it properly - which partition should be Primary, which Extended, what file systems should I use on each of them? And what exactly install first - Win7 or Ubuntu ?

---

### Post by 2F4U on 2012-05-30
It is usually recommended to install Ubuntu after Windows, because Windows will overwrite Ubuntu's boot loader grub, but you can also install the other way around. For detailed instructions see here:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Regarding the space, that largely depends on what you want to use each OS for. Ubuntu doesn't need that much space, but it will depend on what amount of data you intend to store.

---

### Post by Dragon2012 on 2012-05-30
OK, I'll divide it due to my needs, but what is the difference between Primary and Extended partition? I will first create one partition for Win7, it will be NTFS, should it be Primary or Extended Partition?

---

### Post by 2F4U on 2012-05-30
On a msdos partition table you can only have up to 4 primary partitions. As far as I know, Windows wants to be on a primary partition. Ubuntu is more flexible and can also be on an extended partition.

---

### Post by Dragon2012 on 2012-05-30
OK, now I'm installing Win7 on NTFS Primary partition, then I'll take up with Ubuntu. We'll see what will be the outcome.

---

### Post by Dragon2012 on 2012-05-30
I've installed Win7 on NTFS partition, then I booted USB with Ubuntu 11.04, created 3 partitions, as always (/, SWAP and /home) and installed Linux. After reboot it wasn't system-choosing screen again. I've followed an tutorial how to fix GRUB, and what I obtained after reinstalling GRUB was:
[[IMG]http://images38.fotosik.pl/1598/59e9ed685a9df7e6m.jpg[/IMG]](http://www.fotosik.pl/showFullSize.php?id=59e9ed685a9df7e6)
So I suppose it has gone okay. But now, when I turn on my netbook, I have GRUB, but in text mode - I have only "grub>" and I can type some commands. What should I do now?

---

### Post by kc1di on 2012-05-30
> **Dragon2012 said:**
> I've installed Win7 on NTFS partition, then I booted USB with Ubuntu 11.04, created 3 partitions, as always (/, SWAP and /home) and installed Linux. After reboot it wasn't system-choosing screen again. I've followed an tutorial how to fix GRUB, and what I obtained after reinstalling GRUB was:
[[IMG]http://images38.fotosik.pl/1598/59e9ed685a9df7e6m.jpg[/IMG]](http://www.fotosik.pl/showFullSize.php?id=59e9ed685a9df7e6)
So I suppose it has gone okay. But now, when I turn on my netbook, I have GRUB, but in text mode - I have only "grub>" and I can type some commands. What should I do now?

Go here and install boot repair and run it.
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by Dragon2012 on 2012-05-30
**kc1di** - what an awesome app ! It solved all of my problems automatically ! :) Thanks a lot, after a week of 'fighting' I'm home now :).
GRUB is repaired and I have system-choosing screen with Ubuntu and Win7. Thank you very much everyone !

---

### Post by darkod on 2012-05-30
Wait a little before running boot-repair, lets see what you've got first.

Can you post the output of:
sudo parted /dev/sda print

again? Lets see if the disk is really msdos and what partitions are on it.

---

### Post by Dragon2012 on 2012-05-30
**darkod**, Boot-Repair has done everything quickly and very simply by one click and typing a few commands in the Terminal. Awesome app. Problem is solved, thanks one more time !

---

### Post by kc1di on 2012-05-30
> **Dragon2012 said:**
> **kc1di** - what an awesome app ! It solved all of my problems automatically ! :) Thanks a lot, after a week of 'fighting' I'm home now :).
GRUB is repaired and I have system-choosing screen with Ubuntu and Win7. Thank you very much everyone !


Glad it's working for you ;)
enjoy

---

