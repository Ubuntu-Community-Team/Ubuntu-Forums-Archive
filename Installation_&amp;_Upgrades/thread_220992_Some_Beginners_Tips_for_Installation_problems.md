---
title: "Some Beginners Tips for Installation problems"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by dimeotane on 2006-07-22
These tips are mostly for regular humans and not your veteran linux nerds.

Overview for first timers:
  This is my third or fourth Ubuntu install... still lots to learn, but it does get easier. Don't bother making a comparison to Windows being 'easier'.  After you've tried to exterminate a infestation of 150 viruses, trojans and rootkits every year on each of your Windows XP boxes, learning Ubuntu is *easy as pie*.  
  Its normal for the average person to dislike entering terminal commands, because they're gibberish and scary.  Don't worry; day to day for basic computing needs you won't need to use the terminal, just problem solving during setup. But remember that with a copy and paste of a single text command in the terminal, you're often able to do a task that would normally (in the graphical Windows interface) take much longer to do finding menus and checkboxes, wading through confusing control panels. Eventually you might find yourself doing a whole backup of your harddrive with a copy and paste of one command! 

Problem solving to get *everything* working perfectly can take several hours. You could have a decent OS with web and word proccessing in an hour. 

Major tip: I don't think problem solving an install can be done without another working PC with net access to the forums however!  Keep this in mind if you're installing to a PC with a wireless connection.  


Machine Specs:
I installed Ubuntu Drake 6.06.  Everything appears to work now after a few hours. The computer is a four year old Emachine H2602 AMD Athlon Nvidia GeForce 4mx destop.  The display is some crappy  'Visual Sensations' KDS monitor. The printer is an HP Laserjet 1020.  The wireless is a "SMCWUSBT 108Mbps Wireless USB 2.0 Adapter"


Juicy Beginner Tips:

Here's some of the install problems and how they were solved:

Problem 1:  after putting in the CD and running the default option, the graphical boot up sequence gets as far as starting X... a little white cursor flashes in the upper left and then the monitor makes a click sound (like it does when changing resolutions) then the power light changes from green to red and the whole display is black.  

Solution 1: don't despair, try this tip first, as Ubuntu may still be running fine! Press ALT+CTRL+ +key to switch resolutions, press it until you find one which fits your monitor.  You should see the brown Ubuntu desktop and menu bars on top and bottom.  To avoid having to do this everytime your machine boots, after installation, you'll need to edit your X settings for your monitor. Backup your xorg.conf first before editing.
in the Applications-->accessories-->Terminal window copy, paste and enter each command (skip the $):
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
$ sudo nano /etc/X11/xorg.conf
find 'Section "Screen"' delete the modes that your monitor can't handle. All I have left now for this POS is "1024x768" "800x600" "640x480" under each of the sections for monitor depths.



Problem 2: After installing Ubuntu onto some free space on my hard drive and rebooting I found I have no sound and no USB is detected.  My USB flash disk, USB mouse, and USB wireless card all don't work and can't be seen under System-->Administration-->device manager.  Or in the terminal 
$ lsusb  ( nothing happens)

Solution 2:  in the terminal:
$ sudo cp boot/grub/menu.lst /boot/grub/menu.lst-backup
$ sudo nano /boot/grub/menu.lst

look for this towards the bottom: 
  ## ## End Default Options ##
  kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash live acpi=off noapic nolapic
delete this "acpi=off noapic nolapic" (or comment it out by moving it to a new line and adding ## in front). 

Perhaps some linux veterans can comment further about which of these were probably causing the problem, and which commands should perhaps stay.  Also, when I installed the updates, Ubuntu rewrote the GRUB menu.lst file so the problem returned until I removed these commands.  


Problem 3:  My USB wireless did not automatically work when I ran the web browser =( it can't access any web pages.

Solution 3: I was happy to discover that ndiswrapper actually works on a USB wireless card, (and regardless of what USB port I've put it into.)

Find the CD that came with the USB wireless adaptor.  There should be a drivers folder on the CD  (You could also wade through your windows program files to find the drivers)   

Copy the drivers folder into your Ubuntu home directory.  I needed athfmwdl.inf and net5523.inf for this USB wireless adaptor. 

Put in your Ubuntu CD. In the terminal enter:
$ sudo apt-get install ndiswrapper-utils

Or you could also use your mouse and the GUI to wade through windows. Go to System--->Administration-->Synaptic package manager, type in your admin password.
Settings-->Repositories click on Add CDrom. Click search and look for ndiswrapper.   right click on ndiswrapper-utils and mark for installation. Click apply. Still think the terminal is too complicated?



Open a terminal window 
$ cd drivers  
(or whatever you called your wifi drivers folder)
 
$ sudo ndiswrapper -i net5523.inf
$ sudo ndiswrapper -i athfmwdl.inf
$ sudo ndiswrapper -m
$ sudo modprobe ndiswrapper
$ sudo ndiswrapper -l 

( your terminal should show)
Installed ndis drivers:
athfmwdl                driver present
net5523         driver present, hardware present

Now reboot your machine. go to System-->Administration-->Networking
you should see "wireless connection" Click on properties. enter the ESSID of your wifi connection.
Enable this connection should be checked.  Enter your WEP key.  Choose Plain (ASCII) unless your key is in hex.  OK and Activate.  Load a page in your browser. 


If it doesn't work, check to see if the card is recognized. In the terminal enter:
$ iwconfig wlan0

(if it's working you should see something like this:)

wlan0     IEEE 802.11g  ESSID:"MyRouter"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 0C:0C:E5:55:16:1E
          Bit Rate:54 Mb/s
          Power Management min timeout:0us  mode:All packets received
          Link Quality:0/100  Signal level:-59 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Continue problem solving with these threads in the forums: 


Wireless problems: 
[http://www.ubuntuforums.org/showthread.php?t=218918&highlight=wireless](http://www.ubuntuforums.org/showthread.php?t=218918&highlight=wireless)
[http://www.ubuntuforums.org/showthread.php?t=211820&highlight=ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=211820&highlight=ndiswrapper)

Huge Broadcom guide: 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

WEP support:
[http://www.ubuntuforums.org/showthread.php?t=220297&highlight=wireless](http://www.ubuntuforums.org/showthread.php?t=220297&highlight=wireless)

WPA support
[http://www.ubuntuforums.org/showthread.php?t=220299&highlight=wireless](http://www.ubuntuforums.org/showthread.php?t=220299&highlight=wireless)

Broadcom 4306 & ndiswrapper tips
[http://www.ubuntuforums.org/showthread.php?t=201902&highlight=wireless](http://www.ubuntuforums.org/showthread.php?t=201902&highlight=wireless)
Broadcom 4318 & more hacking wireless tips
[http://www.ubuntuforums.org/showthread.php?t=197102&highlight=wireles](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=wireles)

Problem 4: My HP laserjet 1020 / HP laserjet 1018 / HP laserjet 1005 / and HP laserjet 1000 doesn't work.  It's automatically detected, but when I send a file to print, nothing happens. 

Solution 4: 
I've also posted this in the hardware printers forum: [http://www.ubuntuforums.org/showthread.php?t=220766](http://www.ubuntuforums.org/showthread.php?t=220766) 

Your Laserjet 1020 doesn't appear to work in Drake 6.06 even with the latest updates installed as of today (July 22 '06). It is detected but when you send a file to be printed nothing actually is printed.

This solution probably also applies to the HP laserjet 1018, HP laserjet 1005, and HP laserjet 1000. I'm just guessing.



Here's how you can get it to work:

1) Install build-essential files FIRST:
$ sudo apt-get install build-essential

2) go to [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) and follow the "Download and Install" instructions there: I've copied them here:
$ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
$ tar zxf foo2zjs.tar.gz
$ cd foo2zjs
$ make
$ ./getweb 1020
$ sudo make install
$ sudo make install-hotplug
$ sudo make cups
$ sudo gnome-cups-manager (or use mouse: System-->Administration-->Printing)

create printer entries:

follow the instructions here:
[http://foo2zjs.rkkda.com/ubuntu/hp1020.html](http://foo2zjs.rkkda.com/ubuntu/hp1020.html)

Unplug and replug your printer. lights should flash. Try printing a test page now, and it should work.


More instructions here:
[http://foo2zjs.rkkda.com/INSTALL](http://foo2zjs.rkkda.com/INSTALL)

This issue is discussed in these other threads:
[http://www.ubuntuforums.org/showthre...=laserjet+1020](http://www.ubuntuforums.org/showthre...=laserjet+1020)
[http://www.ubuntuforums.org/showthre...=laserjet+1020](http://www.ubuntuforums.org/showthre...=laserjet+1020)
[http://www.ubuntuforums.org/showthre...=laserjet+1020](http://www.ubuntuforums.org/showthre...=laserjet+1020)
[http://www.ubuntuforums.org/showthre...aserjet+](http://www.ubuntuforums.org/showthre...aserjet+) 1020

---

