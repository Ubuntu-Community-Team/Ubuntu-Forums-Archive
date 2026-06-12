---
title: "Lucid: tablet pcs no longer supported?"
date: 2010-01-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hunteke on 2010-01-20
Given recent news that Lynx will no longer use HAL (Ubuntu's Hardware Abstraction Layer), I'm concerned that there will be no functional replacement for the Wacom drivers.  I use a tablet PC and heavily rely on the stylus for teaching my classes, annotating papers, and generally working in the academic environment.

From Ubuntu Weekly News ([Issue #176]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue176")):

"[HAL] has now disappeared entirely from the current Ubuntu 10.04 test version, and it's function being taken over among other things by DeviceKit. The advantage to this, according to the official announcement, is that Ubuntu has a faster boot and startup from hibernate time. Removing HAL has the consequence that Wacom drivers can no longer be used for drawing tablets."

Is this just a temporary Alpha step, or are tablet PCs no longer to be supported?

---

### Post by Favux on 2010-01-20
Hi hunteke,

I think it's just a temporary Alpha step.  I think that got a little garbled.  The real problem in Lucid is Xserver 1.7.  Linuxwacom doesn't work with it yet.  But they're working on it and it should be ready by Lucid release.

Plus the Xserver driver of linuxwacom is being somewhat merged/synched with with the Xorg/XFree86 XInput drivers.  And that version works with Xserver 1.7 currently.  So you could probably cobble together [xf86-input-wacom-0.10.4]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page") for a linuxwacom X driver with, if you have a usb tablet, the wacom.ko from linuxwacom and get a working Lucid setup.

---

### Post by hunteke on 2010-01-20
> **Favux said:**
> I think it's just a temporary Alpha step.  I think that got a little garbled.  The real problem in Lucid is Xserver 1.7.  Linuxwacom doesn't work with it yet.  But they're working on it and it should be ready by Lucid release.

Oh good stuff.  One of the problems I have is that I'm a noob in these parts, and don't know which projects go where, and to whom to ask questions.  Okay, somewhat relieved.

> **Favux said:**
> Plus the Xserver driver of linuxwacom is being somewhat merged/synched with with the Xorg/XFree86 XInput drivers.  And that version works with Xserver 1.7 currently.  So you could probably cobble together [xf86-input-wacom-0.10.4]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page") for a linuxwacom X driver with, if you have a usb tablet, the wacom.ko from linuxwacom and get a working Lucid setup.

Ugh.  It's that hobbling that I don't know how to do.  Here's to hoping it's back to a working state soon.

Thanks for the reply, Favux.

---

### Post by TSJason on 2010-02-19
I had good luck on a fresh install using the most recent daily iso build of lucid (02/18/2010) on i386 (Compaq tc4200 tablet). 

[http://cdimage.ubuntu.com/kubuntu/daily-live/current/lucid-desktop-i386.iso](http://cdimage.ubuntu.com/kubuntu/daily-live/current/lucid-desktop-i386.iso)

I enabled backports, proposed and partner in sources.list, apt-get dist-upgrade and then:

apt-get install xserver-xorg-dev git-core autogen autoconf build-essential libtool xutils-dev cellwriter

I used the guide on sourceforge to build and install the module: 
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom)

In the suggested xorg.conf changes I had to add:
Option "Button2" "3" 
to each of the new InputDevice sections to make my stylus able to right-click with the modifier button.

I also used some of the resources from:
[http://www.ser1.net/Files/Reviews/HP4200/index.html](http://www.ser1.net/Files/Reviews/HP4200/index.html)

Most specifically, I modified the rotate script he provided to work more like a toggle....if already rotated left, then it flips back to normal.

```

#!/bin/bash                                          
# On the HP, rotation is (normally) CW or NORMAL     

x_min=0
x_max=24700
y_min=0    
y_max=18520

function ROTATE() {
  curr=`xrandr | awk '/Current rotation/ { print $4 }'`
  case $curr in                                        
    normal)                                            
      CW                                               
      ;;                                               
    *)                                                 
      NORMAL                                           
      ;;                                               
  esac                                                 
}                                                      


function PORTRAIT() {
  #xsetwacom set Eraser BottomX $x_max
  #xsetwacom set Eraser BottomY $y_max
  echo portrait                       
}                                     

                                                                                                                                                                                      
function LANDSCAPE() {
  #xsetwacom set Eraser BottomX $y_max
  #xsetwacom set Eraser BottomY $x_max
  echo landscape
}


function NORMAL() {
  xrandr -o normal
  xsetwacom set stylus  Rotate NONE
  xsetwacom set eraser  Rotate NONE
  PORTRAIT
}


function CCW() {
        if [[ `xrandr -q |grep ^LVDS |awk '{print $4}'` != "left" ]] ; then
                xrandr -o left
                xsetwacom set stylus    Rotate CCW
                xsetwacom set eraser    Rotate CCW
                LANDSCAPE
        else
                NORMAL
        fi
}


function CW() {
        if [[ `xrandr -q |grep ^LVDS |awk '{print $4}'` != "right" ]] ; then
                xrandr -o right
                xsetwacom set stylus    Rotate CW
                xsetwacom set eraser    Rotate CW
                LANDSCAPE
        else
                NORMAL
        fi
}


function INVERT() {
        if [[ `xrandr -q |grep ^LVDS |awk '{print $4}'` != "inverted" ]] ; then
                xrandr -o inverted
                xsetwacom set stylus    Rotate HALF
                xsetwacom set eraser    Rotate HALF
                LANDSCAPE
        else
                NORMAL
        fi
}

case $1 in
  -l)
    CCW
    ;;
  -r)
    CW
    ;;
  -n)
    NORMAL
    ;;
  -i)
    INVERT
    ;;
  *)
    ROTATE
    ;;
esac

```


Hopefully some of this might prove to be helpful to you.

---

