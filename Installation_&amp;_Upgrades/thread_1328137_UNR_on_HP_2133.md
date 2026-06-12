---
title: "UNR on HP 2133"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by judith_sw on 2009-11-16
Hi,
 
I am very, very new to all of this, so please be gentle :p
 
I have finally got hold of a fairly cheap netbook so that I can get to know open source software and OSs. My HP 2133 came with SUSE 10, but I wanted UNR! After a lot of faffing about, I finally managed to burn the disk and boot from the disk.
 
I liked what I saw, so have installed it side by side with SUSE. However, there are one or two issues that I would like to sort out. I realise that this is all part of the experience and am happy to tinker!
 
Firstly, it's REALLY slow! It boots up well, but then crawls along - can I speed it up?
 
It doesn't recognise the wireless Broadcom - I realise this was an issue in the past, but thought it had been fixed. I'm happy to attempt a fix myself, but am unsure how to go about it. Internet works if I connect using an ethernet cable. 
 
Nor can I get the 3 dongle I have to work. It seems to recognise it ... I may be using the wrong settings (I'll check this at home tonight).
 
Sorry about all the questions - I will be grateful for any hints.
 
Thank you :D

---

### Post by Brian88 on 2009-11-16
You said on your post about '3 dongle', is it the USB modem for the '3' cellphone network?

What brand/type is it?

If your modem type is Huawei E620, Huawei E220 or Option GlobeTrotter 3G+ EMEA [1], you can use this software : [http://www.howtoforge.com/vodafone_mobile_connect_card_driver_linux](http://www.howtoforge.com/vodafone_mobile_connect_card_driver_linux)

(If you've correctly set it up on Windows, open the modem's software in Windows and note down the settings. The settings needed usually are APN name, username & password, and maybe some other settings like proxies).

---

### Post by davidryderuk on 2009-11-16
UNR needs good 2D graphics acceleration in order to work quickly. 

Your computer has a via chrome 9 graphics card. There aren't any drivers available for this card on karmic which support 2D graphics acceleration. Therefore your computer does not support UNR 9.10.

The only drivers available which do support 2D graphics acceleration on this card are about alpha quality due to numerous bugs, incompatibility issues, difficulty in installation and little or no updates. Additionally these drivers are only available for 9.04 or below.

Your best bet is to just use the normal desktop version of ubuntu, since this has no requirement for 2D graphics acceleration. 

I'm not sure about your wireless, but a good first step is to try the following:

1. Connect your netbook to the internet using an ethernet cable.

2. Go to System > Administration > Hardware drivers

3. If your wireless driver is listed in the resultant window, then click enable.

4. Reboot your machine and check to see if the wireless is working.

You can find a compatibility report for your laptop in the link below. 

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#HP 2133 Mininote](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#HP 2133 Mininote)

Sorry about the graphics issues.

---

### Post by judith_sw on 2009-11-16
Thanks - is it possible to revert to the desktop version of Ubuntu, or would I read to reinstall? I'm running the latest version of UNR.

---

### Post by davidryderuk on 2009-11-16
> Thanks - is it possible to revert to the desktop version of Ubuntu, or would I read to reinstall? I'm running the latest version of UNR.

I don't think there is any official way of doing that. Unofficially I've detailed most of the changes involved below, however I might have missed something since I just worked them out as I was going along.

1. Go to System > Preferences > Startup applications

2. Untick the check-boxes next to "Maximus window management" and "Netbook Launcher".

3. Right click on the Ubuntu logo on the top panel and select "Remove from panel".

4. Do the same for the blank space at the very left of the top panel. If done right this should cause the icons of any open application to disappear from the top panel.

5. Logout and log back into your machine.

6. Right click on the left part of the top panel and select "Add to panel". 

7. Select "menu bar" and click on add. 

8. Go to System > Preferences > Appearance

9. Change the theme to "Human"

10. Right click on the middle of the top panel (i.e a blank space) and select "New panel".

11. On the very left of the bottom panel add the "Show desktop" applet and immediately next to this add the "Window list" applet.

12. On the very right of the bottom panel add the "Deleted items" applet and immediately to the left of this add the "Workspace switcher" applet. 

13. Right click on the "workspace switcher" applet and select Preferences.

14. Change the "Number of workspaces" to 2.

15. Go to Applications > Accessories > Terminal.

16. Run the following command (use copy and paste to avoid any typos):

```
gconftool -s --type bool /apps/nautilus/preferences/show_desktop true
```

17. Open firefox.

18. Disable or Uninstall the webfav addon.

19. Add your favorite application launchers by finding them in the menu bar and dragging them into an empty space on the top panel.

20. Check your desktop now matches the pictures found in the link below.

[http://www.ubuntu.com/products/whatisubuntu/910features](http://www.ubuntu.com/products/whatisubuntu/910features)

21. If not then move the applets by right clicking on them and selecting "move". You might have to untick the "Lock to panel" option first.

---

### Post by judith_sw on 2009-11-18
Hi,
Thanks for the detailed reply. I have managed to install the latest Ubuntu desktop and it works much, much better than UNR, although UNR looked really good!

I've also managed (with help from another user) to get wireless working. The only remaining problem is the 3Connect dongle. It's the Huawei E156G version. The netbook recognises the dongle as an external drive, but that's about it. I'm going to look at how it's set up in Windows on my computer and will see if I can get it set up that way ...

---

