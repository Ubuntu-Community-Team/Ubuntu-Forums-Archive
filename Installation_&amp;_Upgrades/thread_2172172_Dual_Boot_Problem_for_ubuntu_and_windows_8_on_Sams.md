---
title: "Dual Boot Problem for ubuntu and windows 8 on Samsung serie 3"
date: 2013-09-03
forum: Installation &amp; Upgrades
---

### Post by amineamg28 on 2013-09-03
Hello everyone;
I am trying to install ubuntu on a serie 3 Samsung laptop that came with windows 8.
I managed to successfully install it but I do not get the boot menu to choose between Ubuntu or windows.
I used the recommended Boot Repair choice and got the following error:
[http://paste.ubuntu.com/6059744/](http://paste.ubuntu.com/6059744/)
Please can you advice on how to fix the problem.
Thanks in advance.

---

### Post by amineamg28 on 2013-09-03
I tried the recommended boot repair again with secure boot activated and got the same error with the following link:
[http://paste.ubuntu.com/6059929/](http://paste.ubuntu.com/6059929/)

---

### Post by oldfred on 2013-09-03
We have seen several systems with a locked efi partition (which is not possible). The only work around seems to be to totally back up efi partition to have Windows boot files. Then with gparted delete efi partition, then recreate partition with FAT32 formatting  and boot flag to make it efi. Restore Windows boot files and then grub should install to efi partition.
Last line you your BootInfo report:
      >  Locked-ESP detected. You may want to retry after creating a /boot/efi partition (FAT32, 100MB~250MB, start of the disk, boot flag). ....

    

       grub-efi fails to install with Input/output error - locked efi
[URL="https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829"]https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829

[/URL]  SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

[URL="https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829"]
[/URL]

---

### Post by amineamg28 on 2013-09-05
> **oldfred said:**
> We have seen several systems with a locked efi partition (which is not possible). The only work around seems to be to totally back up efi partition to have Windows boot files. Then with gparted delete efi partition, then recreate partition with FAT32 formatting  and boot flag to make it efi. Restore Windows boot files and then grub should install to efi partition.
Last line you your BootInfo report:
      

       grub-efi fails to install with Input/output error - locked efi
[URL="https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829"]https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829

[/URL]  SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

[URL="https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829"]
[/URL]

Hi Oldfred;
Thank you for your reply.
I will try to do what you recommended but I may need some details and help.
The EFI partition that you are talking about is the sda2 one in my case (according to my report) ?
How can I back up properly the EFI partition using live USB ubuntu? which software?
Thanks.

---

### Post by oldfred on 2013-09-05
Boot script only shows some of the essential boot files. The efi partition may also have additional files.
You can just use the file browser - Nautilus from live installer to copy files. Copy & paste all the top level folders. There may be a setting to show hidden files and you want to do that although I do not think there are any in the efi partition.

It is sda2. After you have copied all the efi folders, use gparted to delete partition and recreate it. Be sure to use the manage flags and add boot flag.

[http://iloveubuntu.net/get-basics-ubuntu-1204s-unity-clear-explanatory-27-minutes-youtube-tutorial](http://iloveubuntu.net/get-basics-ubuntu-1204s-unity-clear-explanatory-27-minutes-youtube-tutorial)

---

### Post by amineamg28 on 2013-09-07
Thanks a lot Oldfred for your help.
I successfully fixed the boot system following your steps. Now I can choose between Ubuntu and Windows 8.
If it can help someone else, that's the link that I got from Boot Repair when it was successful : [http://paste.ubuntu.com/6074363/](http://paste.ubuntu.com/6074363/)

---

### Post by oldfred on 2013-09-07
Glad you got it working. :)

---

