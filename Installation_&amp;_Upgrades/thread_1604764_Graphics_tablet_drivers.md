---
title: "Graphics tablet drivers"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by tmcthree on 2010-10-24
Hi,
So I'm an absolute noob with Ubuntu, but I must say I like what I've found so far, however...

I'm used to installing drivers using windows so I haven't got the foggiest what I'm supposed to do with the linux drivers on this page.

[http://www.aiptek.eu/index.php?option=com_product&task=view&productid=184&Itemid=542](http://www.aiptek.eu/index.php?option=com_product&task=view&productid=184&Itemid=542)

Any help gratefully appreciated.

---

### Post by Favux on 2010-10-24
Hi tmcthree,

Welcome to Ubuntu forums!

We want to find out if your Aiptek tablet needs the Aiptek driver or if they've rebranded another tablet.  So enter (copy & paste) in a terminal (Applications > Accessories > Terminal):
```
xinput --list
```
and post the output.

---

### Post by tmcthree on 2010-10-24
> **Favux said:**
> Hi tmcthree,

Welcome to Ubuntu forums!

We want to find out if your Aiptek tablet needs the Aiptek driver or if they've rebranded another tablet.  So enter (copy & paste) in a terminal (Applications > Accessories > Terminal):
```
xinput --list
```
and post the output.

Cheers


&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627;  USB OPTICAL MOUSE                      	id=8	[slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet  	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]

---

### Post by Favux on 2010-10-24
OK, it's a Waltop tablet.  Are you in Maverick Meerkat (10.10)?  If so have you done all the updates through Update Manager?  Or are you using another release?

---

### Post by tmcthree on 2010-10-24
> **Favux said:**
> OK, it's a Waltop tablet.  Are you in Maverick Meerkat (10.10)?  If so have you done all the updates through Update Manager?  Or are you using another release?

er.. I'm in Ubuntu 10.10 (is that maverick merekat?) I did update a lot of stuff.

Tablet works to an extent, but it doesn't sense pressure or anything like that.

---

### Post by tmcthree on 2010-10-24
I've just checked system > administration > update manager and it says I'm up to date

---

### Post by Favux on 2010-10-24
Hi tmcthree,

OK, good.  Yes you are using Maverick.  10.10 means released in October 2010, with the year first followed by the month.  Probably what is happening is the evdev driver is picking up the tablet.  Evdev functions as a fail safe, if no driver is assigned to a device it tries to pick it up.  That's why it isn't working right.

I just had a Waltop tablet user put his tablet on the wacom driver in a completely up to date Maverick.  The Wacom driver is what the Waltop tablets are suppose to use.  But there's been a problem with the Waltop usb driver in the kernel up to now.  So we've been using the wizardpen driver temporarily in Lucid (10.4) and Maverick.

Let's see if we can set you up on the Wacom driver too.  Make sure you've run Update Manager and are completely up to date.  Mainly we're looking for kernel stuff, but do everything.  Then check in Synaptic Package Manager that you have xserver-xorg-input-wacom installed.  You should.  That's the Ubuntu package that contains the actual Wacom X driver xf86-input-wacom.  If not install it.

---

### Post by tmcthree on 2010-10-24
> **Favux said:**
> Hi tmcthree,

OK, good.  Yes you are using Maverick.  10.10 means released in October 2010, with the year first followed by the month.  Probably what is happening is the evdev driver is picking up the tablet.  Evdev functions as a fail safe, if no driver is assigned to a device it tries to pick it up.  That's why it isn't working right.

I just had a Waltop tablet user put his tablet on the wacom driver in a completely up to date Maverick.  The Wacom driver is what the Waltop tablets are suppose to use.  But there's been a problem with the Waltop usb driver in the kernel up to now.  So we've been using the wizardpen driver temporarily in Lucid (10.4) and Maverick.

Let's see if we can set you up on the Wacom driver too.  Make sure you've run Update Manager and are completely up to date.  Mainly we're looking for kernel stuff, but do everything.  Then check in Synaptic Package Manager that you have xserver-xorg-input-wacom installed.  You should.  That's the Ubuntu package that contains the actual Wacom X driver xf86-input-wacom.  If not install it.

Thanks Favux I really appreciate this.

Ok The udate manager says computer up to date and the synaptics package manager has a green checkbox next to xserver-xorg-input-wacom so I'm assuming that it's loaded.

---

### Post by Favux on 2010-10-24
Right, it's loaded.

So now we want to change the first snippet in 50-wacom.conf.  That's the usb snippet for usb tablets.  We want to go from something like this:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

```
where Waltop is commented out to:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
	MatchProduct "Wacom|WALTOP|WACOM"
#	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

```
Where we've activated the WALTOP and commented out just Wacom MatchProduct.  To edit the file use in a terminal:
```
gksudo gedit /usr/share/X11/xorg.conf.d/50-wacom.conf
```
sudo and gksudo make you root or super user.  You use gksudo when using a graphical program.  Since gedit is a graphical text editor that's why you're using gksudo.  The rest is the directory path to the file.

Then Save, Close, and reboot.  You may need to reboot several times for things to "shake out".  Then to see if it's worked enter in a terminal:
```
xsetwacom list
```
If you see stylus in the output it's on the wacom driver.

If that works we can set up with a xsetwacom script to give you finer control over the stylus.

---

### Post by tmcthree on 2010-10-24
Thanks so much! That seems to have worked!

---

### Post by Favux on 2010-10-24
Outstanding!  :)

Keep me updated as to how it is working.  It looks like I can change the HOW TO's.  So I need confirmation that you're getting pressure, etc.

As promised attached to the bottom of the post is the xsetwacom script for the stylus.  Instructions for installing it are in step IV. at the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

---

### Post by tmcthree on 2010-11-09
> **Favux said:**
> Outstanding!  :)

Keep me updated as to how it is working.  It looks like I can change the HOW TO's.  So I need confirmation that you're getting pressure, etc.

As promised attached to the bottom of the post is the xsetwacom script for the stylus.  Instructions for installing it are in step IV. at the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

Hi Favux, this is slightly embarrassing but I got a bit scared of the other page you sent me to so I carried on using a tablet-mouse combo to get all of the buttons working. 

Anyway I finally summoned up the courage to give it a go and it doesn't seem to work.

Initially, (before I run the script) there is no mouse 2 ([edit] both rocker buttons are the middle button). The top button on the stylus is the middle mouse. Then when I run the script there is no middle button and both of the rocker buttons on the stylus are mouse 2.

Any thoughts?

Edit Could the stylus be knackered?

---

### Post by Favux on 2010-11-09
Hi tmcthree,

> so I carried on using a tablet-mouse combo to get all of the buttons working.
Do you mind unpacking that a little and explain what you were doing?

OK, so you just tried the attached script for the stylus and the stylus buttons aren't working right.  It could be your "Device name" for the stylus is different from the one in the script.  Please post the output of:
```
xinput --list
```
in a terminal.

---

### Post by tmcthree on 2010-11-09
> **Favux said:**
> Hi tmcthree,


Do you mind unpacking that a little and explain what you were doing?

OK, so you just tried the attached script for the stylus and the stylus buttons aren't working right.  It could be your "Device name" for the stylus is different from the one in the script.  Please post the output of:
```
xinput --list
```
in a terminal.

Ok, what I mean by using the mouse and tablet is that I simply use the mouse for whatever button is currently inoperable. The best combination is that I use the tablet for drawing and navigation and the mouse to select. (because I do more drawing and navigation than selecting) 

Here is the output.

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627;  USB OPTICAL MOUSE                      	id=8	[slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet eraser	id=9	[slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet stylus	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[sl

---

### Post by Favux on 2010-11-09
OK, I follow you.  And you wanted to start using the stylus buttons instead of the mouse buttons.  You weren't saying you had a Waltop tablet mouse.

Well do the stylus buttons work in windows?  Are they separate buttons or is it a rocker switch?

Does this happen in a certain program or generally?

The "Device name" is correct so the commands should work.  What happens if you comment them out?:
```
#xsetwacom set "WALTOP International Corp. Slim Tablet stylus" Button2 "3"  # right mouse click
#xsetwacom set "WALTOP International Corp. Slim Tablet stylus" Button3 "2"  # middle mouse click
```

---

### Post by tmcthree on 2010-11-19
Wow, things are going from bad to worse.

Now the pen nib (mouse 1) is flickering on and off when I move the pen over the pad (without touching).

I've checked the pad on windows and it works fine.

---

### Post by Favux on 2010-11-19
Hi tmcthree,

That doesn't sound good.  Did anything change lately?  A kernel update or anything?  Is 'xinput --list' unchanged?  Did you see my edit on ClickForce in the HOW TO?

---

### Post by tmcthree on 2010-11-19
Hi Faux, thanks for gatting back to me.

Well I did a regular update and it seemed to start after that I've gone through the steps in this thread again and it doesn't seem t work. 

Its even stranger than I thought. The flickering mouse 1 only seems to happen with some programs. It happens on the Ubuntu desktop, in Chrome and in blender. But it doesn't happen in the drawing area of Gimp, or Zbrush running under wine.

I'll look at the new step in teh how to now.

---

### Post by tmcthree on 2010-11-19
Ok it is happening in Zbrush. The only place it definitely doesn't happen is GIMP, while drawing. GIMP when doing anything else, menus, moving the canvas etc, it happens.

---

### Post by tmcthree on 2010-11-19
Thanks faux that seems to have worked. 

I set it to xsetwacom set "WALTOP International Corp. Slim Tablet stylus" ClickForce "100"  # default is 27, 0-1024

It still happened when set to 27 but 100 seems ok. Do you know why it just started happening now?

---

### Post by Favux on 2010-11-19
Nice job.

No.  I guess we still need some changes in the kernel that are coming for things to totally iron out.  But if modifying ClickForce fixes it I'd call that good!

By the way the range should be 0-2047.  Let me check on the HOW TO.

---

### Post by tmcthree on 2011-01-03
Hi Favux,

Sorry to bother you (yet again), but my tablet has finally given up the ghost (it doesn't work on windows now either so its dead).

So I'm thinking of getting a new ne but I want to make sure it works on linux, which is a bit of a problem because none of them (including my current one) seem to  say they support linux. Is there any way to tell in advance?

For example this one, any idea?
[http://www.amazon.co.uk/gp/product/B003A6EJ8U/ref=noref?ie=UTF8&s=computers&psc=1](http://www.amazon.co.uk/gp/product/B003A6EJ8U/ref=noref?ie=UTF8&s=computers&psc=1)

---

### Post by Favux on 2011-01-04
Hi tmcthree,

Sorry to hear that.  It isn't that you just need a new battery in the stylus by any chance?


No I don't know anyway unless they tell you on the packaging or their web site.  Otherwise you have to do a google search and see if someone has set up the same or similar model.  There is a supported hardware linux site but I don't know how complete and up to date it is.

Since it's an Aiptek you'd figure it would use the Aiptek driver.  But it may be something else rebranded by them.

Since you use Ubuntu you might want to do a site search with google:

site:ubuntuforums.org Aiptek HyperPen Mini Nature

---

### Post by ArtMonkey on 2011-01-11
> **Favux said:**
> Outstanding!  :)

Keep me updated as to how it is working.  It looks like I can change the HOW TO's.  So I need confirmation that you're getting pressure, etc.

As promised attached to the bottom of the post is the xsetwacom script for the stylus.  Instructions for installing it are in step IV. at the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").


Hi there. I'm new to Ubuntu. I have installed 10.10 amd x64 version. I'm attempting to move most of my work over to Ubuntu and your instructions have been most helpful for this tablet.  I haven't tried this above script yet but the tablet is working beautifully in Krita after the reboot. So I thought I'd join the forum just to say thanks :)

One thing I noticed is there is an "xserver-xorg-input-aiptek" driver in the Ubuntu software centre. I tried this before but it wouldn't work. Just wondered why it's there?

Thanks again!

---

### Post by Favux on 2011-01-11
Hi ArtMonkey,

Welcome to Ubuntu forums!

Glad it helped you.  An updated xsetwacom stylus script is on the [Waltop HOW TO]("http://ubuntuforums.org/showpost.php?p=9966110&postcount=1").
> One thing I noticed is there is an "xserver-xorg-input-aiptek" driver in the Ubuntu software centre. I tried this before but it wouldn't work. Just wondered why it's there?

Because there are some tablets that need to use the Aiptek or WizardPen driver because they don't work with Wacom.

---

### Post by ArtMonkey on 2011-01-11
Thanks! I'll give that a whirl :)

I'm getting used to Ubuntu. Getting the tablet going is a real plus. Getting acclimatised to Gimp is the next big job to do after years of Photoshop use in Windows.

---

