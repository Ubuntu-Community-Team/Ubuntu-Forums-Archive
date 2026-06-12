---
title: "“booting system without network configuration” from a livecd created with remastersys"
date: 2012-12-30
forum: Installation &amp; Upgrades
---

### Post by Jaoyur on 2012-12-30
I have ubuntu 12.04 with KDE. I have installed remastersys and made a  livecd (distribution) burnet with k3b on a dvd (3.2gb), but I left the  video card ati driver because I would use this livecd only on the  computer in which I created it, so with the same gpu. 

The big problem is that while booting, the screen stays on: Kubuntu 12.04 .... "booting system without network configuration", and  nothing happens.  I have tried to burn it again but same thing. Surfing on google it seems to be a problem that other people had after  upgrading from a ubuntu version to onother, but of course it's not my  case.


  Hope someone could help me, 

Thanks

**edit:**
so I think that my problem is about the .iso I created with Remastersys, I don't know what is wrong. that's why I have followed the advices for making livecd from remastersys.com, it says:
- You should not install any proprietary video drivers like the nvidia or ati drivers as they will not be used on the livecd and users will have to reinstall them after installation.  
- Clean up history and cache and copy over the contents to /etc/skel but be sure to change the ownership of everything in /etc/skel to root.  
- While the livecd/dvd is being created, you should not open any other apps or windows.   
- Do not under any circumstances enable auto login as it will cause the live user creation portion of casper to fail and you will not get to the desktop. 
I did all, the only thing I left is the video card driver.
I have also cleaned the system with ubuntu tweak and after all these operations I created a backup .iso with remastersys and then a livecd .iso, I have tried them in virtualbox and at boot I can only see:   
"ISOLINUX  3.63 Debian-2008-07-15 Copyright © 1994-2008 H. Peter Anvin boot : " and virtualbox has given an error, so I've burnt a dvd and same thing on my real pc. 
At least before doing these operations I could see the normal livecd screen of my distribution where I could choose what to do (memtest, livecd, install distribution, boot hd etc...), but now I can't.

I'm confused, please help me!

---

