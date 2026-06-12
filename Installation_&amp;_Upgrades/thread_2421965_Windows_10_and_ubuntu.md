---
title: "Windows 10 and ubuntu"
date: 2019-06-30
forum: Installation &amp; Upgrades
---

### Post by dellboy56 on 2019-06-30
Hello Guys Im not new to using Linux but i want to be able to "dual boot" ubuntu alongside windows i have a spare SSD in my computer laying around doing nothing and i am wondering how i can get Linux on that ssd without messing with my Windows 10 installation on another ssd present in my system thanks!

---

### Post by yancek on 2019-06-30
As luck would have it, Ubuntu developers have written details on how to do that and it is at the web site below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-06-30
With two drives, easiest is to disconnect (logically in UEFI or physically) the Windows drive.
Grub will auto install its boot loader files to the ESP - efi system partition on drive seen as sda, of if NVMe first drive.
Best to manually partition in advance and include an ESP on Ubuntu SSD.
You can after install, copy /EFI/ubuntu boot files from sda to Ubuntu drive. You can do this work around when installing or just leave booting in UEFI mode from Windows ESP.

       Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

---

### Post by dellboy56 on 2019-06-30
Ok i will try and have a go installing today so im assuming i have to take my windows 10 M.2 drive and leave the other one m.2 in so i can install ubuntu on it. Also kind of not understanding what you mean about ESP etc.

---

### Post by Agradilius on 2019-06-30
What I do is unplug the Linux drive(s), then install windows on it's own drive. Plug the linux drive back in and install Linux. As long as both OS's are UEFI, then grub should autodetect the windows boot loader on the windows drive without having to do anything special. I literally just did this about an hour ago with kubuntu and windows 10. My Pc boots to grub and both linux and windows are listed.

---

### Post by dellboy56 on 2019-06-30
And also im assuming ill have to create manual partitons etc on my the drive  i want to install linux on or can i utilize the full drives space without partioning

---

### Post by oldfred on 2019-06-30
If only drive, default install with Ubuntu in UEFI mode will be an ESP - efi system partition (FAT32) and / (root) as ext4. 

Many users also like to have system separate from user data, so add a /home partition. But then you have to use the Something Else install option to create or use a previously created partition for /home.

       Two Drive UEFI installs
[https://ubuntuforums.org/showthread.php?t=2305876](https://ubuntuforums.org/showthread.php?t=2305876)
[https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)
[https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration](https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration)
[http://linuxbsdos.com/2015/10/31/how-to-dual-boot-windows-10-and-ubuntu-15-10-on-two-hard-drives/](http://linuxbsdos.com/2015/10/31/how-to-dual-boot-windows-10-and-ubuntu-15-10-on-two-hard-drives/)

---

### Post by emma199 on 2019-07-01
I tried to do the dual boot but after that I noticed that my [windows 10 startup folder not working]("https://oniton.com/blog/windows-10-startup-folder-not-working/") and I am not able to find out the exact reason behind this issue. Kindly let me know if anyone has any idea about this.

---

### Post by dellboy56 on 2019-07-01
it asks me when i go to install if i want to install alongside windows boot manager and or other things it also lists a lot of partitions in when i chose something else what should i do

---

### Post by yancek on 2019-07-01
If you want to keep your windows and Ubuntu separated on their individual drives, what is suggested above is that after you have installed windows and successfully tested it to verify that it boot, dis-connect the windows drive and install Ubuntu to the second drive.  You need to create an EFI partition on that drive and Ubuntu will install the EFI boot files there and install the OS to another partition using the rest of the drive for the / (root filesystem) partition.  Using the Something Else option to install, if it succeeds reboot and set the Ubuntu drive to first boot priority in the BIOS and then boot Ubuntu after re-attaching the windows drive.  If Ubuntu boots, open a terminal and run:  sudo update-grub and watch the output for a windows entry.  The link I posted earlier and the links posted above by oldfred give details on this process.

---

### Post by oldfred on 2019-07-01
You still need to turn off Windows fast start up and while reconfiguring best to turn off UEFI fast boot as sometimes you have issues pressing key for UEFI, UEFI boot menu or Escape key for grub menu. Boot with fast boot on can be very quick, so no time to press key unless you do a full cold boot from power totally off for a bit.

See steps to install in link in my signature. Do not skip backup even though installing to separate drive. If you make an error and overwrite Windows it is a big deal to try to reinstall. But if you have backup, only a minor issue to restore.

---

### Post by dellboy56 on 2019-07-01
so your saying that the Efi partition has to go onto my drive i want to install ubuntu on yet i cant install ubuntu on that drive and i have to install it to another one instead. I Mean both my drives are the M.2 form factor so i have no problem taking the Windows one out. anyways i will have a go at trying to do that I thought it was more complicated but ill have a go at trying to understand what i have to do.

---

### Post by oldfred on 2019-07-01
When you disconnect the Windows drive, then the remaining drive becomes the first NVMe drive where grub will install its boot files into the ESP on that drive.
If you have created partitions in advance, you still use Something Else install option but use the change button to select which partition is / (root) and which is /home. And select the format as ext4. It will automatically use the ESP. Those without an ESP, then get errors that grub boot loader cannot install at end of install process.

---

### Post by dellboy56 on 2019-07-02
what is better to use The LTS version or not i found that the LTS version does not support my ASUS PCEAC88 PCIE wifi card out of the box however 19.04 Does any reason behind that? all i know is the chip is a broadcom one so.

---

### Post by dellboy56 on 2019-07-02
[IMG]https://ibb.co/MRZRST4 <a href=https://ibb.co/jLjJHZ9 target=_blank>https://ibb.co/jLjJHZ9</a> https://ibb.co/Bfyv1m9[/IMG]i had photos but having trouble trying to upload them.

---

### Post by yancek on 2019-07-02
Always better to use an LTS release.  One of the few exceptions is if some hardware does NOT work with LTS and does work with non-LTS so use 19.04.  You then need to be aware of when support for that specific release ends.

---

