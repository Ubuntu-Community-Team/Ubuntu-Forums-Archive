---
title: "Logitech Mouse Driver"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by measekite on 2007-09-08
Re:  Logitech G7 Wireless Laser Mouse

When using Windows I have a software disk from Logitech that supported the features of the mouse.  Most notably the leds for mouse speed and the back button as well as other features.

In Ubuntu these features are not available in the standard mouse driver.  Specifically the back button does not work and I do not get an on screen message to change the battery.

Where can I get an appropriate mouse driver that will mimic all of the Vendor's functions?

---

### Post by Pumalite on 2007-09-08
System>Preferences>Mouse

---

### Post by merlinus on 2007-09-08
The answer is that Logitech does not support linux.

You can search for workarounds. There are quite a few threads addressing these issues, but you will probably never get everything working the same as with their windows driver.

-merlin

---

### Post by roro100 on 2008-05-11
I have the same problem. Seems like we are stuck with only primitive functions.

---

### Post by measekite on 2008-05-15
> **roro100 said:**
> I have the same problem. Seems like we are stuck with only primitive functions.

**[COLOR=Red]This is what I got to work with the Logitech G7.  Let me know if this helps.[/COLOR]**

Logitech G7 Mouse
THIS WORKED FOR THE G7

You can test the mouse buttons using:        xev

Activate side-mouse-buttons in Firefox Add-ons
Just add two lines to xorg.conf will activate side*mouse*buttons in Firefox Add-ons. This should work with most 
5*button mouse. Here is a list of mice that worked with this instruction. 
•    Logitech MX310 
•    Logitech MX510 
•    Logitech MX518 
•    Logitech MX700 
•    Logitech MX Revolution 
•   Intellimouse Explorer (first edition) 
•   Razer Copperhead 
    
Backup X.org configuration file 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

Modify the X.org configuration file 
gksudo gedit /etc/X11/xorg.conf

Find the Input Device section for your mouse and add two lines as shown below. You may also increase 
the number of buttons if your mouse has more than 7, just fix the rest of the section based upon the 
number of buttons (remember back/forward, wheel click & tilt left/right all count as buttons) 

Change: 
Section "InputDevice"
          Identifier "Configured Mouse"
          Driver "mouse"
          Option "CorePointer"
          ...
          Option "Protocol" "ExplorerPS/2"
          ...
          Option "Emulate3Buttons"                 "true"
EndSection

to: 
Section "InputDevice"
         Identifier "Configured Mouse"
         Driver "mouse"
         Option "CorePointer"
         Option "Device" "/dev/input/mice"
         Option "Protocol" "ExplorerPS/2"
         Option "ZAxisMapping" "4 5"
         Option "Emulate3Buttons" "true"
         Option "Buttons" "7"
        Option "ButtonMapping" "1 2 3 6 7"
EndSection

Buttons still won't work in Nautilus unless you install the imwheel dameon. 
Install & Configure IMWheel

Install IMWheel 
   
sudo apt-get install imwheel

Modify IMWheel configuration file 
    •
gksudo gedit /etc/X11/imwheel/imwheelrc

Insert the following at the bottom of this existing file 

".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right
"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

 Create IMWheel start*up script 
    •
sudo mkdir /home/login
gksudo gedit /home/login/mouse

 Insert the following into this new file 
    •
#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 4 5 6 7" &
exec imwheel -k -b "6 7" &
exec $REALSTARTUP


Grant execution for everyone to this new script 
    •
sudo chmod +x /home/login/mouse

 Configure this script to be executed at start*up 
    •
           1. Select 'System' > 'Preferences' > 'Sessions' 
           2. Click the StartUp tab 
           3. Click Add, then input: /home/login/mouse 
           4. Click OK, then Close 
      Reboot your computer or your Gnome environment and then test your back/forward mouse 
    •
      buttons in Nautilus 

End End End End End End End End End End End End

---

