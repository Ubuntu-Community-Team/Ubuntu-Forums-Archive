---
title: "just upgraded ibex, usb kb/mouse dead"
date: 2008-08-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by coder_cotton on 2008-08-04
Subject pretty much says it all, the xorg.conf has them in there, but they are both dead on the login screen.  Both are regular Dell usb devices.  Its not locked up, the login cursor is blinking and I can ssh in etc.  Any ideas?

TIA,
Cotton

---

### Post by mattisking on 2008-08-04
Not yet - rebooted without Usplash or quiet, Ctrl F1 and logged in on terminal, waiting for update I'm quite sure will fix it.

But at least I can tell you it's not just you.

Update: You can also elect, of course, to roll back to the previous version as I've just done.

---

### Post by Nullack on 2008-08-05
yeah, not often Im effected to this extent - I dont use Kubuntu :lolflag:

Hope it gets fixed soon. At first I thought it was GDM, but editing the gdm conf to autologin resulted in no mouse. However the keyboard does have limited functionality into tty1 for example ready for grabbing the fix when it arrives.

EDIT: Has anyone raised this with the Ubuntu X people on IRC Im not able to log onto IRC currently.

---

### Post by isrich on 2008-08-05
Same here no mouse and keyboard in X after upgrade :popcorn:

gave up a minute ago :(

---

### Post by mgsfan on 2008-08-05
same here

---

### Post by caryb on 2008-08-05
I'm so ashamed I have had to use that 5G partition with Vista on it:( Have been bitten as well!


Cary

---

### Post by mc4100 on 2008-08-05
same. still Got mouse for standard cut/paste functions (like This)

---

### Post by ronacc on 2008-08-05
just for info I just updated and I am not having this problem , I tried a reboot to see if that would bring it on but still normal , I'm gnome and 64bit .

---

### Post by mc4100 on 2008-08-05
> **mc4100 said:**
> same. still Got mouse for standard cut/paste functions (like This)
For me, this is Catastrophic Failure No. 1 ... but I still love testing, it's hilarious ;)
I'm on a Hardy Live Cd, now, so I can elaborate (BTW, I actually had to copy/paste every single letter for that post and also a few commands like sudo apt-get update, etc., from a spare -long- document because I got rid of the on-screen keyboard, thinking how I'd *never* need it! Lol):
The touchpad (synaptics) on my laptop works just fine, but not the built-in keyboard...so I set gdm.conf to autologin to avoid not being able to type my password ... and then I get the keyring bug, where it doesn't unlock they keyring on login ... and then I find you cannot paste anything in when it asks you to unlock it!

---

### Post by caryb on 2008-08-05
Is this a Kubuntu problem or *buntu:confused:


Cary

---

### Post by natros on 2008-08-05
Try adding 

Inputdevice "Generic Keyboard"
Inputdevice "Configured Mouse"   

to Section "ServerLayout"

That should work

---

### Post by shenki on 2008-08-05
> **coder_cotton said:**
> Subject pretty much says it all, the xorg.conf has them in there, but they are both dead on the login screen.  Both are regular Dell usb devices.  Its not locked up, the login cursor is blinking and I can ssh in etc.  Any ideas?

My xorg-fu is limited, but I know the answer is hidden in this blog post by Peter Hutterer, who wrote MPX (and is therefore God for all things input related):

[http://who-t.blogspot.com/2008/07/input-configuration-in-nutshell.html](http://who-t.blogspot.com/2008/07/input-configuration-in-nutshell.html)

If you're just after a quick fix add to your /etc/X11/xorg.conf, inside the ServerLayout section, the following:

```
Option "AutoAddDevices" "off"
```

It Worked For Me™.  Be sure to revert this change once an official fix comes out - which would be setting up hal and the evdev driver to handle our input devices.

---

### Post by mc4100 on 2008-08-05
> **natros said:**
> Try adding 

Inputdevice "Generic Keyboard"
Inputdevice "Configured Mouse"   

to Section "ServerLayout"

That should work

Catastrophe averted. "Inputdevice "Generic Keyboard" fixed my keyboard issues. :)

Edit: By the way, has anyone tried the xfix option, from inside recovery mode? It just occurred to me.

---

### Post by shenki on 2008-08-05
```
 hal (0.5.11-3~ubuntu5) intrepid; urgency=low
 .
  * Enable input-hotplug for xorg
    - 85_set_property_direct.patch: a patch from Fedora to add --direct
      option to hal-set-property.
    - debian/debian-setup-keyboard: modify a callout script from Fedora to
      work with console-setup.
    - debian/10-x11-keymap.fdi: add a callout to run debian-setup-keyboard
    - debian/rules, debian/hal.install: install 10-x11-input.fdi again.

```

This, and perhaps evdev=1:2.0.3-2, should fix the issue for everyone.

---

### Post by caryb on 2008-08-05
> Option "AutoAddDevices" "off"

Worked for me! Back in Kubuntuland:guitar:


Thanks Cary

---

### Post by BC7333 on 2008-08-05
> **mc4100 said:**
> Catastrophe averted. "Inputdevice "Generic Keyboard" fixed my keyboard issues. :)

Edit: By the way, has anyone tried the xfix option, from inside recovery mode? It just occurred to me.

xfix option did not fix it

Inputdevice "Generic Keyboard"
Inputdevice "Configured Mouse"

did fix it.. -whew... thanks folks!

---

### Post by hebetude on 2008-08-05
Just curious, shouldn't it have asked me about changing my xorg.conf.  I don't recall accepting any changes to my xorg.conf last night during that mass update.  Thanks for finding the fix.

---

### Post by mc4100 on 2008-08-05
> **hebetude said:**
> Just curious, shouldn't it have asked me about changing my xorg.conf.  I don't recall accepting any changes to my xorg.conf last night during that mass update.  Thanks for finding the fix.
Could be wrong but I don't think it originally changed your xorg.conf -- that's just how you fix it, i.e., something changed behind the scenes with hal and evdev, and changing xorg.conf is a workaround to make it play nice.

---

### Post by mattisking on 2008-08-05
> **caryb said:**
> Is this a Kubuntu problem or *buntu:confused:


Cary

For me, it's Ubuntu.

---

### Post by tawmas on 2008-08-05
I've had this on Ubuntu AMD64, no keyboard even trying to use a spare PS2 keyboard... It's solved now with the latest updates, dunno if it was hal or evdev though :-)

---

### Post by Slug71 on 2008-08-05
I have a similiar issue. Have Alpha 3 and did updates last night before bed and now i cant log in. Wont let me type in the username box. Im on a laptop though.

---

### Post by Nullack on 2008-08-05
> **Slug71 said:**
> I have a similiar issue. Have Alpha 3 and did updates last night before bed and now i cant log in. Wont let me type in the username box. Im on a laptop though.

Did you follow the thread though? If you simply update and uprgade youll be fixed - if your d/l mirror is slow to update you can try another.

---

### Post by Slug71 on 2008-08-05
Yeh the updates etc are fine, i shut the laptop down lastnight. When i powered up this morning it goes to the Username screen. Well i cant enter my Username. So i cant get in.

---

### Post by coder_cotton on 2008-08-05
It's fixed now in this mornings updates.

---

### Post by Slug71 on 2008-08-05
I still need to log in to do the update though.

---

### Post by mattduckman on 2008-08-05
> **Slug71 said:**
> Well i cant enter my Username. So i cant get in.

Pushing Alt + Ctrl + F1 to get to a terminal still works. Login, use
```
sudo apt-get update
sudo apt-get upgrade
```
and reboot.

---

### Post by Nullack on 2008-08-05
Youll find your still able to access tty1 via CTL+ALT+F1

---

### Post by Slug71 on 2008-08-05
Thanks for that guys.

---

### Post by ubername on 2008-08-05
Same here. I have Ibex on an external drive, so could boot back into Heron, but my USB keyboard and mouse were dead after selecting the ibex kernel from Grub, but worked on the grub screen (well, the keyboard did, don't know about the mouse.) 

Any clues how I could fix this, as I can't get into Ibex (can't enter user or password) to do any work?

---

### Post by mattduckman on 2008-08-05
are you saying that you didn't read the entire thread, or that the solution stated above doesn't work?

---

### Post by matthewbpt on 2008-08-05
> **mattisking said:**
> 
Update: You can also elect, of course, to roll back to the previous version as I've just done.

How do you roll back to previous version?

---

### Post by ubername on 2008-08-05
> **mattduckman said:**
> are you saying that you didn't read the entire thread, or that the solution stated above doesn't work?

Embarrassingly enough it is both. I apologise for not reading the entire thread, I must have just got to the end of page one and thought that was the end. But then after I actually posted I saw the instructions (Ctl-Alt-F1, sudo apt-get update, sudo apt-get upgrade, lots of activity) and rebooted. Still no mouse / keyboard.

Might it be a lag between the update server I have (can't tell which one at the mo, for reasons explained above) and the main server for upgrades? If someone can tell me a command line to switch to the main server that would help.

TIA

---

### Post by Nullack on 2008-08-05
> **matthewbpt said:**
> How do you roll back to previous version?

Why do that when theres updates in the repo fixing it - it would hamper your ability to test Intrepid :)

ubername, edit your sources - main canonical is the most up to date

---

### Post by ubername on 2008-08-05
> **Nullack said:**
> Why do that when theres updates in the repo fixing it - it would hamper your ability to test Intrepid :)

ubername, edit your sources - main canonical is the most up to date

I feel pretty stupid. How do I edit my sources from the command line?

---

### Post by BC7333 on 2008-08-05
> **BC7333 said:**
> xfix option did not fix it

Inputdevice "Generic Keyboard"
Inputdevice "Configured Mouse"

did fix it.. -whew... thanks folks!

After updating I deleted the two lines in xorg, rebooted x and all is well.

---

### Post by knarf on 2008-08-05
I have not lost my keyboard (on a Thinkpad T23) but I did 'lose' the cursor keys and several other auxiliary keys. Cursor-Left now gives Right-Alt, Cursor-Right is Print, etctera. Adding 'Option "AutoAddDevices" "off"' to the ServerLayout section of xorg.conf works around this problem. Anyone else having problems of this sort?

---

### Post by BwackNinja on 2008-08-05
Almost the exact same problem as knarf. Though for me the only key I could distinguish was up-arrow giving me print, and page up giving me "*". The most annoying thing is delete not working. It's nice to know once in a while that you're not crazy.

---

### Post by Nullack on 2008-08-05
> **ubername said:**
> I feel pretty stupid. How do I edit my sources from the command line?

Google is your friend. :)

---

### Post by tawmas on 2008-08-06
Yep, I recovered my keyboard but lost a bunch of keys as others already reported. Also, I still can't use my wireless mouse, but can do with a USB mouse plugged...

I'm now going to try the suggested workaround and see if it's any help, but first I need to change my password from the console, as one of the characters in it got, funnily enough, remapped to ENTER...

**Edit:** I recovered my keys, but the wireless mouse is still missing... :-(

---

### Post by Nullack on 2008-08-06
So whats the bug number that your reported? :) Its an alpha, were testing remember.

---

### Post by tawmas on 2008-08-06
Still trying to figure out the details so I can file against the proper package and attach the required information... I know too little about X input.

I guess it's got something to do with the fact the both the keyword and the mouse are linked to a single wireless controller which is in turn plugged into a single USB port.

---

### Post by tawmas on 2008-08-06
Ok, after some digging in my log files, I think I need some help.

I started from messages. From what I find there, it looks like the kernel is seeing both my keyboard and mouse (both wireless, both linked to a single receiver unit plugged into a single USB port):

```
Aug  7 01:21:19 tylke klogd: [   16.271923] input: Microsoft Microsoft Wireless Optical Desktop\Uffffffff 2.10 as /class/input/input1
Aug  7 01:21:19 tylke klogd: [   16.292048] input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop\Uffffffff 2.10] on usb-0000:00:1d.0-2
Aug  7 01:21:19 tylke klogd: [   16.377035] input: Microsoft Microsoft Wireless Optical Desktop\Uffffffff 2.10 as /class/input/input2
Aug  7 01:21:19 tylke klogd: [   16.402005] input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop\Uffffffff 2.10] on usb-0000:00:1d.0-2
```

Both the log for the keyboard (working) and the mouse (not working) look alike, and the log for the mouse also looks like the log for the working wired USB mouse which I'm using as a replacement:

```
Aug  7 01:30:01 tylke klogd: [  595.316998] input: Logitech USB-PS/2 Optical Mouse as /class/input/input6
Aug  7 01:30:01 tylke klogd: [  595.363965] input,hidraw2: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.3-2
```

When I look at Xorg.0.log, it looks like nothing should be working:

```
(II) config/hal: Adding input device Microsoft Microsoft Wireless Optical Desktop? 2.10
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Microsoft Microsoft Wireless Optical Desktop? 2.10
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Macintosh mouse button emulation
(EE) config/hal: NewInputDeviceRequest failed
(II) config/hal: Adding input device Logitech USB-PS/2 Optical Mouse
(EE) config/hal: NewInputDeviceRequest failed
```

(dunno where the Macintosh mouse button emulation is coming from, btw).

I believe I'm looking at the wrong places, or am overlooking something too obvious. Any hint or pointer would be much helpful, and dearly appreciated!

---

