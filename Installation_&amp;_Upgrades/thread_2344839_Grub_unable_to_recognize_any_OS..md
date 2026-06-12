---
title: "Grub unable to recognize any OS."
date: 2016-11-28
forum: Installation &amp; Upgrades
---

### Post by lebedev123 on 2016-11-28
Hello, this is my first time trying to install Kubuntu on my PC and I seem to be completely stuck. 
I have two hard drives (sda and sdb according to Ubuntu) and I have Windows 10 installed on the sdb1 disk. I installed Ubuntu on the free space of sdb.
As sdb is my bootable drive, I installed Grub on sdb. After the installation, my computer loaded Grub in recovery mode.
"ls"-command gave me a list of all my disks. However, checking all of them with "ls" resulted in the "Filesystem unknown" message, no matter if I checked the Windows partition or the Linux one (I know exactly where they are).
It seems that Grub fails to recognize any systems... What should I do?

---

### Post by oldfred on 2016-11-28
Newer UEFI system or older BIOS system.
Windows typically works better as first drive or sda. It sometimes still has boot partition on sda, even if "c: drive" on sdb.
If UEFI grub only installs to ESP - efi system partition on sda.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by lebedev123 on 2016-11-28
It's a BIOS system. I will try to get boot-info asap.
I tried installing Grub on sda to no effect as well. Windows seems to boot from sdb.

---

### Post by courtney2 on 2016-11-28
I am having the exact same issue as of yesterday. Windows 8.1 and was Fedora. I thought maybe F25 update caused the problem so I'm trying Kubuntu, no dice. Straight into grub recovery. I'm still working on it, finding no combination of drives works (Windows still boots if I point to that drive first) but something just decided to change for some reason

---

### Post by courtney2 on 2016-11-28
I found a good resource, my problem is it's not going into grub rescue as yours is, but grub. Check out what this article says and get down to the spot where he is talking about grub rescue. I'm still working on mine. I can boot into Kubuntu now, but I cannot get my changes to stay and I have to boot from grub manually each time. Your case is different so I will create my own thread and not hijack yours. Hopefully the link helps you

[https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux](https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux)

---

### Post by lebedev123 on 2016-11-29
Here is my boot-info. [http://paste2.org/x6W5w3L0](http://paste2.org/x6W5w3L0)
After many things I tried I am still unsuccessful...
I used the Boot-repair tool from Live-cd to try and fix any problems it found but the result is STILL exatcly the same.
By the way, now grub in rescue mode only recognizes 2 partitions.
ls: (hd0) (hd0,msdos1) (hd1) (hd1,msdos5)
I assume these are the NTFS ones.

---

### Post by oldfred on 2016-11-29
I am not seeing much, and Boot-Repair says grub installed correctly.
But your partitions on both drives are unusual.

Your sda drive only has one partition, but it is a logical inside an extended. And is nearer the end of the drive as if you had other partitions before it.

Your sdb drive starts at sector 64.
Since Windows 7 and Linux soon after partitions start at sector 2048 for compatibility with newer 4K and SSD drives. Only back in the Windows XP era did first partition start at sector 63, not even 64.
So you must have manually set that somehow during install.

Is Windows 10 fast start (always on hibernation) up still on? The Linux NTFS driver cannot mount a hibernate nor a NTFS that needs chkdsk. And any resize of NTFS needs chkdsk.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

I also prefer if you have two or more drives to keep each operating system on separate drives. Windows typically prefers to be first as it is not good about sharing. And then on second drive install Ubuntu. And use SATA ports in order on motherboard, or start with SATA0 and skip no port. 

You may need to reinstall a Windows boot loader to sdb and see if you can shutdown fast startup, run chkdsk or make other repairs. Grub only boots working Windows, so make sure you have a Windows repair/recovery or the installer with the repair console to fix Windows. And then if Windows is on its own drive you can keep Windows boot loader in the MBR of that drive so you can directly boot Windows whenever you have Windows issues.

Since grub says it installed ok, not sure why you still have boot issue. 
Are drives set to AHCI, not IDE, not RAID in BIOS?
You can also try fsck which is like chkdsk but for ext2, ext3 or ext4 formatted partitions.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by lebedev123 on 2016-11-29
I will now try to install Ubuntu on a different drive and see how it goes. Thanks for your quick and informative responses.

---

### Post by lebedev123 on 2016-11-29
SUCCESS!
After installing Kubuntu to a different drive everything works smoothly!
Thank you for your help, I really appreciate it. Love the Ubuntu community!

---

