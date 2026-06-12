---
title: "[drm:drm_crtc_helper_set_config]"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by atom715 on 2012-02-13
I have installed ubuntu 11.10 on an hp desktop with 160GB hdd and between 1 and 2GB ram with an onboard video card and get an error that says "[drm:drm_crtc_helper_set_config] *ERROR* failed to set mode on [CRTC:6]"

I can play around on from the live CD and install it fine but once it finishes the install and asks me to take out the CD and restart i have nothing but problems from that point on.  I do not know what to do to fix the problem, and am open to suggestions.

Thank you, atom715

---

### Post by MAFoElffen on 2012-02-13
> **atom715 said:**
> I have installed ubuntu 11.10 on an hp desktop with 160GB hdd and between 1 and 2GB ram with an onboard video card and get an error that says "[drm:drm_crtc_helper_set_config] *ERROR* failed to set mode on [CRTC:6]"

I can play around on from the live CD and install it fine but once it finishes the install and asks me to take out the CD and restart i have nothing but problems from that point on.  I do not know what to do to fix the problem, and am open to suggestions.

Thank you, atom715
What graphics chip do you have?

At what point of the bootup do you get this error?

---

### Post by atom715 on 2012-02-13
The computer is an hp pavilion a1620y with an Integrated graphics (ATI Radeon Xpress 200), the link that i get the information from is... 

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01064838&lc=en&cc=us&dlc=en&product=3253998](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01064838&lc=en&cc=us&dlc=en&product=3253998) 

From the beginning, my monitor goes blank after it shows the hp start-up menu, then about 30 seconds later the text strings in the picture appears on my screen.  When i try and go into the grub menu it says on the screen 'GRUB loading.' but a blank screen appears then the text strings appear within 10 to 20 seconds.

---

### Post by atom715 on 2012-02-13
I have looked at other forums and i now am able to login to the gui but i have to press ctrl+alt+f1 then enter a username and password then enter the command startx, then my gui works.  so now my question is if there is a way to bypass the text string and go right to the main ubuntu login screen.  I am updating the desktop now and will post updates as i go along with everything.

---

### Post by MAFoElffen on 2012-02-14
> **atom715 said:**
> I have looked at other forums and i now am able to login to the gui but i have to press ctrl+alt+f1 then enter a username and password then enter the command startx, then my gui works.  so now my question is if there is a way to bypass the text string and go right to the main ubuntu login screen.  I am updating the desktop now and will post updates as i go along with everything.
Problem of not going directly to the graphical logon and desktop is most likely a problem with the Desktop Manager, which in 11.10 is lightdm--
```

sudo dpkg-reconfigure lightdm

```

---

### Post by MAFoElffen on 2012-02-15
> **atom715 said:**
> The computer is an hp pavilion a1620y with an Integrated graphics (ATI Radeon Xpress 200), the link that i get the information from is... 

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01064838&lc=en&cc=us&dlc=en&product=3253998](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01064838&lc=en&cc=us&dlc=en&product=3253998) 

From the beginning, my monitor goes blank after it shows the hp start-up menu, then about 30 seconds later the text strings in the picture appears on my screen.  When i try and go into the grub menu it says on the screen 'GRUB loading.' but a blank screen appears then the text strings appear within 10 to 20 seconds.
From where your Picture of messages is and where the last errors are...

- Hung at "Checking Battery State" indicates a graphics driver problem... either that a graphics driver does not exist or is having problems loading.

- DRM is the direct rendering manager of a graphics driver...

Did you install the fglrx packaged driver or the ATI binary driver?  If you did, remove it and reinstall.

If you didn't, at <Cntrl><Alt><F2>, login and follow the instructions for either:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][B]
[Installing ATI Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10950714&postcount=334")[/B] 

[**Installing ATI Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467052&postcount=798")
[/SIZE][/COLOR][/SIZE][/COLOR]

---

### Post by atom715 on 2012-02-20
I got the computer working and the login screen in the gui up and running.  when the computer was spitting out the code i pressed Crtl+Alt+F1 and logged in, then entered the gui with the command 'startx'.  from there i updated the computer and added a video driver.

---

### Post by MAFoElffen on 2012-02-20
> **atom715 said:**
> I got the computer working and the login screen in the gui up and running.  when the computer was spitting out the code i pressed Crtl+Alt+F1 and logged in, then entered the gui with the command 'startx'.  from there i updated the computer and added a video driver.
Good Job. Please use the Thread's Thread Tools to mark this thread as "Solved"

---

