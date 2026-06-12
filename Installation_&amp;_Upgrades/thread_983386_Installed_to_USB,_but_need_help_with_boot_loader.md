---
title: "Installed to USB, but need help with boot loader"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by jcoles on 2008-11-15
Using the Ubuntu 8.04 Alternate CD, I was able to install to an 8GB USB flash drive. But, any attempt to boot from this drive results in a hang that can only be fixed by powering down.

My USB drive is /dev/sdc1 when I boot normally from my HD. Could the device designation be  different if I use the BIOS boot menu to boot from the USB drive? The same question applies to the grub notation. Is hd2,0 possibly the wrong value for groot?

Is there a way to make the USB drive bootable independent of differing device designations on different computers?

---

### Post by caljohnsmith on 2008-11-15
> **jcoles said:**
> Using the Ubuntu 8.04 Alternate CD, I was able to install to an 8GB USB flash drive. But, any attempt to boot from this drive results in a hang that can only be fixed by powering down.

My USB drive is /dev/sdc1 when I boot normally from my HD. Could the device designation be  different if I use the BIOS boot menu to boot from the USB drive? The same question applies to the grub notation. Is hd2,0 possibly the wrong value for groot?

Is there a way to make the USB drive bootable independent of differing device designations on different computers?
So did you use the Ubuntu installer to do a full installation to your USB drive, or did you install the Live CD to it via something like UNetBootin or Intrepid's USB creator? If you have Grub properly installed to the USB drive's MBR (Master Boot Record), then it should boot as long as you set your BIOS to boot it. About the Grub notation, the first boot drive on start up is always (hd0), so your OS entries in the /boot/grub/menu.lst should use (hd0) and not (hd2). 

Can you download a Live CD to use for troubleshooting? Without a Live CD it is nearly impossible to troubleshoot these kind of issues. If you can get a Live CD, open a terminal with Applications > Accessories > Terminal, and please post:
```

sudo fdisk -lu
sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdc bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
That will help clarify your setup.

---

### Post by jcoles on 2008-11-15
I used the installer to do a full install to the USB drive. When asked about grub installation, I specified /dev/sdc, the USB device. The grub files are present in /boot/grub.

I have edited the menu.lst file to change hd2 to hd0.

I have Ubuntu 8.04 on a hard drive partition. Do I need to use the Live CD? 
Here's the output of the commands:
jcoles@thispc:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4d554d54

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   100358054    50178996   83  Linux
/dev/sda2       150239880   156296384     3028252+   5  Extended
/dev/sda3       100358055   150239879    24940912+  83  Linux
/dev/sda5       150239943   156296384     3028221   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001b217

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   312576704   156288321    5  Extended
/dev/sdb5             126   312576704   156288289+  83  Linux

Disk /dev/sdc: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007c553

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    14924384     7462161   83  Linux
/dev/sdc2        14924385    15695504      385560    5  Extended
/dev/sdc5        14924448    15695504      385528+  82  Linux swap / Solaris
jcoles@thispc:~$ sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
jcoles@thispc:~$ sudo dd if=/dev/sdc bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
0000

---

### Post by caljohnsmith on 2008-11-15
According to the "dd" commands you ran, Grub is unfortunately not installed to the MBR of your sdc drive; how about doing the following to install Grub to the sdc drive MBR:
```
sudo grub
grub> root (hd2,0)
grub> setup (hd2)
grub> quit
```
And please post the output of the above commands. Go ahead and reboot, and let me know if the sdc drive boots OK or not.

---

### Post by jcoles on 2008-11-16
I can boot the USB device now. Thanks.

Command output:
grub> root (hd2,0)

grub> setup (hd2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd2) (hd2)1+16 p (hd2,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

The dd commands now show no output for either command. Does this mean MBR is OK? Previously, the second command returned '0000'. 

Thanks for your help.

---

### Post by caljohnsmith on 2008-11-16
> **jcoles said:**
> 

The dd commands now show no output for either command. Does this mean MBR is OK? Previously, the second command returned '0000'. 

Thanks for your help.
That's great news you can boot your USB drive now. About those above commands, when the first dd command returns "Missing operating system", that actually isn't an error, it just means that you have a Windows boot loader in the MBR of that drive (ironic output though, isn't it?). If that first dd command instead returns "GRUB", then you have Grub in the MBR. The second "dd" command is only valid if you have Grub in the MBR, and it gives the location of the drive and partition that Grub is pointing to for its boot files. In your case, since Grub is pointing to the first partition on the same drive, the output should be "ff00"; "ff" means the same drive, and the "00" is the partition in Grub's numbering system, which begins at zero, so "00" is the 1st partition. 

Anyway, cheers and have fun with Ubuntu. :)

---

### Post by delog on 2008-12-05
Hi I have a similar problem. I installed ubuntu 8.10 to 8gb usb memory. Everything is ok, but if i dont plug in usb driver before starting the Pc, it gives error like GRub does not found. If I plug in usb before starting, grub appears and there is no problem. But I want to start XP without usb memory,and  i want to use ubuntu when boot computer from usb directly.(without grub). What can i do for this ? Thank you

Not: If I set the bios booting from usb, it says there is no bootable device. I think, installation changed the harddisk MBR and wrote grub files to usb. :(

---

### Post by caljohnsmith on 2008-12-05
> **delog said:**
> Hi I have a similar problem. I installed ubuntu 8.10 to 8gb usb memory. Everything is ok, but if i dont plug in usb driver before starting the Pc, it gives error like GRub does not found. If I plug in usb before starting, grub appears and there is no problem. But I want to start XP without usb memory,and  i want to use ubuntu when boot computer from usb directly.(without grub). What can i do for this ? Thank you

Not: If I set the bios booting from usb, it says there is no bootable device. I think, installation changed the harddisk MBR and wrote grub files to usb. :(
First, to install Grub to your USB drive so you can boot from it directly, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands. Then to reinstall a Windows style MBR to your internal Windows drive, just do:
```
sudo lilo -M  /dev/sda mbr
```
Then reboot, and if you select the USB drive to boot, you should at least get the Grub menu; if you select the Windows drive to boot, you should boot directly into Windows. How about giving that a shot and let me know how it goes, or if you run into problems, then please post the output of the commands given in post #2.

---

