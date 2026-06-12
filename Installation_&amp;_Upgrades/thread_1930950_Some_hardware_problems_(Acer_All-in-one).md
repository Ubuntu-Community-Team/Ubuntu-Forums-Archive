---
title: "Some hardware problems (Acer All-in-one)"
date: 2012-02-24
forum: Installation &amp; Upgrades
---

### Post by danielkabrinski on 2012-02-24
Hello!  I've actually been a Linux user for a while, jumping from Slackware to Xubuntu, now I want to give Ubuntu 11.10 a shot because I think the new interface is pretty slick and should work nicely with my new computer.  However, I have a few problems.

I have an Acer Aspire Z3771.  Don't judge me if it's a bad system but I got a very good deal (well under half the price).  Specifications found [here]("http://support.acer.com/us/en/product/default.aspx?modelId=3980") and [here (PDF)]("http://eduace.net/acer/product_photos/asZ3771%20spec.pdf").

1 - The Touchscreen works but I can't tap icons or "click" them or use it the way I would with Windows 7.

[COLOR=Red]2 - The Card reader on the left does not work, including the USB port, microphone plugin, and headphone plugin attached to it.[/COLOR] [COLOR=Black]- Worked out of the box.[/COLOR]

[COLOR=Red]3 - I've tried many guides and I can't get my wireless card to work.[/COLOR] [COLOR=Black]- Solution below[/COLOR]

4 - I think I know the answer for this, really not too important, but would I be able to use the windows remote or at least configure it to work with Ubuntu?

[COLOR=Red]Right now I actually don't have Linux installed.  I made an attempt with Slackware but Ubuntu seemed to work much better with the live CD.  Any help/advice would be greatly appreciated because I would like to get this system working without Windows 7.  I tried very hard to like it but I miss Linux.[/COLOR]

EDIT:  I do have Ubuntu 11.10 installed hence why I've gotten my wifi to work.

Thank you.

---

### Post by danielkabrinski on 2012-02-25
Well, for those with the same issue as me, I'm here to help.

I have the ra3090 wireless card on this machine.  This is how I fixed the problem on my Acer All-in-One.

Installed [this package]("http://stat.case.edu/%7Ejrt32/how_to_build_rt3090_for_ubuntu_lucid/rt3090-dkms_2.3.1.4-0ubuntu0%7Eppa1_all.deb")

I ran both of these sets of commands

```

[COLOR=Blue][COLOR=Black]sudo mkdir -p /etc/Wireless/RT3090STA/
sudo touch /etc/Wireless/RT3090STA/RT3090STA.dat
[/COLOR][/COLOR]
``````

sudo mkdir -p /etc/Wireless/RT2860STA/
sudo touch /etc/Wireless/RT2860STA/RT2860STA.dat

``````

sudo gedit /etc/modprobe.d/blacklist.conf

```Add this to the bottom:

```

# Blacklist conflicting RaLink driver modules
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta

```Then

```

sudo gedit /etc/modules

```Add this:

```

rt3090sta

```Restart (by running the command below OR restarting your computer) and the card should be working.

```
sudo service network-manager restart
```NOTE:  If that doesn't work, try installing [this version of the driver]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0%7Eppa1_all.deb") and see if it works.

Also, sometimes it's better to use the rt2860sta depending on the model you have (at least it's what I've read in other threads).  So if this doesn't work for you, even after you try using both drivers, you can do this (assuming you've done everything above).

run this command

```

sudo gedit /etc/modprobe.d/blacklist.conf

```remove this line

```

blacklist rt2860sta

```Then run this command

```

sudo gedit /etc/modules

```And replace "ra3090" with this

```

rt2860sta

```This way you're using this driver instead of the 3090.

Hopefully this works for some of you and I spare you some time.  This issue is frustrating and it takes a hell of a long time to figure out without any help.

---

### Post by danielkabrinski on 2012-02-25
For the touchscreen I've followed a few guides and I still can't get it to work.

[http://www.upubuntu.com/2011/08/calibrate-your-tablet-touchscreen-on.html](http://www.upubuntu.com/2011/08/calibrate-your-tablet-touchscreen-on.html)

[http://ubuntuforums.org/showthread.php?t=1252492&page=128](http://ubuntuforums.org/showthread.php?t=1252492&page=128)
with
[http://ubuntuforums.org/showpost.php?p=10037639&postcount=1274](http://ubuntuforums.org/showpost.php?p=10037639&postcount=1274)

I would really appreciate some help with this issue.  I'm trying desperately to avoid going back to Windows 7.  This, along with the wireless card, is what bugs me the most.

EDIT:  I should have said this earlier.  The touchscreen works like a touchpad you would use on a laptop to control the mouse with very unresponsive clicking.  It barely works.

Here's the result of xinput list:

```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; IDEACOM  IDC 6651                           id=8    [slave  pointer  (2)]
&#9116;   &#8627; Primax Wireless Device                      id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; 1.3M WebCam                                 id=9    [slave  keyboard (3)]
    &#8627; Primax Wireless Device                      id=10    [slave  keyboard (3)]
    &#8627; ITE8713 CIR transceiver                     id=12    [slave  keyboard (3)]

```

EDIT:  Also, it's saying that I don't have a drive installed... problem is I can't find the driver and any guide I try to follow doesn't work because every package I try to install isn't available.  Where's all this Ubuntu support?

---

### Post by danielkabrinski on 2012-02-25
Is there ANYONE who can help with this touchscreen issue?

---

### Post by danielkabrinski on 2012-02-25
Not one reply?  Really?  None of the sites I've been too concerning the touchscreen, even areas on this forum, have fixed this problem.

Calibrate Touchscreen does this:

```

Error: No calibratable devices found.

```AND now I'm not even listing IDEACOM in xinput.

UGH.

EDIT:  Nevermind, I enabled it again, but it still works like a very crappy touchpad.

---

### Post by danielkabrinski on 2012-02-26
Well I started testing it using xinput and it seems like it actually did set my touchscreen as a touchpad.  Is there any way to fix this?

Does this help?

```

&#9116;   &#8627; IDEACOM  IDC 6651                           id=8    [slave  pointer  (2)]
    Reporting 3 classes:
        Class originated from: 8
        Buttons supported: 12
        Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right None None None None None
        Button state:
        Class originated from: 8
        Detail for Valuator 0:
          Label: Rel X
          Range: 0.000000 - 8191.000000
          Resolution: 0 units/m
          Mode: relative
        Class originated from: 8
        Detail for Valuator 1:
          Label: Rel Y
          Range: 0.000000 - 8191.000000
          Resolution: 0 units/m
          Mode: relative

```

---

### Post by danielkabrinski on 2012-02-27
Progress.  I can now run touchscreen calibrator but it still behaves like a touchpad.

I created two files in /usr/share/X11/xorg.conf.d

99.idc.conf

```

Section "InputClass"
        Identifier "IDEACOM Touchscreen"
        MatchProduct "IDEACOM"
        MatchDevicePath "/dev/input/event*"
        #MatchIsTouchscreen "on"
        Driver "evdev"
EndSection

```

NOTE:  Without the hash tag (or disabling that line) I'm back at square one.

99-calibration.conf

```

Section "InputClass"
    Identifier    "calibration"
    MatchProduct    "IDEACOM  IDC 6651"
    Option    "Calibration"    "5 8190 13 8189"
        Option  "ReportingMode"    "Raw"
        Option  "TapTimer"          "90"
        Option  "LongTouchTimer"    "150"
        Option  "Emulate3Buttons"
        Option  "Emulate3Timeout" "50"
        Option  "SendCoreEvents"
EndSection

```

Can someone help me at all?  I feel like I'm getting close to getting this problem solved but it something outside of what I already know or just haven't noticed.

ALL I want to be able to do is click by touch.  ](*,)

---

### Post by danielkabrinski on 2012-02-28
Skip the last post...  you only need this below.

I managed to do this which seems like tapping could be enabled if I can figure it out.  I'll tap the screen and the mouse cursor appears there.  A LOT better than what was going on before...  it's a start.

I created a file:

```

sudo nano /usr/share/X11/xorg.conf.d/99-calibration.conf

```

```

Section "InputClass"
        Identifier      "calibration"
        MatchProduct    "IDEACOM  IDC 6651"
        Driver  "evdev"
        Option  "Mode"  "Absolute"
        Option  "MinX"  "5"
        Option  "MaxX"  "8192"
        Option  "MinY"  "4"
        Option  "MaxY"  "8193"
EndSection

```

I tried messing with some button configurations but I can't get it right.  I'll keep at it.  The Absolute mode is probably what's going to work for this thing.

Any insight from ANYONE?

---

### Post by danielkabrinski on 2012-02-29
Well, did an upgrade to 12.04 just to see, and it's not looking good for me.  Disables my wifi and can't find/list my touchscreen.

Looks like I'm saying goodbye to Ubuntu.  Thought there was going to be more focus on touchscreens.

---

### Post by Mark Phelps on 2012-02-29
Hey ... know just how you feel -- really!

Had to do the same for my Tablet PC.  Worked great under 8.04 -- stylus, rotation, bezel keys -- every worked!

Upgraded it to 8.10, things stopped working.

Had to eventually pull Ubuntu from it.  Got tired of spending hours and hours hacking away TRYING to get stuff working again, when in contrast (with Win7) everything just worked "out of the box".

---

### Post by danielkabrinski on 2012-02-29
Yeah it's a pain in the neck.  What gets me is that it is actually the same kind of screen or chip or whatever that is already on a Ubuntu Certified machine.  It's like they want to kill everything.

---

