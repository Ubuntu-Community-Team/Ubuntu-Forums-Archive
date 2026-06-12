---
title: "Boot Repair Utility and the Internet"
date: 2013-08-17
forum: Installation &amp; Upgrades
---

### Post by Connor_Mahaffey on 2013-08-17
So like a lot of people in these threads I got the awful surprise that my motherboard uses UEFI. The install went fine, using Ubuntu's built-in "install alongside" feature. I gave it 50GB and gave Windows 7 the rest (450GB). Right now it just completely ignores the Ubuntu 13.04 partition and boots straight into Windows 7. 

Here's what UEFI for my MB looks like: [http://www.techspot.com/articles-info/521/images/Asrock/UEFI_01.jpg](http://www.techspot.com/articles-info/521/images/Asrock/UEFI_01.jpg)


Obviously I'd like to have the GRUB menu to switch between the two. Some looking around led me to the Boot-Repair-Tool, which I burned on a CD.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I booted it up fine and ran just the diagnostic, which you can find here:
[https://www.dropbox.com/s/q6xl027pveq28bs/Boot-Info_2013-08-17__09h31.txt](https://www.dropbox.com/s/q6xl027pveq28bs/Boot-Info_2013-08-17__09h31.txt)


Unfortunately, I do not have an internet connection. The cheap usb wifi hotspot I use is very weak and our router is very far away; it can't reach. In a live environment I can't install the drivers that might help it on linux. Whenever I go to start the utility, it warns me that doing so will leave me in an unbootable state without internet.

Does anyone know if that's the truth? Does it really not come with the necessary software to fix the issue or is it simply complaining because it won't be able to give me the diagnostic link at the end?


Of course everything is backed up on this system, but ideally, I'd like to not have to re-download and reinstall like 300GB of stuff, ya know? I'd also like to avoid moving the massive gaming PC to the living room.

EDIT: wifi USB is an ASUS N10

---

### Post by oldfred on 2013-08-17
Boot-Repair wants Internet as a lot of its functions need to download the most current packages from the repository to make sure your system works correctly.

You have UEFI, but have both Windows & Ubuntu installed in BIOS/CSM/Legacy mode or whatever your system calls it.

You do not want Boot-Repair to purge as that deletes grub, but you probably just need to install grub to the MBR.
You can change default/auto by unchecking auto, but check fix MBR. Then under advanced boot options choose to reinstall grub to MBR.

If you cannot get Boot-Repair to do that, you can just use live flash drive to install grub to MBR (the way we did before Boot-Repair automated everything).

       #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by Connor_Mahaffey on 2013-08-17
Thanks for such a well written response. Dragging the computer out to the living room won't be much fun, but it is what it is.


Before I mark it as solved (hopefully all goes well!) will letting Boot-Repair do it's automatic mode actually 'break' the computer, or just take more time to complete?


Nice link in the description as well. That one doesn't show up on Google oddly enough.

---

### Post by oldfred on 2013-08-17
If you have not done other updates, it may take a bit as when Boot-Repair runs it is just running a Ubuntu update so other apps with updates may also download. If system is current then it really is just wanting to uninstall grub2 completely and totally reinstall it from a fresh download. But while un-installed you cannot reboot and have a working system. There are ways to reinstall just the installed version by setting update to run from installer DVD or Flash drive, but those would not be the most current versions. But often a new install is quicker or maybe just easier to explain?

I do not know wi-fi issues, but there are a lot of threads by chip type. Often the live installer does not have every driver for wi-fi, so a wired Ethernet install works better as then it can download the correct wi-fi driver. Some have to download separately to another system, then copy and manually install.

---

### Post by Connor_Mahaffey on 2013-08-18
Well, I ran your commands and they worked great! No internet needed :D


Seems like I got wifi to work now too, as I'm typing this from Ubuntu. Thanks for your responses!

---

### Post by oldfred on 2013-08-18
Glad you got it working. :)

---

