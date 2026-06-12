---
title: "Installing Windows OS after multi-boot linux system"
date: 2015-11-23
forum: Installation &amp; Upgrades
---

### Post by Hodevah on 2015-11-23
Hello. 
I have been both researching and thinking of installing Windows on a multi-boot Linux system. Some of my research throughout the Internet that I have gathered has taken me to this thread here: > [http://askubuntu.com/questions/129058/how-to-install-windows-7-after-ubuntu-and-dual-boot](http://askubuntu.com/questions/129058/how-to-install-windows-7-after-ubuntu-and-dual-boot)

I would like to gather some additional information. For one thing, that particular post is about  2 years old. Knowing that technology changes each year as equally as does methodologies for doing what I have in mind, I would like to know from others who have installed Windows sometime after they had installed a Linux/GNU system. Either multi or solo GNU system. 

Here is my lsblk output:

> sudo lsblk -a
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1   8:1    0 460.1G  0 part 
&#9500;&#9472;sda2   8:2    0 231.8G  0 part /
&#9500;&#9472;sda3   8:3    0     1K  0 part 
&#9500;&#9472;sda4   8:4    0 231.8G  0 part 
&#9492;&#9472;sda5   8:5    0   7.8G  0 part [SWAP]
sdb      8:16   0  29.8G  0 disk 
&#9492;&#9472;sdb1   8:17   0  29.8G  0 part

or 

> sudo lsblk -fl
NAME FSTYPE LABEL    UUID                                 MOUNTPOINT
sda                                                       
sda1 ext4   Antergos b8e55e95-d5d9-422d-bd92-8506516d04a1 
sda2 ext4   Kubuntu  f211db28-021e-4475-baa2-db2d92d862dc /
sda3                                                      
sda4 ext4   Fedora22 6e661348-80f5-4041-b05a-1031c995e37a 
sda5 swap            49e89d3d-6164-4957-a3be-f306674da2d3 [SWAP]
sdb                                                       
sdb1 ntfs            72FC5A6909409415

and 

> sudo lsblk -S
NAME HCTL       TYPE VENDOR   MODEL             REV TRAN
sda  0:0:0:0    disk ATA      WDC WD10SPCX-75H 1A01 sata
sdb  1:0:0:0    disk ATA      LITEONIT LMS-32L 10E  sata

For interest's sake, I have a graphical output of the above **lsblk** output:

[ATTACH=CONFIG]265742[/ATTACH]

  If there are no other safe methodologies available (other than the one from above link) then my plan is to shrink the Arch based system (since it handles/manages Grub) anywhere from 50-100 GB with Live Gparted .iso (all partitions unmounted at that time)
Format from **/dev/sda1** about 50-100 GB NTFS and then install Windows;
Use Rescatux to regain Grub and update Grub there after of all OS. 
Much like it would say in the link I provided earlier; however, I would still like to gather other's experiences, support, and ideas of this.

Will Windows (7,8, or 10), after install, be stubborn and prevent me in some way that I may not be aware of at the moment, to re-install Grub using above name method?

Additional information: 
It is an UEFI system. However, I have not a separate **/boot/efi **partition. 
The Arch system, managing all OS on this system,  has Grub in it's **/boot** partition. 


thank you in advance for your responses.

---

### Post by oldfred on 2015-11-23
You have to have a primary partition like sda1 formatted NTFS with the boot flag for Windows. It normally uses 2 partition, a small boot & main, but will install to one.
Make sure you boot installer in BIOS/CSM mode, or it will convert to gpt and in effect erase drive.

You have to make sure Windows fast start up or always on hibernation is off. 
And will have to reinstall grub from whichever version you want to use, with Linux live installer.

       Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Grub only boots working Windows that does not need chkdsk nor is hibernated. So best to have a repair flash drive or Windows installer with repair console to fix Windows when needed.

---

### Post by Hodevah on 2015-11-24
@oldfred
Thank you for your answer.

---

