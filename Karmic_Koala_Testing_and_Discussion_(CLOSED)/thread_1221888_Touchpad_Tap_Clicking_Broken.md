---
title: "Touchpad Tap Clicking Broken"
date: 2009-07-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tekstr1der on 2009-07-24
After the recent update to gnome-settings-daemon, although the option is enabled under Preferences > Mouse > Touchpad, tap clicking is broken again.

```
~$ synclient TapButton1=1
```

gets it working again (for the session anyway).

---

### Post by taavikko on 2009-07-24
And horizontal scrolling :(

Which can be enabled via
```
synclient horizedgescroll=1
```

---

### Post by wayne_cat on 2009-07-24
the same problem here ... Macbook Pro ... setting the options in xorg.conf or via HAL
does not fix the problem.

Bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/404219](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/404219)

edit: please confirm the problem in the bug report (-> click on "This bug affects me too") or add further information.

---

### Post by taavikko on 2009-07-24
confirmed.

just noticed funny thing, if opening a pic with EOG, using "horizedgescroll" it acts like vertical scroll... hmm.. malformed line.. anyone?

---

### Post by infamousrev on 2009-07-24
> **taavikko said:**
> And horizontal scrolling :(

Which can be enabled via
```
synclient horizedgescroll=1
```


This solution isnt working for me.

Any other suggestions?

---

### Post by infamousrev on 2009-07-24
> **Vertical Scroll:**
synclient VertEdgeScroll=1
synclient VertTwoFingerScroll=1

**Horizontal Scroll:**
synclient HorizTwoFingerScroll=1
synclient HorizEdgeScroll=1

Fixed it :)

---

### Post by wayne_cat on 2009-07-24
> **infamousrev said:**
> Fixed it :)

yes ... after this horizontal and vertical scrolling are back again.

---

### Post by tjeremiah on 2009-07-24
enable the touchpad again with [gsynaptics]("apt://gsynaptics").

---

### Post by wayne_cat on 2009-07-24
> **tjeremiah said:**
> enable the touchpad again with [gsynaptics]("apt://gsynaptics").

the touchpad is already enabled ... re-enabling does not fix the "scroll problem"

---

### Post by tjeremiah on 2009-07-24
> **wayne_cat said:**
> the touchpad is already enabled ... re-enabling does not fix the "scroll problem"

after the update, mines wasn't enabled. I just re-downloaded gsynaptics and all was well.

---

### Post by Nburnes on 2009-07-24
The download gsynaptics as people are stating works.

I have my tapping and side scrolling back on my Synaptic Trackpad.

---

### Post by wayne_cat on 2009-07-24
> **Nburnes said:**
> The download gsynaptics as people are stating works.

I have my tapping and side scrolling back on my Synaptic Trackpad.

unfortunately gsynaptics is a deprecated tool (no longer maintained). A fixed 
gnome-settings-daemon will be available soon.

edit: the gsynaptics follower -- [http://live.gnome.org/GPointingDeviceSettings](http://live.gnome.org/GPointingDeviceSettings)

---

### Post by chrisccoulson on 2009-07-24
It will be an updated gnome-control-center first, to migrate the mouse settings capplet UI to use the new touchpad settings in gnome-settings-daemon.

A gnome-settings-daemon update will come after to make sure that existing configs are migrated correctly on upgrade.

Incidentally, the touchpad settings can currently be configured with the following gconf keys:

```
/desktop/gnome/peripherals/touchpad/disable_while_typing (bool)
/desktop/gnome/peripherals/touchpad/tap_to_click (bool)
/desktop/gnome/peripherals/touchpad/scroll_method (int 0=off, 1=edge-scrolling, 2=two-finger-scrolling)
/desktop/gnome/peripherals/touchpad/horiz_scroll_enabled (bool)
```

---

### Post by tekstr1der on 2009-07-24
Thanks for those keys. That's a nice fix for now till the updated packages come down.

---

### Post by wayne_cat on 2009-07-24
From the bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/404219](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/404219)

```
This is actually already fixed upstream in g-c-c, and will be in the
2.27.4 upload
```good job!

---

### Post by mariner09 on 2009-07-24
Installing gsynaptics and enabling touchpad clicks worked for me...

---

### Post by mariner09 on 2009-07-24
Of course, after replying I actually read the thread and installed the gpointing-devices applet and that works just as well...

---

### Post by DanaG on 2009-07-25
Copied from my post on that bug report:

> Hmm, something new I just noticed: the latest gnome-settings-daemon FORCES me to choose either two-finger scrolling OR edge-scrolling, and does not allow both -- thus overriding my preference I have set in a custom FDI file! In addition, it's not content to just reset the settings once.... it does it over and over and over again. Can we please add a third possible value for the gconf key?
/desktop/gnome/peripherals/touchpad/scroll_method
Current values:
0 - disabled.
1 - edge.
2 - two-finger.
3 - DOES NOT EXIST, should be "both".

If we can't do that, then I'll have to find another way to make Gnome keep its "grubby little hands" off the thing, to use a figure of speech.


---

### Post by taavikko on 2009-07-25
> **chrisccoulson said:**
> 
Incidentally, the touchpad settings can currently be configured with the following gconf keys:

```
/desktop/gnome/peripherals/touchpad/disable_while_typing (bool)
/desktop/gnome/peripherals/touchpad/tap_to_click (bool)
/desktop/gnome/peripherals/touchpad/scroll_method (int 0=off, 1=edge-scrolling, 2=two-finger-scrolling)
/desktop/gnome/peripherals/touchpad/horiz_scroll_enabled (bool)
```

Thank you very much.

---

### Post by SushiR on 2009-07-25
> **wayne_cat said:**
> unfortunately gsynaptics is a deprecated tool (no longer maintained). A fixed 
gnome-settings-daemon will be available soon.

edit: the gsynaptics follower -- [http://live.gnome.org/GPointingDeviceSettings](http://live.gnome.org/GPointingDeviceSettings)

Wow! My touchpad on my Eee 901 is working for the first time like it should. PLUS it is disabled while typing.

---

### Post by dude2425 on 2009-07-25
I've had a terrible experience with this new update. On my Eee 1000h I used to use two fingers to scroll, two finger tap to middle click, and three finger tap to right click. It made sense to me that way. Now suddenly my settings in xorg.conf are completely ignored and right and middle click are reversed.

Can I please switch my right and middle click back to their original functionality? I'd much prefer to have my  xorg.conf back. I liked that.

---

### Post by iaskedalice09 on 2009-07-29
I agree. gnome-settings-daemon at least didn't break my trackpad.

---

### Post by dude2425 on 2009-07-31
Can someone please fix the multi-tap troubles? My right click and middle click are reversed still and there's no working configuration exposed to the end user to switch the two. My xorg.conf and 11-x11-synaptics.fdi don't change anything.

```
    Option        "TapButton3"        "3"
    Option        "TapButton2"        "2"
    Option        "TapButton1"        "1"
```
and
```
     <merge key="input.x11_options.TapButton3" type="string">3</merge>
    <merge key="input.x11_options.TapButton2" type="string">2</merge>
    <merge key="input.x11_options.TapButton1" type="string">1</merge>
```

are set in xorg.conf andd 11-x11-synaptics.fdi respectively. They don't seem to affect anything anymore.

---

### Post by iaskedalice09 on 2009-07-31
I'm sorry I can't help you. Thought I'd say after the latest gnome-settings-daemon update, I'm still having trouble.

I definitely feel your pain. :(

---

### Post by azanutta on 2009-08-07
> **dude2425 said:**
> Can someone please fix the multi-tap troubles? My right click and middle click are reversed still and there's no working configuration exposed to the end user to switch the two. My xorg.conf and 11-x11-synaptics.fdi don't change anything.

```
    Option        "TapButton3"        "3"
    Option        "TapButton2"        "2"
    Option        "TapButton1"        "1"
```
and
```
     <merge key="input.x11_options.TapButton3" type="string">3</merge>
    <merge key="input.x11_options.TapButton2" type="string">2</merge>
    <merge key="input.x11_options.TapButton1" type="string">1</merge>
```

are set in xorg.conf andd 11-x11-synaptics.fdi respectively. They don't seem to affect anything anymore.

the same behaviour here... keys are always reversed and switching 3 to 2 in HAL doesn't change anything...
it's really annoying..
anyone came out with a solution or a workaround?!?!

---

### Post by SushiR on 2009-08-07
> **azanutta said:**
> the same behaviour here... keys are always reversed and switching 3 to 2 in HAL doesn't change anything...
it's really annoying..
anyone came out with a solution or a workaround?!?!+1

I don't know why the behaviour changed? Doesn't make any sense, does it?!

---

### Post by azanutta on 2009-08-07
> **SushiR said:**
> +1

I don't know why the behaviour changed? Doesn't make any sense, does it?!

yep.. if only there's a way to change it... coz the touchpad senses the 3 or 2 fingers well

---

### Post by DanaG on 2009-08-08
I can also confirm this... in the Xorg log, I see the following:
(**) Option "TapButton1" "1"
(**) Option "TapButton2" "2"
(**) Option "TapButton3" "3"

... and yet, when I log into gnome, I see this in synclient -l: 
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2

This may also have something to do with the thing acknowledging, and then later throwing out, my edge threshold settings.

---

### Post by jmmL on 2009-08-10
I can also confirm the swapped right and middle click. It's quite annoying!
Does anyone know if this is supposed to be a "feature"?

---

### Post by fondle-em on 2009-08-12
Is there any way to permanently disable tap-to-click without also disabling scrolling?  Permanently as in *permanently*.

---

### Post by dude2425 on 2009-08-12
> **DanaG said:**
> I can also confirm this... in the Xorg log, I see the following:
(**) Option "TapButton1" "1"
(**) Option "TapButton2" "2"
(**) Option "TapButton3" "3"

... and yet, when I log into gnome, I see this in synclient -l: 
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2

This may also have something to do with the thing acknowledging, and then later throwing out, my edge threshold settings.

I can't even use synclient to change this. `synclient TapButton2=2` `synclient TapButton3=3` does nothing for me.

This is frustrating

---

### Post by iaskedalice09 on 2009-08-14
Here's a bug report. If you're having trouble with the new gnome-settings-daemon on similar hardware, pls confirm

[Bug #412291 in gnome-settings-daemon (Ubuntu): &#8220;Trackpad and Mouse Odd on Dell Inspiron 1525n&#8221;](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/412291)

---

### Post by wendall911 on 2009-10-18
According to the Gnome bug for adding touchpad support here: [https://bugzilla.gnome.org/show_bug.cgi?id=578444](https://bugzilla.gnome.org/show_bug.cgi?id=578444) The default setting for click was hardcoded to 1/3/2. Lame, and typical of Gnome devs. Especially when it would have been trivial to:

1. Just use the system default
2. Set a gconf key to configure.

There is a wishlist item in to have this added here: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/140602](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/140602)

---

