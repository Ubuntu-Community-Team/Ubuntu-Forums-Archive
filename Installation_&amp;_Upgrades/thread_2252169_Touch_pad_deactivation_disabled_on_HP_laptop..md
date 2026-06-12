---
title: "Touch pad deactivation disabled on HP laptop."
date: 2014-11-09
forum: Installation &amp; Upgrades
---

### Post by Owen Thomas on 2014-11-09
Hello again Ubuntu.

I have recently installed Ubuntu 14.4 on a new HP laptop. The OS has installed fine, yet I find that the feature where I can double-tap the touch pad in the top-left hand corner to disable it is not working. I have called HP and they confirm to me that the feature is present on all its laptops.

Is there a driver for Ubuntu that needs to be installed to activate this feature? It is a continual frustration to have my computer do things I don't want it to do whenever I am trying to use the keyboard (like while I'm writing this) and the palms of my hands make inadvertant contact with the touchpad.

Thanks,

  Owen.

---

### Post by Owen Thomas on 2014-11-09
Okay...

I found [this]("http://askubuntu.com/questions/83590/how-do-i-disable-the-touchpad-using-the-upper-left-corner-on-an-hp-pavilion-dv6"), but still I'm not sure if this would work for my computer and no mention of a driver... has any materialised since this was posted?

The About This Computer information says my computer is an HP-250-G3-Notebook-PC. This is actually tacked on the end of my computer's device name, and I see nowhere else where this information might be written.

---

### Post by Owen Thomas on 2014-11-09
Hmmm....

The "Disable while typing" check box of the OS's Mouse and Touchpad settings dialogue is checked. Yet, my pointer is racing around the screen while I type this... not happy!

---

### Post by Owen Thomas on 2014-11-09
What would be nice is if I could disable the touchpad by double-tapping its top left corner is I am promised by operating instructions...

So my question remains to be answered... :)

---

### Post by Impavidus on 2014-11-10
Tapping to disable the touchpad doesn't work on my HP laptop either. But I enabled to option to disable the touchpad whilst typing and it works very well. There is a slider underneath (at least, there is on xubuntu) and I set the timeout to 2 second. Maybe yours is at 0.2 seconds?

---

### Post by irv on 2014-11-10
I did some testing on my touchpad on my Asus using these commands found on this page.
[https://help.ubuntu.com/community/SynapticsTouchpad]("https://help.ubuntu.com/community/SynapticsTouchpad")

---

### Post by irv on 2014-11-10
I also found this:
> Disable the touchpad while typing and adapt the delay

16. It's pretty useful to disable the touchpad (trackpad) of your laptop during typing, and tweak the delay. Especially on small laptops.

In Ubuntu, that's easy to configure: 

First, the disabling with the default delay: click on the grey Ubuntu logo (Dash home). Query: touchpad. 

Click on Mouse & Touchpad

The following option should be ticked:
Disable while typing

Note: in Ubuntu, this only disables the touchpad functions of tapping and scrolling. Mouse pointer movements are still allowed.
In Xubuntu, not even mouse pointer movements are allowed then.

Now the delay. When the touchpad has been configured like this, the default delay is two whole seconds. That's too long and interferes with productivity. When you wish to shorten the delay to one second, you can do this:

First entirely undo the current disabling: remove the tick for Disable touchpad while typing. Close the mouse and touchpad settings window.

Now create an adapted startup application:
Click on the grey Ubuntu logo (Dash home). Query: startup. 
Click Startup Applications - Add
Fill out the fields as follows (use copy/paste, that's easiest):

Name:
Syndaemon

Command:
syndaemon -i 1.0 -K -R -t

Comment:
Disable touchpad while typing, with a reasonable delay and only for tapping and scrolling

Click Add and then Close.

Reboot your computer.

Finally, check whether it's working, with the help of the following terminal command (copy/paste the line below in a terminal and press Enter):
ps aux|grep syndaemon

---

### Post by sudodus on 2014-11-10
There is also this link

[https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey](https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey)

with commands and scripts that work for me in several computers.

Basically

```
synclient touchpadoff=1
```

switches it off, and 

```
synclient touchpadoff=0
```

switches it on.

You can activate the touchpad automatically in 'autostart' or run a 'toggle script' in a terminal window to turn it on/off easily. You could also assign a hotkey combination for it.

See also this recent thread in the Ubuntu Forums

[http://ubuntuforums.org/showthread.php?t=2250916](http://ubuntuforums.org/showthread.php?t=2250916)

---

### Post by irv on 2014-11-10
I have a hot key on my Asus laptop [fn] + [F9] to turn touchpad on and off. Maybe you have a hot key on your HP?

---

