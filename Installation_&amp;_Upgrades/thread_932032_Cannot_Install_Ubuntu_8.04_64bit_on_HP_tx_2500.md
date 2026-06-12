---
title: "Cannot Install Ubuntu 8.04 64bit on HP tx 2500"
date: 2008-09-27
forum: Installation &amp; Upgrades
---

### Post by lifemaximum on 2008-09-27
Hi all,

I am trying to install the Ubuntu 8.04 64 Bit on my new laptop HP tx 2500.


when I choose Load from Live CD and install , it will show the loading bar filling in and all , but after that it starts filling out and than says remove the CD and press Enter to reboot, and this keeps happening every time, so I can not load it and install through live.

First time I put the DVD in it gave some sort of error , but I missed it so I don't know what it was , but now that error doesn't show anymore:mad:.

BTW is there any wiki on how to install drivers and stuff for HP TX 2000 laptops, and getting the touch screen stuff and tablet functions enabled in ubuntu?

would appreciate your help?

---

### Post by hurryup on 2008-10-27
Hi,

i´ve got the same problem with my hp pavilion tx 2550eg. When I activate the log files, it displays "reached critical temperature (67C)"
But I'm not sure if it is realy a temperature problem, because the fan turns not very fast. 

Did you solve your problem, yet?

---

### Post by lifemaximum on 2008-10-27
well i have been looking for solutions for a while now, this is what i got from another forum might help you out.

it seems hp tx 2000 models don't play well with ubuntu ,i guess we should hope for future versions if ubuntu to support it.
:(:(

HP Pavilion tx2000 Hardware solutions !!! 
I have been using Ubuntu for 2 years and I have installed it in many laptops and desktops including: HP, IBM, Dell, Acer, Toshiba & many assembled PC's

I have never find problems with drivers as much as what I had with the HP Pavilion tx2000

OS: Ubuntu Hardy (8.04) AMD64


I wanted to tell people how I managed to get through all of them (YES ALL)

1.VGA
Problem: Not Working Perfectly (Driver Problem)
Solution:Go to synaptic and install the "nvidia-glx-new" package. It will work fine after you restart the laptop.

2-Audio:
Problem: Not Working (LED indicate that it is mute)
Solution: in Terminal write the code
PHP Code:
sudo gedit /etc/modprobe.d/alsa-base  
Write at the end of the file in new line:
PHP Code:
options snd-hda-intel model=hp  
Save the file and the sound will work after reboot

3.Lightscribe:
Problem: Not Working (Need Driver and Application)
Solution: Download the following packages and install them:
Driver: lightscribe-1.12.37.1-linux-2.6-intel.deb
Software: lightscribeApplications-1.10.19.1-linux-2.6-intel.deb
Additional Links:
Template Label Gallery
Label Gallery


4.Fingerprint:
Problem: Not Working (Detected but does not work when you log in)
Solution: You need three packages & since one or two of them are not available in Synaptic you can get them here: [http://legacy.madman2k.net/comments/105](http://legacy.madman2k.net/comments/105)
The packages are: libfprint, pam_fprint and fprint_demo.
Then Write in the Terminal:
PHP Code:
tar -xjf libfprint-0.0.4.tar.bz2 
cd libfprint-0.0.4 
./configure --prefix=/usr 
make 
sudo make install  
and repeat it again for pam_fprint and fprint_demo.

5-Wireless:
Problem: Detected but not working at all
Solution:
A.install ndiswrapper packages:
PHP Code:
sudo apt-get install ndiswrapper-utils 
sudo apt-get install ndiswrapper-common  
B.Download this driver
C.Open the Terminal and write:
PHP Code:
sudo cabextract SP34152.exe 
sudo ndiswrapper -i bcmwl5.inf 
sudo ndiswrapper -m 
sudo depmod -a 
sudo modprobe ndiswrapper 
sudo gedit /etc/modules  
Write at end of that file: "ndiswrapper" and It should be working without reboot


6.WACON "Touch Screen"
This is very new & I worked very hard to find it BUT after finding it and fighting to install it I found that neko18 wrote a new Thread all about it and it was the first topic in front if me when I came to post mine.
Link: [http://ubuntuforums.org/showthread.php?t=765915](http://ubuntuforums.org/showthread.php?t=765915)
"Thanks & I wish I have found your topic an hour ago."

7.Monitor Rotation:
Problem: Not working
Solution:I need more time to check it fully
I Found this helpful link: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

Thank you

---

### Post by lifemaximum on 2008-10-27
you might want to also take a look at **Wubi** for windows.

Wubi is an officially supported Ubuntu installer for Windows users that can bring you to the Linux world with a single click. Wubi allows you to install and uninstall Ubuntu as any other Windows application, in a simple and safe way. No need to burn a CD, just run the installer, enter a password for the new account, and click "Install". Wubi will download and prepare the required files, and ask you to reboot in order to complete the installation. You keep Windows as it is, Wubi only adds an extra option to boot into Ubuntu.

Wubi does not require you to modify the partitions of your PC, or to use a different bootloader, and does not install special drivers. Wubi keeps most of the files in one folder, and if you do not like it, you can simply uninstall it as any other application. Version 8.04.1 includes unspecified updates.

link :[http://www.download.com/Wubi/3000-2094_4-10701841.html?tag=contentMain;contentBody&cdlPid=10861938](http://www.download.com/Wubi/3000-2094_4-10701841.html?tag=contentMain;contentBody&cdlPid=10861938)

---

### Post by gali98 on 2008-10-28
Okay a great guide for the tx2500 is here:
[http://ubuntuforums.org/showthread.php?t=873188](http://ubuntuforums.org/showthread.php?t=873188)
But if you wait two days and install Intrepid, it will be much better. It fixes all the thermal issues and the wireless should work out of box :)
Kory

---

### Post by lifemaximum on 2008-10-29
thanks

I guess i am going to wait than...
That is great they are going to fix the wifi.

---

