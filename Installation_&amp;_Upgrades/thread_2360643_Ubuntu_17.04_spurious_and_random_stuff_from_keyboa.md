---
title: "Ubuntu 17.04 spurious and random stuff from keyboard/pad"
date: 2017-05-06
forum: Installation &amp; Upgrades
---

### Post by thomas-walker-lynch on 2017-05-06
fresh install, first time with this distro.  

as the subject says I'm getting spurious mouse clicks and it makes the system difficult to use.  Very frustrating when trying to work.

It is not due to palm on the touch pad.  I've now witnessed it three times when typing with hands raised.  It almost seems that there is a chord on the keyboard doing it, as it seemingly happens when typing fast or fumble finger on the keyboard.

It is a Lenovo 510s.  The machine had Debian loaded on it before Ubuntu.  Though there were no spurious mouse clicks, the touch pad driver installed with no finger on pad mouse clicks (instead required mechanical button clicks).

Using xfce4 most of the time.  Hard to know if it is related because I don't use Unity often.  (Could it be?)

---

### Post by WMDwebs on 2017-05-07
Having the same issue since upgrade to 17.04 from Ubuntu-Gnome 16.10 on an HP Envy. 
no response for help led me to attempt to upgrade to the 17.10 developer...still random KB junk going on.

can't program or even write a paragraph of text without a ton of hassle.

---

### Post by thomas-walker-lynch on 2017-05-08
I've been playing with this more.  Initially I put my palms up on folded paper towels.  I tested and a palm rub through the towel did not register as a click.  However I still get spurious clicks.  Then I tried typing while holding my hands off the platform up in the air.  Wow, still got spurious clicks, and that proves they are spurious.  

It seems that the sensitivity of the pad is increasing with time.  It becomes so sensitive after a while that the smallest of grazing of the pad with my finger tip makes a click.  When waiting longer the pad appears to go off on its own, perhaps triggered by vibration or proximity.  After the click, the sensitivity goes back to normal.  Hence, with regular use one might not see the problem.  However, in emacs, where I don't use the pad at all, it eventually gives me a spurious click.  It always seems to happen when in the zone and typing quickly hence a lot of text spillage occurs in the wrong place.  That combined with emacs hot key commands and it can be quite a show.

This is a security bug.  I had a spurious click occur just as I started typing a password, and then the password went visibly into a window.

I found a setting in xfce4 to turn off the pad while typing.  I turned it on, and verified it was working by hitting the pad while typing with the other hand.   It was working.  However, I have witnessed spurious mouse clicks while typing while this feature was turned on.  I am again wondering if there is aliasing between emacs cording and that of hot keys for the windowing system.  After the the spurious click while typing the mouse pointer is stuck in one place.   This has happened twice now.  Though the mouse pointer will not move, one can still use the buttons; for example to right click and to log out.

Often when the spurious click occurs,  the emacs buffer menu comes up.  This problem has been seen before, and a workaround is given for emacs, though no general solution:
[https://askubuntu.com/questions/596143/emacs-keeps-popping-up-buffer-menu-when-i-dont-want-it](https://askubuntu.com/questions/596143/emacs-keeps-popping-up-buffer-menu-when-i-dont-want-it)

---

### Post by #&amp;thj^% on 2017-05-08
I use the following properties for mine to reduce the overall sensitivity:

```
xinput set-prop "Touchpad Name" "Synaptics Noise Cancellation" 20 20
xinput set-prop "Touchpad Name" "Synaptics Finger" 50 90 255
```

NOTE: replace Touchpad Name with yours from the "xinput list"
```
xinput list
```

 I recommend keeping "Synaptics Noise Cancellation" low like 10 10 as it doesn't help solve the oversensitivity problem and makes the touchpad seem laggy for some when set higher. But works for me.
Also see this: [https://blog.laimbock.com/2014/11/23/howto-fix-a-too-sensitive-touchpad-on-linux/](https://blog.laimbock.com/2014/11/23/howto-fix-a-too-sensitive-touchpad-on-linux/)

---

### Post by thomas-walker-lynch on 2017-05-10
Those settings were a little too insensitive,  these work well on my system:

xinput list  # to see the name of the page,  below I used the name for the pad on my Lenovo, of course yours might be different
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Noise Cancellation" 10 10
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Finger" 40 70 192

This helps, and I am going to keep it in my .login file; however, it does not solve the problem.  It appears this is because the pad grows more sensitive over time, between clicks.  Eventually your are going to get a spurious click.  If this is due to static buildup (just guessing) then it will be a function of the weather, the environment of the building, and the grounding of the machine and user - yikes!

On the xfce4 mouse/pad menu there is an option for turning off the pad while typing.  This is a brilliant idea, and it almost works, except for this:  they do not block control-mouse-1 etc.  Hence while in emacs and one is cording with control alt, shift, etc.  One still gets spurious mouse clicks, the most common being control-mouse-1 which causes the buffer menu to pop up.  Above, I noted a post where they suggest leaving the mouse pointer on the title bar.  I found this to help, but I also found that the mouse pointer walks off the title bar after some time, and then I get a spurious mouse click, and the emacs buffer change menu - and perhaps more action depending on which keys are queued.

Haha, just now while typing this post on said system, with the pad sensitivity turned down (settings above) I just got a spurious mouse click, while typing with my hands held above the keybaord.  It selected the 'insert column before' button on the little html editor here.  I'm in Unity and I don't have the 'turn pad off while typing'  turned on.   Is there such a setting in Unity?

Summary:
1. touch pad sensitivity appears to grow with time between clicks, so adjusting the sensitivity down doesn't solve the problem.
2. xfce4 option to turn off the pad while typing is great, but they forgot to turn off control-mouse-1 etc.  so still getting spurious control-mouse-1 (etc.) clicks while in emacs.
3. this is a serious security bug, it potentially causes window focus changes and other actions while typing in passwords 

How can we turn off the pad while typing in general, and include turning off the control and alt mouse buttons??  This would be a good stop gap solution until someone figures out how to prevent #1 above.

---

### Post by #&amp;thj^% on 2017-05-10
I don't see mine as growing more sensitive with time...sorry about that.
This command worked for me (1) is the number of seconds to wait after the last key is pressed before re-enabling the touchpad, change it to whatever value you desire):

```
syndaemon -i 1 -K -d
```

Just add it to Startup Applications to make it work after reboot/shutdown. To see more options type this command in a terminal:

**syndaemon --help or man syndaemon**

_**Please Note below**_
And just a heads up If you add it to your Startup Applications though, you must also have **"Disable while typing" unchecked i**n the Mouse & Touchpad settings, otherwise the two mechanisms interfere with each other and the touchpad stops working completely.
EDIT: BTW there is also a PPA that adds support for touchpads.
Ask Ubuntu has refered to this PPA a few times...but I have no first hand knowedge with it so you would be on your own here: [https://launchpad.net/~atareao/+archive/ubuntu/atareao/+index?batch=75&memo=75&start=75](https://launchpad.net/~atareao/+archive/ubuntu/atareao/+index?batch=75&memo=75&start=75)
The item to look for is "touchpad-indicator"

---

