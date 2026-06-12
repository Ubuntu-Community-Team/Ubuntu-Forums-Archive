---
title: "Am I the only one who thinks Emulate3Buttons should be off by default?!"
date: 2009-07-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by SKLP on 2009-07-05
RANT WARNING

Am I the only one who thinks Emulate3Buttons should be off by default? It causes horrible lag so I don't think it should be enabled even if one only has two mousebuttons. Most apps work fine with 2 mouse buttons anyway. It's kinda lame to have to put a file in /etc/hal/fdi/policy on every install, when no other operating system(I'm not counting other linux distros) has this crappy lag. 

Information about the bug:
[http://bugs.freedesktop.org/show_bug.cgi?id=1752](http://bugs.freedesktop.org/show_bug.cgi?id=1752)

---

### Post by 23meg on 2009-07-05
I've edited the thread title to reflect the content. Please use descriptive titles.

---

### Post by cdahmedeh on 2009-07-05
It seems that it is already disabled for mice with a middle click button. However, certain things like my touchpad have only two buttons, so I disagree with this. I use the middle click often, even when I'm on the go with laptop using the touchpad.

---

### Post by SKLP on 2009-07-06
> **23meg said:**
> I've edited the thread title to reflect the content. Please use descriptive titles. Yup, my bad.

> **cdahmedeh said:**
> It seems that it is already disabled for mice with a middle click button.It is not disabled by default( at least in jaunty). Haven't tried it in karmic but I do not believe it's fixed there either.

> **cdahmedeh said:**
> However, certain things like my touchpad have only two buttons, so I disagree with this. I use the middle click often, even when I'm on the go with laptop using the touchpad.Well there is a debate to be had about what is best: super laggy clicks or some apps which require three buttons to function will fail. (Things like new tab in firefox can be done with a hotkey+left click, also for instance to move gnome-panel applets you can either middle click or right click->move. So maybe there aren't many apps which are dependant on middle click?)
I certainly favor disabling it altogether. Do windows or OSX enable three-button emulation by default? No, and a benefit to them: their mouse clicks doesn't lag!

But regardless of whether it should be enabled when one has less than three buttons, most people should be able to agree that it should be disabled on input devices with 3+ buttons, so it would be good if atleast that would be fixed. Don't you agree?

I currently do this to disable Emulate3Buttons on my mouse:
/etc/hal/fdi/policy/disable-lag.fdi :
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="info.capabilities" contains="input.mouse">
   <merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
  </match>
 </device>
</deviceinfo>
```
My problem is that I'm unsure how to make it remove emulation for the touchpad as well, anyone know?

---

### Post by robert.rankin.jr on 2009-07-07
I love it, and have never experienced lag from it.

---

### Post by SKLP on 2009-07-07
> **robert.rankin.jr said:**
> I love it, and have never experienced lag from it.Oh, you gotta be kidding me... 

I quote the bug report I linked: > For every "click and move" gesture it is annoying : you put your pointer on an
area, click and move quickly and the system click outside the area (button,
window, widget ...)

Each time you click you have to press "hard" = "with a slight pause" the left
button in order to be sure to have a correct GUI response.

So you cannot reproduce this at all? Try putting the mouse cursor on a window title bar, and make a fast gesture to click and then drag it down as fast as possible immidiately. I think it's VERY noticable as I sometimes get it to click MANY pixels down from where i actually clicked. But I notice it when I'm not specifically trying to see the bug too.... well guess I'm too fast with my mouse gestures for poor ubuntu :(

---

### Post by SKLP on 2009-07-07
I did some testing and it seems to be that it automatically disables emulation for input devices once it detects a real middle-click from them. So I guess I should file a bug named "Emulate3Buttons should not be disabled when first middle-click is detected, it should be disabled immediately using the mouse button count from evdev".

But really, the feature should just be removed altogether preferably.

---

### Post by durand on 2009-07-07
> **robert.rankin.jr said:**
> I love it, and have never experienced lag from it.

+ 1 I use it extensively with my touchpad.

---

### Post by BoyOfDestiny on 2009-07-08
> **durand said:**
> + 1 I use it extensively with my touchpad.

++ To this also. I use it constantly, whether it is for pasting or opening links in a new tab. 
In fact, the emulated middle click is one of my favorite features, if I'm using a touchpad or 2 button mouse, it is indispensable and efficient. 

So to respond to the thread title... Yes, op, you are the only one who wants it out by default. ;)

---

### Post by qamelian on 2009-07-08
> **SKLP said:**
> Oh, you gotta be kidding me... 

I quote the bug report I linked: 

So you cannot reproduce this at all? Try putting the mouse cursor on a window title bar, and make a fast gesture to click and then drag it down as fast as possible immidiately. I think it's VERY noticable as I sometimes get it to click MANY pixels down from where i actually clicked. But I notice it when I'm not specifically trying to see the bug too.... well guess I'm too fast with my mouse gestures for poor ubuntu :(
I have to agree this the poster you replied to. I have never experienced the symptoms you are describing on any of my Linux machines. I don't experience any kind of lag on mouse clicks.

---

### Post by durand on 2009-07-08
Maybe your mouse is the problem? Perhaps it can't support multiple button clicks at the same time.

---

### Post by Buffalo Soldier on 2009-07-08
Wow. This is the first time I'm reading this bug. As far as I can tell, I never had a problem with Emulate3Buttons.

---

### Post by kerry_s on 2009-07-08
how about some details about the hardware your having this problem with ?
i'v never had that problem with the mouse.

---

### Post by jpeddicord on 2009-07-08
> **SKLP said:**
> It is not disabled by default( at least in jaunty). Haven't tried it in karmic but I do not believe it's fixed there either

You really should try Karmic before saying much, then.

My mouse will not emulate a middle click as it already has a middle mouse button, but my touchpad is able to. That is really how it should be. YMMV.

---

### Post by SKLP on 2009-07-21
> **qamelian said:**
> I have to agree this the poster you replied to. I have never experienced the symptoms you are describing on any of my Linux machines. I don't experience any kind of lag on mouse clicks.Well maybe it's either because a) the first middle click you do causes it to be disabled for that mouse b) you just dont notice it (i.e. you never click and move the mouse fast enough)

> **durand said:**
> Maybe your mouse is the problem? Perhaps it can't support multiple button clicks at the same time.My mouse is not the problem; I've tried this on all ubuntu machines I've had plus on my friends machines. It's there on all machines and they notice it, too.

> **jacobmp92 said:**
> You really should try Karmic before saying much, then.
I already noticed it:
> **SKLP said:**
> I did some testing and it seems to be that it automatically disables emulation for input devices once it detects a real middle-click from them. So I guess I should file a bug named "Emulate3Buttons should not be disabled when first middle-click is detected, it should be disabled immediately using the mouse button count from evdev".

But really, the feature should just be removed altogether preferably.

---

### Post by durand on 2009-07-21
> **SKLP said:**
> Well maybe it's either because a) the first middle click you do causes it to be disabled for that mouse b) you just dont notice it (i.e. you never click and move the mouse fast enough)


I'm not sure what you actually do with the middle mouse button? I think I make full use of it (scrolling, clicking to open and close tabs, click and drag in blender) and I've never even noticed a tiny amount of lag. Does this happen on other linux distros or on windows?

---

### Post by ahmatti on 2009-07-21
> **BoyOfDestiny said:**
> I use it constantly, whether it is for pasting or opening links in a new tab. 
In fact, the emulated middle click is one of my favorite features, if I'm using a touchpad or 2 button mouse, it is indispensable and efficient. 


I agree! I suppose the durand might know that you can also paste the text with the middle click. Maybe he is a "click to focus" kindofguy anyway... This explains the use of the 3rd button [http://www.ghacks.net/2009/03/03/get-to-know-linux-copy-and-paste/](http://www.ghacks.net/2009/03/03/get-to-know-linux-copy-and-paste/) for the curious.

---

### Post by durand on 2009-07-21
> **ahmatti said:**
> I agree! I suppose the durand might know that you can also paste the text with the middle click. Maybe he is a "click to focus" kindofguy anyway... This explains the use of the 3rd button [http://www.ghacks.net/2009/03/03/get-to-know-linux-copy-and-paste/](http://www.ghacks.net/2009/03/03/get-to-know-linux-copy-and-paste/) for the curious.

Yup, I use the select to copy, click to paste thing all the time!

---

### Post by qamelian on 2009-07-21
> **SKLP said:**
> Well maybe it's either because a) the first middle click you do causes it to be disabled for that mouse b) you just dont notice it (i.e. you never click and move the mouse fast enough)
I can't middle-click without it. I have a two-button touchpad only. I click and dragquite quickly all the time and there is absolutely no lag what-so-ever and never has been on any release of Ubuntu (or any other distro for that matter) that I have installed on my laptop.

---

### Post by Xamiga on 2009-07-21
Yes, yes, yes.   Glad I found this thread.  I turned Emulate3Buttons off and now Kdenlive keyframe editing and timeline cursor positioning works correctly. 

I vote: Emulate3Buttons should be off by default.

p.s. Using logitech wireless keyboard and mouse on Toshiba laptop.

---

### Post by q3buddha on 2009-09-08
I use a razer diamondback 3g and like to play quake 3, quake 4 and quake live.  This has been a major headache for me since hal took over xorg.  Every time I do an install I must find this info and turn it off.  Its kind of a pain.  Just built a new computer and here we go again.  The "Macintosh mouse button emulation" causes pretty bad mouse button lag and at time to the point where clicks aren't registered at all.  It took me months to figure this out the first time.  I would say it doesn't necessarily need to be off by default but it would be nice if it weren't so complicated to turn off.  For me as a relatively experienced linux user its not a horrible problem but it is annoying.  I propose a setting that could be switched from the mouse settings screen.

Humbly,

Chris

---

### Post by Sophont on 2009-09-08
Obviously this feature should not be removed.
For the sake of some you want to remove a feature for many (Laptops ain't rare anymore)?

Further I don't have that lag. Neither with touchpad (2 button), nor with (bluetooth, 3-button) mouse.
So it sounds like one of those bugs where the affected assume it's universal, while it actually is not. I click, I move - I do it a lot and not slow either.

And if the emulation is turned off as soon as the middle button is clicked - what exactly is the problem?

I hope the underlying problem gets fixxd soon so that those affected by this lag don't have to suffer anymore - but don't ask to remove useful features instead of asking for bug to be fixed.

---

