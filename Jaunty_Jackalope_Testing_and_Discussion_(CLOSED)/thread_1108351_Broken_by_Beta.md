---
title: "Broken by Beta"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by snkngshps on 2009-03-27
First, I know it's completely my fault for upgrading to a Beta release on my main machine. I've done it in the past and just worked through the bugs (it's kind of fun for me in some weird way) but this time it's completely broken!

When I boot up, it goes through the new boot splash screen, but then instead of loading a login screen or my desktop, it goes back to more command line text and eventually asks me to login command line style. If I log in through the command line I'm then stuck at the command line for a few seconds and then my display goes nuts. I could take a picture if you like, but it's essentially a lot of messed up colors and two distorted ubuntu logos. From there I can't do anything else until I shut off my machine. I'm using a Dell Inspiron 1501 with my hardware specs in my signature.

I can see a few error messages during the startup but the text scrolls too quickly for me to relay any of them. Anyone have any ideas? :-/

---

### Post by kestrel1 on 2009-03-27
Sounds like a graphics driver problem. Can you get to a terminal if you press CTRL, ALT & F1 together?

---

### Post by snkngshps on 2009-03-27
I think so too. Once my screen goes nuts, no matter what I press, nothing changes on the display.. But, if I start it in recovery mode, I can access the terminal with networking.

---

### Post by kestrel1 on 2009-03-27
Once you are in the terminal you could remove your xorg.conf file & reboot. This will force a replacement of your xorg.conf file. I have managed to get to a GUI login after doing this. To remove the file type:```
sudo rm /etc/X11/xorg.conf
```
You could back up the file first with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Reboot with```
sudo reboot
```

---

### Post by snkngshps on 2009-03-27
> **kestrel1 said:**
> Once you are in the terminal you could remove your xorg.conf file & reboot. This will force a replacement of your xorg.conf file. I have managed to get to a GUI login after doing this. To remove the file type:```
sudo rm /etc/X11/xorg.conf
```
You could back up the file first with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Reboot with```
sudo reboot
```

Ok I followed all of that but I'm still having a crazy display freakout shortly after the splash screen. This time it's different though, just staticy lines and it blinks for a while. When that happens I can't do anything else :-/

---

### Post by kestrel1 on 2009-03-27
Are you still unable to get to the terminal with CTRL, ALT & F1?

---

### Post by snkngshps on 2009-03-27
> **kestrel1 said:**
> Are you still unable to get to the terminal with CTRL, ALT & F1?

Nope. I can get to the terminal through recovery mode, but when the screen is going crazy, nothing works, even CTRL, ALT, F1

---

### Post by aditirex on 2009-03-27
You have an Ati card  ? Same things happends to me . Ati driver is broken ...

---

### Post by snkngshps on 2009-03-27
> **aditirex said:**
> You have an Ati card  ? Same things happends to me . Ati driver is broken ...

Damn. I imagine there is no fix for it yet huh?

---

### Post by kestrel1 on 2009-03-27
I wonder if the updates will help.
If you have networking when in recovery mode type```
sudo apt-get update
```
When that finishes type```
sudo apt-get upgrade
```
Reboot after this has finished.

---

### Post by optimusmedia on 2009-03-27
Excellent description of my same issue, snkngshps.  I've tried the steps listed here.. also "no joy" because I too have the ATI card.

Side note to newbies reading this: find your card type by going to hitting escape to get the Grub menu. Choose the recovery option. Scroll down to netroot or root options and then enter "lspci".   If you see ATI all over the place, you are in the same boat as we are. Grab an oar. ;)

Now.. here's my newbie like question. Any easy way to downgrade back to  8.10? like "sudo update-manager --oh-no" :) 

Thankfully, a full restore is an option because I was on a test machine.

---

### Post by kestrel1 on 2009-03-27
Looks like a good time to suggest reporting this as a bug then guys.

---

### Post by loomsen on 2009-03-27
I stumbled upon a fix for a similar bug recently, dont know where tho...

However, and as weird as it sounds...

Renaming your gdm rc script from 
SXXgdm to sxxgdm 
stops gdm from being restarted,

locate gdm |grep S| grep /etc/rc

Will show the files.

Just give it a try.

And don't forget to run update-rc.d afterwards...

I imply u boot into single user mode if sth is broken...

---

### Post by ktp on 2009-03-27
If you have ATI card, then you should know that fglrx dropped support for R300-R500.  You have to use open source ati drivers.  

If you had remove your fglrx driver:

sudo apt-get purge xorg-driver-fglrx

Then make sure xorg.config does not have fglrx in it.  I would just remove or backup the existing xorg config.

---

### Post by snkngshps on 2009-03-27
> **ktp said:**
> If you have ATI card, then you should know that fglrx dropped support for R300-R500.  You have to use open source ati drivers.  

If you had remove your fglrx driver:

sudo apt-get purge xorg-driver-fglrx

Then make sure xorg.config does not have fglrx in it.  I would just remove or backup the existing xorg config.

Yay! This worked for me! I still have a couple of nasty screens pop up but only for a second. Is there anything I need to do now that i'm able to log in and everything?

---

### Post by ktp on 2009-03-27
I was having little issues with rendering with open source drivers so I added few options to xorg config which made it lot better.

[PHP]Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
#       SubSection "Display"
#               Virtual 2960 1050
#       EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "ati"
        Option          "AccelDFS" "on"
        Option          "AccelMethod"  "EXA"
        Option          "MigrationHeuristic"  "smart"
        Option          "EnablePageFlip"  "on"
        Option          "EnableDepthMoves"  "on"
        Option          "ColorTiling"  "on"
#       Option          "DisplayPriority"  "HIGH"
#       Option          "DepthBits"  "24"
#       Option          "SubPixelOrder"  "RBG"
#       Option          "DRI" "on"
        Option          "FBTexPercent"  "0"
        Option          "RenderAccel"  "on"
EndSection

Section "ServerFlags"
        Option          "DontZap"       "off"
EndSection
[/PHP]

---

