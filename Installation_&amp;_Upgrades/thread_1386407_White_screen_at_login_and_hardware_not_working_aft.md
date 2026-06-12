---
title: "White screen at login and hardware not working after upgrading to Karmic Koala 9.10."
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by zenofase on 2010-01-20
I upgraded my netbook to Karmic Koala 9.10 the other day and had nothing but trouble, which I admit now was my fault.  Once it was all installed and ready to go I noticed I didn't get the pretty new splash screen and the login screen was plain and ugly.  I log into my user and got nothing but a white screen with a cursor. I couldn't move the cursor at first so decided to plug in a USB mouse to see if it was the touchpad drive.  It was.  I could move the cursor much like I heard other people on forums say and I knew where to go to log off and my screen would flash my normal desktop before logging off. 

After looking at people's post I found (or so I thought) the problem, compiz fusion.  I uninstalled it and could log in but things were still jacked up and my touchpad still didn't work.  looking into the touchpad problem I found the culprit to all my problems:

I have a partitioned hard drive and a Windows install on it so I kept my custom menu.lst when asked what to do during the upgrade.  I didnt think it would cause any problems but it did.



The issue was my system was still trying to boot 9.10 off of the old kernel.

So I went into my menu.lst  (found under boot/grub/) and edited the kernel and initrd information to the newest kernel and initrd I found under /boot.  

after that everything is back to normal touchpad working reinstalled compiz and no white screen of death. 


so for those wanting to skip my BS:



make sure you have the earliest versions of kernel and initrd in your grub menu.lst


Hope this helps  :D

---

