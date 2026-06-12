---
title: "Compaq Prasario F756NR"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by ljoslin on 2008-06-25
I bought a new laptop, everything works fine under Vista.  I resized my Partition and install Ubuntu 8.04, everything seemed to go fine.  However on Reboot I don't have any network cards working, wired or wireless?!  The odd thing I have noticed is the light that indicates if the wireless card is on or off always shows off.  I remember a issue previously with my Desktop that windows was putting the card to sleep, and linux couldn't wake it up, could that be the issue again?  I can find lots of fixes for the wireless card, but with no network it's pretty hard to do any one them!  Any help would be great.  Thanks!

-=Ljoslin=-

network info :

Wired card

description: Ehternet interface
product: MCP67
vendor : nVidia Corporation
physical id : a
bus info : pci@0000:00:0a.0
version : a2
serial : 00:1e:68:15:39:44

Wireless

product AR242x 802.11abg Wireless PCI Express Adapter
vendor : Atheros Communications Inc.
physical id : 0
bus info : pci@0000:03:00.0
version : 01


hardware info :

AMD Turion 64 X2
2024 MB Ram
NVidia GEForce 7000m

---

### Post by avtolle on 2008-06-25
There are a number of threads on the Forum concerning configuring the Atheros card, and since the solution varies depending upon the card itself, all that you can do is search for one that works. FYI, most of the fixes do not affect the LED, so your card may well be "on", but the LED will show "off".

---

### Post by ljoslin on 2008-06-25
> **avtolle said:**
> There are a number of threads on the Forum concerning configuring the Atheros card, and since the solution varies depending upon the card itself, all that you can do is search for one that works. FYI, most of the fixes do not affect the LED, so your card may well be "on", but the LED will show "off".


I know I have seen several fixes for the wireless, but they all need the wired to work.  The wired I can't find anything on!

-=Ljoslin=-

---

### Post by avtolle on 2008-06-25
Misunderstood a bit what your problem is. I had the wireless problem, but not the wired problem, which I've not seen anything about.

---

### Post by Midwest-Linux on 2008-06-25
If you have another Ubuntu computer download the mad wifi for the Atheros 5007. tar xfz madwifi-ng-r2756+ar5007.tar.gz

 You find this at the mad wifi site.

/////////////////////////NOTE////////////////////////

 You might have to also download from Ubuntu 


sudo apt-get install build-essential



////////////////////////////////////////////////////////////

If you can drag the file to a thumb drive (formatted to ext 3) or a CD. Then install it on this computer by dragging the file from the thumb drive or cd. Here is the original script. 


////////////////////////////////////////////////////////////////

sudo apt-get install build-essential

wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

sudo make 

sudo make install

sudo modprobe ath_pci

sudo reboot

////////////////////////////////////////////////////////////////


 Since you downloaded the mad wifi driver through another means and now have it on the computer. Try modifying the script like this.
//////////////////////////////////////////////////////////////////

cd madwifi-ng-r2756+ar5007

sudo make 

sudo make install

sudo modprobe ath_pci

sudo reboot

/////////////////////////////////////////////////////////////////
 Reboot manually if sudo reboot doesn't work for some odd reason.

Or try downloading the Atheros 5007 mad wifi driver in Windows and see if you can drag over the driver to Ubuntu by accessing the Windows file in Ubuntu. (Puppy Linux can access NTFS files).

 Or use puppy Linux CD to access both the Windows and Ubuntu partitions and see if you can drag over the driver from Windows to Ubuntu that way.

 Or see if you can get on the internet with Puppy Linux, see if you can download both the 
sudo apt-get install build-essential and the driver directly to the Ubuntu desktop files or folder files using puppy to access the internet. 

 See if you can get on the internet using that Ubuntu live CD. Yes I know it sounds dumb but stranger things have happened...

Try reinstalling Ubuntu with the internet connected to the LAN.


If the mad wifi site is down, there is another site you can get the driver from. Forget where ...do a search.

Also, once you get it working. Watch out for those kernel updates. It killed my wireless and caused other issues. 

This might not help your wired connection though, maybe just wireless. BTW I have the Compaq FT 762NR with Vista and Ubuntu.

Good Luck

---

### Post by ljoslin on 2008-06-25
Well, I have good news and bad news, good news I did a fresh install and the wired is now working, however I found those instructions and the wireless is still down! :(  Any other ideas??

-=Ljoslin=-

---

### Post by avtolle on 2008-06-25
[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html) has been helpful to many, including me (I'm running the AMD 64 version). HTH.

EDIT: It has also been helpful to those running 32 bit as well, from reading other threads, just wanted to point out it worked for me as you might be running the AMD 64 version.

---

### Post by ljoslin on 2008-06-25
> **avtolle said:**
> [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html) has been helpful to many, including me (I'm running the AMD 64 version). HTH.

EDIT: It has also been helpful to those running 32 bit as well, from reading other threads, just wanted to point out it worked for me as you might be running the AMD 64 version.


Tried those instructions, and it failed....I am running a AMD 64 as well, but nothing!  This is getting really frustrating!

-=ljoslin=-

---

### Post by ljoslin on 2008-06-25
Well I fixed it!  Thanks for everyones help!!  I used this post!!

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)


similar to the last post but slightly different!

-=ljoslin=-

---

