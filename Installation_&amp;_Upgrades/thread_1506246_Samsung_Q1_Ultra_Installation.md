---
title: "Samsung Q1 Ultra Installation"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by border on 2010-06-10
This thread is meant for everybody who has experience with installing ubuntu (and linux in general) on a Samsung Q1 and more specific the Ultra model, and for everybody who has some knowledge to share or something to ask about it.

I've got 10.04 (Lucid) installed on the device and out of the box it recognises all the hardware. It seems like everything works fine. Just the touchscreen doesn't.

I did try a lot to get it working and after all it does seem to be quite simple to fix. Just install xserver-xorg-input-evtouch

```
sudo apt-get install xserver-xorg-input-evtouch
``` 

and add a file named 11-touchkit.conf with the following contents:

```
Section "InputClass"
	Identifier "Touchkit Touch"
	MatchIsTablet	"on"
	MatchDevicePath "/dev/input/event*"
	Driver 	"evtouch"
	Option	"ReportingMode"	"Raw"
	Option	"Emulate3Buttons"
	Option	"Emultate3Timeout"	"50"
	Option	"SendCoreEvents"	"On"
	Option	"TapTimer"		"200"
	Option	"LongTouchTimer"	"400"
	Option	"MinX"			"145"
	Option	"MinY"			"193"
	Option	"MaxX"			"3973"
	Option	"MaxY"			"3898"
EndSection
```

The name of the file may differ, just the number has to be greater than any other file in that directory to make sure it gets loaded after any other possible touchscreen configurations.
I just chose touchkit, because xorg reports it as Touchkit Touch (see /var/log/Xorg.0.log)

It should be better if we got the touchscreen working with the evdev driver, since evtouch is not getting updated anymore, and the calibration method provided in the evtouch package seems to require hal which is deprecated now.

Evdev seems to recognise the touchscreen since it registers clicking on a clean install, but it reacts by moving the pointer to the upper left corner.
Which supsects me to believe that all the needs to be found is good calibration values, but I haven't gotten that far yet.

There is a calibrator available for xinput devices
[xinput_calibrator]("http://www.freedesktop.org/wiki/Software/xinput_calibrator")
But I haven't found a useful way to apply the outcome of the calibration.
I found the program in the [following thread]("http://ubuntuforums.org/showthread.php?t=1478877"). So maybe anyone else has more success with it?

Wireless seems to be establishing a connection which is not very stable. But I don't use it actually, so I should still check that out.

So far, so good

---

### Post by Cka3o4nik on 2010-06-12
> **liviococcia said:**
> ...
i then did a little more web browsing, about an hour, and then disconnected the Plusnet connection.


You're lucky to have WiFi working stable for such period of time.

> After checking if you have latest BIO's version, and installing it if you don't, i would then go back into the BIO's again and make sure to 'Load Default settings', and 'Save and Exit', just incase something has changed, or was never quite right with the Wireless adapter in the settings for running Ubuntu.


Since WiFi adapter is a PCI device, it might not depend on BIOS. However BIOS can affect some low-level device interaction, so I'll update it if software solutions won't help.

> I then delete any current network connections you have, and, any old Wireless or Mobile connections you previously had used, through the 'Network Connections' software, then restart the Q1 ultra

I did so, the problem remains. But I guess the problem is in authentication method, 'cause now I've got authentication requests popping up every time Q1U tries to reconnect. Only first connection passes normally, but it lasts not longer than a couple of minutes. I'll try some other authentication scheme later.

What WiFi authentication method was set up at your router?

> , i wouldn't setup a Wireless connection again on the router your having these issues with, but would try someone elses router first, this may show the problems with your router.


I'm sure for 90% that it's ubuntu driver/kernel configuration problem becase everything work properly when I boot WinXP. I've got 2 routers and I can't connect both under Ubuntu while XP is running as it is.

> If doing the above did point to the router, i'd first get another Microfilter


What do you mean?

> , and would unplug any phones and turn any 'cordless' phones and there 'handsets' off completely, leave them unplugged for now, check all the connections between the BT socket a 'new' Microfilter and the router, then ask a friend to 'Wirelessly' connect to your router (someone with a dual 'OS' (Win/ubuntu) computer would be best, or using a 'Live' Ubuntu version), if they experiance wireless issues, i do a 'full reset' of the router to make sure it's set to it's defaults (make sure you have the 'Default' WAP/WEP security access keys, your router manufacturer 'defualt' one for your model, your ISP's original one, and the one you might have created yourself before resetting the router).

My routers are working properly, as I described above. 

> it could really only be corruption somewhere in the Ubuntu networking part of the software

I agree only if it's NetworkManager's wireless connection fault. My Q1's wired networking works fine.

> , or it's hardware drivers settings, but give it another check using a Ubuntu Netbook Edition or Ubuntu in a 'Live' CD run, and see if it runs Ok this way, 


Maybe later, when I'll got my USB drive with Ubuntu back from work. It's not an easy task - to run Live CD without optical drive.

> If you find that you are both connecting ok, i know this may sound crazy but just try a few household electrical items while you are still connected, like microwaves, coffee machines, turn off and on Fridges and Freezers, and game consols. My sister had a strange problem with both here Wireless router from Sky, an XBox 360 and an electric expresso coffee machine, even though the household wiring was all new and to spec, if she turned any of these items on her wireless connection would drop for some strange reason.


If we discover WiFi under Ubuntu and XP runs at different radio frequences with the same routers, it'll be quite shocking for me :-)

> 
Hope something here might be of help

regards

I also hope that. Thanks for help :-)

---

### Post by border on 2010-06-14
The only thing I've noticed so far with the WiFi is the funny thing that I disabled it in the BIOS but that didn't keep it from discovering the available connections in my neighbourhood.
So the only way to disable WiFi permanently I've found so far is blacklisting the driver. 
Maybe it also works when you disable wireless connection in the networkmanager but I believe those settings don't persist after a reboot. But that behaviour might have changed recently (need to check on that).

---

### Post by Cka3o4nik on 2010-06-15
It seems my Q1U's WiFi began to work somehow after a couple of my wireless network connection removals in Network Manager and a couple of networking restarts. So now it's working stable enough. I hope this state will remain...

---

### Post by liviococcia on 2010-06-17
Hello Members, just thought i'd post everything related to the Samsung Q1 Ultra over to this thread, all this info was a combination of some great help form all the members who contributed, and gave direct instruction to rectifying my issues, which might help other users, thanks alot


_Samsung Q1 Ultra Touchscreen problem_(A big thanks Cka3o4nik)

1: I first installed 'xserver-xorg-input-evtouch' package by going to the main Ubuntu desktop menu, clicking onto 'System' then onto 'synaptic package manager, in the search box type EVTOUCH, this should bring up the package, then mark it for installation, and install.

2: I then opened the 'File manager' in administrator mode by using the 'Run Applications' box, to do this hold the 'Alt' button and while held down press the 'F2' button, in the box that appears type ' gksudo nautilus ' file manager will open, click onto 'File system' and follow the folder path below:

/usr/lib/X11/xorg,conf.d

3:Open any file with it's name ending in '.conf' contained in the 'xorg.conf.d' folder, and without making any changes to the contents of the file you have opened, go to 'File' then 'Save as..', a window will now open, in the 'name' box rename the file to 11-touchkit.conf then click onto the '+' sign next to 'Browse for other folders' and navigate again by clicking first onto 'File System' then 'usr' > 'lib' > 'X11' > 'xorg,conf.d', you will see this folders contents, making sure you have followed all the above click the 'Save' button.

4: While the 'File Manager' window remains open in 'administrator' mode (if not follow step 2 of these instructions to reopen), double click onto your newly created '11-touchkit.conf' file, be aware that the contents of this new file now need to be changed, in the Gedit app that has open the file, click onto 'Edit' then 'Select All' of which the contents should now be highlighted, then click onto 'Edit' then 'Delete', the file's contents should now be gone, copy and paste the instructions below into the blank page of file:-

Section "InputClass"
Identifier "Touchkit Touch"
MatchIsTablet "on"
MatchDevicePath "/dev/input/event*"
Driver "evtouch"
Option "ReportingMode" "Raw"
Option "Emulate3Buttons"
Option "Emultate3Timeout" "50"
Option "SendCoreEvents" "On"
Option "TapTimer" "200"
Option "LongTouchTimer" "400"
Option "MinX" "145"
Option "MinY" "193"
Option "MaxX" "3973"
Option "MaxY" "3898"
EndSection

5: Click onto 'File' then 'Save', and now close your new document, if the 'File Manager' window is still open you should notice your new '11-touchkit.conf' file in the 'xorg.conf.d' folder

6: Close the 'File Manager' window, (I notice whenever i open 'File Manager' using the gksudo nautilus instruction and then finish with it, it seems to make my desktop go blank, and I have to shut the Q1 Ultra down by holding the off/on switch in the 'off' position, it doesn't seem to do any permanent harm though) 

Also... if you were using the Samsung USB integrated keyboard & mouse, or any USB dual keyboard and mouse while following the above instructions, make sure you unplug this before turning the Q1 Ultra back on, in my case I've found that I couldn't have the keyboard plugged in, as the touch-screen would not work correctly, once the Q1 Ultra was started up without it, the touch-screen worked no problems, following this does seem to be the only way it will work.

When you do restart with no USB integrated mouse & keyboard, remember to follow 'step 1' below to first open the 'Onboard' screen keyboard' so allowing you to login, if it doesn't first show, verify you've chosen to turn it on and just restart the Q1 again.


I got the 'onboard' assistive technologies touch keyboard to pop-up at Ubuntu's start-up for loging in, to do this:-

1:At the initial login screen i clicked onto the man in a circle icon, then preferences, and in the box that appears, put a check mark next to the item regarding the use of the Onboard screen keyboard.

I also now have it load apon the desktop opening,to do this:-

2: Go to the main Ubuntu Netbook Edition 10.04 menu bar, click on 'System' then 'Assistive Technologies', a window will open put a check against 'Enable Assistive Technologies' click onto the 'Prefered Applications'button , click onto the 'Mobility'section drop-down arrow, and choose 'Onboard' and put a check against 'Run at Start' and close.

There's also settings in the 'Onboard' screen keyboard when you click in the puple area within the keyboard to the bottom right, doing this will show a 'Settings' button, this will allow you to have the 'Onboard' screen keyboard start when the desktop loads up minimised to the application bar, or as a small floating icon on the desktop.

Also within the 'Onboard' keyboard settings section, there is an option to have it always appear when a password window activates i.e when the screen saver locks the desktop, or it's logged off. I would suggest this related item has a check mark against it. 

_Samsung Q1 Ultra Wireless connection issues, things to try.._

I would also mention that my Q1 Ultra has been fitted with the maximum memory modules allowed in it, and that i did have BIO's updates installed via the Samsung Update Plus software when it was running Windows XP, i ran the Samsung Update check on a regular basis, i've only been running Ubuntu Netbook Edition 10.04 for around month, or just over.

After checking if you have latest BIO's version, and installing it if you don't, i would then go back into the BIO's again and make sure to 'Load Default settings', and 'Save and Exit', just incase something has changed, or was never quite right with the Wireless adapter in the settings for running Ubuntu.

I then delete any current network connections you have, and, any old Wireless or Mobile connections you previously had used, through the 'Network Connections' software, then restart the Q1 ultra, i wouldn't setup a Wireless connection again on the router your having these issues with, but would try someone elses router first, this may show the problems with your router.

If doing the above did point to the router, i'd first get another Microfilter, and would unplug any phones and turn any 'cordless' phones and there 'handsets' off completely, leave them unplugged for now, check all the connections between the BT socket a 'new' Microfilter and the router, then ask a friend to 'Wirelessly' connect to your router (someone with a dual 'OS' (Win/ubuntu) computer would be best, or using a 'Live' Ubuntu version), if they experiance wireless issues, i do a 'full reset' of the router to make sure it's set to it's defaults (make sure you have the 'Default' WAP/WEP security access keys, your router manufacturer 'defualt' one for your model, your ISP's original one, and the one you might have created yourself before resetting the router).

If they didn't experiance any problems connecting, after using there computer for a bit, and while they are still connected to your router, setup your connection on the Q1 Ultra, if you are still suffering the same problems then you know it could really only be corruption somewhere in the Ubuntu networking part of the software, or it's hardware drivers settings, but give it another check using a Ubuntu Netbook Edition or Ubuntu in a 'Live' CD run, and see if it runs Ok this way, if it does, then it has to almost certainly be the Wireless driver settings or the Wireless Hardware driver's it's using.

_Samsung Q1 Ultra running Avast Antivirus(An error occured in avast! engine: Invalid argument_

I first checked for any Ubuntu updates, and accepted any that were outstanding, after restarting the computer open a 'Terminal' window, and type this command below..

sudo sysctl -w kernel.shmmax=128000000

Then press the 'Enter' key, and it will ask for your password which you will not see anything as you type, then press the 'Enter' key, the line below will now appear
 
kernel.shmmax = 128000000

Close the 'Terminal' window

Press the 'Alt' +'F2' keys to open the 'Run application' box and typed into it..
gksu gedit 

This opens the text editor application Gedit as an administrator user, form within the Gedit application open the folder 'etc', within this folder is a file called 'sysctl.conf', at the bottom of this files text add the line below...

kernel.shmmax = 128000000

..then 'Save' the changes.

After restarting the computer, and upon opening Avast Antivirus the error should have gone.

If you haven't got Avast Antivirus installed but want to install it, do the procedure above first, and then install the application. 

I do understand there are many that do not there's any need for Antivirus software, but i do go between Windows and Ubuntu OS's occasionally

Kind Regards  
Livio

---

### Post by gsd2010 on 2010-07-05
I have just installed ubuntu 10.04 in Samsung Q1 F001 following the advices about touch screen.  The touch screen and the wireless lan work.  However, the wired lan is failed.  The system seems cannot recognizes the lan cable.  Any similar experience?

---

### Post by Cka3o4nik on 2010-07-05
Hello

> **gsd2010 said:**
> the wired lan is failed.  The system seems cannot recognizes the lan cable.  Any similar experience?

Nope, wired lan worked out of the box on my Q1 Ultra. I installed 10.04 Netbook Edition.

---

### Post by GroovingClockwork on 2010-07-13
Hello people,

This thread is of interest to me even if I have a Q1 (non-Ultra) running Mint 9 (based off Lucid) -- I figure a lot of the configuration is similar.

I was wondering if anyone has needed to and tried to make Linux recognize more of the hardware buttons. Out-of-the-box I get the left hand side joystick and the right hand side 'Enter' button working, but not the other two hardware buttons nor the 4-directional (U1...U4) dial. Also, with the USB keyboard attached, some function keys are recognized (e.g. Fn+left arrow and Fn+right arrow to alter volume) but many are not (e.g. Fn+up arrow/down arrow). The latter is not just a matter of no action being associated with the keypress: using the

showkey -s

command it appears the problematic key and button presses are not registered at all (no scancode appears).

Now in [this post]("http://www.mepisimo.com/forum/index.php?topic=76.0") it is said that in Mepis it is possible to have all buttons working -- but this assumes that the key/buttonpresses generate scancodes in the first place. I have no idea how to make that happen in Mint/Ubuntu.

Any advice much appreciated! Thanks.

---

### Post by ulugeyik on 2010-08-13
Yes, unfortunately Ubuntu has taken some steps back in the last several releases in terms of good support for Samsung Q1U or may be I do not understand something. Early one, there was a .deb package that one could install and it would enable UDF, vol, menu , the cursor keys etc. Now, we have to do all that manually. The link you provided from MEPIS also basically suggests the same thing I am going to write.

default:
UDF: maximize windows
vol: in regular ubuntu, it works in lubuntu it does not seem to do much.
menu: in regular ubuntu brings the start menu up but in lubuntu did not do much.

I do not remember how to enable UDF and volume but for the cursor keys around "enter", the following works for me which you can put in a shell script:

sudo setkeycodes e056 108
sudo setkeycodes e057 105
sudo setkeycodes e058 103
sudo setkeycodes e059 106

basically, those keys are mapped as  s up = F1, down = F3, right = F10,
left = F9 by default and we are reassigning them to cursor actions.

running "xev"  returns this information but right now, I could not decipher to figure out where I know which one is e056. 

I was told that you could edit the following .fdi file to make it default (look under Samsung Q1U) but I did not try that:
/usr/share/hal/fdi/information/10freedesktop/30-keymap-misc.fdi

Also , see:
[https://wiki.ubuntu.com/MobileTeam/Mobile/HowTo/KeyMapping](https://wiki.ubuntu.com/MobileTeam/Mobile/HowTo/KeyMapping)

btw, out of the box I get the reverse webcam working but not the forward one. is it possible to switch them?

---

### Post by Marcia-y on 2010-10-05
> **GroovingClockwork said:**
> Hello people,

This thread is of interest to me even if I have a Q1 (non-Ultra) running Mint 9 (based off Lucid) -- I figure a lot of the configuration is similar.

I was wondering if anyone has needed to and tried to make Linux recognize more of the hardware buttons. Out-of-the-box I get the left hand side joystick and the right hand side 'Enter' button working, but not the other two hardware buttons nor the 4-directional (U1...U4) dial. Also, with the USB keyboard attached, some function keys are recognized (e.g. Fn+left arrow and Fn+right arrow to alter volume) but many are not (e.g. Fn+up arrow/down arrow). The latter is not just a matter of no action being associated with the keypress: using the

showkey -s

command it appears the problematic key and button presses are not registered at all (no scancode appears).

Now in [this post]("http://www.mepisimo.com/forum/index.php?topic=76.0") it is said that in Mepis it is possible to have all buttons working -- but this assumes that the key/buttonpresses generate scancodes in the first place. I have no idea how to make that happen in Mint/Ubuntu.

Any advice much appreciated! Thanks.

Hi hope this will work,

I have found a solution with my Q1 ultra with the 4-Directional buttons on the right as Lucid no longer supports HAL and uses Rules instead i have found but don't know if this will work ok for you but it did for me.

Find the folder: /lib/udev/keymaps/ 

In there are varies text files relating to different models of laptops that govern the key mapping.

I used:

sudo gedit /lib/udev/keymaps/samsung-sq1us

and made the following adjustments from:

0xD4 menu
0xD8 f1
0xD9 f10 
0xD6 f3
0xD7 f9
0xE4 f5
0xEE f11

To:

0xD4 menu
0xD8 up
0xD9 right
0xD6 down
0xD7 left
0xE4 f5
0xEE f11

Saved, rebooted and the keys work fine.

P.S - Works with Ubuntu 10.10 too... :)

---

### Post by badmotor on 2010-10-13
> **liviococcia said:**
> Hello Members, just thought i'd post everything related to the Samsung Q1 Ultra over to this thread, all this info was a combination of some great help form all the members who contributed, and gave direct instruction to rectifying my issues, which might help other users, thanks alot


_Samsung Q1 Ultra Touchscreen problem_(A big thanks Cka3o4nik)

1: I first installed 'xserver-xorg-input-evtouch' package by going to the main Ubuntu desktop menu, clicking onto 'System' then onto 'synaptic package manager, in the search box type EVTOUCH, this should bring up the package, then mark it for installation, and install.

2: I then opened the 'File manager' in administrator mode by using the 'Run Applications' box, to do this hold the 'Alt' button and while held down press the 'F2' button, in the box that appears type ' gksudo nautilus ' file manager will open, click onto 'File system' and follow the folder path below:

/usr/lib/X11/xorg,conf.d

3:Open any file with it's name ending in '.conf' contained in the 'xorg.conf.d' folder, and without making any changes to the contents of the file you have opened, go to 'File' then 'Save as..', a window will now open, in the 'name' box rename the file to 11-touchkit.conf then click onto the '+' sign next to 'Browse for other folders' and navigate again by clicking first onto 'File System' then 'usr' > 'lib' > 'X11' > 'xorg,conf.d', you will see this folders contents, making sure you have followed all the above click the 'Save' button.

4: While the 'File Manager' window remains open in 'administrator' mode (if not follow step 2 of these instructions to reopen), double click onto your newly created '11-touchkit.conf' file, be aware that the contents of this new file now need to be changed, in the Gedit app that has open the file, click onto 'Edit' then 'Select All' of which the contents should now be highlighted, then click onto 'Edit' then 'Delete', the file's contents should now be gone, copy and paste the instructions below into the blank page of file:-

Section "InputClass"
Identifier "Touchkit Touch"
MatchIsTablet "on"
MatchDevicePath "/dev/input/event*"
Driver "evtouch"
Option "ReportingMode" "Raw"
Option "Emulate3Buttons"
Option "Emultate3Timeout" "50"
Option "SendCoreEvents" "On"
Option "TapTimer" "200"
Option "LongTouchTimer" "400"
Option "MinX" "145"
Option "MinY" "193"
Option "MaxX" "3973"
Option "MaxY" "3898"
EndSection

5: Click onto 'File' then 'Save', and now close your new document, if the 'File Manager' window is still open you should notice your new '11-touchkit.conf' file in the 'xorg.conf.d' folder

6: Close the 'File Manager' window, (I notice whenever i open 'File Manager' using the gksudo nautilus instruction and then finish with it, it seems to make my desktop go blank, and I have to shut the Q1 Ultra down by holding the off/on switch in the 'off' position, it doesn't seem to do any permanent harm though) 


Livio

Is anyone able to modify this for Kubuntu?  I am using Maverick, but the file structure is a little different in KDE and there is no Xorg.conf.d file in X11 folder.  I don't know where to put the configuration file, or if the same file will work OK in Kubuntu.

---

### Post by Marcia-y on 2010-10-17
Hi [badmotor,]("http://ubuntuforums.org/member.php?u=374304")

I've got touch screen working in Maverick KDE.

Try this:

1. Activate both backports lines in the "Origin of Packages" in KPackageKit via settings then install the evtouch driver.

2. Copy and paste in terminal: 

kdesudo kate /usr/share/X11/xorg.conf.d/11-touchscreen.conf

Type in your password

3. Then copy and paste into the text editor:

Section "InputClass"
    Identifier "Touchkit Touch"
    MatchIsTablet    "on"
    MatchDevicePath "/dev/input/event*"
    Driver     "evtouch"
    Option    "ReportingMode"    "Raw"
    Option    "Emulate3Buttons"
    Option    "Emultate3Timeout"    "50"
    Option    "SendCoreEvents"    "On"
    Option    "TapTimer"        "200"
    Option    "LongTouchTimer"    "10"
    Option    "MinX"            "130"
    Option    "MinY"            "210"
    Option    "MaxX"            "3950"
    Option    "MaxY"            "3898"
EndSection

And click on save.

Reboot and all should be well :)

To sort the right navigation keys in KDE type in terminal:

kdesudo kate /lib/udev/keymaps/samsung-sq1us

Adjust file the same as in my previous posting about ubuntu.

---

### Post by juanfi on 2011-11-01
Hi,

I got 11.04 and just recently upgraded to 11.10. Everything works nicely. Unity is more fun with a touchscreen. The touchscreen had to be calibrated using xinput_calibrator (basically I got the same limits that have been published in this thread).

Also, installed the scrolling plugin for firefox, now that fennec has disappeared:
[https://addons.mozilla.org/en-US/firefox/addon/grab-and-drag/]("https://addons.mozilla.org/en-US/firefox/addon/grab-and-drag/")
I tried to install the opera-mobile for meego (RPM through alien), but it gives me "Illegal instruction".

Ok, it is not a dual-core 2011-style tablet, but I can run any ubuntu program on it (including spotify) so it beats android in many aspects and is fairly usable.

Also found a neat brightness widget for unity:
[http://codevanrohde.nl/wordpress/?p=128]("http://codevanrohde.nl/wordpress/?p=128")

Juan

---

### Post by oldos2er on 2011-11-01
Closed, please don't bump old threads.

---

