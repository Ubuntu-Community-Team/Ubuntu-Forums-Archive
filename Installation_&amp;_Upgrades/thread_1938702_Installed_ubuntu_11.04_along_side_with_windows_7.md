---
title: "Installed ubuntu 11.04 along side with windows 7"
date: 2012-03-10
forum: Installation &amp; Upgrades
---

### Post by vral on 2012-03-10
Hi All,
 
I installed ubuntu alongside with windows 7 but I am not getting the option for ubuntu in the windows boot loader. 
 
I have a 320 gb hard disk:
C: drive - 40 gb windows has been installed on this
D and E drives - 250 gb used for data
 
F: drive - 15 gb firstly formatted as NTFS but used gparted to change the filesyste. This is the partition I used to install ubuntu. This was divided into three partitions:
/dev/sda5 mounted to /
/dev/sda6 used as swap area
/dev/sda7 mounted to /home
 
While installing it asked for device to install bootloader and I selected the /dev/sda5 partition. It got installed but everytime it gets to windows 7.
 
I tried with easybcd to modify the windows bootloader.
Default: Windows 7
Timeout: 30 seconds
EasyBCD Boot Device: C:\
Entry #1
Name: Windows 7
BCD ID: {current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.exe
Entry #2
Name: Ubuntu
BCD ID: {50c1c685-6aa0-11e1-8dec-0026b91ed998}
Drive: C:\
Bootloader Path: \NST\AutoNeoGrub1.mbr
 
By doing this I was able to get the option but it never starts ubuntu. It gives me some error that the file \NST\AutoNeoGrub1.mbr is missing or corrupt.
 
Please let me know how to fix this.
 
 
Thanks

---

### Post by darkod on 2012-03-10
The bootloader goes to the MBR of the disk, not on a partition. You selected the partition #5, sda5, so it left windows bootloader on the MBR which can't run ubuntu by default.

I suggest you undo everything you did in EasyBCD, and install grub2 onto the MBR.

After you sort out the EasyBCD (delete what you did), you can boot with the ubuntu cd in live mode and in terminal install grub2 onto the MBR (/dev/sda):

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

That should get it going.

---

### Post by vral on 2012-03-10
Thanks Darko.
 
Doing that would still let me have access to windows right ??

---

### Post by darkod on 2012-03-10
Of course, grub2 can boot various OSs, including windows.

---

### Post by vral on 2012-03-10
Thanks a lot Darko....:P

That did it. I am able to use both of them now.

---

