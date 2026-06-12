---
title: "Touchscreen - Please help!"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by ogro0 on 2010-08-07
Hello everyone

Iam gettin some problems with ubuntu 10.4. Iam using it in a HP tx2 1274 and I couldnt find any thread that solves my problem: My touchscreen doesnt work.:(

When I installed Ubuntu 10.4 touchscreen did work, but not the multi-touch. Then I tried to solve that, now Iam without the touch. (I've already done all the upgrades)

Help me please! thanks since now.

---

### Post by Favux on 2010-08-07
Hi ogro0,

Welcome to Ubuntu forums!

What did you change from the default Lucid set up to try and get multi-touch?

Let's look at your Xorg.0.log in /var/log.  Compress it with right click and Create Archive and use Manage Attachments to attach it to your next post.

---

### Post by ogro0 on 2010-08-07
thanks for the answer, man! but I dont know how to do that, Iam quite new to linux.

can u tell me how to do that?

thanks!

---

### Post by Favux on 2010-08-07
Sure.  Use Places (Nautilus) to navigate to /var/log.  Then right click on Xorg.0.log and open in gedit.  Save the file as ogro0_Xorg.0.log onto your Desktop.  The right click on it and compress it with Create Archives.  Then in Manage Attachments below browse your Desktop till you find the compressed file and upload it.

By the way what changes did you make to Lucid that lost you touch?  In other words what did you do to enable multi-touch?

---

### Post by ogro0 on 2010-08-07
what I did? well, I just followed some guides ("How to") and done some updates, but all guides failed during the process.

here it is, the Xorg

---

### Post by Favux on 2010-08-07
Which guides or How to's?  Nothing is showing up in Xorg.0.log, so your n-trig digitizer isn't being recognized currently.

Let's see what the output of:
```
xinput --list
```
in a terminal looks like.

---

### Post by ogro0 on 2010-08-07
ogro0@ogro-note:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Basic Optical Mouse               id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HP Webcam                                   id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

---

### Post by Favux on 2010-08-07
Alright, not there either.

Check Synaptic Package manager if xserver-xorg-input-wacom is installed.  If not install it, unless you tried to clone/compile xf86-input-wacom.  If you did that let me know.

Go to /usr/lib/X11/xorg.conf.d/ with Places.  See if there is a file called 10-wacom.conf.  Open it in gedit.  There should be at least three sections/snippets.  The n-trig snippet should look like:
```
Section "InputClass"
 	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
 	MatchDevicePath "/dev/input/event*"
 	Driver "wacom"
	Option "Button2" "3"
EndSection
```
If it doesn't change the snippet so it does.  You can edit the file by entering (copy and paste) in a terminal:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
```
Gksudo is the graphical version of sudo which makes you root/super user so you can change system files.  Gedit is the gnome editor which is a graphical editor which is why you're using gksudo.  Make the changes, Save and reboot.

---

### Post by ogro0 on 2010-08-07
man, I did it all. But touch still not working =/

what coud it be?

ah, and thanks for the attention

---

### Post by Favux on 2010-08-07
Touch isn't working, but is the stylus now working?  And does touch do anything?

Now we need to look at your Xorg.0.log again.

---

### Post by ogro0 on 2010-08-07
touch doesn't work =/

---

### Post by Favux on 2010-08-07
Hi ogro0,

Well that was interesting.  At this point Xorg.0.log should show the Wacom driver initializing/grabbing the stylus and that isn't happening.  So something is messed up.  Does the stylus do anything?  Touch should be picked up by the evdev driver and that isn't happening either.  Show me the contents of your 10-wacom.conf.

When you were messing with things did you mess with something called hid-ntrig.ko?

This is the easy part and honestly shouldn't be hard.

---

### Post by ogro0 on 2010-08-08
hid-ntrig.ko, yea, there was something like that!

---

### Post by Favux on 2010-08-08
Hi ogro0,

OK, your 10-wacom.conf looks right.

To explain things a little:  With a default Lucid setup the TX2z stylus should work out of the box and so should touch.  The stylus is assigned to the linuxwacom driver by the 10-wacom.conf, which might need some tweaking (which we already did).  Single finger touch falls through and is picked up by the evdev driver touchscreen (or touchpad?) catchall in the evdev.conf.

So you can make a hybrid screen rotation script that picks up both the wacom controlled stylus and the evdev controlled single finger touch.

As you know it gets a little more complicated if you want to go to multi-touch or use the linuxwacom drivers two finger gesture support.

Basically we'll be working out of the [Ntrig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").

Back from the explanation it sounds like you broke the default hid-ntrig.ko.  The hid-trig.ko takes the usb signals/raw data from your n-trig digitizer and feeds them to whatever X driver you're using, like linuxwacom's or evdev's.  So let's see if it is loading.  Look in the output of:
```
lsmod
```
and see if you see anything with ntrig in it's name.  This may work:
```
lsmod | grep ntrig
```

---

### Post by ogro0 on 2010-08-19
sorry about the delay, man

I just followed the "[B][SIZE=2][COLOR=RoyalBlue]Ayuthia's hid-ntrig.ko and Linuxwacom Driver Installer in Python for Karmic and Lucid" 


[/COLOR][/SIZE][/B][SIZE=2][COLOR=RoyalBlue][COLOR=Black]and now my touch works! thanks!
but I wanted to multi touch, can u explain me how, please?

thanks once more, bro!
[/COLOR][/COLOR][/SIZE][B][SIZE=2][COLOR=RoyalBlue]
[/COLOR][/SIZE][/B]

---

### Post by Favux on 2010-08-19
Hi ogro0,

Good!  Did you use Ayuthia's installer to install anything besides the hid-ntrig.ko?

For multi-touch first we have to know what firmware you have installed.  Are you dual booting Windows?  Vista or Win7?

---

### Post by ogro0 on 2010-08-19
iam not dual booting windows, but Iam planning to. I need to use autocad, and I couldnt find anything same for linux.

---

### Post by Favux on 2010-08-19
There are a few autocad-like linuxw app.s.  Qcad 2 and Archimedes come to mind.  Have you looked at them?

---

### Post by srnissen on 2010-08-22
On a related note, I am unable to find out how to calibrate my touch screen. My laptop is a HP tx1345eo, approximately two years old. It *does* register my touch screen, but I cannot find any utilities preinstalled (I use xubuntu 10.4) that will let me calibrate my touch screen. I have tried installing evtouch through synaptic, which seems to have done the trick for other people, but all guides seem to expect the installation of evtouch to add a "calibrate touch screen" icon to the App menu and I can't find such a menu item. Is this an issue you can shedd some light on?

---

### Post by Favux on 2010-08-22
Hi srnissen,

Welcome to Ubuntu forums!

I gather you have an HP TX1000 touch screen tablet.  Evtouch is the right driver.  Is there a manual ('man evtouch'), and if so does it tell you how to calibrate?  Or a README?

You could try xinput calibrate:  [http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator)

The other option is to try the eGalax touchscreen driver:  [http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)  It has a calibrator built in.  Discussed in the READ ME I think.

---

### Post by srnissen on 2010-08-22
Hey Favux

typing 'man evtouch' into the terminal just tells me there's no such thing, but I am quite new to this OS, so I may have done it wrong - is there a specific directory I should be in when doing this? 

I can see when going applications>settings>xfce 4 settings manager>mouse that I have something called "eGalax INC. USB TouchController," which indicates that I already have a touchscreen driver which is not evtouch - to test this, I've removed evtouch again, and my touch screen still responds. However, I have no idea how to calibrate using egalax either, because just like evtouch, there is no calibration tool anywhere in the applications menu, or at least, not with any name that indicates it's a calibration tool.

---

### Post by srnissen on 2010-08-22
Having fiddled with it a little further - it would seem that I already have a package called xinput but, again, I run into the trouble of not having the calibration tool, or at least not being able to find it. Maybe they're part of Ubuntu but not Xubuntu?

I tried downloading the xinput calibrate tool at your link, but unfortunately, that's only for i386 machines, I'm using an AMD.

---

### Post by Favux on 2010-08-22
Hi srnissen,

For xinput calibrator you can either download the source code tarball and compile it or add the ppa to your Software Sources.  The link I gave you links to both.  Here's the ppa:  [https://launchpad.net/~tias/+archive/xinput-calibrator-ppa](https://launchpad.net/~tias/+archive/xinput-calibrator-ppa)

---

### Post by srnissen on 2010-08-22
Thank you, using the PPA finally got me the calibration software. Unfortunately, it doesn't work for me - or rather it does, but not as expected.

When running the calibration tool, the pointer does not move when the stylus does. As such, only the first of the points (in the upper left corner, where the pointer always defaults to when I press the screen) can be pressed - pressing anywhere near the second point makes the pointer, again, register a click in the top left corner. Does this sound like a problem you've ever encountered before?

---

### Post by Favux on 2010-08-22
If the pointer is jumping to the upper left corner that usually means the Xserver isn't getting input, or correct input, from the driver.
> I've removed evtouch again, and my touch screen still responds. However, I have no idea how to calibrate using egalax either, because just like evtouch, there is no calibration tool anywhere in the applications menu, or at least, not with any name that indicates it's a calibration tool.
Without evtouch the driver probably handling touch is evdev through it's touchscreen or touchpad catchall.  That's probably the cause.
> I can see when going applications>settings>xfce 4 settings manager>mouse that I have something called "eGalax INC. USB TouchController," which indicates that I already have a touchscreen driver which is not evtouch
I suspect this is telling you you have the eGalax touchscreen, not that you have the driver.  I think you need to reinstall the evtouch driver or install the eGalax driver.

---

### Post by srnissen on 2010-08-22
I'm going to try and download the eGalax driver from their home page, then - I've tried with the evtouch driver already, and that doesn't work - but I'm surprised that it understands my touch screen *at all* if it doesn't have an appropriate driver installed.

---

### Post by Favux on 2010-08-22
Evdev is the driver of last resort.  It tries to pick up stuff if no other driver has claimed it.  That's why it has the catchall snippets in it's .conf.

---

