---
title: "Restart after installation leads to gnu grub"
date: 2018-07-09
forum: Installation &amp; Upgrades
---

### Post by hungig on 2018-07-09
I succesfully installed Ubuntu from USB stick but after the restart I get into GNU grub terminal. I tried repair GRUB using this guide [https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/) which didnt help. This is the report from the boot-repair: [http://paste.ubuntu.com/p/w8tj29KJ6n/](http://paste.ubuntu.com/p/w8tj29KJ6n/). If anyone could help me I'd really appreciate it.

---

### Post by paranoidcoder on 2018-07-09
This is happening to me and I can't figure out why yet. I've tried all kinds of things with no luck. Here's another thread with the same issue: [https://ubuntuforums.org/showthread.php?t=2395999](https://ubuntuforums.org/showthread.php?t=2395999)

What I have tried:
- Tested 2 different flash drives, one of which I have used to install on my system previously
- Restore UEFI/BIOS defaults
- Disable secure boot/fast boot
- Unplug all drives other than destination drive
- Ensure the UEFI Ubuntu install option is booted
- Perform a "Normal install" without downloading updates or extra packages

---

### Post by oldfred on 2018-07-09
@paranoidcoder     
If answers in this thread do not help you and they may, as boot issues are often unique as system is different brand/model and configuration, please start your own thread and post link to summary report from Boot-Repair.

OP
                          
                     
                                       What version of Ubuntu? 

You  still show an UEFI Windows boot entry and multiple ubuntu entries but they show different GUIDs or you reformatted ESP - efi system partition. Also some  systems only boot from fallback or hard drive entry. 

I would first  remove all old/duplicate UEFI entries to avoid confusion & then a total  reinstall grub with Boot-Repair's advanced options.  

use  this to see details on UEFI boot entries as also shown in report.
sudo efibootmgr -v
Delete all ubuntu, grub & the Windows entry. You may also delete folders in /EFI/ubuntu, /EFI/grub & /EFI/Windows. The /EFI/ubuntu folder will be recreated with total new install of grub if using UEFI mode.
Delete with this, some require all 4 hex characters, other just need the one or two significant digits.
        sudo efibootmgr -b XXXX -B
More details:
man efibootmgr 

    
You may need to boot hard drive or fallback boot entry. Some systems do not want to boot anything but "Windows Boot Manager".
Since only booting ubuntu, you can use the work around that uses a Windows description but actually boots the shimx64.efi grub boot file. They seem to only check description not actual boot file.
See link in my signature below for other work arounds.
       **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by hungig on 2018-07-10
Ubuntu 18.04

---

### Post by paranoidcoder on 2018-07-10
Try and install without any internet access, so no WiFi or ethernet. That seems to be causing my issues. I was able to install without internet access successfully, followed by a failed installation with internet access, and then yet again a successful installation without internet access.

---

### Post by oldfred on 2018-07-10
Even if planning to use Wi-Fi, better to install with hardwired Internet connection. Generally quicker & if you need a new or updated wireless driver, then it can be installed.

---

### Post by paranoidcoder on 2018-07-10
@oldfred it seems you will run into these issues even if you have a wired internet connection currently.

---

