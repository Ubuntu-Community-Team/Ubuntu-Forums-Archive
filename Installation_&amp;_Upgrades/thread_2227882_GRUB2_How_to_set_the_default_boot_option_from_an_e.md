---
title: "GRUB2 How to set the default boot option from an external file"
date: 2014-06-04
forum: Installation &amp; Upgrades
---

### Post by vassor on 2014-06-04
Hi All,

The GRUB variable GRUB_DEFAULT in /etc/default/grub contain the default boot menu option.
After a call at sudo update-grub
the /boot/grub/grub.cfg will contain this value in the "default" variable.

I would like to update this value by reading an external file located on a another partition (a Windows Partition in fact)

If I have GRUB_DEFAULT=2 I will have the line set default="2" in the grub.cfg


Is there a way to mount this external partition and to read the value after like so:
mkdir /media/WIN
mount /dev/sda2 /media/WIN
set default=`cat /media/WIN/default_boot_option.txt`

It's possible to realize this operation directly from the grub.cfg file ?
If yes, how can I do that ?

Thank for your Help
BR,
Xavier

---

### Post by oldfred on 2014-06-04
Not easily and probably not from Windows.
There are a few drivers for Windows that say they can read Linux partitions, but they do not write or do not work with ext4.
Also grub.cfg is set as read only, as you are not supposed to be directly editing it.

A bit more advanced would be to create a separate grub only partition. You would have to manually maintain the grub.cfg in that partition, but the partition could be fat32 or NTFS, it does not have to be Linux formatted.
I do that for all my flash drives and have used NTFS, FAT32 and ext4. And I normally add chain entries to my MBR on my hard drive or direct entries using the links in / so I boot most current kernel. 

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

Other possiblities may be to dd a Windows boot loader to MBR to boot Windows and copy back the grub boot loader (not sure how to dd type copy MBR in Windows?).
Or install grub to Linux PBR - partition boot sector. Then move boot flag to Windows partition to boot Windows and move it to Linux partition to boot grub from PBR. Generally installing grub to PBR is not recommended as it converts to blocklists which is less reliable.

---

### Post by vassor on 2014-06-05
Thank for your help,

-I don't want windows user access the GRUB partition, only the inverse.
 GRUB will read a file on the Windows partition (NTFS) which contain the default boot option (will set the 'default' variable value).

- Yes gruf.cfg is on readonly access, the part of this code could be present in the GRUB 00_header file for example.
My question is , it is possible to mount the windows partition and access it after like so:
    mount /dev/sda2 /media/WIN
    set default=`cat /media/WIN/default_boot_option.txt`

Yes or Not ?

If Not, i can use a dedicated grub partition (NTFS format) and ask to windows user to rebuild the grub.cfg file after setting the default option.
- edit the file /etc/default/grub and set 'GRUB_DEFAULT='
- execute the command 'update-grub' 
  but I think this command is not exist on Windows system ... but I can simulate it.

In this second solution I have a dependence between Windows and the GRUB partition that I don't want to have.

From Windows point of view there is no other system only him.

In the first solution (Mount + read file) if the mount operation is not supported, perhaps I can add a new primitive inside GRUB source code to realize this operation ?

Thank for your Help,
BR,
Xavier

---

### Post by oldfred on 2014-06-05
Another option is to just install grub to a flash drive and put it in you pocket. Then no access to grub unless you manually plug it in. You can still use flash drive for data as only MBR is used. And if USB is first in boot order it will boot it if plugged in, or boot Windows if that is second in boot order and no USB flash drive present.
Or you install grub2 to flash drive with the /boot/grub folder and manually create and maintain your grub.cfg file.

I do not know of a way from Windows to edit grub in a Linux format. If NTFS then it is accessible from Windows to change, but then your Windows user can also access it.

---

### Post by vassor on 2014-06-06
The option to connect or not a flash drive (USB or SATA) is a solution for enabling or not the boot on it but in my case the hardware must not be manipulate by user for security reason. 
Ok now if I decide to install GRUB on the flash drive and ask it to get his grub.cfg configuration file on the Windows partition do you think it's possible ?
For another security reason the flash drive partition will be write protected.

Thank for your help,
Xavier

---

### Post by oldfred on 2014-06-06
As long as a user has physical access, you do not have total security.

Anyone can take a flash drive and boot with Supergrub or many other tools.

All you really can do it restrict it some. You could totally encrypt your install so you need a pass phrase to totally lock it. Default installs of Ubuntu fully encrypted is a full drive install.

---

### Post by vassor on 2014-06-10
When you install GRUB on a windows partition where GRUB is really installed ?
Grub write his own first bootloader into the MBR but where is located the GRUB filesystem ?
MBR is only 512 bytes. In my example I assume we have only one partition on the hard drive and no more free space to create a second partition.

---

### Post by oldfred on 2014-06-10
You still install grub to the MBR, the area after the MBR is where core.img is hidden and grub folder is in the same /boot folder as Windows. You do have to be careful as Windows is not case sensitive so /boot and /Boot are the same, but grub may install in another /boot with different case. You can only have one and have to move the files.

Never install grub to a PBR or partition boot sector of a NTFS partition. That has to have Windows signature even if a data only partition.

I installed grub to my Windows 7 NTFS repair flash drive. I was not sure it would work, but it did. I could boot Windows repair console and boot my other repair ISO with grub2's loopmount.

And unless grub is in a Linux install, you have to manually maintain the grub.cfg as none of the scripts are available.

---

