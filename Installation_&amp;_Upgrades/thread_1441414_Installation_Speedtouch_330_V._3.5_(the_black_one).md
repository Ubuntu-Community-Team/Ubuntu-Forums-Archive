---
title: "Installation Speedtouch 330 V. 3.5 (the black one) USB on Ubuntu 9.10 Karmic Koala"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by beyercj on 2010-03-28
This is how I installed Speedtouch 330 V. 3.5 (the black one) USB on Ubuntu 9.10 Karmic Koala on a [Gericom Frontman]("http://download.gericom.com/LCD-PC/Frontman-L19IN0/DATASHEET/L19.pdf") Computer  (please read my comments below):

Go to a computer or another operating system with internet access. 

Visit Ubuntu Packages Search <http://packages.ubuntu.com/> and search 
for each of the following packages. Download them to a folder that is 
also visible from Ubuntu (or to a USB stick). 

   1. python-gtkmozembed 

            for 32 bit 
            [http://packages.ubuntu.com/karmic/i386/python-gtkmozembed/download](http://packages.ubuntu.com/karmic/i386/python-gtkmozembed/download) 
            
   2. python-eggtrayicon

            for 32 bit 
            [http://packages.ubuntu.com/karmic/i386/python-eggtrayicon/download](http://packages.ubuntu.com/karmic/i386/python-eggtrayicon/download) 
            for 64 bit 
            [http://packages.ubuntu.com/karmic/amd64/python-eggtrayicon/download](http://packages.ubuntu.com/karmic/amd64/python-eggtrayicon/download) 


   3. python-gtkspell  

            for 32 bit 
            [http://packages.ubuntu.com/karmic/i386/python-gtkspell/download](http://packages.ubuntu.com/karmic/i386/python-gtkspell/download) 
            for 64 bit 
            [http://packages.ubuntu.com/karmic/amd64/python-gtkspell/download](http://packages.ubuntu.com/karmic/amd64/python-gtkspell/download) 


   4. python-gksu2 
   5. libgdl-1-common 
   6. libgdl-1-3 
   7. python-gdl 
   8. libgda-4.0-common 
   9. libgda-4.0-4 
  10. python2.5-minimal 
  11. libdb4.6 
  12. python2.5 
  13. python-gda 
  14. python-gnome2-extras 



Now download USB ADSL Modem Manager 
[http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/usbadslmodemmanager_0.5.8_i386.deb](http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/usbadslmodemmanager_0.5.8_i386.deb)
and install it.
 
Get firmware-extractor.tar.gz and follow these instructions:

SpeedTouch Firmware Extractor is a small application to prepare and install the firmware for a SpeedTouch USB modem so that a 2.6.10 kernel (or later) can load the firmware without the assistance of modem_run. In order for it to work you will need to have the hotplug scripts installed and have hotplug firmware loading enabled in your 
kernel. 
Put a copy of the firmware for your modem in this folder and rename it mgmt.o 
To find out what version (revision) of the SpeedTouch you have, use the command 

cat /proc/bus/usb/devices* | grep -B 1 ALCATEL 
cat /proc/bus/usb/devices* | grep -B 1 THOMSON 

At the end of the first line it should say Rev=X.00 
X is the version of the modem you have. 
If you have a revision 0 or revision 2 SpeedTouch copy the KQD6_3.012 file into this folder 
and rename it mgmt.o, if you have a revision four modem, use the ZZZL_3.012 file 
instead. 
If you have a revision 0 modem you could also use the mgmt.o file from this tarball 

Now use the traditional commands 

./configure 
make 

Then su to become root and install the firmware with the command 

make install 

The kernel should load the firmware in the background during the boot process. 
You then need to configure and run pppd. Good luck!

After installation, to access the USB ADSL Modem Manager, go to 
Applications...Internet...USB ADSL Modem Manager. 

When first run, it will ask for the settings of your connection: 
Username, Password, VP and VC (in the UK VP is 0 and VC is 38)

To connect, right click the tray icon with your mouse and choose 
*Connect* from the context menu.  

I spent hours to work this out. [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch) Method 1 did not work for me. Luckily, I found the following threads: [http://ubuntuforums.org/printthread.php?t=796697&pp=10&page=2](http://ubuntuforums.org/printthread.php?t=796697&pp=10&page=2) and [http://ubuntuforums.org/showpost.php?p=4813601&postcount=114](http://ubuntuforums.org/showpost.php?p=4813601&postcount=114). I had to download ADSL Modem Manager version 0.5.8_i386.deb, the others did not work for me.

Hope it helps you, too.

Joerg

---

### Post by bidefordjon on 2010-05-09
TOTAL NEWBIE ALERT!!

I've just loaded 9.10 on my old Tiny PC as I'd heard so much about it and a friend recommended.  My main bit of kit is an iMac G5 so the Ubuntu installation is just for fun so to speak.

The unit I've installed it on has no network card and no wireless card so I only have the Speedtouch 330 (silver) to use.

What you have described above seems WAY above my knowledge as I don't even know what half of it means let alone how to go about doing it.  

Is that really the only way of getting internet access through my Speedtouch without getting a wireless card?

---

### Post by nigsy on 2010-05-10
See my reply on facebook.
Think VM server is the way to go with the MAC!!

---

### Post by bidefordjon on 2010-05-11
I'll read it again in a few days and see if it makes sense.  (Don't hold your breath)

I have no idea how to run the files I have to download or enter the programming lines.  I'm not a techie/programming kind of guy.

I don't want to put it on the Mac as I want to make use of a currently redundant PC with Windows ME on it.  The Mac is fantastic as it is.

Re: the Facebook post,  if I get a network card and give up on the Speedtouch modem will it plug and play or will it need file downloads and scripts in the same way as the Speedtouch, albeit differently?

---

### Post by beyercj on 2010-06-01
I think unfortunately yes. I tried another method copying and pasting a bootscript etc because I was of the same opinion as you and it did not work. Downloading and installing is not that hard after all.

---

