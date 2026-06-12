---
title: "Why is my Synaptic touchpad being treated like a normal mouse?"
date: 2008-08-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Starks on 2008-08-19
I don't appreciate how X isn't detecting it as a touchpad.

I can't even disable tapping without manually configuring xorg.conf and then reconfiguring again and again whenever Ibex forces me to a do dpkg-reconfigure of the xserver.

---

### Post by Quikee on 2008-08-19
> **Starks said:**
> I don't appreciate how X isn't detecting it as a touchpad.

I can't even disable tapping without manually configuring xorg.conf and then reconfiguring again and again whenever Ibex forces me to a do dpkg-reconfigure of the xserver.

You can set: ```
"SHMConfig"    "true"
``` in the xorg.conf and use  a program like [GSynaptics]("http://gsynaptics.sourceforge.jp/") for configuration.

---

### Post by Starks on 2008-08-19
> **Quikee said:**
> You can set: ```
"SHMConfig"    "true"
``` in the xorg.conf and use  a program like [GSynaptics]("http://gsynaptics.sourceforge.jp/") for configuration.

Please read my post again.

The xorg.conf doesn't even configure the touchpad (ie: 1 inputdevice entry = both my mx510 mouse and my touchpad) and I would prefer not having to do it manually over and over again.

I know how to do it, but I shouldn't have to.

---

### Post by Starks on 2008-08-20
Bumping because this is important to me.

---

### Post by MadMan2k on 2008-08-20
try this kind of configuration:
[http://mvogt.wordpress.com/2008/08/15/xorg-evdev-and-emulatewheel/](http://mvogt.wordpress.com/2008/08/15/xorg-evdev-and-emulatewheel/)

---

### Post by Starks on 2008-08-21
Thanks. But it doesn't help.

The people working on X development have clearly shot themselves in the foot. Their desire for a config-less X server has prompted them to sacrifice the once-present comprehensive support for touchpads and resort to simply assigning a driver that 'works', yet lacks critical functionality.

---

### Post by ronacc on 2008-08-21
try replacing your xorg.conf with a known working copy , the one from your hardy install will work fine .if there is a "full" xorg.conf present it will be used .

---

### Post by Starks on 2008-08-21
> **ronacc said:**
> try replacing your xorg.conf with a known working copy , the one from your hardy install will work fine .if there is a "full" xorg.conf present it will be used .
Yes. I know that. But I have to dpkg-reconfigure whenever X chooses not to start my display after a few power cycles. So, it doesn't last.

---

### Post by ronacc on 2008-08-21
are you getting the low graphics warning ?  if so try this , do not click anything , kill the low graphics warning with ctrl+alt+bkspc then alt+F1 login to the term and either restart GDM or reboot and see if that works , continuing in low graphis mode trashes your xorg.conf   .

---

### Post by nanog on 2008-08-31
This is a *bug* and a regression. My previously perfectly recognized synaptics touchpad (in hardy and intrepid) is now detected as a mouse. The only way to get around this is to manually fix xorg. I'll file a bug when I have time.

---

### Post by nanog on 2008-08-31
A temporary fix is to add this to your xorg.conf:

```

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option         "SHMConfig"  "on"
EndSection

```

In my case I had to add:
```

    Option         "SHMConfig"  "on"

```

(I use my old xorg because several monitors are not detect by recent xserves.)

---

### Post by zd3nik on 2008-08-31
I've also been manually updating xorg.conf to get around this problem.  And I'm getting weird results.  Occasionally the xorg conf is reverted (which is annoying), and sometimes it just plain ignores what's there (which is REALLY annoying).  I even go as far as rebooting to make sure X server is restarted properly.  Yet the SHMConfig option I put in there is being completely ignored (sometimes).

Maybe this is part of the bug or maybe I'm just doing something stupid.  Here is the relevant section of my xorg.conf:

```
Section "InputDevice"
    Identifier  "Synaptics Touchpad"
    Driver      "synaptics"
    Option      "SendCoreEvents"    "true"
    Option      "Device"    "/dev/psaux"
    Option      "Protocol"  "auto-dev"
    Option      "HorizEdgeScroll"   "0"
    Option      "MaxTapTime"    "0"
    Option      "SHMConfig" "on"
EndSection

```

And even though, at this moment, I have just finished a clean boot (not "absolutely" necessary I know) there is no "Touchpad" tab in the mouse preferences window.  And when I try to run the Synaptics Touchpad app it gives me the dreaded "You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics" message.

I have tried using "true" instead of "on".  No difference.  And as you can see I have also added the MaxTapTime 0 option.

So to sum it up:

* Sometimes manually configuring xorg.conf works.
* Sometimes xorg.conf gets reverted back and I have to make the changes again.
* Sometimes the options I put into xorg.conf are ignored (X has been restarted)

WTF???

Z

---

### Post by Starks on 2008-08-31
Is a ServerLayout entry needed?

---

### Post by zd3nik on 2008-08-31
> **Starks said:**
> Is a ServerLayout entry needed?

```

Section "ServerLayout"
    Identifier  "Default Layout"
  screen "Default Screen"
    Inputdevice "Synaptics Touchpad"
EndSection

```

I've also gone as far as removing the Generic Mouse input device entry from the config entirely.  I've also gone as far as modifying the xorg.conf.failsafe to match the regular xorg.conf (the relevant sections anyway).

Here is some more info that may help anyone that has the means and the inclination to actually try to fix this problem: I have two laptops, a Dell Inspiron E1505 and a Dell XPS M1530.  I've had the E1505 for a while and have never had the touchpad issue on that machine.  Only the M1530 is having this issue.  I have the exact same version of everything loaded on both machines.  So obviously this is a hardware detection issue, not necessarily and issue with the way X configures itself in general.

Z

---

### Post by Nullack on 2008-08-31
Generally it is better to allow HAL to identify devices and have an absolute minimum xorg.conf.

---

### Post by Starks on 2008-08-31
The X devs were very foolish when they decided that doing away with xorg.conf was a good idea.

---

### Post by zd3nik on 2008-08-31
> **Nullack said:**
> Generally it is better to allow HAL to identify devices and have an absolute minimum xorg.conf.

Agreed, but since that doesn't work we're stuck with tweaking xorg.conf until this bug is fixed, unless you have any other suggestions that might work.

Z

---

### Post by Nullack on 2008-08-31
> **Starks said:**
> The X devs were very foolish when they decided that doing away with xorg.conf was a good idea.

I suggest your being foolish :)

If you think more about hot plugging and many associated use patterns you will see the need for it.

---

### Post by Starks on 2008-08-31
> **Nullack said:**
> I suggest your being foolish :)

If you think more about hot plugging and many associated use patterns you will see the need for it.

Not until multiple monitors on Intel chipsets and Synaptics touchpads are properly supported.

---

### Post by AikonIV on 2008-09-01
Temporary regressions are sometimes a byproduct of the process of refactoring a system to move beyond design decisions made years before which have since become restrictive to future development (cf. KDE4...) I am confident that X is moving in the right direction, albeit rather slowly.

In the meantime, make sure bugs get reported so nothing falls through the cracks (there's been a lot of activity with the new synaptics driver stuff lately btw) and keep your more extensive xorg.conf in place. If you get too frustrated with having it consistently overwritten, I would suggest staying away from the latest packages until things have matured further. :)

---

### Post by nanog on 2008-09-01
Lets keep this thread on topic please. 

I've reported a bug (not sure if HAL is the right package). Please confirm and add comments.

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/263662](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/263662)

---

### Post by ntetreau on 2008-09-04
At least on my setup, the latest updates to the synaptic driver package fixes the issue, my touchpad is recognized as such even after removing my custom xorg.conf (I'm now running without one).  I still have the touchpad tab in the mouse configuration utility.

---

### Post by _oOMOo_ on 2008-09-04
> **ntetreau said:**
> At least on my setup, the latest updates to the synaptic driver package fixes the issue, my touchpad is recognized as such even after removing my custom xorg.conf (I'm now running without one).  I still have the touchpad tab in the mouse configuration utility.

About time too, we had all this when testing Hardy too. I still have to edit my xorg.conf though, or I can't set up 3-finger and 2-finger tapping to emulate middle and right button events.

---

### Post by wgrant on 2008-09-06
> **ntetreau said:**
> At least on my setup, the latest updates to the synaptic driver package fixes the issue, my touchpad is recognized as such even after removing my custom xorg.conf (I'm now running without one).  I still have the touchpad tab in the mouse configuration utility.

The default is that a two-finger tap is a middle click, and a three-finger tap is a right click. It has been that way for a few days now, though it was broken for a while.

You don't need to edit xorg.conf to change such settings any more; almost everything can be customised using 'xinput'. That's how I reimplemented the Touchpad tab.

---

### Post by zd3nik on 2008-09-06
> **ntetreau said:**
> At least on my setup, the latest updates to the synaptic driver package fixes the issue, my touchpad is recognized as such even after removing my custom xorg.conf (I'm now running without one).  I still have the touchpad tab in the mouse configuration utility.

Stupid question: Where do you get the synaptec driver package?

Z

---

### Post by phenest on 2008-09-07
> **fujitsu said:**
> You don't need to edit xorg.conf to change such settings any more; almost everything can be customised using 'xinput'. That's how I reimplemented the Touchpad tab.

I don't have the touchpad tab.

---

### Post by wgrant on 2008-09-07
> **phenest said:**
> I don't have the touchpad tab.

Upgrade and reboot. That has fixed it for all cases I've heard of so far. If it doesn't... well, we'll debug further.

---

### Post by zombiepig on 2008-09-07
> **fujitsu said:**
> Upgrade and reboot. That has fixed it for all cases I've heard of so far. If it doesn't... well, we'll debug further.

fujitsu - I've installed a clean copy of alpha 5, with all updates, and rebooted a few times, but I'm also missing the touchpad settings. Is there anything I can provide to help you track this down? Or would you like me to file a new bug report for it?

---

### Post by wgrant on 2008-09-07
> **zombiepig said:**
> fujitsu - I've installed a clean copy of alpha 5, with all updates, and rebooted a few times, but I'm also missing the touchpad settings. Is there anything I can provide to help you track this down? Or would you like me to file a new bug report for it?

Please file a bug at [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+filebug](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+filebug), and attach /var/log/Xorg.0.log.

---

### Post by zombiepig on 2008-09-07
thanks fujistu, here's the bug report:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/267611](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/267611)

---

