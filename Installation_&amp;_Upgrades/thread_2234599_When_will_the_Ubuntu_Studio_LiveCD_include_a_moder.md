---
title: "When will the Ubuntu Studio LiveCD include a modern (updated) Wine?"
date: 2014-07-15
forum: Installation &amp; Upgrades
---

### Post by Nistegmos on 2014-07-15
Hello, I am wondering when the Ubuntu Studio LiveCD (DVD boot/install disc) will include an updated version of wine?  
Right now I'm using Ubuntu Studio v14.04 LTS and it only comes with Wine v162 even though Wine development is currently beyond v1.7.  

A developer told me that Wine v1.7 includes some important CPU load improvements and allows better CPU thread handling of realtime and audio buffering related / time critical processing.  

This is desirable for me because I mainly use Wine for use with the REAPER digital audio workstation program for electronic music composition.  I get usable results with it, but any improvements are appreciated as I've had to disable certain features just to get it to work reasonably for playback.  

If, in the near future the Ubuntu Studio LiveCD comes with v1.7 or later, I would be able to install a more stable and advanced system.  

It is important to note that right now, my main computer doesn't have any internet access, and that won't change because internet access is too expensive in my area.  I rely upon taking a portable computer to a library wi-fi hotspot for manual downloads, but that computer is not my music workstation computer which is offline.  I am not able to do most of the upgrades on my main computer for this reason.  I know of the apt-offline support page, but it seems stuck in the past at Ubuntu v12 or so.  

If anybody can tell me when the next hard copy (ISO) version will be upgraded to include the new Wine I would appreciate it greatly.  I'm hoping it happens before or during the next LTS (Long Time Support) version of Ubuntu Studio.  If it's not included, that would be a real shame since improvements have been made to Wine over the last months and years.  

Thanks and peace.

---

### Post by MartyBuntu on 2014-07-15
WINE is a moving target. Canonical has to do a software freeze at some point before their releases...

---

### Post by mastablasta on 2014-07-16
> **Nistegmos said:**
> 

A developer told me that Wine v1.7 includes some important CPU load improvements and allows better CPU thread handling of realtime and audio buffering related / time critical processing.  


If anybody can tell me when the next hard copy (ISO) version will be upgraded to include the new Wine I would appreciate it greatly.  I'm hoping it happens before or during the next LTS (Long Time Support) version of Ubuntu Studio.  If it's not included, that would be a real shame since improvements have been made to Wine over the last months and years.  



LTS will most likely stay as it is. the updated programs are then found in new version of the OS. alternatively you have maual install of newer version or possibly .deb files. [http://www.winehq.org/download](http://www.winehq.org/download)

here is the thing - new features mean new bugs. LTS aims to be as stable as possible. stable means that the bugs are known (predictable) and are being crushed/solved/patched. from that point stable is predictable for longer period of time. imagine having LTS in a company with thousands of desktops and then an update came that made you app run better but actually mess up all those user's experience and causing crashes or worse to them. no one would like such a system. I am not saying wine 1.7 will do that just that new programs that haven't been thoroughly tested should just be brought easilly into the system.

and you will notice this on their download site:
> Latest stable release: Wine 1.6.2 See the installation and configuration how-to for post-installation instructions. 
Latest development release: Wine 1.7.22
and on ubuntu part:
> *The 1.7 packages here are beta packages.  This means they will  periodically suffer from  *[*regressions*]("http://wiki.winehq.org/RegressionTesting")*, and as a result an  update may break functionality in Wine. **If the stable 1.6 Wine version works  for you, then you may not want to use these beta packages**.*

so experimental/dev version of software by default on LTS? no way! 

I suggest using perhaps some frontend such as play on Linux to maintain various wine versions and then manually install newer version in it. r

eality is, that if you want updated system you need an internet connection. no one ships them on CD or floppies anymore. though I still wish there would be more .debs for people like you.

---

### Post by grahammechanical on 2014-07-16
I have just installed Ubuntu Studio to test out what you are asking for. I am now running Ubuntu Studio 14.10 under development and it does not install Wine unless we install it through the Ubuntu Software Centre (version 1.6) or if we want version 1.7 (beta) through the Wine PPA. Internet access needed in both cases.

Anyone can download the latest ISO image of Ubuntu Studio and burn it to a DVD disk or USB stick (I have just done that) but although the download is about 2 GB it will not include Wine. I have checked through all the default installed applications (there are many, many applications) and Wine not among them. So, although we can use a Ubuntu Live Session DVD as an offline repository it will not include Wine.

You need to work out how to create an offline repository that will include this package using that portable machine. The references may be for Ubuntu 12.04 but the principles are the same.

I do not think that wine 1.7 will get into the Ubuntu Software Centre/repositories until it is no longer beta software and 14.10 is released at the end of October.

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

Regards.

---

