---
title: "Wacom support gone slightly awry in Maverick"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by Dave M G on 2010-10-10
I have just upgraded to Ubuntu 10.10, and as with every upgrade, the Wacom tablet has problems.

The problem is simply that when I boot or log in, the Wacom is not in "relative" mode, and the buttons are not configured as I have previously set them.

It seems that it has reverted to the default, and is ignoring my configuration files.

Any advice on how to diagnose and solve this problem would be much appreciated.

Here is the contents of my **/usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi**:

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="info.product" type="string">stylus</merge>
    <merge key="input.x11_options.Mode" type="string">Relative</merge>
           <merge key="input.x11_options.Button2" type="string">3</merge>
           <merge key="input.x11_options.Button3" type="string">2</merge>
           <merge key="input.x11_options.Speed" type="string">1.2</merge>
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
          <append key="wacom.types" type="strlist">eraser</append>
          <append key="wacom.types" type="strlist">cursor</append>
          <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="eraser">
      <merge key="info.product" type="string">eraser</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="cursor">
      <merge key="info.product" type="string">cursor</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="pad">
      <merge key="info.product" type="string">pad</merge>
    </match>
  </device>
</deviceinfo>
```

Here is the output of **xinput --list**:

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ATEN UC-10KM V1.3.124                       id=9    [slave  pointer  (2)]
&#9116;   &#8627; Dexin Corp. LASER Mouse                     id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 6x8 eraser                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 6x8 cursor                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 6x8 pad                     id=14    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 6x8 stylus                  id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; ATEN UC-10KM V1.3.124                       id=8    [slave  keyboard (3)]
    &#8627; zc3xx                                       id=11    [slave  keyboard (3)]

```

And here is the output of **xsetwacom list**:

```
Wacom Graphire4 6x8 eraser ERASER    
Wacom Graphire4 6x8 cursor CURSOR    
Wacom Graphire4 6x8 pad PAD       
Wacom Graphire4 6x8 stylus STYLUS
```

---

### Post by Favux on 2010-10-10
Hi Dave M G,

With Lucid and Maverick HAL/.fdi is no more.  Configuration is now done through the 10-wacom.conf in /usr/lib/X11/xorg.conf.d/.  You can think of the new .conf files in xorg.conf.d as extensions of the xorg.conf.

I've forgotten what tablet you have.  You can do some configuration in the 10-wacom.conf.  Most likely to configure it you'll want to use an xsetwacom script.

---

### Post by Dave M G on 2010-10-10
Favux,

Thank you for replying.

I do not seem to have the directory you are talking about:

```
$ cd /usr/lib/X11/xorg.conf.d/
bash: cd: /usr/lib/X11/xorg.conf.d/: No such file or directory
```

I do, however, a **/usr/share/X11/xorg.conf.d/50-wacom.conf** file, which contains the following:

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

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection
```

Is this what I want to edit, and if so, how do I swap over the configurations I had in order to do so?

---

### Post by Favux on 2010-10-10
Yep, that's it.  Looks like they renamed it and changed the directory.

You can add some options there.  What are the options you want?  In other words what was your configuration?

---

### Post by Dave M G on 2010-10-10
Favux,

Thank you for replying.

The options I want to move over from the old configuration are:

```
<merge key="input.x11_options.Mode" type="string">Relative</merge>
           <merge key="input.x11_options.Button2" type="string">3</merge>
           <merge key="input.x11_options.Button3" type="string">2</merge>
           <merge key="input.x11_options.Speed" type="string">1.2</merge>
```

In other words, for the default mode to be "relative", and to switch the buttons so that "left click" button is the one closest to the tip of the stylus.

What is the equivalent configurations in the new config file?

I seem to have also long ago set a speed option, but that is lower priority.

By the way, have you seen this [Wacom Control Panel]("http://www.ubuntugeek.com/wacom-control-panel-easily-configure-wacom-tablet.html")? I hope that something like this becomes the default method for configuring Wacom tablets. Right now, it doesn't seem to support either of the changes I want to make, I can only change pen pressure with it. The button and mode options are grayed out.

---

### Post by Favux on 2010-10-10
Those shouldn't be a problem.  Except speed which I believe has been dropped.  You could also do them with an xsetwacom script.  I already have some for several tablets.  Which tablet do you have?

Yes I've seen that.  I keep meaning to test it.  I think I tried an earlier version about a year ago that didn't work too well.  Unfortunately the LWP developers want one that works with the gnome settings daemon etc.

---

### Post by Dave M G on 2010-10-10
Favux,

Thank you for your continued help.

Um... sorry, I might be a bit slow, but when you say "those shouldn't be a problem", that sounds good, but I'm not really sure on what I'm supposed to be doing?

What is the syntax, and which section in the new configuration file am I supposed to put them?

If there is an online guide I should be using, please point me in the right direction.

---

### Post by Favux on 2010-10-10
Sorry, I need to know the type of tablet you have so I know what snippet to add them to.  I'm not just being nosy.  I'll guess you have a usb tablet so we'll add them to the usb snippet like so:
```
Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#    MatchProduct "Wacom|WALTOP|WACOM"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Mode" "Relative"
    Option "Button2" "3"
    Option "Button3" "2"
EndSection
```
And like I've been saying you can get finer control of your tablet by setting up a .xsetwacom.sh script specific to your tablet.

---

### Post by Dave M G on 2010-10-11
Favux,

Thanks so much for your help. It's working as hoped now.

I hope that something like the Wacom Control Panel evolves to become the standard interface for configurations.

Because I never want to look at a Wacom configuration file again for the rest of my life.

---

### Post by AdrianPtchv on 2010-10-11
Hi!

After every upgrade I have the same problem with my tablet.
After the last two upgrades the method of setting up the tablets changed too so the information I keep from the previous time, which helps me recover with the settings I want, doesn't work any more.

I have wacom bamboo pen CTF-430.
The problem after every upgrade of the OS is that buttons 2 and 3 of the pen work when the pen is not in touch with the tablet. I want them to work **only when the pen's tip touches the tablet**.

The last thing which worked for me was:

```
Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    

Option "TPCButton" "on"
```

put in /usr/lib/X11/xorg.conf.d/10-wacom.conf

This time with Ubuntu 10.10 it doesn't work again (why this guys have to change the conf files and the method altogether every upgrade - first it wast xconfig, then HAL, after this config and now other thing?).

Can you please help me make my tablet work properly again?
I want the buttons of the pen working **only when the pen is in touch with the tablet**.
Now I have to click them while keeping the pen above the tablet which is uncomfortable and makes my hand hurt.

I just can't find proper information as to how one should generate the proper config file this time and what all the commands and options mean and are.

---

### Post by Favux on 2010-10-11
Hi AdrianPtchv,

> This time with Ubuntu 10.10 it doesn't work again (why this guys have to change the conf files and the method altogether every upgrade - first it wast xconfig, then HAL, after this config and now other thing?).

Well what happened is that HAL/.fdi was a temporary thing to get usb hotplugging working while they developed udev and the xorg.conf.d xxxx.conf files for hotplugging.  Which took over a year.  But it is the "permanent" solution, so things shouldn't change too much for now on.  Changing the directory really isn't a big change.  And changing the file number from 10 to 50 just means they decided the wacom.conf should execute a little later.

Since you and Dave both asked for links:

[http://who-t.blogspot.com/2010_01_01_archive.html](http://who-t.blogspot.com/2010_01_01_archive.html)

[https://fedoraproject.org/wiki/Input_device_configuration](https://fedoraproject.org/wiki/Input_device_configuration)

[http://manpages.ubuntu.com/manpages/lucid/man5/xorg.conf.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/xorg.conf.5.html)

For you the change to the usb snippet should look like:
```
Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#    MatchProduct "Wacom|WALTOP|WACOM"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "TPCButton" "on"
EndSection
```
And to edit the 50-wacom.conf use:
```
gksudo gedit /usr/share/X11/xorg.conf.d/50-wacom.conf
```
Save, close, and reboot for it to take effect.

One note of caution.  I noticed recently they caught a bug at the LWP in which the meaning of TPCButton was reversed.  Off was on, and vice versa.  I don't know if this was for a specific tablet or all tablets or when the bug started.  As far as I could tell it was working right.  So if "on" doesn't work for you it could mean you have the bug in the default Maverick 0.10.8 xf86-input-wacom.  In which case just change "on" to "off" and you should be good to go.

---

### Post by Favux on 2010-10-11
Oops, double posted.  I don't know how.  :(

---

### Post by AdrianPtchv on 2010-10-11
Thank you!

This code works for me.

---

### Post by icodemonkey on 2010-10-11
am in the same boat but i have a "Capax USB Vista Pad" a re-branded Waltop International Corp. Slim Tablet according to lsusb.
but the moment i go to use it my entire system freezes and only returns to normal if i unplug the tablet.
any ideas on getting it to play nice?

---

### Post by Favux on 2010-10-11
Hi icodemonkey,

Sure.  Actually the Waltops are suppose to use the wacom driver too but there is a problem with the waltop usb hid kernel driver so they don't work with it yet.  Patches have been submitted to the kernel to fix it, but obviously too late for the Maverick kernel.

So folks are using the WizardPen driver as a temporary workaround.  It works fairly well.  So go to Synaptic Package manager and install the xserver-xorg-input-wizardpen package.  I'll hunt around for where I stashed the modified 70-wizardpen.conf file to get it to work.

---

### Post by icodemonkey on 2010-10-11
hey thanks for that
 ** gives Favux a virtual beer

---

### Post by Favux on 2010-10-11
Thanks for the beer!

So change the 70-wizardpen.conf to:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
#        Option  "TopX"  "775"
#        Option  "TopY"  "726"
#        Option  "BottomX"  "19237"
#        Option  "BottomY"  "11614"
#        Option  "TopZ"  "20"  # minimum pressure, default is 20
#        Option  "BottomZ"  "1023"  # maximum pressure
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
using:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/70-wizardpen.conf
```
Save, close, and reboot.

I commented out some options in the first snippet that I'm not sure apply to your Waltop tablet.

---

### Post by icodemonkey on 2010-10-11
ok well it plays nice to a degree now. what i mean by that is now the system picks up that button 1  the nib, (pen has 3 buttons i think 1. nib 2&3 on body) is constantly pressed eg in text it selects every thing if you drag it down the page and on the desk top you get the selection square

---

### Post by Favux on 2010-10-11
Not sure if we can fix that or not.  I need to see the output of:
```
xinput --list
```

---

### Post by icodemonkey on 2010-10-11
> **Favux said:**
> Not sure if we can fix that or not.  I need to see the output of:
```
xinput --list
```

done
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Digital Media Keyboard 3000    id=9    [slave  pointer  (2)]
&#9116;   &#8627; PIXART USB OPTICAL MOUSE                    id=10    [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet      id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Microsoft Microsoft® Digital Media Keyboard 3000    id=8    [slave  keyboard (3)]

```

---

### Post by Favux on 2010-10-11
OK, let's see if we can figure out what the WizardPen driver is telling the Xserver what your tablet/stylus can do.  Enter in a terminal:
```
xinput list-props "WALTOP International Corp. Slim Tablet"
```
and post the output.

---

### Post by icodemonkey on 2010-10-12
for your very much viewing pleasure 
```
Device 'WALTOP International Corp. Slim Tablet':
    Device Enabled (134):    1
    Coordinate Transformation Matrix (136):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (253):    0
    Device Accel Constant Deceleration (254):    1.000000
    Device Accel Adaptive Deceleration (255):    1.000000
    Device Accel Velocity Scaling (256):    10.000000
    Evdev Reopen Attempts (251):    10
    Evdev Axis Inversion (257):    0, 0
    Evdev Axis Calibration (258):    <no items>
    Evdev Axes Swap (259):    0
    Axis Labels (260):    "Abs X" (271), "Abs Y" (272), "Abs Pressure" (508), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
    Button Labels (261):    "Button Left" (137), "Button Middle" (138), "Button Right" (139), "Button Wheel Up" (140), "Button Wheel Down" (141), "Button Horiz Wheel Left" (142), "Button Horiz Wheel Right" (143), "Button Side" (506), "Button Extra" (507), "Button Unknown" (252), "Button Unknown" (252), "Button Unknown" (252), "Button Unknown" (252)
    Evdev Middle Button Emulation (262):    2
    Evdev Middle Button Timeout (263):    50
    Evdev Wheel Emulation (264):    0
    Evdev Wheel Emulation Axes (265):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (266):    10
    Evdev Wheel Emulation Timeout (267):    200
    Evdev Wheel Emulation Button (268):    4
    Evdev Drag Lock Buttons (269):    0


```

---

### Post by Favux on 2010-10-12
Oops.  Something is wrong.  It's saying you're on the evdev driver, not the WizardPen driver.  So either the WizardPen package wasn't installed correctly or the wizardpen.conf wasn't.  Or possibly we have a problem with the match line.

We've kind of hijacked Dave's Wacom thread.  You probably should really start a new thread in say Hardware and Laptops.  You can link to this thread and post any relevant output from here to there.

So the first thing to do is use Synaptic Package Manager to reinstall the WizardPen package.  Remember that will overwrite your modified 70-wizardpen.conf.  So you'll have to change it back and then reboot.

---

### Post by icodemonkey on 2010-10-12
continued here [http://ubuntuforums.org/showthread.php?t=1594056](http://ubuntuforums.org/showthread.php?t=1594056)

---

### Post by AdrianPtchv on 2011-10-16
> **AdrianPtchv said:**
> Hi!

After every upgrade I have the same problem with my tablet.
After the last two upgrades the method of setting up the tablets changed too so the information I keep from the previous time, which helps me recover with the settings I want, doesn't work any more.

I have wacom bamboo pen CTF-430.
The problem after every upgrade of the OS is that buttons 2 and 3 of the pen work when the pen is not in touch with the tablet. I want them to work **only when the pen's tip touches the tablet**.

The last thing which worked for me was:

```
Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    

Option "TPCButton" "on"
```

put in /usr/lib/X11/xorg.conf.d/10-wacom.conf

This time with Ubuntu 10.10 it doesn't work again (why this guys have to change the conf files and the method altogether every upgrade - first it wast xconfig, then HAL, after this config and now other thing?).

Can you please help me make my tablet work properly again?
I want the buttons of the pen working **only when the pen is in touch with the tablet**.
Now I have to click them while keeping the pen above the tablet which is uncomfortable and makes my hand hurt.

I just can't find proper information as to how one should generate the proper config file this time and what all the commands and options mean and are.


Well, here it goes again. Another upgrade and the same problem with the wacom tablet as usual.
I am already sick of it.

The problem after every upgrade of the OS is that buttons 2 and 3 of the pen work when the pen is not in touch with the tablet. I want them to work **only when the pen's tip touches the tablet**.

I tried to edit 50-wacom.conf with the setting that worked for the previous upgrade and it didn't work. As usual.

If someone has an idea, please share.

---

