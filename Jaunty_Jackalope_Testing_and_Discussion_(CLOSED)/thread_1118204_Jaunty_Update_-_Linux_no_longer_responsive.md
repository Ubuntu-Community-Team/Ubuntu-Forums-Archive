---
title: "Jaunty Update - Linux no longer responsive"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by edwin.galloway on 2009-04-06
I run Jaunty on a Gateway laptop, specs will be forthcoming if it comes to that.

I came home, ran the update manager, and was prompted to restart. I did, the system got past bios, ran a disk check, and then the loading bar showed up. When it got to the end, I was greeted by a black screen with a red pixel gibberish stipe across the top, and a pixel-y smear across the middle. The CPU is not 'working' and it sits there though the laptop's lights are still on, and it's built in function keys and images still work (i.e. the brightness indicator goes up and down onscreen).

I have restarted, and I have tried logging in blindly, but this doesn't seem to have any effect.

Apart from reinstalling, any ideas?

---

### Post by jmmL on 2009-04-06
Haven't experienced anything like this myself. Try ctrl+alt+f1 to go to a console and log in from there. Then issue *startx*. Not sure if this will work, but worth a try.

Specs might well be useful - particularly the make and model of your graphics card.

---

### Post by jfernyhough on 2009-04-06
I'll wager you have integrated Intel graphics.

Restart in recovery mode, edit /etc/X11/xorg.conf and change Driver "Intel" to Driver "vesa".

Restart. X should load. Keep the settings intact until the xorg-drivers-intel drivers are updated, then change the configuration back to Intel driver.

Even if you don't have an Intel chipset the above will at least allow you to get logged in.

---

### Post by edwin.galloway on 2009-04-06
I did try switching to a terminal no dice - but I'll try again for fun.

Also:

	Motherboard ATI 128MB w/945PM and 1394 
	Intel Pentium Dual-Core Processor T2130
I also believe there is an ATI mobility in there somewhere too, which I know is real informative.

---

### Post by rbmorse on 2009-04-06
That's OK...what jfernyhough posted should still apply.

---

### Post by edwin.galloway on 2009-04-06
Thank you for your help so far:

1)the driver said ati, rather than Intel. I changed it to vesa anywho, but the problem persisted.

2) I did notice when I tried to boot from recovery mode that the kvm module was failing

could that be related?

---

### Post by kansasnoob on 2009-04-06
I ran out of room - literally - and had to run:

```
sudo apt-get autoclean && sudo apt-get clean
```

During these dev processes things don't always clean up like they would in a full release!

---

### Post by edwin.galloway on 2009-04-06
While that made me feel like I was accomplishing something, it didn't fix my issue...

---

### Post by elcman on 2009-04-06
Wow, I'm glad that I've finally found post that said that the intel video drivers are broken. I've been running in VESA mode ever since I installed Jackalope on a C400 Dell laptop.

But now even my VESA settings are giving me a blank white screen when I log in. It seems to load a background image first, then it goes white and seems to be waiting at a dialog that I can't see. (I can see the dialog box when I hit the power switch and it starts to shut everything down.)

Also, another question about VESA, since it seems I'm stuck with it. Is there a way to run it at a resolution higher than 640x480? I've looked all over and can't seem to find any information on it. I've tried to muck with xorg.conf, but since it seems to autodetect most things, it doesn't always work exactly as I expect.

Any help would be very much appreciated. Thanks!

~~
Erik

---

### Post by Ericyzfr1 on 2009-04-06
I had a similar problem....After updates I entered login and password, then nothing, pointer and keyboard were unresponsive. I reinstalled, updated and the same thing happened.....Went through the process again and it worked. I know it is a beta, so hopefully the real thing will run like a champ.

---

### Post by edwin.galloway on 2009-04-07
Well, god knows I have no clue, but it seems like this ought to be fixable.

I could have reinstalled 15 times by now, but since other people are having this problem, and even reinstalling is no gurantee...

---

### Post by elcman on 2009-04-07
I must say that I've been experiencing intel driver issues since when I first installed Intrepid so this isn't all that new to me. However, it seems to have gotten considerably worse.

My symptom when I'm using the Intel driver is a proper display when I get to gdm... then as soon as I try to type, it takes the first character and freezes. I tried to type my username and password just to see if it was working in the background, but I didn't get hard drive activity like I expected when I usually first log in.

I did get *some* activity, but it seemed like the usual momentary activity you get when a background process is running.

My next question would be... how do I cleanly and completely remove the intel driver and make sure I'm actually getting a new one. I did a **apt-get remove xserver-xorg-video-intel** once and my system nearly ended up in tears, it was so frustrated. :)

I'm wondering if I still have some residual artifacts in current configuration that isn't allowing me to properly use the drivers. Does that make any sense?

I'm going to try and apt-get remove and another apt-get to see if I can get the latest stuff cleanly installed. It sounds like *someone* is having luck with it... I hope that someone will someday be me. :)

---

### Post by edwin.galloway on 2009-04-07
elcman, what your are describing sounds exactly like my issue. I have tinkered with my xorg until I can't stand to look at it but I am out of ideas. the gdm thing does seem like a lead...

---

### Post by DougieFresh4U on 2009-04-07
I know a while back when I had Intel graphics and my machine locked up etc etc., there was this fix to get Intel working and I am not sure if it still works, but it did a couple of months ago when Intel was giving my machine a fit. 
Just a thought
```
Re: X-server breakage

Put this in file:
[B]/etc/X11/xorg.conf

Section "Device"
Identifier "Configured Video Device"
Driver "Intel"
Option "NoAccel" "true"
EndSection
Good luck 
```
EDIT: If you can't get into your xorg conf  because of 'borked' machine, this is what helped me get in via live cd (I am no 'guru' by all means)
Don't worry about the "borked" system---from your LiveCD--

```
In a terminal

1. sudo mkdir /media/a <return>
2. sudo mount /dev/sda1 /media/a <return> (this assumes that your OS is on sda1--if this is different, supply the correct info--depends on if you have Windows installed & a couple of other factors)
3. sudo gedit /media/a/etc/X11/xorg.conf <return>
4. save the change
5. reboot into your OS
```

---

### Post by elcman on 2009-04-07
DougieFresh4U, you rock my world!

I have always made sure to keep the recovery console available so that I could get past any hard X11 errors, so it was a simple nip-tuck with the "NoAccel" command.

Funny thing, I researched that a LONG time ago, but subsequently forgot that I did that. You mentioning it brought all those bitter-sweet memories back.

Hey, one other question now... for *some reason* I'm now booting to a white screen and an active cursor. This is like it was in VESA mode with a hidden dialog box somewhere on the page... Any idea what caused this?

Other than that, I'm booting in at full screen and I didn't experience the freeze. I've had the Accelerated stuff working int he past, albeit not that well, but I'm glad you pointed me in the right direction again.

Now to research the white screen issue I'm having...

~~
erik

---

