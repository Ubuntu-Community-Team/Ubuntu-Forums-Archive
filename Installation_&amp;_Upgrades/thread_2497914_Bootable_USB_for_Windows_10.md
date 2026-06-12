---
title: "Bootable USB for Windows 10"
date: 2024-05-22
forum: Installation &amp; Upgrades
---

### Post by angel mike on 2024-05-22
Trying to make a bootable USB for Windows 10, The WoeUSB method gave the 'Install' option as greyed out. Can anyone suggest a reason or better method.
Just looking at Wine to use for the Garmin Express to update my maps. This is the only reason for using Windows. Found what might be a useful link [https://christitus.com/garmin-express-linux/](https://christitus.com/garmin-express-linux/)

---

### Post by gezzer2 on 2024-05-23
i have the same setup for Garmin Express Win 10 In Boxes.

go to the Win 10 ISO and Right click the ISO.
on that menu choose "open with"

then click on "Disk Image Writer"

then follow the instructions and you will be able to make a bootable USB of Win 10.

###

in boxes you can just use the Win 10 ISO to install Windows and then use Windows via Gnome Boxes ..

as stated i have this setup for Garmin Express ..

---

### Post by angel mike on 2024-05-23
Thanks gezzer2 will give that a try.

---

### Post by angel mike on 2024-05-24
I still cannot get WoeUsb to work. When I load the Woeusb application it shows the USB target file but the source button does not work If I go to the iso file I can eventually get it into the box but the 'instal' button is greyed out. 

If I try 'gezzer2' method then l -then I right click on the iso the menu shows 'open with Disk Image Mounter' so I choose open with other which gave a menu list containing 'Image disc writer' which I chose. But it asked for a destination which did only included the USB name not Woeusb - I copied the iso file to the USB but could not boot with it. The Woe panel was not used.

---

### Post by yancek on 2024-05-24
I've never used WoeUSB but were the instructions you originally used similar to those described at the link below?

[https://itsfoss.com/install-woeusb-ubuntu/](https://itsfoss.com/install-woeusb-ubuntu/)

I generally just mount the windows iso to a directory mount point in Linux, then copy the contents to the mounted USB drive which has never failed to boot.

---

### Post by ubfan1 on 2024-05-24
Install the wimtools package, and use the wimsplit program to break up the big .wim file from the ISO.  Then just copy all the ISO files, replacing the big one with the two you split up .swm to a FAT formatted USB.

---

### Post by angel mike on 2024-05-26
Yes tried the foss method and a similar one. Thanks for all the contributions - will have another go.

---

### Post by angel mike on 2024-05-26
'I generally just mount the windows iso to a directory mount point in Linux,' How do you do that Yancek ? ie how do you find or create a directory mount point?

---

### Post by yancek on 2024-05-26
You can use any empty directory or create one.  When using Linux, if you have downloaded some windows iso file, it should be in your user Downloads directory so open a terminal and navigate to your user Downloads directory where the windows iso is.  You can use the GUI to create a directory there as a mount point or do it from a terminal:  sudo mkdir windows (you can name it something other than windows, just an example)  In this example, if the windows iso file you have is named windows.iso you would do:

sudo mount -o loop windows.iso windows

This is done from the directory (Downloads?) in which the iso is.  This will mount and make accessible all the files in the windows iso and you can then copy them from the mount point 'windows' in your Downloads folder to wherever your usb is mounted.  You may need to do something as suggested in post 6 as it has been some years since I have bothered with any windows.

---

### Post by angel mike on 2024-05-26
Thanks Yancek for those details.  I formatted the usb with zeros using Disks. I assume your referring to ubfan1 and wimtools - not familiar with that - FAT format has a restriction on the file size which presumably suits the split files?

---

### Post by angel mike on 2024-05-26
I found this link for mounting iso files which might be useful [https://askubuntu.com/questions/164227/how-to-mount-an-iso-file](https://askubuntu.com/questions/164227/how-to-mount-an-iso-file)

---

### Post by ubfan1 on 2024-05-26
Yes the FAT limit on filesize is 4GB.  There are two big files under ...sources/ boot.wim and install.wim.  Only the install.wim is larger than 4GB, so should be split up with the wimsplit tool before copying to the FAT USB.

---

### Post by tea for one on 2024-05-26
Ventoy uses exfat and there is no 4GB filesize limitation.
[https://www.ventoy.net/en/doc_linux_gui.html](https://www.ventoy.net/en/doc_linux_gui.html)

---

### Post by angel mike on 2024-05-27
Thanks for all your contributions - I tried Ventoy but could not get the iso onto the usb. I'll have a closer look at wimtool and Ventroy

---

### Post by ubfan1 on 2024-05-27
Note that exfat is not a valid UEFI partition filessystem.  Legacy boots may use exfat (or even ntfs).

---

### Post by angel mike on 2024-05-27
I've tried to use Ventoy but cannot load Ventoy into the Device. Can someone give a link which explains every step in detail

---

### Post by tea for one on 2024-05-28
Navigate to [https://www.ventoy.net/en/index.html](https://www.ventoy.net/en/index.html)
Open Downloads tab
Click ventoy-1.0.98-linux.tar.gz
This will take you to the sourceforge page where the file is located.
Download ventoy-1.0.98-linux.gz to your Downloads folder
Open your Downloads folder
Decompress (double click) ventoy-1.0.98-linux.gz 
This provides a folder ventoy-1.0.98-linux
Insert your USB (suggestion 32GB)
Open the folder ventoy-1.0.98-linux and then open the subsequent folder ventoy-1.0.98
The installation executable is VentoyGUI.x86_64 
Double click VentoyGUI.x86_64 (this will install Ventoy to your USB)
Enter your user password
Open the options tab for more preferences
Click install when you have made your selections

After you have successfully installed Ventoy to your USB, you will see a Ventoy folder
Copy the Windows iso to the Ventoy folder

---

### Post by angel mike on 2024-05-28
Thanks for the detailed response - that looks straight forward.

---

### Post by angel mike on 2024-05-28
The Microsoft Windows iso comes with a 48 hr warning about validity - does this mean that the validation keys must be entered during this period?

---

### Post by gezzer2 on 2024-05-28
i believe that is for how long the download link is valid for ..

---

### Post by yancek on 2024-05-28
I think that is in reference to the actual download so if you don't download within 24 hours again, you apparently need to start over.  

[https://answers.microsoft.com/en-us/windows/forum/all/why-there-is-24-hours-limit-for-download-windows/a8b7d027-b4c9-4685-97da-4a55a72e1931](https://answers.microsoft.com/en-us/windows/forum/all/why-there-is-24-hours-limit-for-download-windows/a8b7d027-b4c9-4685-97da-4a55a72e1931)

More info on it.  As I understand, you need to buy a license if you do not have one as that information is not on the iso.

[https://www.reddit.com/r/windows/comments/1b9340t/why_does_microsoft_let_you_download_windows_isos/](https://www.reddit.com/r/windows/comments/1b9340t/why_does_microsoft_let_you_download_windows_isos/)

---

### Post by angel mike on 2024-05-28
Thanks yancek and gezzer2 for info and links - very useful.

---

### Post by ubfan1 on 2024-05-28
Oddly to my way of thinking, neither the install nor the running of Windows 10/11 requires a license.  Most machines these days come with a Microsoft digital license on the motherboard, so after an install, you may find that the system has actually been activated (all the license offers you).  Supposedly, after a trial period, the background turns blue with a reminder to activate, but all patches are available.  I forced a Win 11 install on two old underconfigured laptops, and both picked up the activation automatically from previous W10 activation. One I even upgraded to W11 pro with a win7 pro key off the bottom of a blown laptop (which never actually ran w7, it was immediately upgraded to W8.  I keep a W11 VM around,  never do much except apply patches, have never activated it, and never had it go blue background on me.  The cheap $30-$40 w11 pro licenses you see advertised are supposedly scraped off old machines, or from bulk OEM licenses, or just a total scam that you have difficulty canceling -- do you feel lucky?

---

### Post by angel mike on 2024-07-09
Thanks ubfan1 an interesting comment - will have to see when I get it usb working

---

### Post by angel mike on 2024-07-11
**tea for one** has given a detailed response on how to use Ventoy but I am stuck on knowing what 'options' I should be choosing.
Secure boot mode ?
Partition style MBR or GPT ?
Configurations - what should I be using ?

---

### Post by angel mike on 2024-07-12
I have managed to get ventoy installed on a usb but cannot copy the windows 10 iso to it

---

