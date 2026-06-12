---
title: "Windows 10 won't boot after 18.04 [mint] reinstall - Dual boot"
date: 2018-07-18
forum: MINT
---

### Post by 8link on 2018-07-18
Hello,

I have a dual boot UEFI Mint/Windows 10 setup that has been working as expected for a long time.  I recently wiped and reinstalled 18.02 [mint 19] on /dev/sda7.  18.04 boots as expected but I am unable to get my Windows 10 installation to boot.  Windows is installed on /dev/sda4.  EFI is installed on /dev/sda2.  I used boot-repair successfully in the past and tried it again this time but have had no luck.

Here's my bootinfo file:
[https://paste.ubuntu.com/p/BcM99BJYYv/](https://paste.ubuntu.com/p/BcM99BJYYv/)

Any help you can provide is appreciated.

Thanks!

---

### Post by wildmanne39 on 2018-07-18
*Thread moved to **MINT for a more appropriate fit**.*

---

### Post by oldfred on 2018-07-19
Can you directly boot Windows from UEFI boot menu. Often f10 or f12 check your manual.

Grub only boots working Windows. And Windows 10 will turn fast start up or always on hibernation with updates. And then grub will not boot it.

It looks like Boot-Repair also added to 25_custom grub scripts folder a lot of new grub menu entries.
Many or all of those probably are not required.

       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub 
[https://askubuntu.com/questions/778663/what-is-the-difference-between-windows-uefi-bootmgfw-efi-and-windows-uefi-bkpboo/778705#778705](https://askubuntu.com/questions/778663/what-is-the-difference-between-windows-uefi-bootmgfw-efi-and-windows-uefi-bkpboo/778705#778705)

---

### Post by 8link on 2018-07-19
Ah, maybe its fast start preventing grub from booting it.  It was working fine previously and I rarely boot to windows, its quite possible that is the problem. It doesn't seem relevant here I suppose but do you have any ideas on how to get windows booting without reinstalling it?  I planned on paring down my grub menu options after I got windows booting.  I appreciate the directions to do so.  Thanks much!

---

### Post by oldfred on 2018-07-19
You should be able to directly boot Windows from UEFI.
If it needs repairs, you may be able to then use f8 to get into repair console.

Or you should have a Windows repair disk or installer with the repair console. 
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by jeremy31 on 2018-07-19
8link When did you download the Linux Mint 19 ISO?

---

### Post by 8link on 2018-07-22
It was downloaded the day it was released. Why?

---

### Post by jeremy31 on 2018-07-22
New downloads were released to fix some issues that involved grub install on fresh EFI installs but it normally prevented any boot

The original ISO's were fine up until July 10

---

### Post by 8link on 2018-07-23
I resolved this by downloading a windows 10 iso; creating a usb installation boot disk with it; booting windows; selecting repair and then command prompt and running bcdboot as the following to repair the windows boot files that were messed up by my mint install. 
         ```
bcdboot %path_to_windows_directory% /s %efi_boot_partition% /addlast  
```

This reinstalled the needed windows boot files and allowed me to boot the windows boot manager option which previously just hung.  
Thanks for all your help!

---

