---
title: "Ubuntu installer doesn't detect windows 10 OS"
date: 2015-11-14
forum: Installation &amp; Upgrades
---

### Post by joao8 on 2015-11-14
Hi, sorry but searched if there was a resolution for this problem and didnt find it, had to make a new account.

Well then let me explain everything.

Bought laptop, formated and installed with windows 8 because previously it had bloatware and the laptop had a free key and attached to the bios.

So installed windows 8 and upgraded it to windows 10.

But now i want a dual boot with ubuntu and in the ubuntu installer there isn't an option to install side by side with windows.

Using live cd i go to ubuntu's terminal and write: sudo os-prober 
and it gives me:  /dev/sda1:Windows 8 (loader):Windows:chain

Shouldnt be a windows 10 loader?

Any ideas? Thanks.

---

### Post by grahammechanical on 2015-11-15
I cannot really tell you why the upgrade from Windows 8 to Windows 10  has not renamed the loader. That is not really something a Ubuntu user  forum can answer. Perhaps the Microsoft engineers decided that there was  no need to rename it because no one would notice that they had not  upgraded the boot loader. After all, if there is only Windows on the  machine then no one need ever know about the boot loader so long as it  does its stuff.

As to why the Ubuntu installer is not offering  the Install Alongside option, that can be explained by the possibility  that the motherboard has a BIOS boot system and a msdos partition table  for the hard disk and not a UEFI boot system and GPT partition table.

With  an msdos partition table we are allowed only 4 primary partitions and  if that 4 primary partition allocation is used up there is no where for  the Ubuntu installer to install Ubuntu. And so the Ubuntu installer  offers the only option it can and that is to Erase disk and install  Ubuntu.

Please use a Windows utility to take a screenshot of the  partition layout and post the screenshot in your thread, then we can  know for sure the situation. Please also read about primary, extended  and logical partitions. It will help you understand the situation.

[https://en.wikipedia.org/wiki/Disk_partitioning#Primary_partition](https://en.wikipedia.org/wiki/Disk_partitioning#Primary_partition)

Regards.

---

### Post by joao8 on 2015-11-16
Not much to say, i have 1 hard drive with 1 part used for windows and the other completely empty.

---

### Post by oldfred on 2015-11-16
Actually the issue is the grub2 os-prober. It searches for known Windows versions and uses that to label entry. But it has not been updated t include Windows 10 in its search.

You can live with it, or manually copy boot stanza to 40_custom and edit description at will. And then turn off os-prober so you do not have duplicate entries.

 gedit /boot/grub/grub.cfg
gksudo gedit /etc/grub.d/40_custom
sudo update-grub

If entry you copied works
 gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
sudo update-grub

---

### Post by yancek on 2015-11-16
If you have windows 10 upgraded from 8 it is probably UEFI.  You should be able to determine this from booting windows.  If you installed it your self then you would know if it is EFI or not.  If it is, you need Ubuntu installed EFI also.  You should use the Something Else options when installing.  Using the auto-install Alongside method, if something goes wrong you have no idea what it might have been.  As to it showing 8 instead of 10, I don't know why but previous versions were similar, it would show vista for 7 and it doesn't have any significance to the install.  You can change the menuentry label any time. 

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by joao8 on 2015-11-27
Looks like i had installed the windows 8 with legacy mode of bios. Installed everything in UEFI mode and its all good but there isnt the boot menu that before appeared when to choose between OS. I prefered the windows management boot, more clean and black and ill use more windows than linux, but when i put boot priority to windows management boot in the bios, it goes straight forward to windows without any option of OS, so anyone has sugestions?

---

### Post by oldfred on 2015-11-27
If mostly Windows, you can add a BCD entry in Windows. I believe it uses the UEFI one time reboot, so you boot into Windows & it reboots into grub/Ubuntu.

 Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

Some like a gui boot manager.
      
 Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)
Now has a ppa to make it easy to install:
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

---

