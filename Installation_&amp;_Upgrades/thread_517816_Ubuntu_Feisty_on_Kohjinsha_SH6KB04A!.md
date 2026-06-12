---
title: "Ubuntu Feisty on Kohjinsha SH6KB04A!"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by crazebenny on 2007-08-05
I JUST got Ubuntu Feisty installed on my Kohjinsha SH6KB04A. This is actually my first thread in the Ubuntu Forums. Why I haven't made a forum account sooner... I don't really know. I have been a Ubuntu user for some time now.  (Previously a Debian-user =X). I thought I should make a thread on the progress of the install, incase anyone else wants to install Ubuntu on their Kohji or need help with it... :)

Right now... My wireless device, doesn't seem to be detecting properly. I'll give you guys an update on that and screenshots soon!

---

### Post by Warren Watts on 2007-08-05
I had to Google it to figger out what in holy heck a "Kohjinsha SH6KB04A" was....

Pretty nifty little device....

Keep us updated on your progress with Ubuntu!

---

### Post by crazebenny on 2007-08-05
HAHA, yeah... it's pretty nifty!!! it had vista home addition installed. I couldn't wait to get rid of it ):P

I have attached a few screenshots from my treo, it's pretty poor quality... my bro is borrowing my digi cam at the moment.

PROGRESS:
Wireless, Touchscreen, TV, Camera not working out of the box.

---

### Post by crazebenny on 2007-08-07
Sorry been busy... I finally got the Touchscreen working.

Simply downloaded the Linux drivers from penmount.com

[http://www.penmount.com/down_2_1.php]("http://www.penmount.com/down_2_1.php")

It is the **PenMount 6000 Driver**, and guess what... there's one for Ubuntu!


Simply extract to folder and run the following script in the Drivers folder:
**sudo ./install.sh**

Configure it for Penmount 6000 [USB], you can customize your right click timing on the touch screen, etc.

Now after you've finished installing the drivers, simply restart X :)

---

### Post by dottydan on 2007-08-16
Great work!
Do keep us posted on your progress - would love to see the KH6 run Linux seamlessly!

---

### Post by crazebenny on 2007-08-21
Status:
Bluetooth works out of the box. 

To make things a bit easier in gnome install the following applications:

sudo apt-get install bluez-gnome gnome-bluetooth

restart gnome desktop and you'll see a pretty little bluetooth icon on your notification area

---

### Post by crazebenny on 2007-08-21
Screen Resolution:
To get the correct screen solution on the Kohjinsha (1024x600)

Type this in the terminal:

sudo apt-get install 915resolution
sudo 915resolution -l

and restart X :)



Side Note:
TV is noted as useless on Conics site. I guess the TV adapter only works in Japan? Skipping this until I can find further info.

---

### Post by crazebenny on 2007-08-21
Another Note:
SD Card works out of the box. I have yet to test CF. Don't have a CF card to test with =(
Directional Pad works
Brightness
Scroll buttons work on the screen

The FN buttons seem to work, but it's hard to tell if they're working or not besides checking the fan noise and the Bluetooth and Wireless lights on the screen.


What doesn't work yet:
Buttons: Launcher, Shutter, Rotation, Enter
Wireless (Gnome NetworkManager, iwlist scanning, damn rt73usb)

---

### Post by ziritrion on 2007-08-25
May I ask how did you install Ubuntu on it? I've just gotten a brand new Khojinsha SH6 and I have no clue about where to begin for installing Ubuntu and/or Windows XP instead of the Vista Home Premium that comes preloaded. Did you use a bootable pendrive? An external CD drive?

---

### Post by jeclarim on 2007-08-31
I just got  my Kohjinsha K601 (Korean version of the Japanese SH6) this week and I installed Ubuntu 7.04 Feisty on it :)

I did the install thru the network, setting up my other Ubuntu PC as a DHCP+TFTP server.

Wifi wasn't working out of box but it does now after I compiled Ralink driver version 1.0.4.0
See this page: [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73")

However, configuration is static with the default conf file /etc/Wireless/RT73STA/rt73sta.dat
and scanning wasn't working. I was able to fix that by changing source file rtmp_main.c
all #ifdef testing for WIRELESS_EXT <= 21 now instead of <= 20

About the special function keys on the right of the screen (Launcher, Shutter, Rotation), it's possible
to map them to execute shell scripts under Gnome desktop. First you have to map their scancodes (65, 5a, 66) to keycodes using e.g. setkeycodes 66 122 
Then with gconf-editor, you can change /apps/metacity parameters global_keybindings setting run_command_1 to 0xd2 (keycodes are different but you can get them with "xev") and keybinding_commands command_1 to a shell script path.
For example, Rotation key can launch a command "xrandr -o left" to change screen orientation

The webcam doesn't seem work. 
USB vendor/product id is 05c8:0109 Cheng Uei Precision Industry Co., Ltd (Foxlink)
uvcvideo module is loaded but cannot initialize the device :(

---

### Post by jeclarim on 2007-09-05
Latest CVS release of rt73 serialmonkey driver is now working on my Kohjinsha :)
I told them to add Qcom WiFi device USB ID 18e8:6238
You can get it here: [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)

---

### Post by crazebenny on 2007-09-08
So, 'iwlist scanning' works after you changed 20 to 21? I'm gonna have to try that. And thanks for the keymapping tip! =D

Also, about the post on installing Ubuntu on the Kohji, the easiest way is to just get a USB cdrom. I  have tried installing Ubuntu off a flash drive, but it kept getting a kernel panic. Or, try a network install =)

---

### Post by cybrough on 2007-11-18
I just installed 7.04 on my kohjinsha SA1.  It works ok except I have no sound in my applications, system sounds are ok.  Any ideas?  I tryed updating to 7.10 but    it will not boot.

---

### Post by Shiruban on 2008-02-19
Hi I am a happy owner of a kohjinsha SH8

I made another thread for some info on the ubuntu mobile edition, but couldn't wait and put  an ubuntu gutsy  on the little thing.

I am more or less at the same point : wifi ok, webcam no, touchpanel "ok"

for the touch panel, i could make it work with the driver from penmount website, but I cannot calibrate it. If I launch the advance or the standard calibration, it start the calibration screen and then crash forcing me to hard reboot... It is very annoying cause the edge of the screen are unusable like this.

For the webcam it seems that someone made it work with unicap modules (forgot the link) personnaly couldn't usb video is still loading I have to blacklist it perhaps. Will work on it. 

For the key map it is possible also to define it in compiz

Fn key for silent mode really works (i do not hear a difference)???

Suspend and Hibernate just reboot on a black screen. no idea?

For the tv i have no idea atm but living in japan I would like to use it but i will work on it later.

Too many problems still for a good usability, so many work to go don't know from what I should start...

Long time this  thread was not active but hope it will start again...

Yoroshiku

---

### Post by punong_bisyonaryo on 2008-02-26
I'm also consider buying a Kohjinsha SH. Oboyoboyoboy, I hope you get the other stuff working too! I'm getting pretty excited!:D

---

### Post by tdhedengren on 2008-03-01
I've got wireless, touch screen,correct resolution, sound, etc. working. Just remember to turn off all visual bling bling (ie set to none under Appearence) when you calibrate your touchscreen and you'll be fine.

Camera isn't working, and I have yet to figure out how to rotate the screen and program the launcher/shutter/rotation/enter buttons. It's fully ready for the road though. Now if I just could configure the keyboard my way, using Swedish layout but it's not 100% (sorry for all the weird ' for instance), and some keys are just not used.

Just an update for anyone curious. This thread's been a great help!

Oh, TV is 1seg which is Japan only. Not much to do there, eh?

---

### Post by punong_bisyonaryo on 2008-03-02
> **Shiruban said:**
> For the tv i have no idea atm but living in japan I would like to use it but i will work on it later.

I just got an SH6. Can you point me in the right direction or can we collaborate on getting the tv working? I'm currently in Japan and will be able to test it for a month before I leave, hopefully we can get it working within that time.

&#12424;&#12429;&#12375;&#12367;&#12397;:)

---

### Post by Shiruban on 2008-03-03
Hi sorry to not posted an update I was quite busy in the real life and decided to upgrade to hardy, give it a try though.
Now I am running hardy. the touchscreen works direct, the wifi also. The camera seems to work with v4l2,  i couldn't get an image but put I got a response from it. Camorama doesn't accept the v4l2 and so vlc so i will try with something else, perhaps amsn?? (don't know too much about v4l2 have to learn) the touchscreen was not calibrated and I think even under hardy we will have to install the penmount driver to have a calibration tool. Thanks for the tips on compiz and calibration I will try this as soon as I come back home
Unfortunately the upgrade to hardy (still in version alpha, do not install if ti is not to play) kill some other useful function, the gnome preference manager start crashing alot and I couldn't get the vga out working anymore. Well and finaly I killed my system by trying to install the hildon desktop...no good. 
This week I will work again under gutsy.
 I still have a problem with xrandr, the touchpanel is not turning with the screen and so it is not useable at all. I am looking for a way to synchronise them and it seems other people had the same problem with graphics tablet or synaptics touchpad.
For the tv, as this tv, what a mystery, I have no experience with tv tuner, so first thing I try blind, install some common driver, no chance, lspci cannot see the tv, lsusb neither, but where is it plugged? Under vista they use a software only for japan...so for the moment I am in the black. first thing I should find the model of the tv, and I will ask on the japanese forum if they know.

So in conclusion sorry no big good news, but it seems hardy will be a good thing for kohjinsha owner, once some small stuffs, are fixed. And the camera is on the good way. The touchscreen too (how didn't I though about removing the visual bling bling :) So now I am in the phase documentation, reading, googling, etc.

matane

---

### Post by punong_bisyonaryo on 2008-03-03
@Shiruban, thanks for all the info. I have not yet wiped out Vista only because so I can get information about the hardware components and the software used to run them.

I'm not sure if this will be useful to any of you guys, but the Vista device manager has this and I assume this is the tv tuner: SDB-T 1 Segment USB Adapter for Alps Nim (BDA) DigiBest Technology Co Ltd.

BTW, when you say the tuner is for Japan only, do you mean that the hardware itself can only tune in to Japan's 1seg? Or can a driver/software allow it to be useable in other countries?

---

### Post by punong_bisyonaryo on 2008-03-03
I installed Gutsy last night over Vista, and though I wanted to be able to recover Vista later on, stupidity dawned on me: you can't run the recovery tool without Windows Vista (what the hell??)! Is there another way to restore from the recovery partition? Please PM me if anyone knows how.

Anyway, I got webcam working...sort of...
I had a fresh install of Gutsy and had to do voice calls right away, so I assumed that the webcam was not yet working and proceeded to install my other USB webcam. I had to blacklist the zc0301 module because of [this]("http://ubuntuforums.org/showthread.php?t=583132") issue, and restarted. Afterwards, I ran Wengo, went to configuration, and tested my webcam.

The built-in webcam (FO13FF-68 PC-CAM, module uvcvideo) was in video0, and my A4Tech PK35N (Vimicro, module gspca) was in video1 (subsequent tries had the gspca as video0 and uvcvideo at video1. Not sure if this'll help). I accidentally forgot to select my USB webcam when I clicked the Test button. To my surprise, it worked! But I couldn't get it working again after that. All I do know at this point is that it can work, it just needs some playing around with the modules or something.

Also, I tried installing Pendrive this morning and encountered a few difficulties with permissions. I extracted it to my home folder as a normal user. First, the files had no write permissions so I had to sudo chmod a+x them. But afterwards, the script was still giving me permission denied errors. I did them manually, copying line by line from the script file, and was able to run pm-setup. However, it doesn't work. I restart my computer and the pen is still not working. Any ideas?

---

### Post by Shiruban on 2008-03-04
I came back too late from university yesterday night to be able to work on the small kohji

I am happy to see that the webcam is working. I think in fact it was working from the beginning (or perhaps  have to blacklist some modules) but the problem is that it is a v4l2 only webcam, so applications like camorama or other doesn't work. Looking in other threads on v4l2 webcam it seems that ekiga, amsn cvs, and cheese (never tried) work with v4l2, also xawtv. I will do some test as soon as I have time. wengo is still  in testing phase for the support of v4l2 camera, I use also wengo but we will have to wait on their side for a better support perhaps, you can try the nightly builds however.

The tv is a digibest tuner (even the software name under vista is digibestTV thanks for pointing me in the good direction, I am a little stupid sometimes. Now I don't know yet how to make it work under linux, still need many documentation. Oneseg technology is use in other country than japan? I am not sure if the korean version or the american one of the kohjinsha include a tv tuner, and if it is the same. I think it is easy to find if oneseg is available in your country too. for example do you have mobile phone with tv, or psp, nintendo ds and such other mobile devices ?

I had the same problems of permission with the penmount driver, had to chmod +x everything, even the pm_setup in /usr/sbin, strange, but after that it works.If you have still problem you can post your xorg, we will see if the pm_setup has worked.  thanks again for the tips on compiz, it works great.

It seems that we are quite a lot to play with the kohji and ubuntu hope we will make it fully works, especialy because it was chosen a typical McCaslin device for testing the ubuntu mobile edition ([https://wiki.ubuntu.com/MobileAndEmbedded](https://wiki.ubuntu.com/MobileAndEmbedded)). the best will be to have a typical ubuntu for production and a hildon desktop fro use as a tablet pc. Still a dream but possible.

I hope to have more time soon to work again on the kohji, yesterday I put back a gutsy, but that's all.

for the recovery problem, I have the same, I push f8 during the boot as it is written in the manual but nothing happens. I read a page in japanese where he gave instruction on how to recover and then try a linux, but my japanese is still poor and it was already too late. anyway could you get your windows in english or it all in japanese? mine is all in japanese, I chose japanese first time I booted it up, what stupid I am, it was to use it with my girlfriend, and I though that I could change later, but vista is not GNU and localization support is expensive (have to upgrade to ultimate) thanks for the internationnal people ... I will look more for the recovery problem but first I would like to focus on ubuntu.

---

### Post by tdhedengren on 2008-03-04
1seg is Japan only, and it's basically TV for mobile devices (I've got it in my Japanese PSP, but can't watch it from Sweden, obviously). I doubt that we can use the tuner for any other network, but it would be sweet if it was possible.

More about 1seg: [http://en.wikipedia.org/wiki/1seg](http://en.wikipedia.org/wiki/1seg)

As for recovering to Vista, I saved that partition as well, and pressing enter during startup gives me a menu where I can fiddle with these things. That should do it, you shouldn't need Vista DVDs or anything.

Vista is all Japanese in my Kohjinsha. Only Ultimate versions of Vista will actually let you change the system language, what you select in the install is just keyboard layout, agreement languages and things like that.

---

### Post by punong_bisyonaryo on 2008-03-04
Call me stupid, but I couln't get my Penmount working. I reinstalled Gutsy and was able to successfully run the install.sh, but after restarting my Kohji, it's still not working. What's wrong?

I also noticed that the penmount module is not being loaded when I check with lsmod. Should I manually add it to the modules?

I really want to get this fixed.:(

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"jp106"
	Option		"XkbLayout"	"jp,jp"
	Option		"XkbVariant"	"latin,"
	Option		"XkbOptions"	"grp:alt_shift_toggle,grp_led:scroll"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"PenMount"
	Driver		"penmount"
	Option		"Protocol"	"PM6000USB"
	Option		"Device"	"/dev/input/event0"
	Option		"PMode"		"1"
	Option		"MinX"		"10"
	Option		"MaxX"		"1000"
	Option		"MinY"		"10"
	Option		"MaxY"		"1000"
	Option		"ADBit"		"10"
	Option		"Beep"	"1"		#  0 = no beep, 1 = beep enabled
	Option		"PressVol"	"100"	#  volume of beep (press event)
	Option		"PressPitch"	"880"	#  pitch of beep (press event)
	Option		"PressDur"	"15"	#  length of beep in 10ms (press event)
	Option		"ReleaseVol"	"0"		#  volume of beep (release event)
	Option		"ReleasePitch"	"1200"	#  pitch of beep (release event)
	Option		"ReleaseDur"	"10"	#  len of beep in 10ms (release event)
	Option		"RightButton"	"1"	#  right button active in ms
	Option		"RightButtonStart"	"500"	#  right button active in ms
	Option		"RightButtonEnd"	"900"	#  right button inactive in ms
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	InputDevice    "Penmount" "AlwaysCore"
EndSection
```

Regarding 1seg, what's a good tv tuner program to test if it can detect the tuner properly? (I'm in Japan at the moment).

---

### Post by punong_bisyonaryo on 2008-03-04
@tdhedengren, I tried pressing Enter at startup and fiddling with the menus, I couldn't find anything to recover from the partition. What were you referring to?

As soon as I get my Penmount working, I'll start working on the webcam and the tuner. Damn this touch screen driver...

---

### Post by Shiruban on 2008-03-04
Hi every kohjinsha owner,

For the touchscreen, after running the install and restarting the x if it is not working yet.
open a terminal and type ```
 more /proc/bus/input/devices
```
then you should find something like this :
```
I: Bus=0003 Vendor=14e1 Product=6000 Version=0001
N: Name="DIALOGUE INC PenMount USB"
P: Phys=usb-0000:00:1d.3-2/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=js0 event2 
B: EV=b
B: KEY=30000 0 0 0 0 0 0 0 0
B: ABS=3

```

Please note the number following event in my case it is the event2
to check we didn't mistake in the number type, replace 2 by your actual number
```
xxd /dev/input/event2
```

When you touch the screen you should have some stuff written in the terminal. If yes go to next step if not go back to first step. 

Now that we know the good number of event associated with the touchscreen we have to change it in the xorg, penmount put by default event0 but it is not always the case.

```
sudo nano /etc/X11/xorg.conf
```

Here is my xorg.conf adjusted to the right event.
```
sylvain@kohji:~$ cat /etc/X11/xorg.conf 
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "jp106"
        Option          "XkbLayout"     "jp,jp"
        Option          "XkbVariant"    "latin,"
        Option          "XkbOptions"    "grp:alt_shift_toggle,grp_led:scroll"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection


Section "InputDevice"
        Identifier      "PenMount"
        Driver          "penmount"
        Option          "Protocol"              "PM6000USB"
        Option          "Device"                "/dev/input/event2"
        Option          "PMode"                 "1"
        Option          "MinX"                  "10"
        Option          "MaxX"                  "1000"
        Option          "MinY"                  "10"
        Option          "MaxY"                  "1000"
        Option          "ADBit"                 "10"
        Option          "Baudrate"              "19200"
        Option          "Beep"                  "1"             #  0 = no beep, 1 = beep enabled
        Option          "PressVol"              "100"   #  volume of beep (press event)
        Option          "PressPitch"    "880"   #  pitch of beep (press event)
        Option          "PressDur"              "15"    #  length of beep in 10ms (press event)
        Option          "ReleaseVol"    "0"             #  volume of beep (release event)
        Option          "ReleasePitch"  "1200"  #  pitch of beep (release event)
        Option          "ReleaseDur"    "10"    #  len of beep in 10ms (release event)
        Option          "RightButton"   "1"     #  right button active in ms
        Option          "RightButtonStart"      "500"   #  right button active in ms
        Option          "RightButtonEnd"        "900"   #  right button inactive in ms
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse""
        InputDevice     "Synaptics Touchpad"
        InputDevice    "Penmount" "AlwaysCore"
EndSection

```

As you can see I removed all the stuff concerning the wacom...

After this it should work.

Little report of my ubuntu on kohjinsha, after a fresh reinstall of gusty :
5 min to get the wifi working
10 min for the touchscreen, including calibration
the camera work out of the box but is v4l2, it means only compatible applications will work, I tried with ekiga and cheese no problem, good quality. If it seems to not work, in cheese, it means it is off, just push fn f5 one time and restart cheese. To monitor the state of your camera just install cameramonitor, it is a small applet that will tell you if your camera is off or on

Still missing good rotation with xrandr, TV, silent mode, and suspend...

As a small utility, for using as a tablet, we need an on screen keyboard or hand writing. Two are available, gnome-on.screen-keybord (GOK) in the repo, but it is only a very good keyboard, and cellwriter [http://risujin.org/cellwriter/](http://risujin.org/cellwriter/) just install the deb it works, very good after training it recognize more than half of my bad writing, didn't try japanese yet

Another tips, don't forget to use the fullscreen mode of firefox, f11, and the enhanced zoom of compiz, super R, zoom on the active window, very useful

Enjoy, I think now kohjinsha is fully ok to hit the road, as it was said previously...:)

---

### Post by punong_bisyonaryo on 2008-03-04
@shiruban, thanks a lot for the guide! My pen now works after setting it to the right event (mine is also event2). I'll try to work on my Kohjinsha after I get home from work. I will see if I can find anything about the 1seg tuner, and/or get the webcam running.

---

### Post by Shiruban on 2008-03-04
nice to hear it works,

Still couldn't find anything on the oneseg, tonight I will try on the japanese forum...

The camera is already working , I hope, I will try wengo tonight too...

Now before focusing on the tv I  would like to make work the suspend to ram, hibernate works out og the box, but not suspend, very bad for a mobile device... no idea around here? I tried some stuffs but nothing did : disabling compiz some modif of xorg and sleep.sh...

---

### Post by tdhedengren on 2008-03-06
> **punong_bisyonaryo said:**
> @tdhedengren, I tried pressing Enter at startup and fiddling with the menus, I couldn't find anything to recover from the partition. What were you referring to?

Ah, my bad! I got the option because I had an external DVD with a Windows install disc in, which asked me if I wanted to revert. Sorry. :oops:

---

### Post by punong_bisyonaryo on 2008-03-06
I wasn't able to work on my Kohji recently, but confirmed it uses uvcvideo, which does not support v4l1. CF card is also confirmed working.

BTW, sometimes when I reboot, my touch screen event changes. Sometimes it's event2, sometimes event4. Any ideas here? Also, I can't seem to calibrate my screen properly. I run the calibration, I press on the little squares, but after that I still cannot access the edges of the screen.

I installed Klear and XawTV, they wouldn't work, but I haven't tinkered with them yet.

@tdhedengren, would an XP install disc do or do I need to acquire a Vista disc?

---

### Post by Shiruban on 2008-03-06
Hello

the event should not change after reboot...it has never happen to me... Perhaps are you plugin an external mouse or keyboard that take the event of the touchscreen ? I will look to see if it is possible to fix in hard the event number.

After calibration me too I still have problem to reach the very edge of the screen but it seems it is a limitation of the kohjinsha, I read that people has also this problem under windows. But for me it is not so bad, it is very useable. perhaps you should do again the calibration.

I didn't advance on the problem of suspend, it  is still crashing when waking up and nothing for the tv  too...

some little tips I found :
To assign the different buttons like launcher, shutter and rotation you can follow this guide :[https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys) . the buttons are not mapped so we have to map them. Then you can assign the buttons to a command in compiz.
To rotate the screen with xrandr have to disable compiz, it is then working very well but the touchscreen is not turning, I mailed penmount to know if the linux driver support rotation and how to set it up, still no answer.

good luck

---

### Post by tdhedengren on 2008-03-09
> **punong_bisyonaryo said:**
> @tdhedengren, would an XP install disc do or do I need to acquire a Vista disc?

It might work with an XP install disc, I got the question but didn't go for it, as I needed my XP partition working for sure for a trip. If you give it a go, let me know how it went!

---

### Post by punong_bisyonaryo on 2008-03-12
I've been so busy recently, haven't made any progress whatsoever.

Last time, stupid me, I was running the calibration program but not as root, that was why I couldn't reach the screen's edges. My touchscreen still switches between event2 and event4 every now and then. I don't have any external usb device connected.

I also installed the wifi driver from the serialmonkey website, unfortunately I've not been able to test it due to lack of hotspots. Say, when you install the wifi driver, do you have to scan via terminal or will the GUI work?

---

### Post by Shiruban on 2008-03-12
Hi everybody

The wifi is working through the gui, network-manager. You don't have to set manualy anything it is just finding the network alone.

I had the same problem of switching event number and I solved it, I started by googling it, find a thread on a similar problem with a remote control, read udev manual, and with some inspiration made it work

Shortly we have to say to udev to create a symlink to use instead of the eventX.
How to do it

```
sudo nano /etc/udev/rules.d/60-symlinks.rules
```
then add at the end:

```
#create a symlink for PenMount
SUBSYSTEMS=="usb", ATTRS{product}=="PenMount USB", SYMLINK+="input/touchscreen"
```

Then modify the device field of penmount in xorg.conf, replace eventX by input/touchscreen

```
sylvain@kohji:~$ cat /etc/X11/xorg.conf 
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "jp106"
        Option          "XkbLayout"     "jp,jp"
        Option          "XkbVariant"    "latin,"
        Option          "XkbOptions"    "grp:alt_shift_toggle,grp_led:scroll"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection


Section "InputDevice"
        Identifier      "PenMount"
        Driver          "penmount"
        Option          "Protocol"              "PM6000USB"
        Option          "Device"                "/dev/input/touchscreen"
        Option          "PMode"                 "1"
        Option          "MinX"                  "10"
        Option          "MaxX"                  "1000"
        Option          "MinY"                  "10"
        Option          "MaxY"                  "1000"
        Option          "ADBit"                 "10"
        Option          "Baudrate"              "19200"
        Option          "Beep"                  "1"             #  0 = no beep, 1 = beep enabled
        Option          "PressVol"              "100"   #  volume of beep (press event)
        Option          "PressPitch"    "880"   #  pitch of beep (press event)
        Option          "PressDur"              "15"    #  length of beep in 10ms (press event)
        Option          "ReleaseVol"    "0"             #  volume of beep (release event)
        Option          "ReleasePitch"  "1200"  #  pitch of beep (release event)
        Option          "ReleaseDur"    "10"    #  len of beep in 10ms (release event)
        Option          "RightButton"   "1"     #  right button active in ms
        Option          "RightButtonStart"      "500"   #  right button active in ms
        Option          "RightButtonEnd"        "900"   #  right button inactive in ms
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option "VBERestore" "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
        InputDevice    "Penmount" "AlwaysCore"
EndSection

```

Reboot and it should work!

Still two problems:
High priority : Fix suspend
Low priority : oneseg tv, but I think without big coding can't.

Tips of the day : 
Using elisa as media player in very cool in tablet mode
Replacing gnome-panel by avant-window-navigator is very good to use with the fingers and very eye candy, if you want to remove all panel but keep function as alt+F2 to launch run command I can explain, but now I am going to bed, sorry.

When I will have time I want to make a video to show the world ubuntu on kohjinsha, but not soon because next week I will be in business trip so now I am really busy.

Have fun

---

### Post by zaeku Park on 2008-03-12
Yesterday. I tested the hardy on my k800(korean version of SH8 series).
Impressively, many devices work well without additional drivers installation.

RT73 wireless lan work as wireless in roaming mode(in 7.10, It's required driver and it dosent work in roaming mode.), webcam is well go on (I checked in skype), and bluetooth's too.

but still have some problem. first, I cannot calibrate the penmount touch screen. I work without additional driver and if I install additional driver it doesnt effect anything. second I cannot use the mike. and last, the buttons in right of screen, launcher, shutter and rotation are doesn't work, neither.

I think the 2nd, and 3rd problem is not big problem. Maybe it easily solvable. But first thing is big problem to me.
I hope next version of ubuntu provide calibration utility.

---

### Post by tdhedengren on 2008-03-13
> **zaeku Park said:**
> but still have some problem. first, I cannot calibrate the penmount touch screen. I work without additional driver and if I install additional driver it doesnt effect anything. 

If you follow the instructions for calibration in this thread, and make sure you disable all visual effects, it'll work just fine. That latter thing is the key.

---

### Post by Shiruban on 2008-03-13
At Zaeku :
as thedengren said just follow the instruction in this thread and you will find all the instruction on how to make work everything except the television and suspend... but it is for gutsy. I tried hardy alpha 4 but there was too many problem to use it in productivity, so I returned to gutsy. 
Perhaps you can tell us does suspend work with hardy? Also do you have TV on the korean version, if yes what type? 
For the button me I mapped them to F86Launcher and then through compiz, in general option, command, bind them to button launcher : cellwriter, shutter cheese, and rotation expo plugin. Enter is already mapped to enter keyboard, so if you want to change you have to change the keycode.

For everybody, the touchpad is unfortunately **still** jumping, **it is not working 100% yet**, I talked too fast sorry[-(. Today after reboot it is agin not working, I will work on it more but I think the udev symlink is the good way. Perhaps we have to say to the driver too to look for the symlink ??? I will investigate more

---

### Post by punong_bisyonaryo on 2008-03-20
I brought my Kohjinsha on a bus trip to Tokyo, hoping to do some work on the road. While the touchscreen occasionally needs fiddling with to get working, but not really a big hassle. The Kohjinsha is perfect for the road warrior.

What got me in a pinch though, was that the wireless driver seems not be working perfectly (I wasn't able to test it at home, because I'm wired there). From the network manager applet, sometimes it detects WiFi spots, sometimes it doesn't. When it doesn't, I tried "Connect to Other Wireless Network", enter the essid etc. I'm not sure if it's a problem with the driver, or because WEP-128 bit passphrase is not supported (man iwconfig says it's not supported). I also was not able to find a WIRELESS_EXT <= 20 in the source, so I tried replacing the similar looking WIRELESS_EXT < 17 with 21.

---

### Post by geoSol on 2008-03-25
Hi all

I have the SH8 model of the kohjinsha running xubuntu 7.10. Since I couldn't get suspend working and the wireless is a little flakey, I decided to give the ubuntu Gutsy Beta a whirl last night. Here's the results:

wireless working out of the box, WEP, WPA and WPA2 working
touchscreen working out of box, uncalibrated
sound works out of box
display mirroring working out of the box
hibernate working out of box
suspend sort of working - under 7.10, the Kohjinsha would hang on recovery. Now it seems like it goes all the way back up but the display remains off. Will see if fiddling with /etc/defaults/acpi-config will get some setting that works. 

Regards

---

### Post by geoSol on 2008-03-26
Hi all

Suspend now works on my Kohjinsha running ubuntu Hardy Heron Beta.

Go to /etc/default/acpi-support 

and change the line

POST_VIDEO=true 

to 

POST_VIDEO=false

enjoy your suspend!

---

### Post by punong_bisyonaryo on 2008-03-27
Hmm, I just might try out the Hardy Beta, if so much works (especially Wifi). BTW, do you calibrate the touch screen as in the old penmount driver way?

---

### Post by geoSol on 2008-03-27
the touchscreen cannot be calibrated with gCalib in my setup. However i think it has something to do with me having 2 window-managers installed. (Gnome & XFCE) the other thing is that this is a beta and I suspect that gCalib will be re-written for Hardy by the penmount people.

Wireless works via GUI, i just verified it with open-access, WEP, WPA, WPA2 and VPN(PPTP).]

volume button also works. (it didnt work under xubuntu gutsy, which is a mystery to me, because XFCE uses the same gtk applets)

PS. if any of you want to install the xbunutu-beta, then the wireless (nm-applet) WONT WORK. you need something that GNOME provides (cant figure out what it is). If you want to run XFCE, which is way faster on your Kohjinsha, install the Ubuntu Hardy Heron beta first, then do

sudo apt-get install xubuntu-desktop

perhaps someone can try doing a clean install of ubuntu hardy and running gCalib?

---

### Post by punong_bisyonaryo on 2008-03-28
I do hope the calibration utility gets re-written for Hardy. Anyway, unfortunately I won't be able to try out Hardy until middle of next week, since I don't have my external optical drive with me right now, and other install options aren't available as well (no big enough usb disk, no network install PC). I'll try this one as soon as I can. I wonder if Shiruban and the others could try this out?

---

### Post by tdhedengren on 2008-04-02
I installed the beta today, same result as previous poster. Could give gCalib a go if someone tells me what/where it is. :)

However, the panels seems to be reloading themselves every now and then. A beta issue or what?

---

### Post by geoSol on 2008-04-02
gCalib is a calibration utility that is provided by penmount. it is found on the penmount driver website.

After speaking with the penmount people, i've been told that they are aware of gCalib not working on Hardy, and they are working on a new updated driver (phew it wasnt my setup)

As for the screen redrawing, I don't have that issue. Perhaps you might want to try and turn off effects?

---

### Post by tdhedengren on 2008-04-04
Ah, so it was Penmount. Roger that, I know about that one.

Good regarding the driver by the way. Then I won't give it a go just yet.

I'm going to play around with settings some more. It is probably the effects making it funky. However, they worked perfectly well with the previous Ubuntu version (7) so I just wondered if others were having the issue as well.

---

### Post by punong_bisyonaryo on 2008-04-06
Damn, need to get me a new batch of CD-Rs. I must've bought a bad batch; none of them are working, on any writer I have.Anyway...

Does the mic work in Hardy? That's one of the important features for me right now, since I can't do video calls without a working mic.

---

### Post by Shiruban on 2008-04-11
Hi back in the place and ready to work on the kojinsha !

After some time working (for my  thesis, not for ubuntu) on it with gutsy I am quite happy of it, but as punong_bisyonaryo pointed out the mic is not working, i didn't realise it before making a video call, and I didn't brought a mic wit me. I am a little bit ashame but on this windows save my life :lolflag:

When I was in trip I saw that the hardy beta was out and was impatient to try it on my kohji. Moreover I see that you got some good results : especially the suspend! Great thank you so much  geoSol !

Also I got an answer from penmount, I mailed them about the impossible rotation, and the jumping touchscreen, they told me that they have a kohji SR and they are working on it, trying ubuntu Hardy! So we can expect some amelioration but when..?

Enough talking, the iso is soon finish to download : let's work ! I will make a complete reinstall with hardy beta :)

See you soon

---

### Post by cstross on 2008-04-13
> **geoSol said:**
> Hi all

Suspend now works on my Kohjinsha running ubuntu Hardy Heron Beta.

Go to /etc/default/acpi-support 

and change the line

POST_VIDEO=true 

to 

POST_VIDEO=false

enjoy your suspend!

Doesn't work for me. (Machine: SH6WP10A. OS: Ubuntu Hardy Heron 8.04 RC, upgraded from 7.10, Kernel 2.6.22-14). Not sure this isn't an older kernel left over from 7.10 -- any ideas?

---

### Post by geoSol on 2008-04-13
You don't have the right kernel - are you sure you upgraded the machine? Ubuntu Hardy ships with a kernel linux-2.6.24-12-generic. 

Try running your update again. 

also, you need to modify the file with something that has root permissions, and restart X. 


I hope that they fix the rotation issue, but in Gutsy I had script that ran gCalib when i did a rotate. The problem is not that the screen rotation is broken, its actually behaving correctly. You'll understand what i mean if you try to rotate the screen on a normal PC. the mouse axis does not change. I think the underlying problem is that the kohjinsha touchscreen is installed as a normal mouse, and therefore flips in the same way as all the normal mouse when you use the xrandr command. 

Anyway, I dont have the script i used in gutsy with me right now, but if anyone wants it let me know.

---

### Post by Shiruban on 2008-04-14
So the results of the install of hardy :

wifi : OK out of the box

supend : OK out of the box (didn't modify anything, it just worked after installation and dist-upgrade, new kernel)
hibernate : Ok out of the box
Just one thing is strange : I set up to suspend when close the lid but it only works one time after a reboot, after I close the lid but screen turns black but no suspend?? am i alone with this?

touchscreen : working but impossible to calibrate it, tried with the old driver too bu no... can't use at the moment

camera : work with ekiga, but not anymore with cheese : it turns it on then before displaying image turn it off, submitted a bug

integrated microphone : not working

no sound in firefox when playing flash, seems to not be specific to kohjinsha, but more to firefox beta 3 and flash.

also very low volume level on the headphone output. Mic, vokume and sound in firefox might be correlated : the kohjinsha is equipped of a HDA intel with a Realtek ALC262 for soundcard and it seems there is quite a lot of problem with it. Following[ this]("https://help.ubuntu.com/community/HdaIntelSoundHowto") I am now trying different model to see which fit the best our little kohji.

conclusion two big improvement with suspend and wifi, but no luck for the touchscreen, may have to wait from the penmount people a new driver...

Finaly concerning the ubuntu mobile edition it seems, that our kohji is not a test machine finaly. They test only on the samsung Q1 and they focus on the new processor menlow of intel, no luck, we bought it to fast. But some people used ume on kohji and only got problem with the hardware, so if we solve the pb of hardware we have here it might be possible to run it anyway :)

---

### Post by geoSol on 2008-04-14
Hi

I dont have any issues with the audio - i've watched the clone wars trailer on it this morning, although you're right the mic doesnt work. try this command in console:

%alsamixer

a curses based gui interface should come up and you should be able to adjust all the volumes properly. remember that alsa driver settings are OFF by default. I have managed to the the volumes up to the usual levels with this interface.

Regarding Ubuntu mobile edition - i'm not sure that it is even a useful thing for the Kohjinsha - full ubuntu works fine. If you really wanted the same effect you could just set the icons to larger when the penmount driver is fixed. no issues there. Ubuntu mobile edition is basically an interface for ubuntu that gives you nice big icons that you can poke with your finger.

---

### Post by nekocafe on 2008-04-14
Hi,

I'm wondering about buying a kohjinsha and have some questions after having read this thread. Thanks in advance if you have a little time ^^


How long does the battery last with a stock ubuntu ? And with some power management optimizations ? Does anyone have these numbers with the bigger battery ?

From what I understood, suspend and hibernate are now working. How long does it take to come back from suspend mode to a fully operational desktop ? And from hibernate mode ?
By the way, do you know how much power does the suspend mode use ?

Can all the buttons around the screen be used ? (yes in gutsy from what I've seen ?)

I've seen some were able to rotate the screen with xrandr. Has someone been able to rotate the screen "live" (during a working session) ? Does X handle that without any problem ? What about opened windows ?
And the problem with the touchscreen not rotating is only with hardy or also with gutsy ?

Does the "silent" key work ? (some say yes, others say no)

Last question : for the moment still nobody has been able to use the tv tuner ?

Sorry for all these questions !


The Penmount people seem very cooperative and linux friendly, that's nice ! (and so uncommon ...)

---

### Post by geoSol on 2008-04-14
I've a SH8 model kohjinsha loaded with Ubuntu Hardy beta. Here are some figures (with no optimizations)

I've never actually been able to run it to flat because of the way I use the machine, but the longest I've had with the machine on battery was 2 hours, and it seems to still have some life left. (on a standard battery) I'm not sure how you would like to measure power consumption during suspend - perhaps you could read the documentation for the A110 chip on the intel website and it will give you the wattage for Low Power Mode.

Suspend to working is almost instantaneous (5 sec maybe?) Hibernate is closer to a full boot. It takes my machine around 30 sec to boot up with a vanilla kernel

The buttons on the screen are mapped to regular keyboard events with the exception of rotate and shutter. You can assign events to these yourself. The details are in the thread.

xrandr works live. I'm not sure what exactly you're asking. You just type the command in console and it will rotate the session immediately

like i said before, the touchscreen is actually behaving correctly because its identified as a "mouse". However, for the touchscreen to match the new rotated screen dimensions it needs to be identified as something else so that the x-y ordinate mapping can match the viewable area.

---

### Post by Shiruban on 2008-04-15
Hi everybody

Thanks for the answer geoSol, in fact the sound problem appears only after suspend. I haven't check again the volume of earphone but when I saw the problem my first reflex was the alsamixer and all up, however no change... I will check tonight  here i don t have any earphone.
**Edit :** earphone volume OK now.... but after suspend it is not only firefox but no sound at all!

for ume it was just by geek pleasure that I wanted to try it, as you can see in the screenshot attached I solved the problem with avant-window-navigator

BUT i found another problem that can be really serious for those who take the plane : I can't stop the wifi, Fn F4 has no effect, so I try to switch off using the front switch, but wifi still on. I am now writing with all off! can somebody confirm this. I though the front switch was physical but it doesn't seem : shock! also it may decrease the battery life. 

For nekocafe, I can't tell you the exact battery life but I used continuously the kohjinsha in the shinkansen and air plane (under gutsy) for almost 3h if I cumulate. and now with hardy my kohji is always suspended and i wake it up sometimes and it last more than one days if I don'tuse it much, so suspend doesn't consume a lot.... nekocafe, are you japanese or living in japan? because tv is japan only. Anyway no hint to use it under linux...

---

### Post by nekocafe on 2008-04-15
Hi geoSol and Shiruban,

Thanks to both of you for your answers (and thanks a lot to geoSol for your very detailed answer).

> **geoSol said:**
> xrandr works live. I'm not sure what exactly you're asking. You just type the command in console and it will rotate the session immediately

I meant I've never made any rotation with X (never had to  ^^ ) and I wondered how windows already opened when you rotate will behave. For example if you have a Firefox window opened in landscape mode (with a width of more than 600 pixels), how does it appear after the rotation ? Is its width automatically reduced to 600 pixels or is it a bit "out of the screen" ?


> **Shiruban said:**
> nekocafe, are you japanese or living in japan? because tv is japan only. Anyway no hint to use it under linux...

I'm living in Japan so that's why I was asking the question.

As you're in Japan too, do you know if the E-mobile offer (internet access through mobile communication) works under Linux ? I saw a specific soft that was used in Windows to initiate the connection, but I didn't check yet if it was just a frontend to standard initiation/connection protocols (that's what I think), and so connection could be easily managed in Linux, or some proprietary black magic.


PS : I saw your first name in your screenshot and now understand the origin of your nick. I'm really not yet accustomed to the "japanisation" of foreign names and words  :mrgreen:

---

### Post by geoSol on 2008-04-15
Hi

xrandr rotates the session by mapping ((x=0, y=0), (x= 1024, y=600)) to ((x=0, y=0), (x= 600, y=1024)) on the axis. Since window location is determined by the topmost left corner, this means that what was previously (x=10, y=20) is now applied with the rotation matrix to get the new ordinate. Size is not considered.

What this means is that it is entirely possible to have windows out of the viewable area due to the application of the rotation matrix. However, in practice what usually happens is that the windows appear partway offscreen. This does not affect windows in full screen mode as the rotation (x=0, y=0) produces the same result, and the size is defined as the screen area, which is a constant. Any taskbars obey the rule "from top" and "from bottom" so they will always appear how you expect them to.

Hope this answers your question.


Oh I noticed that with the volume as well - you need to restart the sound server. 

I fix that with this command at the command line: 
"/etc/init.d/alsa-utils restart" and it works. 

I was messing with trying to determine which of the modules is not getting initialised properly on resume from suspend, but I havent had time to look at it properly. 

The idea is that the problem occurs because the sound subsystem does not shut down properly, resulting in stale handles that are then used by alsa. The fix is to identify the problem module and unload it during the suspend process by specifying it in /etc/default/acpi-support. however, there are alot of sound modules "lsmod", and so i havent been able to isolate the one with the problem.

---

### Post by Shiruban on 2008-04-16
thanks geoSol for the tips for the sounds. I found it also on a thread on problem with hda. I am not on the kohjinsha now but there maybe a module that concern specifically the hda... I am trying different model to add in the alsa-base to try to make work the internal mic but no luck until now, well I tried only 2 as now, not much time...However I saw that in the new alsa they added support for the samsung Q1 premium something, with some luck it may work for the kojinsha?? Will try to upgrade if no model works...when I will hve some time.

Nekocafe, you don't understand yet katanago ;), it will come soon... With my name because they couldn't pronounce it they soon changed it, now i even have an hanko with it and shiruban is registered as my japanese name!! Usualy on forum I use seal20 (if you speak french you may understand) but it was already used so I used Shiruban.
 Well enough for nickname but to answer your question i never  tried the e mobile, but the harder may not be connection but more that the card is detected. If you are thinking to invest you may check on the subject connection 3g because it is what it is and this is not japan only. But be careful I have a friend (he is using mac) who has it and if you use it as your main internet you will soon reach the maximum price, to stay at the minimum you need to surf a little and check some mail, but forget downloadig your favorite linux or spending your time watching video on youtube. Perhaps punong_bisyonaryo bought the kohji with the e mobile discount at yodobashi camera, i think I read this on his blog, so perhaps he knows. If he comes by here he may tell you. 

Another things about the rotation of the screen, geoSol made a perfect explanation so I will add my personnal experience only. in fact I do not used it or need it because it is useful to read ebooks or pdf and in adobe reader or fbreader (to read plucker file, that you can download a lot on gutenberg project website) you can change the orientation of the text. So finaly the rotation may be useful only for firefox, sometimes...

Ciao everybody and I hope penmount will fix the touchscreen for hardy release...

---

### Post by punong_bisyonaryo on 2008-04-16
I don't know about E-mobile. I got my Kohji from Sofmap in Nipponbashi, and what they were offering was a packaged Yahoo!Broadband.

My Kohji is still on Gutsy, I've been very very busy these days, but I'm happily using my Kohji despite the Gutsy limitations. I'm glad everybody's gathering around and making good progress with Hardy m(_ _)m   I can't wait to try them out myself!:D

Mata ne:D

---

### Post by geoSol on 2008-04-17
Hi,

I don't know if its a setting or something, but avant-window-navigator breaks xrandr. Just a heads up. The rotation will work, but the screen will not update. I originally thought it was a compositor problem, but after uninstalling avant-window-navigator, the rotation works properly with compiz

Regards

---

### Post by punong_bisyonaryo on 2008-04-27
Finally, I've been able to try Hardy on my Kohjinsha. As Shiruban mentioned, the WiFi doesn't seem to turn off. Also, the mic still has a problem. Cheese works fine out of the box. So far so good. Now if only we can get that touchscreen calibration and Oneseq tuner...

---

### Post by monti on 2008-05-12
I got this answer from penmount today when I asked about the availability of a touch screen driver and calibration program for Ubuntu 8.04:

> Dear Sir

Thank you for your email.
Currently PenMount supports Ubuntu 7.10 and earlier versions.
The Driver for Ubuntu 8.04 is still under development,
we will update it on our website when it is ready
Thank you.

Best regards,

Kent 

---

### Post by SnappyU on 2008-05-15
Penmount ... where are you ... can't wait ... :)
Now, should I revert to 7.10? hmmm... ...

---

### Post by punong_bisyonaryo on 2008-05-15
I'm eagerly awaiting that driver as well. I emailed them just now, to put a little more pressure, and to tell them that "hey, you have Linux-users using your product". Hopefully, they put more resources into finishing that driver more quickly.

In the meantime, has anyone gotten their Oneseg tuners working? I'm currently not in Japan so I can't play with it right now.

---

### Post by punong_bisyonaryo on 2008-05-17
Would anyone know if Wifi now works out of the box in Gutsy? (Are there still fixes being made in Gutsy since Hardy is already out?). The major factor for me to upgrade my Kohji to Hardy is only for the Wifi, which for me was really important. So I'm currently contemplating going back if I can get wifi working (or at least till Penmount drivers are out, I'm finding Hardy a tad slow).

---

### Post by monti on 2008-05-23
I received a beta version of the Penmount driver for 8.04 today (pmlinux-ubuntu beta1 20080522.zip).  I'll try it tonight and post some results.

---

### Post by punong_bisyonaryo on 2008-05-23
> **monti said:**
> I received a beta version of the Penmount driver for 8.04 today (pmlinux-ubuntu beta1 20080522.zip).  I'll try it tonight and post some results.

Could you tell us where you got the driver? I'd also like to test it out.

---

### Post by monti on 2008-05-25
I got it from the developers at penmount.com.  

Get it from [http://www.yousendit.com/transfer.php?action=download&ufid=705C652A78290FFE](http://www.yousendit.com/transfer.php?action=download&ufid=705C652A78290FFE) (it's there for 7 days).

The driver worked great for me, just follow the instructions in readme.txt and reboot afterwards.

---

### Post by monti on 2008-05-26
I got this answer from penmount.  Great news!

> Dear Sir,

Thank you for your email,
we are glad to see the driver works fine on your machine.
Currently we are planning to commit the updated source of our driver to
X.org, so it can support all the PenMount control boards.
Thank you again for sharing ideas on improving our product in the future.

Best Regards,


Kent 

---

### Post by punong_bisyonaryo on 2008-05-26
> **monti said:**
> I got this answer from penmount.  Great news!

Please relay our appreciation to their company for being one of the few supporters of Linux.:)

---

### Post by punong_bisyonaryo on 2008-06-05
I noticed today that headphone volume is now ok. must've been one of the updates.

Has anyone heard of [Remix]("http://arstechnica.com/news.ars/post/20080604-hands-on-with-the-ubuntu-netbook-remix.html")?
Looks nice, maybe better than UME.

---

### Post by punong_bisyonaryo on 2008-06-05
I've just tried the beta driver from Penmount (20080526 version). Seems I'm having a few problems with it:

1. If I add Option          "Device"           "/dev/input/mouse2" 
, my mouse and pointer (the one on the left of the screen) stops working.
2. If I don't put #1, clicking on the desktop leaves selection boxes on it. Click behavior is also unstable.

Otherwise, calibration is good.

How did everyone else's Kohji go?

---

### Post by monti on 2008-06-06
FYI, I received this bulletin from Penmount today:
> Bulletin No. PMY08020
	
Released Date&#65306;Jun  4, 2008

PenMount Driver Supports the Latest Linux Operating System

At present, there are some latest Notebook products using Linux as the default operating system in the market. Some of the primary advantages are that there are no licensing fees for Linux system and the new version of Linux is able to provide a user-friendly operation. The latest products such as ASUS Eee PC and HP Mini-Note are pre-installed with Linux as the default OS. We believe this type of products will continue to grow as there will be more Notebook and desktop system choosing Linux OS  in the future. Moreover, many peripheral devices, like PenMount also provide drivers to support the latest Linux OS.

The latest Linux release for the first half year of 2008 is kernels 2.6.24 and 2.6.25. For examples, Ubuntu 8.04, Mandriva 2008.1 and Slackware 12.1 use  2.6.24, while Fedora 9 and openSUSE11.0 use 2.6.25. These Linux operating systems  are able to manage the input devices systematically and support hot-plug feature for USB devices and SATA hard disk. It can provide 3D effect under the latest X Window application. In Ubunta 8.04, the installation can be set-up easily and user may install directly in the Microsoft Window platform. This enables the user who is familiar with Windows OS originally to adapt the Linux OS quickly. Ubuntu 8.04 also provides a three year service and support thus encouraging enterprise user to change to Linux.

Most of the updated Linux kernel release are much more user friendly on device control. The USB HID Device Manager Program can detect hot-plug and able to make classification on the device type, therefore, when under the X Window it is able to load the correct driver for plug in device. But this USD HID device detection feature is not perfect, it will classify PenMount device as a mouse device by mistake. Thus, the PenMount device operates incorrectly by behaving like a mouse&#8217;s relative coordination method when under X Window.

For Linux kernel to detect PenMount correctly when installing the PenMount 6000 and 5000 series USB interface, the easiest way is changing the mouse settings in X window configuration file (xorg.conf). This is to ensure the default mouse driver will not control the plug-in PenMount device. Please read the &#8216;readme file&#8217; and follow the instructions described before installing the PenMount driver.

For more PenMount controllers and drivers information, please visit our websites: [http://www.salt.com.tw](http://www.salt.com.tw) and [http://www.penmount.com](http://www.penmount.com). Please feel free to contact us at our email address [email]salt@salt.com.tw[/email] or [email]service@penmount.com[/email] .

Salt International Corp.

ADD&#65306;7F-1, No, 92, Bao-Jhong Road, Shin-Dian City. Taipei 231, Taiwan

TEL&#65306;+886-2-2914-6684

FAX&#65306;+886-2-2911-5345

E-mail&#65306;salt@salt.com.tw

---

### Post by punong_bisyonaryo on 2008-06-30
After several months, WiFi still doesn't turn off (either softswitch or the Wireless slider), also my touchscreen still ain't perfect. Sound sometimes disappear after coming out of standy. Anyone filed a bug report? I will if there are none. How's everyone else's Kohjinshas doing?

---

### Post by kazzttor on 2008-07-06
> **punong_bisyonaryo said:**
> @Shiruban, thanks for all the info. I have not yet wiped out Vista only because so I can get information about the hardware components and the software used to run them.

I'm not sure if this will be useful to any of you guys, but the Vista device manager has this and I assume this is the tv tuner: SDB-T 1 Segment USB Adapter for Alps Nim (BDA) DigiBest Technology Co Ltd.

BTW, when you say the tuner is for Japan only, do you mean that the hardware itself can only tune in to Japan's 1seg? Or can a driver/software allow it to be useable in other countries?

Hi there,

Here in Brazil, we use the japanese Digital TV system and this tunner is sold as AOC ConnectTVDigital and I need the driver for use it on linux.

---

### Post by punong_bisyonaryo on 2008-07-06
> **kazzttor said:**
> Hi there,

Here in Brazil, we use the japanese Digital TV system and this tunner is sold as AOC ConnectTVDigital and I need the driver for use it on linux.

I found the Digibest page for the Kohjinsha tuner on the Digibest website: [http://www.digibest-tech.com/modules/tinyd8/index.php?id=2](http://www.digibest-tech.com/modules/tinyd8/index.php?id=2)
I think we have some variant of it. I haven't contacted them yet about a Linux version of their software. The Digibest tuner is the one in the SH6 model. What model do you have?

---

### Post by punong_bisyonaryo on 2008-07-10
Hello all!

I tried out setting my touchscreen again for the nth time in Hardy. Well, seems I have a livable work-around. My problem (same as before) was when I setup the Penmount, regardless if Compiz is turned on or not, if I click-drag on the desktop, artifacts of the selection boxes remain. And the mouse/touchpad/pointer sometimes can no longer click on buttons, etc. So my current workaround is: don't click-drag around the desktop, because it seems that's the only place it happens. Click dragging in windows has no detrimental effect whatsoever.

I'm considering filing a bug report and/or reporting this to Penmount to see if anyone can come up with a solution.

Anybody have any insights/workarounds on this?

---

### Post by Ax of Ganto on 2008-07-12
> **punong_bisyonaryo said:**
> Anybody have any insights/workarounds on this?

That sounds like the problem I was having.  I did what was suggested [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/196711"), and it worked.  In xorg.conf, change this:

```
Section "ServerLayout"
[...]
    InputDevice "Penmount"
[...]
EndSection
```

to this:

```
Section "ServerLayout"
[...]
    InputDevice "Penmount" "CorePointer"
[...]
EndSection
```

I haven't found a fix for the audio problem on waking from suspend, though.

---

### Post by punong_bisyonaryo on 2008-07-13
> **Ax of Ganto said:**
> That sounds like the problem I was having.  I did what was suggested [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/196711"), and it worked.  In xorg.conf, change this:

```
Section "ServerLayout"
[...]
    InputDevice "Penmount"
[...]
EndSection
```

to this:

```
Section "ServerLayout"
[...]
    InputDevice "Penmount" "CorePointer"
[...]
EndSection
```

I haven't found a fix for the audio problem on waking from suspend, though.

Always could rely on the Ubuntu community for answers.:) Anyway, it does fix the problem with the touchscreen. However, my mouse no longer works when PenMount is configured as "CorePointer". Could you post your xorg.conf file?

---

### Post by Ax of Ganto on 2008-07-14
> **punong_bisyonaryo said:**
> However, my mouse no longer works when PenMount is configured as "CorePointer".

I see what you mean.  I don't usually use a usb mouse with my Kohjinsha, but I tried it just now and it doesn't work for me either.

---

