---
title: "Pen Tablet hover stops after clicking - WizardPen"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by TLangas on 2010-09-20
I'm attempting to set up my ***"    Tablet PF1209"*** pen tablet in Ubuntu 10.04. There should be 4 spaces before Tablet but this forum removes them. I've followed several of the HOW TOs and the best two I've found were:

[LIST]
[*][http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1528329&highlight=wizardpen](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1528329&highlight=wizardpen)
[*][https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)
[/LIST]

Everything works the way it should except once I 'click' with my pen. After I press down to select something or paint, I can't get the hover feature to return. Well it returns if I unplug and plug it back in. It's kinda hard to use a pen tablet when you can only move the cursor when painting/dragging.

I've never had this issue the last time I used my tablet (Ubuntu 7.04) so I'm a little stomped. I know a lot has changed since then so I'll need some help. Anyone have any ideas?

***Edit***
Finally updated to 10.10 and reinstalled driver.
Followed the steps:
[http://ubuntuforums.org/showpost.php...90&postcount=1]("http://ubuntuforums.org/showpost.php?p=9252390&postcount=1"),
and [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) for further troubleshooting.

***Edit***
After further testing, the issue may be caused by missing the [FONT=Courier New][FONT=Courier New]/usr/lib/X11/xorg.conf.d/ [/FONT][/FONT]folder, which would prevent the [FONT=Courier New][FONT=Courier New]70-wizardpen.conf[/FONT][/FONT] from being created.[FONT=Courier New][FONT=Courier New]
[/FONT][/FONT]

---

### Post by Joundill on 2010-10-15
I'm also having the same problem with my Aiptek 600u, which worked fine on 9.04, but has this error on 10.10

---

### Post by Favux on 2010-10-15
Hi,

We could try:
```
Option  "TPCButton"  "on"  # or "off"
```
in the 70-wizardpen.conf.  See:  [http://ubuntuforums.org/showthread.php?t=1595648](http://ubuntuforums.org/showthread.php?t=1595648)  It's for the Waltop but the Options are for the WizardPen and should work.

---

### Post by celticbhoy on 2010-10-21
> **Favux said:**
> Hi,

We could try:
```
Option  "TPCButton"  "on"  # or "off"
```
in the 70-wizardpen.conf.  See:  [http://ubuntuforums.org/showthread.php?t=1595648](http://ubuntuforums.org/showthread.php?t=1595648)  It's for the Waltop but the Options are for the WizardPen and should work.

Just tried your suggestion Favux, but still get the same results on a Trust TB-2100, which uses the aiptek chipset.

On boot hover works until I press down with the nib, then as said only pushing down will move the pointer.

I have only applied the 'fix' to install wizardpen, as there seem to be a few 'solutions' to this, but all a little different. The other problem is that so many are written Lucid as opposed to Maveric.

```
ection "InputClass"
   Identifier      "wizardpen"
   MatchIsTablet   "on"
   MatchDevicePath "/dev/input/event*"
   MatchTag        "wizardpen"
   Driver          "wizardpen"

EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchDevicePath "/dev/input/mouse*"
   MatchTag        "wizardpen"
   Driver          "mouse"
   Option          "MouseSpeed" "16"
   Option          "ignore"     "true"
   Option          "TPCButton"  "off"
EndSection
```

This is the output from my /usr/share/X11/xorg.conf.d/70-wizardpen.conf

At this point I have no aiptek conf file in the above directory

Any ideas

---

### Post by Favux on 2010-10-21
Hi celticbhoy,

I need to see your 'xinput --list' so I can fix the match lines in the .conf for you.  I haven't tried putting an Aiptek tablet on the WizardPen driver yet that I can recall.

---

### Post by celticbhoy on 2010-10-21
[email]office@office-laptop:/usr/share/X11/xorg.conf[/email].d$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Aiptek                                  	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera                          	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
[email]office@office-laptop:/usr/share/X11/xorg.conf[/email].d$

---

### Post by Favux on 2010-10-21
Alright, try this:
```
Section "InputClass"
   Identifier      "WizardPen class"
   MatchIsTablet   "on"
   MatchProduct    "Aiptek|AIPTEK|aiptek"
   MatchDevicePath "/dev/input/event*"
   Driver          "wizardpen"
   Option          "TPCButton"  "off"
EndSection

Section "InputClass"
   Identifier      "WizardPen ignore mouse dev class"
   MatchProduct    "Aiptek|AIPTEK|aiptek"
   MatchDevicePath "/dev/input/mouse*"
   Driver          "mouse"
   Option          "MouseSpeed" "16"
   Option          "ignore"     "true"
EndSection
```

---

### Post by celticbhoy on 2010-10-21
Thanx for the reply Favux.

Mixed results, the pen will now hover without problem, and mouse button2 works fine on the pen (right click on mouse). The problem is that now left click on mouse no longer works. Obviously on the pen this has been disabled, but it also disables on my touchpad.

Any ideas?

---

### Post by Favux on 2010-10-21
We may be able to fix that.  Does your Aiptek tablet have a tablet mouse?  Or are you talking about a generic usb mouse and your touchpad?

---

### Post by celticbhoy on 2010-10-21
> **Favux said:**
> We may be able to fix that.  Does your Aiptek tablet have a tablet mouse?  Or are you talking about a generic usb mouse and your touchpad?

Sorry, should have been clearer. I am talking about my netbook touchpad.

But I have checked, and get this.

If tablet is not plugged in touchpad works fine.
Plug in tablet and touchpad works fine.
Use tablet by pressing nib, touchpad left button stops working.
Un-plug tablet, touchpad works fine.

Hope that makes it a little easier to troubleshoot.

---

### Post by celticbhoy on 2010-10-21
As an additional, the tablet does come with a mouse, and it works fine.
As does the trackpad when using the mouse instead of the pen.

Funny, after using the mouse, the pen no longer stops the trackpad button working, during this session.

---

### Post by Favux on 2010-10-21
OK, so a reboot fixed things?  Let me know if the problem returns.

---

### Post by celticbhoy on 2010-10-21
Not quite all ok, if I use the pen without first using the mouse, my problem persists. But if I use the mouse at any point, then after this it works fine.

Just giving you this info in-case it helps someone else.

I will also try again with the button option set to 'on' and see if the mouse fix's that issue also.

---

### Post by Favux on 2010-10-21
My guess is that if you change the mouse snippet like so:
```
Section "InputClass"
   Identifier      "WizardPen ignore mouse dev class"
   MatchProduct    "Aiptek|AIPTEK|aiptek"
   MatchDevicePath "/dev/input/mouse*"
#   Driver          "mouse"
#   Option          "MouseSpeed" "16"
   Option          "ignore"     "true"
EndSection
```
That will fix it.

---

### Post by celticbhoy on 2010-10-21
will give it a try and post back

---

### Post by celticbhoy on 2010-10-21
Meant to ask, TPCbutton on or off?

---

### Post by celticbhoy on 2010-10-21
OK further update, by using

xinput set-button-map Aiptek 2 1 3 4 5 244

to switch the button order about, I now get a usable pen, without a pressure nib.

This is with TPCbutton off

But the downside is the tablet mouse buttons are mixed up ( 1 & 2 )

Which means the problem is the pressure nib.

---

### Post by matcatc on 2011-01-24
I'm having this same issue and am curious if you ever managed to get it to work correctly. Mine broke sometime after the upgrade to 10.10 (presumably it was the upgrade, but can't say for sure.)

EDIT: I eventually figured out that it was that the 10-aiptek.conf file in xorg.conf.d was supposed to be 50-aiptek.conf. I went ahead and mentioned this in [https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet). Someone might want to make it more explicit though.

---

### Post by TLangas on 2011-04-18
Finally updated to 10.10 and reinstalled driver.
Followed the steps:
[http://ubuntuforums.org/showpost.php?p=9252390&postcount=1](http://ubuntuforums.org/showpost.php?p=9252390&postcount=1),
This post,
and [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) for further troubleshooting.

---

