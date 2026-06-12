---
title: "Dual Boot with Windows 8"
date: 2014-09-03
forum: Installation &amp; Upgrades
---

### Post by josh84 on 2014-09-03
Hello there,

I am trying to install Ubuntu alongside Windows 8. Everything seems to have went smooth until it was time to boot. I am putting my code below that I got from the boot repair option I used inside of Ubuntu. Any help is appreciated. 


[http://paste.ubuntu.com/8226435/](http://paste.ubuntu.com/8226435/)

---

### Post by yancek on 2014-09-03
Which option did you select during the installation of Ubuntu?  There is no sign of any windows partition.  You have the EFI partition, the system partition for Ubuntu and the swap partition.  You don't seem to have even a windows recovery partition, if this was an OEM install it should have, if not then no.  If you still want windows 8, you need an installation medium for it.

---

### Post by josh84 on 2014-09-03
I see that is unfortunate. I am actually unable to single boot now after repeated attempts. It just keeps going back to the flashdrive and the install menu after reboot. If I remove the flashdrive it just keeps saying no media present. It appears to be corrupted somehow only reinstalling over everything does not help.. ideas? I want to start from scratch.

---

### Post by yancek on 2014-09-04
If you remove the flash drive you need to enter the BIOS setup and change the first boot priority to the hard drive.  If you've done that and it still fails with that message you may have to reinstall.  If you want to reinstall both windows 8 and Ubuntu, make sure that you install both in EFI mode OR both in mbr/bios.  The second option will require you to install the UBuntu Grub bootloader to the master boot record of the drive as windows is incapable of booting Linux without third party software.  That' s about the extent of my knowledge of EFI.  Hopefully someone with a little more knowledge on the subject will post.

---

### Post by josh84 on 2014-09-04
I have it set to boot to the disk first... I have tried multiple times to reinstall Ubuntu.. I dont care so much about losing the windows partition... better off without it. I just need help getting a single boot with Ubuntu going.

---

### Post by josh84 on 2014-09-04
I have it set to boot to the disk first... I have tried multiple times to reinstall Ubuntu.. I dont care so much about losing the windows partition... better off without it. I just need help getting a single boot with Ubuntu going.

---

### Post by yancek on 2014-09-04
I don't see any obvious errors in the boot-repair output but I don't use UEFI.  If you remove the flash drive and set the internal hard drive to first boot priority and it still won't boot, there is some other problem.

---

### Post by josh84 on 2014-09-05
Yes clearly.

---

### Post by asharpjr on 2014-09-05
Like Yancek said, I think you might have deleted your windows partition. Do you still have the Windows 8 install Disk or Flash Drive to get that back? When you went to install Ubuntu, you might have chosen the Windows Partition to put Ubuntu on, which formatted and installed Ubuntu on.  Sounds like you might have to start all over again with everything. I had a similar issue, I used this: [http://www.supergrubdisk.org/2010/08/20/sg2d-downloads-20100820/](http://www.supergrubdisk.org/2010/08/20/sg2d-downloads-20100820/) and it worked like a charm...

---

