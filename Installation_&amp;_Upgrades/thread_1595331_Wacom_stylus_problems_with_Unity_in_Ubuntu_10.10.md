---
title: "Wacom stylus problems with Unity in Ubuntu 10.10"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by Kriteas on 2010-10-13
I have a Fujitsu Stylistic st6012 tablet with a wacom digitizer built in. With UNE 10.04 the stylus was working fine, the buttons/rocker did left and right clicks.
After upgrading to 10.10 the stylus was still working, but the buttons were not.
I could click by tapping with the stylus, but to access menus in applications, or even shutdown menu, I have to keep pressing the stylus against the tablet. If I just tap, the menu will appear for a brief millisecond and then disappear again. Like what happens when you double-click with a mouse.

After some searching I have managed to get the stylus buttons to work - setting button closest to the tip as leftclick and the other as rightclick.

The clicking works as expected inside applications, and when the applications menu-bar is on a line of its own - not on the same line as close, minimise, maximise, tray-icons, shutdown... 
In applications where the menu is moved up on the same line as close/minimise/maximise... the clicking must be done by click-hold - if I click-release the menu would go away.

So that is problem number 1. Not sure if it is Maximus that is creating the top panel?

Next, the even bigger problem:
The leftside icons menu introduced with UNE 10.10 is not behaving well with my stylus.
Sometimes the very first tap/click on an icon launches that application. Subsequent taps/clicks on ANY icon does nothing. Only nudges the icon, scrolls the bar slightly or nothing at all.
Other times not even the first tap/click launches anything. 
This makes the OS and my tablet utterly useless :(

After getting the stylus buttons to work, rightclicks actually works on the icon-bar (unity?), bringing up the menu with name and Remove from Launcher options. But it does not respond to taps or leftclicks - other than making the rightclick-menu disappear.

NOTE: the icons-bar and menus work as they should using an external mouse, so the problem must be related to the wacom stylus.

Here is some values from xsetwacom:
kris@kris-st6012:~$ xsetwacom --get "Serial Wacom Tablet" TPCButton
on
kris@kris-st6012:~$ xsetwacom --get "Serial Wacom Tablet" Suppress
4
kris@kris-st6012:~$ xsetwacom --get "Serial Wacom Tablet" RawSample
2
kris@kris-st6012:~$ xsetwacom --get "Serial Wacom Tablet" PressCurve
50 0 100 50
kris@kris-st6012:~$ xsetwacom --get "Serial Wacom Tablet" Mode
Absolute
kris@kris-st6012:~$ xsetwacom --get "Serial Wacom Tablet" Touch
off
kris@kris-st6012:~$ xsetwacom --get "Serial Wacom Tablet" Gesture
off
kris@kris-st6012:~$ xsetwacom --get "Serial Wacom Tablet" TapTime
50
kris@kris-st6012:~$ xsetwacom --get "Serial Wacom Tablet" Capacity
-1
kris@kris-st6012:~$ xsetwacom --get "Serial Wacom Tablet" RawFilter
on
kris@kris-st6012:~$ xsetwacom --get "Serial Wacom Tablet" ClickForce
409
kris@kris-st6012:~$ xsetwacom --get "Serial Wacom Tablet" Button1
1
kris@kris-st6012:~$ xsetwacom --get "Serial Wacom Tablet" Button2
2
kris@kris-st6012:~$ xsetwacom --get "Serial Wacom Tablet" Button3
3


Final note: in applications that are "modified" to move the menu-bar up next to the close/min/max-bar, rightclicking with stylus-button does a (right-)menu show-hide. I have to hold the button for the menu to stay. In applications, like firefox, where the menu-bar has not been moved up, rightclicking with the stylus works like a normal mouse-rightclick.

Anyone heard of similar behaviour, or got any suggestions? I'll try anything to get my stylus working with this Unity menu :)

---

### Post by Favux on 2010-10-13
Hi Kriteas,

Welcome to Ubuntu forums!

If:
> I have managed to get the stylus buttons to work - setting button closest to the tip as leftclick and the other as rightclick.
you did this then:
```
kris@kris-st6012:~$ xsetwacom --get "Serial Wacom Tablet" Button1
1
kris@kris-st6012:~$ xsetwacom --get "Serial Wacom Tablet" Button2
2
kris@kris-st6012:~$ xsetwacom --get "Serial Wacom Tablet" Button3
3

```
wouldn't be the result.  The stylus tip (Button1) is by default 1 = left click.  Middle click = 2 and Right click = 3.

You could try using the sample xsetwacom script .xsetwacom.sh for the TX2000 in post #2 here:  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)  Just remember to use the "Device names" 'xinput --list' returns.  Since you don't have touch remove that section.  And if you don't have an eraser remove that section too.  Instructions are in IV. in the first post.

---

### Post by Kriteas on 2010-10-14
Thanks for replying Favux!
Yea, something was strange with my button setup. I had it set differently in the 50-WACOM conf, but most of the settings there did not take, or were overridden with defaults.

Now, I modified your script to match my tablet:
```

xsetwacom set "Serial Wacom Tablet stylus" Suppress "2"  # data trimmed, 0-100
xsetwacom set "Serial Wacom Tablet stylus" RawSample "20"  # default is 4
xsetwacom set "Serial Wacom Tablet stylus" ClickForce "6"  # 1-21
xsetwacom set "Serial Wacom Tablet stylus" PressCurve "5 10 90 95"
xsetwacom set "Serial Wacom Tablet stylus" TPCButton "on"
xsetwacom set "Serial Wacom Tablet stylus" Mode "Absolute"  # or Relative
xsetwacom set "Serial Wacom Tablet stylus" Button1 "1"  # tip: left mouse click
xsetwacom set "Serial Wacom Tablet stylus" Button2 "3"  # upper?: right mouse click
xsetwacom set "Serial Wacom Tablet stylus" Button3 "1" # lower?: left
# middle mouse click = 2

#Eraser
xsetwacom set "Serial Wacom Tablet eraser" Suppress "2"  # data trimmed, 0-100
xsetwacom set "Serial Wacom Tablet eraser" RawSample "20"  # default is 4
xsetwacom set "Serial Wacom Tablet eraser" ClickForce "6"  # 1-21
xsetwacom set "Serial Wacom Tablet eraser" PressCurve "0 10 90 100"
xsetwacom set "Serial Wacom Tablet eraser" Mode "Absolute"  # or Relative
xsetwacom set "Serial Wacom Tablet eraser" Button1 "1"  # left mouse click

```
And after running this the buttons appear to do the correct clicks.

But it is still not behaving well with Unity (I believe that's what it is called), or Maximus (which is what makes the application menus move up to the titlebar?)

Clicking with the tip or Button3 on the leftside icons does nothing, except nudge the icons. If I click and hold however, then I can drag and rearrange the icons.

Same with the application menus that have been "maximised". I have to click and hold for the menu to stick.

Right-clicking (Button2?) appears to work on the leftside icons (Unity). Right-clicking inside a "maximised" application only does a show-hide of the menu. I have to rightclick-and-hold to use the menu.

Clicking in applications that have not been "maximised" works, just like with a mouse.
Clicking with an external USB-mouse works like normal.
AND: stylus leftclicking (with tip or Button3) works on the little ubuntu icon in the upper left corner.

It is really confusing :(

---

### Post by Kriteas on 2010-10-14
A small update:
If I in gconf check the no_maximise option for Maximus, then right-clicking with the stylus inside an application appears to work again. I.e. the rightclick menu will stay visible without me having to hold the stylus-button.

The application menu will still be stuck on the global-menu line, and I still have to leftclick+hold to use that.

But it seems to me that something related to maximus (and/or unity) is not responding correctly to my stylus clicks. Any ideas?

---

### Post by Favux on 2010-10-14
OK, it looks like we have the stylus buttons straightened out.
> I had it set differently in the 50-WACOM conf, but most of the settings there did not take, or were overridden with defaults.
Configuring in 50-wacom.conf is a little tricky.  I'd have to see what you were using.  For one thing, at least in Lucid, you can't configure dependent devices like the eraser.  You have to use xsetwacom or the xorg.conf to configure dependent devices.  I think that's still true of Maverick.  There is a fix coming but I don't think it's in the distros yet.

I think you've uncovered a bug in Unity with the new Maximus feature.  You could search Launchpad and see if anyone has reported it yet.  Otherwise you should.

I'm assuming you have 0.10.8 xf86-input-wacom as your default.  It would be the xserver-xorg-input-wacom package.  You might want to check the version number.  If it isn't 0.10.8 we could try upgrading it to 0.10.8.

---

### Post by Kriteas on 2010-10-14
Thanks for the tip! I found a bug-report on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/unity-place-applications/+bug/630193?comments=all](https://bugs.launchpad.net/ubuntu/+source/unity-place-applications/+bug/630193?comments=all)

I added my findings to it, and hope someone will look at it :O

I have the 0.10.8 version of the wacom package. I even activated proposed updates, but found nothing that fixes it. Guess I'll have to wait :( Feeling a bit handicapped.

---

### Post by Favux on 2010-10-14
> Guess I'll have to wait  Feeling a bit handicapped.

Hopefully now that you've confirmed the bug the bug report will see some action.  A dev. asking for more information.

---

