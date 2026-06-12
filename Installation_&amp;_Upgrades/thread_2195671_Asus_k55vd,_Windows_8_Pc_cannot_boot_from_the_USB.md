---
title: "Asus k55vd, Windows 8: Pc cannot boot from the USB"
date: 2013-12-25
forum: Installation &amp; Upgrades
---

### Post by sakircimen on 2013-12-25
Hello everyone!

I guess you have faced this type of questions a lot but I'm just a beginner so tolerate me please :)

I have an Asus-k55vd laptop, which has windows 8 installed originally. I was trying to install ubuntu 12.04 LTS on it. 

I have tried to create a bootable USB stick on Windows ( by just following the instructions here; [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

And I was thinking that I was succesful. then I followed the steps here to disable secureboot and fastboot. [http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

then I restarted the pc many times but it simply can not detect the usb to boot up from. It just starts with windows. 

What shall I do?

---

### Post by oldfred on 2013-12-25
Your instructions look ok.

Issue with flash drive can be bad download or install to flash drive. Or just some flash drives do not work or some installers work better (or the reinstall works a second time?). 
You do have to choose from UEFI/BIOS correct UEFI boot from flash drive.

Check that download was correct.
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
      
 Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

    
 Most find this works best
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
      
 
Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

     

Some other Asus, may have mentioned something?
   [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

But some Asus just do not work in UEFI mode.
      
 Asus K55N booting Ubuntu with secure boot
[http://askubuntu.com/questions/353390/having-windows-8-boot-from-ubuntu-menu-issues](http://askubuntu.com/questions/353390/having-windows-8-boot-from-ubuntu-menu-issues)
Asus K55N just does not boot Ubuntu in UEFI mode. Some things to try, but no solution
[http://ubuntuforums.org/showthread.php?t=2137233](http://ubuntuforums.org/showthread.php?t=2137233)

---

### Post by sakircimen on 2013-12-25
I'm really sorry, let me more specific about the problem so I can decrease those resources to read :)

I have just check my bios detailed, and I saw that my USB stick is cannot be seen on that boot priority list. I am putting some photos here. (attachment no. 1) 

When I ask to add new boot option, it shows this screen (attachment no. 2):


In the path for boot option above, there is this explanation: (attachment no. 3)


does the ".efi" thing this mean I have to install ubuntu in efi mode?



*** for some additional info, I am using a Toshiba 4 GB flash drive. it is a few years old and I cannot read it's exact model etc. I have tried to re-install the .iso file to the drive but it didn't work either.

---

### Post by ubfan1 on 2013-12-25
Sometimes setting the supervisor password in the BIOS/UEFI settings will make other boot options available.

---

### Post by oldfred on 2013-12-25
Please attach photos as small size 800x600 or similar small sizes, not in-line. You can use Advanced editor and just use paperclip to add your screenshots. 

It looks like you need to add some boot options. Perhaps you still have secure boot on. But Ubuntu should still show. When secure boot is on, only secure boot systems will be shown. When secure boot is off the flash drive should show twice, one UEFI and another as CSM/BIOS/Legacy or whatever system uses as a name.

Some have posted they have to also create a password for UEFI/BIOS. If so very important to remember it. Others have had settings to enable various devices.

---

### Post by sakircimen on 2013-12-25
edited the attachments. 

OK, I will give it a try with password. Does the password can be changed or removed afterwards?

and the topic here seems useful ([http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)) but I have only 1 flash drive that is larger than 512 MB, and both 2 bootable iso files are larger than 512 MB. Also I have only one PC so I can't rebuild my flash drive during the installation. How can I fix the problem? Can I setup 2 bootable files to 1 flash drive? (of course assuming that file sizes are appropriate)

---

### Post by Eugene King on 2014-01-01
Only way I was able to create a usable USB ubuntu stick was to burn the ISO to a DVD....

Then boot up on the DVD running Ubuntu and selecting the perminant install and then selecting other and choosing the usb stick to install ubuntu on..

Allow the install to format your usb stick in Ext-4 or something like that. And don't forget to select "/" for the boot.....

I am using a USB Ubuntu stick as I'm typing..

---

### Post by oldfred on 2014-01-01
@Eugene King
Your install is a full install which is fine. Best to make sure you have made a few changes to reduce writes to both speed things up and increase life of flash drive.
But the normal installer is FAT32 formatted for greater compatibility for installing. Windows cannot create or see Linux formatted partitions, so otherwise it could not create an Ubuntu install flash drive.

---

### Post by Eugene King on 2014-01-01
> **oldfred said:**
> @Eugene King
Your install is a full install which is fine. Best to make sure you have made a few changes to reduce writes to both speed things up and increase life of flash drive.
But the normal installer is FAT32 formatted for greater compatibility for installing. Windows cannot create or see Linux formatted partitions, so otherwise it could not create an Ubuntu install flash drive.

I will look into that.....It remindes me That I tweeked those "writes" things when I had a little 8g stick that was slow as dirt.....the tweeks made it managable. Also went to the LXDE desktop.

The stick I'm using currently (8g got full) is 32 and is almost as fast as the hard drive install on my laptop......

---

