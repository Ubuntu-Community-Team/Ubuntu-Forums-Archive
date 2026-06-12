---
title: "Problem With New Installation Duel Boot Windows 7 and Ubantu"
date: 2016-07-17
forum: Installation &amp; Upgrades
---

### Post by andrew1000 on 2016-07-17
I would appreciate anyone's help in solving the issue I have.

New build specs:  AsusM5A97R2.0 motherboard (AMD,) SSD 128 GB Windows 7 installed c:, Seagate Hard Drive 1 TB for data e:, SSD 60 GB Ubuntu installed as well as Kodi.

Please note:  Using a registry tweak, the Windows "users" folder along with all sub-directories has been moved to the Hard Drive e:  (This was done to separate data from the operating systems.)

[B]Ultimately, my goal is to essentially have a "PC" running windows with a number of programs which is totally separate from Kodi which will be used as a home theater.  (I was not able to install Kodibuntu and also want the ability to have Ubuntu available.)

[/B]After the Windows instillation, **all** the drives were disconnected leaving only the 60 GB SSD.  

It was my intention that after instillation of Ubuntu, there would be **no** boot menu...that is, I wanted to rely solely upon the bios to choose which drive to use..either c: with Windows 7 or (there is no drive letter) the SSD with Ubuntu and Kodi.  

**However,** I was surprised that after plugging in the other drives, I wound up with a boot menu on the Ubuntu SSD...I can either choose Ubuntu or Windows 7.

That is not how I want to do this.  As I said, I want to boot only from the bios.

So, here are my questions:

1) Is it possible for me to get rid of the boot menu?   (I don't mind reinstalling everything.)
2) The data drive is formatted in Windows NTFS.  I want to store movies and other media on that drive for use in Kodi...that is I need to be able to share that drive with Ubuntu.  (I am able to see both the c: and e: drives in Ubuntu but not in Kodi...so it may be a Kodi issue...I don't know.)  
3) I need to change the computer name in Ubuntu but have not been able to edit the host and hostname files....I cannot save the changes.  How can this be done?

If the easiest way is for me to start over...please let me know how and if I should format some of the e: data drive in etx4   I am not sure how the best way is for the data drive to be shared since as I recall, windows does not recognize etx4 but Ubuntu does recognize NTFS.

I thank anyone in advance who can help me set this up...I am a total newbie with Linux

---

### Post by oldfred on 2016-07-17
You can turn off os-prober, then grub updates will not look for other systems.
I have many Ubuntu installs and some are now obsolete. I turn off os-prober and only add the one's I still want into 40_custom.
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[URL="https://help.ubuntu.com/community/Grub2/CustomMenus"]https://help.ubuntu.com/community/Grub2/CustomMenus

      [/URL]
 In /etc/default/grub I added this line for os-prober:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
sudo nano /etc/default/grub
Add this line into grub, you can change to false if you do want an update later.
GRUB_DISABLE_OS_PROBER=true 
sudo update-grub

Do not turn on hibernation in Windows 7, Windows 8 or later uses fast start which is always on hibernation. Ubuntu will not mount NTFS that is hibernated nor mount if it needs chkdsk.

      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well: 

        [       ]("https://help.ubuntu.com/community/Grub2/CustomMenus")
 ** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data 
   ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a 
    [URL="https://help.ubuntu.com/community/Grub2/CustomMenus"]
[/URL] Do not know about hostnames.

---

### Post by andrew1000 on 2016-07-18
@oldfred.  
Unfortunately, I have very little idea what you are talking about.  I have virtually zero experience with Ubantu.  Additionally, I forgot to mention that I used easy BCD to write the boot menu to windows.  I really do not want any boot menu....What I want is the ability to boot either SSD independently from the BIOS.

---

### Post by oldfred on 2016-07-18
You have to have some menu somewhere, and that is called a boot manager.
New UEFI systems have a boot manager to choose what system to boot. Old BIOS systems just had a simple menu to choose which drive if you had more than one drive.
And grub is both a boot loader and a boot menu.
Windows is just a boot loader for Windows systems, but does allow some manual editing of its BCD to add entries.

If a new system, you really should use UEFI. But Windows 7 is older and default install is BIOS. But it can be converted to UEFI by copying to a flash drive and moving files around to make it UEFI.
Ubuntu can be installed to boot in either UEFI or BIOS boot mode.

But if dual booting, you really should have both systems in same boot mode, either both BIOS or both UEFI.

You can use BIOS, it is well known, but it is over 35 years old and has many fixes to make it work with newer systems. Some early UEFI systems were new and not as well supported, but now better known and the future.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by Geoffrey_Arndt on 2016-07-19
Remember too, that MS-Windows really conflates hardware terms with it's nonsense system of drive letters.    What is referred to as a drive in Windows is often in reality, the same physical drive but just a different partition.

Do you have a screen shot of your hdd, ssd drive (& partitions) topography?   It would be helpful. 

BTW, a boot manager that correctly offers the user OS launch options such as Grub2 (and other boot managers) is a real PLUS for a multi-OS system (even a Win only system with Win7, Win8, Vista).     

BTW2,  do you have the Kodi OS installed, or just the program?   And if just the program, in what OS?

Re hostname, on an installed system, it can be changed - - but if Ubuntu is running off Live media only, there is no "write", just "read" and the config changes will be lost at shutdown.

---

### Post by oldfred on 2016-07-19
If you have Ubuntu installed. Plug in all your drives and run this, you can run from your install or from a live installer:

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by mook765 on 2016-07-24
Windows is able to access ext2, ext3 or ext4 filesystem ( read and write ). you just need to install a driver, e.g. from paragon, free off charge.
there are other drivers available, google for it...

---

