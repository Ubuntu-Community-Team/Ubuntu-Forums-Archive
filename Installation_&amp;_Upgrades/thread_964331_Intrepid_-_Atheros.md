---
title: "Intrepid - Atheros"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Abdul Haqq on 2008-10-30
Before I do a new installation I would like some feedback on those using Atheros WiFi Cards AR5K (eg AR5007ED). I would like to know:

1. Is the latest MadWiFi drivers in included in 8.10?
2. Does WEP work.

Any other issues with this card in 8.10? Finally has anyone installed Intrepid on an Asus X50RL Laptop.

I cannot easily D/L and some expense and time needed to get a copy. Debian 'Lenny' works fine and I may have to go back but I do like Ubuntu.

Thanks

---

### Post by lemming465 on 2008-10-31
I'd stick to Debian for now.  On my Toshiba Satellite laptop the particular atheros chip still isn't supported in the 2.6.27 kernel, and while 8.04 with ndiswrapper could do WPA2-PSK, 8.10 is having a glitch between the wpa_supplicant and the ndiswrapper and doesn't.

---

### Post by Abdul Haqq on 2008-11-01
Thanks for the reply. I did install 8.10 and after hours regretted it. On my laptop it is as unstable as.. I dare not try it on the desktop which is running 7.10

I just ask myself why??

---

### Post by Rbchound on 2008-11-01
I upgraded last evening and have Atheros 5007EG.  I used Madwifi also and installed with no problems.

1: First off be sure the build-essential package is installed
Code:

sudo apt-get install build-essential

2: You will need the linux-restricted-modules package installed to be able to compile the driver
Code:

sudo apt-get install linux-restricted-modules-$(uname -r)

3: Also install subversion
Code:

sudo apt-get install subversion

NOTE:If you have been using ndiswrapper like I was you need to disable/remove it

I recommend doing what I did and run the first command in section 4 before removing ndiswrapper that way you can avoid hooking up to a wired network if your wireless is functional using ndiswrapper
Code:

sudo ndiswrapper -e net5211
sudo modprobe -r ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils ndisgtk

Also run
Code:

gksudo gedit /etc/modprobe.d/blacklist

Remove any references to ath_pci and ath_hal

* Before the next steps go to System ->Administration ->Hardware Drivers and make sure Atheros wireless driver is disabled and reboot the system if it was not.

4: Get the files and install the driver
Code:

svn co [https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6](https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6)
cd ~/madwifi-hal-0.10.5.6
make
sudo make install
sudo depmod -ae
sudo modprobe ath_pci
echo ath_hal | sudo tee -a /etc/modules
echo ath_pci | sudo tee -a /etc/modules

5: Finally go to System ->Administration ->Hardware Drivers and reenable the Atheros wireless driver and reboot the system.

Reboot and I am up and running again.
Hopefully this makes your day like it did mine!

You need to have the linux-restricted-modules package installed,in your case the real time ones.

Code:

sudo apt-get install linux-restricted-modules-rt

If you already have the Madwifi folder with the files.  Got to that folder, open terminal there, and do this:

make
sudo make install
sudo depmod -ae
sudo modprobe ath_pci
echo ath_hal | sudo tee -a /etc/modules
echo ath_pci | sudo tee -a /etc/modules

This is what I did.

Hope this helps

---

### Post by KaSKAraS on 2008-11-01
Thanks. After applying your instructios it worked very well after reboot.

I hope ubuntu guys take note from this post and update the system accordingly.

Very useful.

Regards,
Tomás

---

### Post by Abdul Haqq on 2008-11-01
All mine were clean installs. I never 'ubgrade' any OS.

I did all this except for the subversion code. The install is exactly the same on Debian.

The driver actually worked on 8.04 and found the AP but would not accept the WEP Key. 

I dought I can try it again for a long time. I have to actually do work on my computer and bringing it down again is not an option. BTW love Debian it is so solid.

---

### Post by sammiam on 2009-04-24
I have an Atheros AR928X with 8.10 installed.  The wireless is very unstable, it will run for hours, and then just stop working.  I am able to get it back up by doing a rmmod -f ath9k, and then doing a modprobe ath9k.  I've done some googling and have found many saying that they use madwifi and have no problems, I guess I'll give it a try...

My System:

HP Pavilion dv7-1267cl 
4GB memory
2.20 GHz AMD Turion X2 RM-74 Dual-Core Mobile Processor
ATI Radeon HD 3200 Graphics RS780M
Atheros AR9828X wireless

---

### Post by Robster2 on 2009-04-24
> **sammiam said:**
> I have an Atheros AR928X with 8.10 installed.  The wireless is very unstable, it will run for hours, and then just stop working.  I am able to get it back up by doing a rmmod -f ath9k, and then doing a modprobe ath9k.  I've done some googling and have found many saying that they use madwifi and have no problems, I guess I'll give it a try...

My System:

HP Pavilion dv7-1267cl 
4GB memory
2.20 GHz AMD Turion X2 RM-74 Dual-Core Mobile Processor
ATI Radeon HD 3200 Graphics RS780M
Atheros AR9828X wireless


Same problems with Wifi unstable on Toshiba AMD Turion X2 4GB memory

9.04 64bit fixes all problems and is a lot faster.

Automatic detection of Hardware.  Upgrade now!


:lolflag:

---

