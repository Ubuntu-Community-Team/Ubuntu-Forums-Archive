---
title: "Wireless on Hp pavillion DV600 not working"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by lotakoka on 2008-04-09
I have installed ubuntu 7.10 and i am unable to use wireless. I have following output from lspci .

02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connect

anil@sushma-laptop:~$ sudo /home/anil/ndiswrapper/ndiswrapper-1.43/utils/ndiswrapper -l
[sudo] password for anil:
netw4x32 : invalid driver!
netw4x64 : invalid driver!
anil@sushma-laptop:~$

What am i missing ?

---

### Post by Pumalite on 2008-04-09
You might want to take a look at this:
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

---

### Post by leolibra85 on 2008-04-09
Success making HP Pavilion DV6700 fully functional!!!
Okay, I have been over hundreds of threads in multiple forums and done WAY too many clean installs over the past three days, but now this laptop is up and running in 64 bits of glory!!! The only two things that didn't work for me straight out of the box were the video and the built in wireless card (the hardest part to fix).

Here's what I did for the wireless:
I can't figure out where I found this tutorial as I found it before my last clean install and saved it in an office file on my storage partition... If you know where this tutorial came from, please pm me so I can add accreditation.
So, first I did an absolute clean install. I hooked my LiveDrive and an ethernet cable to my laptop and went straight into the install (LiveDrives work only in Safe Graphics mode on these computers). Once it was finished and I got bored with my game of nibbles, I restarted my computer and logged in. I DID NOT install any updates or programs whatsoever. I think this may be the key. As soon as my desktop loaded, I opened the terminal and followed these instructions:

Quote:
1. Open your terminal

2. Get this version of madwifi:
Code:

wget -c [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

3. Untar the downloaded package:
Code:

tar xvf madwifi-ng-r2756+ar5007.tar.gz

4. Get inside the unpacked directory:
Code:

cd madwifi-ng-r2756+ar5007

5. If you haven’t compiled anything from source before on your linux then you propably need the build essential package:
Code:

sudo apt-get update && sudo aptitude install build-essential

//*NOTE: This will be necessary because you SHOULD NOT install ANYTHING before you follow these instructions.*//

6. Now you can build your madwifi and install the modules:
Code:

make
sudo make install
sudo modprobe ath_pci
sudo modprobe wlan_scan_sta

The last 2 commands can cause some complications on some systems. If they do check your System >> Administration >> Restricted Drivers Manager and disable atheros here. Then try again.

7. Now restart your computer and you should be able to see any available networks in your Network Manager.
I did end up having to disable the HAL in the Restricted Drivers Manager because it is enabled by default. You'll have to restart after you disable HAL, then just run the last two "sudo modprobe" commands again.

---

