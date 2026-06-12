---
title: "Installed Gutsy on HP dv9500z on USB Drive"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by ZachGardner on 2008-02-25
The best info I could find on installing Ubuntu on a USB Drive was for Breezy (5.10). A few things have changed, and a few things could have been more explicitly outlined. (The majority of this is for installing onto a USB Drive and is not dv9500z-specific.)


*Preliminary info for dv9500z users: I had some problems getting into the command prompt. After booting, the screen would flash three times and then it would alert me that it couldn't find a video driver for my monitor. I chose a generic 1600x1400, 1280x900 screen size, and then "Test." On the first attempt, it doesn't display the screen correctly. Try it again and it should work. Once it gets out of that, you might not have a command prompt. (It isn't automatically configured to work with the Broadcom wireless adaptor.) If the command prompt doesn't show up, do CTRL+ALT+F1. "startx" will start an x server.*


1) Use Live CD to do installation. Choose your USB Drive as the one for the partitioning to take place. Note where the device is located because you'll need it in a later stage. (Mine was /dev/sdc.)
*NOTE: You can manually partition the device if you don't plan on having Ubuntu being the only OS on that disk since the partitioner will overwrite the existing partitions.*

2) Continue using the installer until you get to the stage right before the installation. Click on "Advanced" to get into the grub part of the installer. As is, it will say to load grub to (hd0). Change that to whatever the location of your USB device was. (Mine was /dev/sdc.)
*NOTE: This will load grub to your USB drive. I did it this way since I use Vista on my laptop's hard drive. You don't necessarily have to do it this way, but I think that it is the easiest.*

3) The installer will finish and ask if you want to continue using the Live CD or Reboot. Choose to Reboot. Remove the CD when it pops out and boot into your USB Drive.

4) It should boot into grub if everything worked out. Press "c" to enter into the command prompt. Enter "geometry (hd" and then tab to display the hard drives. Enter in the number of the hard drive that you want to test and put in closing parenthesis. You are looking for your USB Drive, which will have a ext3 (or ext2, I can't remember) partition and a swap partition. Once you find it, write it down and reboot into your Live CD.

5) Once your Live CD finishes booting, navigate to where your USB Drive was mounted. (Mine was /media/disk/.) Do the command "vim boot/grub/menu.lst" to open up the menu in vim. Go to almost the end of the file where it lists the operating systems. Change the value in root for Ubuntu based on the hard drive number that you got using geometry in grub. Write and exit out of that file. Open up device.map in the same folder. Change the order of the hard drives based on the grub geometry. (Grub saw my USB Drive as the first hard drive, so I changed (hd0) to be /dev/sdc; it saw my internal hard drive as the second hard drive, so I changed (hd1) to be /dev/sda.) Save and close the file.
*NOTE: To insert text, press "insert;" to exit out of editing mode, press "ESC;" to write the file and close, exit out of editing mode and type "wq."*

6) Reboot into your USB Drive. Select Ubuntu.
*NOTE: If it gives an Error 17 in grub, then something went wrong in your identification of the order of the drives. Go back into grub and check menu.lst and device.map.*

If it boots, you've done everything correctly. Now, onto the dv9500z-specific instructions.

Installing the Wireless driver
*NOTE: This is just a copy and paste of code I found on the second link provided. Also, you need to have your Live CD in the CD drive and be connected to the internet using your ethernet card.*
1) sudo -s
cd (the directory of where your USB Drive is mounted. Mine was /media/disk/)
chroot
*NOTE: This will switch you into the root account.*

2) apt-get remove ndiswrapper-common
ndiswrapper-utils-1.9
sudo apt-get remove bcm43xx-fwcutter
*NOTE: These might tell you that they aren't installed. If it does, don't worry about it.*

3) vim /etc/modprobe.d/blacklist
Add "blacklist bcm43xx" to the bottom of the file.

4) Download the file [http://rapidshare.com/files/70969505/WLANBroadcom.tar.gz.html](http://rapidshare.com/files/70969505/WLANBroadcom.tar.gz.html) and put it on your desktop.

5) apt-get update
apt-get install build-essential
apt-get install linux-headers-`uname -r`
ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
mkdir -p ~/bcm43xx/ndiswrapper
cd ~/bcm43xx/ndiswrapper
wget [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz)
tar xvzf ndiswrapper-1.49.tar.gz
cd ndiswrapper [TAB]
make distclean
make
make install 

6) cd /home/yourname/WLANBroadcom/
ndiswrapper -i bcmwl5.inf
ndiswrapper -l
vim /etc/modules
Add "diswrapper" to the file

7) modprobe ndiswrapper
ndiswrapper -m

8) Reboot. When it boots all the way back up, the blue light for the wireless card should be on. Encryption automatically works, which is pretty cool.

Installing the Graphics Driver
1) System -> Administration -> Software Sources. Enable "Proprietary drivers for devices."

2) Go into terminal. Do "sudo apt-get install nvidia-glx-new."

3) System -> Administration -> Restricted Drivers Manager. Enable the driver.

4) System -> Administration -> Screens and Graphics. Select 1680x1050 widescreen for the display. I set my resolution to 1280x800.


Sources:
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)
[http://ubuntuforums.org/archive/index.php/t-625303.html](http://ubuntuforums.org/archive/index.php/t-625303.html)

---

