---
title: "Can no longer download &quot;Pointing Devices&quot; from Lubuntu Software Centre"
date: 2016-05-09
forum: Installation &amp; Upgrades
---

### Post by michael_brown2 on 2016-05-09
Hey guys

I used to have the above-mentioned program, but, after an update, it disappeared. I tried reinstalling it via lubuntu software centre, but, after I added it to the apps basket and looked in the apps basket, it wasn't there and the "Install Packages" button was greyed out and thus un-clickable. I tried going to synaptic package manager and installing the same thing (here called gpointing-device-settings), but, when I tried to click "Mark for Installation", it came up with an error message displayed below:
 
[ATTACH=CONFIG]268948[/ATTACH]

I used to use this program to disable touchpad "tapping" (the ability for the touchpad to recognise a tap to its main section as a click), which I found really annoying, as I would often accidentally tap the pad with my palm, while typing. It was also useful to disable using the touchpad to scroll, because I also found that annoying for similar reasons. It would be really great if the ability to download this program through either the software centre or the synaptic package manager were re-enabled, or, failing that, could you guys please give me some way to disable tapping.

Thanks
Micheal_Brown2

Edit: I'm running 16.04

---

### Post by BazBear on 2016-05-09
I ran into this when I was running Lubuntu 16.04 alpha/beta. If I recall correctly, I ended up downloading the G Pointing devices .deb file (from Launchpad I think), running it until it failed, then noting in the error message the dependency that needed updating, then I downloaded that .deb package (again, from Launchpad I believe), installed the dependency, then I ran the G Pointing Device .deb again, and Bingo!, it worked. Sorry that I can't recall the offending dependency, and I no longer have that 16.04 installation to check from.

A pain in the butt to be sure, but I hope this helps.

---

### Post by vasa1 on 2016-05-09
Could you please edit your question to include the version of Lubuntu? If you don't know, just run **lsb_release -a** in a terminal and include that output within code tags.

It seems the program you want is not available by default in 16.04: [http://manpages.ubuntu.com/cgi-bin/search.py?q=gpointing-device-settings&op=&cx=003883529982892832976%3A5zl6o8w6f0s&cof=FORID%3A9&ie=UTF-8](http://manpages.ubuntu.com/cgi-bin/search.py?q=gpointing-device-settings&op=&cx=003883529982892832976%3A5zl6o8w6f0s&cof=FORID%3A9&ie=UTF-8)

If you like a do-it-yourself approach, here's a bit of code that you can assign a shortcut key to and then use to toggle the touchpad *totally* on and off if that's what you want:
```
#!/bin/sh

TOGGLE=$HOME/.toggle

if [ ! -e $TOGGLE ]; then
    touch $TOGGLE
    synclient TouchPadOff=1 &
else
    rm $TOGGLE
    synclient TouchPadOff=0 &
fi

exit 0
```
You'd save the contents as, say, *toggle-touchpad* in *~/bin*, make it executable, and assign a shortcut to it by editing *~/.config/openbox/lubuntu-rc.xml*.

---

### Post by BazBear on 2016-05-09
[**[COLOR=#000000]michael_brown2[/COLOR]**]("http://ubuntuforums.org/member.php?u=2031115"), if you can't or don't want to use the method I sorta-kinda outlined above, the method in this post [http://askubuntu.com/questions/369319/how-to-disable-tap-to-click-in-lubuntu-13-10](http://askubuntu.com/questions/369319/how-to-disable-tap-to-click-in-lubuntu-13-10) *might* shut off tap-to-click in 16.04; at least I know it works in both 13.10 and 14.04. Unfortunately, I've yet to find a way to disable edge scroll, other than our old friend G Pointing Devices.

---

### Post by vasa1 on 2016-05-09
```
05:39 AM ~ $ synclient | grep -i edgescroll
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
05:39 AM ~ $ 

```

---

### Post by BazBear on 2016-05-09
> **vasa1 said:**
> ```
05:39 AM ~ $ synclient | grep -i edgescroll
    VertEdgeScroll          = 0
    HorizEdgeScroll         = 0
05:39 AM ~ $ 

```
Thanks _**Vasa1**_! I think had just tried adding "sysclient EdgeScroll=0" to the LXsession autostart list, without the Vert or Horiz! (doh!)

_**michael_brown2**_ , if the tap-to-click "fix" in this article [http://askubuntu.com/questions/369319/how-to-disable-tap-to-click-in-lubuntu-13-10](http://askubuntu.com/questions/369319/how-to-disable-tap-to-click-in-lubuntu-13-10) works, you can try adding these two additional entries to the LXsession autostart list.
```
synclient VertEdgeScroll=0
``````
synclient HorizEdgeScroll=0 
```

It's working like a charm for me, no need for G Pointing Devices anymore.

---

### Post by vasa1 on 2016-05-09
Similarly, there's ```
08:59 AM ~ $ synclient | grep -i touchpad
    TouchpadOff             = 0
08:59 AM ~ $ 


```but then turning on the touchpad requires reversing that which is why I suggested the toggle (thanks to yetimon_64!).

---

### Post by BazBear on 2016-05-10
> **vasa1 said:**
> Similarly, there's ```
08:59 AM ~ $ synclient | grep -i touchpad
    TouchpadOff             = 0
08:59 AM ~ $ 


```but then turning on the touchpad requires reversing that which is why I suggested the toggle (thanks to yetimon_64!).
_**Vasa1**_, I could be mistaken, but I don't think _**michael_brown2**_ wants to totally disable the touchpad. I've been giving him a GUI solution, but if he's comfortable editing a config file in a text editor (quicker and simpler IMO), open ~/.config/lxsession/Lubuntu/autostart in leafpad (or any text editor), then copy & paste the following and add it to the file.```
synclient MaxTapTime=0
synclient VertEdgeScroll= 0
synclient HorizEdgeScroll= 0
```
(This file may be empty to begin with; if not add it below everything else.)
Save the file, log out of Lubuntu (or reboot), then log in, and you should (probably, I've not tested this in 16.04)) be golden regarding tap-to-click and edge scroll.

---

### Post by vasa1 on 2016-05-10
> **BazBear said:**
> _**Vasa1**_, I could be mistaken, but I don't think _**michael_brown2**_ wants to totally disable the touchpad. I've been giving him a GUI solution, but if he's comfortable editing a config file in a text editor (quicker and simpler IMO), open ~/.config/lxsession/Lubuntu/autostart in leafpad (or any text editor), then copy & paste the following and add it to the file.```
synclient MaxTapTime=0
synclient VertEdgeScroll= 0
synclient HorizEdgeScroll= 0
```
(This file may be empty to begin with; if not add it below everything else.)
Save the file, log out of Lubuntu (or reboot), then log in, and you should (probably, I've not tested this in 16.04)) be golden regarding tap-to-click and edge scroll.

Fair enough!

BTW, [a wiki page on Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Mouse#Touchpad_settings") has these tips on the topic:```
Touchpad settings

Edit ~/.config/lxsession/Lubuntu/autostart with the respective values to achieve the desired result on the following.

Please note there are many more options. Looking at the man pages for synaptics (the driver options), synclient (interfaces with the driver), & syndaemon (handles relationship between keyboard and touchpad) should reveal the breadth of them.

You can view current settings with

synclient -l

More common requests include:
Enable horizontal two finger scrolling

synclient HorizTwoFingerScroll=1

Disable tap to click

synclient MaxTapTime=0

Disable coasting (scrolling after release)

synclient CoastingSpeed=0

Disable touchpad while typing

syndaemon -d -t
```

I haven't had much problem with my touchpad and so haven't looked at "syndaemon -d -t".

---

### Post by michael_brown2 on 2016-05-11
Thanks for all that guys, but I just ended up fixing the problem by going with bazbear's first suggestion. I found the missing dependency for the gpointing-device-settings .deb file was libgpds0, which either needed an install or an update past version 1.5 - I'm not sure. Anyway, whichever I did, I did it with a .deb file.

---

### Post by BazBear on 2016-05-11
> **michael_brown2 said:**
> Thanks for all that guys, but I just ended up fixing the problem by going with bazbear's first suggestion. I found the missing dependency for the gpointing-device-settings .deb file was libgpds0, which either needed an install or an update past version 1.5 - I'm not sure. Anyway, whichever I did, I did it with a .deb file.I'm glad to hear my somewhat vague recollection of how I fixed it was enough to send you in the right direction.:)

---

