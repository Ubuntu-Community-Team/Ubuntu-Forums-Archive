---
title: "Need help with Acer 5610Z and BCM4318 wireless."
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by r8dr4life on 2008-01-30
Ok, I am a newbie and I just installed Ubuntu on a USB HDD. Problem is, my wireless won't work. I have blacklisted my BCM4318 and I have installed NDISwrapper and I still can't get a signal with wifi-radar. I have followed the instructions in other posts to get my card to install and it says that it is installed, but still no signal and no connection without a LAN cable. Can somebody please help me out with this. I will also probably need some good instructions because I am a newbie and I am still trying to figure out how to work with the terminal. I really don't want to have to buy a card and plug it into my laptop, I prefer my built in one. Please help. 

Thanks in advance.

---

### Post by sean42 on 2008-02-06
probably not the answer you want, but, I have an acer extensa 4620z that had the broadcomm chipset  wifi mini pci card in it and I was never able to resolve the busted wifi.  Some people have had sucess using the restricted drivers, but this was not the case for me.  I ended up replacing my wifi card with one that has better compatibility with linux.  I purchased the card on ebay for about 13 bucks and it took about 10 minutes to install.  might be worth it considering I spent a good 15 hours of my time to fix the wifi with no sucess before I changed out the card.

[http://search.ebay.com/search/search.dll?from=R40&_trksid=m37&satitle=3945ABG+mini+pci&category0=]("http://search.ebay.com/search/search.dll?from=R40&_trksid=m37&satitle=3945ABG+mini+pci&category0=")

good luck.

---

### Post by nirvash78 on 2008-02-11
I also have an Acer 5610z with BCM4318 wireless.  
This is tutorial I used for mine. [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29")
Don't worry about there not being a /etc/iftab file, I didn't have one.  I followed steps 1 through 5.  Then open a terminal and type iwconfig.  If the driver is working it will list either wlan0 or eth1.  If it does type into the terminal sudo ndiswrapper -m.  I should say "alias wlan0 ndiswrapper.  Then type 
gksudo gedit /etc/modules in the terminal.  In this file type ndiswrapper and save.  the built-in network manager should show a wireless connection

---

