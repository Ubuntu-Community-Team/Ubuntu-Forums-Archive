---
title: "How to Dual boot Ubuntu 13.04 64 bit and Windows 7 on Win8 UEFI Computer"
date: 2013-09-20
forum: Installation &amp; Upgrades
---

### Post by ldfcldfcldfc on 2013-09-20
**I have spent days trying to get my Computer to Dual boot Windows 7 and Ubuntu with any inconviences along the way and I would love to tell the world in the hope that anyone with the same problem will be quickly helped.**

I recently bought a new HP Pavilion g6-2244sa 15.6" Laptop (1TB HDD, 8GB RAM) with Windows 8 pre installed. 

I did not like Windows 8 so wanted to downgrade to Windows 7 dual booting with Ubuntu 13.04 and this was made hard by the new UEFI system, along with the secure boot function which has to be present for a computer to be certified by Microsoft. I presume this is a new way for Microsoft to fight of Competition and to eliminate Linux users to switch between systems.

This setup should work for most HP Laptops or computers with similair spec which has Windows 8 as the default OS and has the new UEFI system.

1. Enabe Legacy boot and Disable Secure boot. To prepare your computer for this boot, you must enter BIOS Setup when you first turn on your computer (usually by pressing ESC) and enable legacy boot and disable secure boot. This is very important and will enable either a Windows 7 or Ubuntu boot or both.

2. Install Windows 7. Put in your Windows DVD and install Windows 7, first by deleting everything off your drive and by selecting a size of the new drive. In my case my Hard Drive is 1TB so I selected 150GB for Windows and the rest will be unallocated and used for the Ubuntu installation. You select the bigger of the two drives you created for the boot and then click Install and install your Windows system.

3. Make a bootable USB drive. When the Windows installation is complete and you are happy, start on the Ubuntu installation. Initially, I had difficulty in Loading the Live CD which stalled at the Purple Ubuntu screen. To get by this and enter setup I made a bootable USB device and then I was able to go onto the installation process. 

To make a USB installer you install the Linux Pen Drive installer and load the suitable iso file and select the device you intend to install it on.

The link  for the full guide can be found here:
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

4. Boot from the USB drive. Once I had booted the USB drive, you need to select 'Try Ubuntu without installing'. This is because you may need to use the Terminal window whilst installing.

5. Make Windows System visible. Click the install Ubuntu option but you may come across the problem I encountered. Ubuntu did not detect the Windows system and made partition impossible. The whole drive appeared that there was no space used but this was simply wrong.

I found that it has something to do with the disk previously having had a GUID partition table but not completely wiping it out before changing to an MBR partition table. This results in an MBR partition table with corrupt GPT signatures, which gparted chokes on.
Assuming Windows is installed on /dev/sda:

Open Terminal and type the following:
sudo dd if=/dev/sda of=sda.mbr bs=512 count=1
To clear the GPT signatures you'll need gdisk by typing:
sudo apt-get install gdisk 
sudo gdisk /dev/sda
Switch to expert mode: x
To "Zap" GPT enter: z
The selection for the first question Y and answer N for MBR!! 

6. Install Ubuntu alongside Windows 7. Once you've finished with GUID you should be able to relaunch the installer and it will detect the partitions along with windows for dual-booting. 

You select the Option 'Install Ubuntu alongside Windows 7' and click next and it will do all the work for you.

The relevant link where I found this solution is here:
[http://askubuntu.com/questions/287352/ubuntu-13-04-amd64-installation-does-not-detect-windows-7](http://askubuntu.com/questions/287352/ubuntu-13-04-amd64-installation-does-not-detect-windows-7)

7. Create Grub menu. Boot to Live USB Drive again. Following the Ubuntu install and partition, the UEFI system is designed to boot from any Windows OS ignoring any other system on the drive making it impossible to boot into Ubuntu. To tackle this by setting up a boot menu which will give you the option of what OS you want to boot from each time you turn on your laptop.

There is a very easy and interactive way to fix the grub problem. Using this method it will start reading all your boot partition and also you will be able to use any operating system. All operating system installed in your computer will be displayed in grub menu.
You have to follow these very simple steps..
Boot from LiveCD or your bootable USB, Select 'Try Ubuntu'.
Install boot-repair ( a good s/w to fix grub )
2.1: $ sudo add-apt-repository ppa:yannubuntu/boot-repair
2.2: $ sudo apt-get update
2.3: $ sudo apt-get install boot-repair
2.4: Run boot-repair from your system or type: (boot-repair &)
When started select Option 'Recommended Repair' from out of two options:
'Recommended Repair' & 'Advanced Options'.
Follow very easy on-screen instruction, it will build/fix your grub..
Restarting your system will display both options to boot from Ubuntu & Windows.

The relevant link I found this solution is here:
[http://askubuntu.com/questions/336597/how-to-dual-boot-windows-7-x64-and-ubuntu-13-04-x64-as-bios-not-efi](http://askubuntu.com/questions/336597/how-to-dual-boot-windows-7-x64-and-ubuntu-13-04-x64-as-bios-not-efi)

8. Enjoy the best of both worlds. After doing this, reboot your Computer and you should be given a choice of which operating system to boot into. This will now occur every time you turn on your computer and allow you to boot from either OS. 

I hope this guide will help anyone else that experiences similar problems.

Enjoy!

---

