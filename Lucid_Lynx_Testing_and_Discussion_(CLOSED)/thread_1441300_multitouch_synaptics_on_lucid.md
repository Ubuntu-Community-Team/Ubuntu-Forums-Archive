---
title: "multitouch synaptics on lucid"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by biasquez on 2010-03-28
hi, i have synaptics touchpad that support multitouch (for example two finger scrolling). i followed this guide: [http://my.opera.com/mazwarbz/blog/pinch-zooming-gestures-for-synaptics-touchpad-ubuntu](http://my.opera.com/mazwarbz/blog/pinch-zooming-gestures-for-synaptics-touchpad-ubuntu). shmconfig is enabled in .fdi but when i run synclient -m 100 i have this error:
Can't access shared memory area. SHMConfig disabled?

Moreover, i can't restart hal service because /etc/init.d/hal doesn't exist... so, how can i enable shmconfig and use multitouch synpaptics?

---

### Post by Astrolabe-fr on 2010-04-06
Hi,

Same for me : I have an asus eeepc, on lucid lynx... And I wanted to use my synaptics touchpad's multitouch capabilities... But unsuccessfully..  I get the same errors as my upper-neighbor.:(

Does somebody has the answer ? Or other tools to get multitouch working on Ubuntu Lucid Lynx ?

Thanks a lot in advance.

---

### Post by maheshasolkar on 2010-04-06
Other way to turn on SHMConfig I have tried in the past (really long back - around Edgy Eft), is this part in the /etc/X11/xorg.conf.


```
Section "InputDevice"
  Identifier "Synaptics Touchpad"
  Driver "synaptics"
  Option "SHMConfig" "on"
EndSection 
```

Not sure if it will work, but it is worth a try.

If /etc/X11/xorg.conf does not exist, I believe you can just create one and add these lines to it. Someone please correct me if this is not the case.

---

### Post by myddewji13 on 2010-04-06
HAL has been taken out of Lucid. I'm not really sure if this will help but try this: 

[http://ubuntuforums.org/showthread.php?t=1435663](http://ubuntuforums.org/showthread.php?t=1435663)

---

### Post by Mr. Picklesworth on 2010-04-06
What you need is a command line tool called xinput. It'll seem strange at first, but the idea is this tool lets you configure all your input devices at runtime.

Here are some commands to get you going:
```

xinput --help
xinput list #note id of your touchpad; I'll refer to it as $ID
xinput list-props $ID
xinput set-int-prop $ID 121 8 0 #disables touchpad (sets property 121, or Device Enabled, to 0)
xinput set-int-prop $ID 121 8 1 #enables touchpad

```

Just come up with the commands you want to run and stick it in a script that runs when you log in.

Otherwise, have you checked System › Preferences › Mouse › Touchpad ? It lets you enable two fingered scrolling, at least. The multi-fingered tapping defaults to 2 fingers for right click, 3 for middle click. (Unless I've messed with it and forgotten).

---

### Post by Astrolabe-fr on 2010-04-08
Thank you so much for your help guys, it worked for the 2 fingers scroll ! (Do you know how to get other multitouch features ?)

I'll put tomorrow the script I did use so it can be useful for others...

Btw, I tried to make this script run automatically on startup... So I put the script into /etc/init.d, and tried to run an "sudo update-rc.d my_script defaults", it does all it needs, but returns a "Missing LSB information" and the script doesn't start with the system anyway... :(

Does someone has an idea ?  :confused:

---

### Post by Niels den Otter on 2010-04-08
You might better add the script to the startup actions when logging in (System-Preferences-Startup Applications) for settings you can't change through the GUI.

I couldn't find a setting for Palm Detection and added that in a script doing;

  otter@sambal:~$ cat ~/bin/touchpad.sh 
  xinput set-prop 10 "Synaptics Palm Detection" 1

(check post above to find the ID. mine is 10)

---

### Post by Mr. Picklesworth on 2010-04-08
Niels den Otter has it right: when I said startup script, I just meant within your session. Make a script, make it executable, add #!/bin/sh at the top, and add a launcher within Startup Applications Preferences :)

I was reminded that the numerical IDs for your input devices could change, which makes that (identifying devices with numbers) a handy shortcut if you're briefly tinkering but not ideal for a script that you're going to use for a while. So, a more reliable command would be something like

xinput list-props "SynPS/2 Synaptics TouchPad"

Where, instead of the ID number, I use the name of the device as in *xinput list*, held together by quotation marks.

---

### Post by azwar on 2010-04-09
> **biasquez said:**
> hi, i have synaptics touchpad that support multitouch (for example two finger scrolling). i followed this guide: [http://my.opera.com/mazwarbz/blog/pinch-zooming-gestures-for-synaptics-touchpad-ubuntu](http://my.opera.com/mazwarbz/blog/pinch-zooming-gestures-for-synaptics-touchpad-ubuntu). shmconfig is enabled in .fdi but when i run synclient -m 100 i have this error:
Can't access shared memory area. SHMConfig disabled?

Moreover, i can't restart hal service because /etc/init.d/hal doesn't exist... so, how can i enable shmconfig and use multitouch synpaptics?

Hi,

The blog you are referred to is my blog. Anyway, the tutorial is not applicable to karmic due to HAL depreciation. I'm also facing the same problem. The synclient cannot detect more than 1 finger while in windows vista/7 it work flawlessly.

As far as I tested, only this tutorial [http://blog.mfabrik.com/2009/10/11/setting-up-multi-touch-scrolling-for-ubuntu-9-10-karmic-koala-linux-on-asus-eee-1005ha-netbook/](http://blog.mfabrik.com/2009/10/11/setting-up-multi-touch-scrolling-for-ubuntu-9-10-karmic-koala-linux-on-asus-eee-1005ha-netbook/) can make my touchpad work with 2 finger scrolling (excluding pinch zooming).

---

### Post by azwar on 2010-04-09
To enable shmconfig.

run this command
```
gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi
```

Then paste and save this file, then reboot.
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">on</merge>
    </match>
  </device>
</deviceinfo>
```

---

### Post by azwar on 2010-04-09
Oppps... sory. 

I overlook the topic... its on Lucid actually not karmic.

Lucid will make a full removal of HAL from the boot process. I'm not sure about it exactly. Please ignore my post above. 

thanks.

---

### Post by Astrolabe-fr on 2010-04-09
Hi guys,

I did try to set my script on startup (Startup applications), but it doesn't work.
On system startup, my script hasn't been run as 2 fingers scroll doens'twork.

And I know my script works, for I can launch it in a terminal when asked.

Does someone has a solution ?

---

### Post by paulinchen on 2010-04-10
Which gestures I can enable with this script. Only two finger one? Cause with this driver

[http://randomtruth.110mb.com/blog/index.php/2009/03/30/v10-of-linux-multi-touch-released/comments/#comment100213-185710](http://randomtruth.110mb.com/blog/index.php/2009/03/30/v10-of-linux-multi-touch-released/comments/#comment100213-185710)

You can also enable three and four finger gestures.
Would be really nice to know if this will work in Lucid as well...

---

### Post by Astrolabe-fr on 2010-04-12
Paulinchen, I don't know if this driver will work with Karmic, but with 10.4 lucid it doesn't : SHMConfig doesn't exist anymore, so it is impossible to disable it. In result, the driver keeps saying it can't access the shared memory...

If someone knows this kind of driver that uses xinput instead, it would be great.

By the way, I can't succeed into setting my 2fingers_scroll script launching on startup... It simply doesn't launch on startup. 
Does anyone has any idea ?  (Please please please...)

---

### Post by Taoye on 2010-04-12
All you need is to have the right configuration in xorg.conf. Here's the synaptics section from mine... my system is a MacBook Pro 13" (5,5)...

I found that without the "alwayscore" and "corepointer" options set, the system wasn't using my configuration. With this config my touchpad works with tapping, scrolling, dragging, etc. The "synclient -m 100" command works for me also... no more SHMConfig errors. To get more multitouch gestures (3-finger swipe) I'm using a perl script in the background that interprets synclient output... 

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Synaptics Touchpad"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "auto-dev"
    Option         "AlwaysCore" "true"
    Option         "CorePointer"
    Option         "SHMConfig" "true"
#speed
    Option         "MinSpeed" "0.80"
    Option         "MaxSpeed" "1"
    Option         "AccelFactor" "0.0015"
#tapping
    Option         "FingerHigh" "60"
    Option         "FingerLow" "20"
    Option         "MaxTapTime" "150"
    Option         "FastTaps" "0"
    Option         "TapButton2" "3"
    Option         "TapButton3" "2"
#disable edge scroll
    Option         "VertEdgeScroll" "0"
    Option         "HorizEdgeScroll" "0"
#other options
    Option         "VertTwoFingerScroll" "1"
    Option         "HorizTwoFingerScroll" "1"
    Option         "PalmDetect" "1"
    Option         "LockedDrags" "1"
    Option         "LockedDragTimeout" "750"
EndSection
```

---

### Post by Mr. Picklesworth on 2010-04-12
> **Astrolabe-fr said:**
> By the way, I can't succeed into setting my 2fingers_scroll script launching on startup... It simply doesn't launch on startup. 
Does anyone has any idea ?  (Please please please...)

Make sure it's executable. Right click the file, go to Properties›Permissions.
Also, at the top of the script you need #!/bin/sh, so double check that's there.

---

### Post by Astrolabe-fr on 2010-04-13
Thanks Taoye for the xorg.conf advice, I'll test that later in the day (it's 12:04 in Paris ;))

@Mr. Picklesworth : Yes, I can confirm I did set the script on mod 777; and ticked execution permission thought graphical interface to be sure. Also, #!/bin/sh/ is at the beginning of my script. 
...And it doesn't work anyway :(

---

### Post by jochem on 2010-04-13
I'm using this script below, it's named touchpad.sh, located in my home folder. Also note the delay.

I added it to Startup Applications, under preferences.
I hit "Add", and under command: 
```
/home/jochem/touchpad.sh
```
Note, I didn't add "sh". I'm not sure if this matters though.

```
#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
# list  current synaptics device properties: xinput list-props '"SynPS/2 Synaptics TouchPad"'
#
sleep 5 #added delay...
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 1
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 4
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 9         # 	Below width 1 finger touch, above width simulate 2 finger touch. - value=pad-pixels
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 1 1 0       # 	vertical, horizontal, corner - values: 0=disable  1=enable
xinput --set-prop --type=int --format=32 "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 250 # 	stabilize 2 finger actions - value=pad-pixels
#xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Tap Action" 0 0 0 0 1 2 3   # pad corners rt rb lt lb tap fingers 1 2 3 (can't simulate more then 2 tap fingers AFAIK) - values: 0=disable 1=left 2=middle 3=right etc. (in FF 8=back 9=forward)
xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 1 0   # 	vertical scrolling, horizontal scrolling - values: 0=disable 1=enable
#xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Circular Scrolling" 1
#xinput --set-prop --type=int --format=8  "SynPS/2 Synaptics TouchPad" "Synaptics Circular Scrolling Trigger" 3

exit
```

---

### Post by Astrolabe-fr on 2010-04-13
Thank you soooo much Jochem, adding the delay made it work just fine ! 
How did you know you had to let time for the system for 5 seconds before launching the script ?

---

### Post by Astrolabe-fr on 2010-04-13
[EDIT] :

Taoye, where do you find the xorg.conf file to modify ? I can't find it.

---

### Post by Taoye on 2010-04-13
It's usually at /etc/X11/xorg.conf

---

### Post by Astrolabe-fr on 2010-04-13
In lucid, xorg.conf doesn't appear in /etc/X11/, so I had to do this [http://ubuntuforums.org/showthread.php?t=1428788](http://ubuntuforums.org/showthread.php?t=1428788).

I did modify my xorg.conf mouse section to put it the same way as yours, and as a result, synclient worked.
But it slows down the cursor and puts it quite not enough sensitive. And more, I don't know what to do with synclient -m 100 working, but no gesture works : no 2 fingers scroll, no horizontal scroll, etc.  :(

---

### Post by paulinchen on 2010-04-15
> **Taoye said:**
> All you need is to have the right configuration in xorg.conf. Here's the synaptics section from mine... my system is a MacBook Pro 13" (5,5)...

I found that without the "alwayscore" and "corepointer" options set, the system wasn't using my configuration. With this config my touchpad works with tapping, scrolling, dragging, etc. The "synclient -m 100" command works for me also... no more SHMConfig errors. To get more multitouch gestures (3-finger swipe) I'm using a perl script in the background that interprets synclient output... 


That means with the perl cript you can get all of the multitouch gestures?
Please can you add your script here. Thank you

By the way the Multitouch driver I posted earlier works in Karmic...

---

### Post by berilac on 2010-04-16
I'm running Lucid (Beta2 i think) 2.6.32-19-generic
On Sony VAIO VPCEB1M1E...

Edge-scrolling, two-finger, etc - do not work.
In mouse options, two-finger scrolling option is actually faded out...

I obviously have same issues regarding synclient not working (to do with HAL not existing, if i understand correctly).


Regarding the potential xorg edits, I thought the standard conf file was no longer existent since Karmic?

What might my options be? (Any questions about my setup, please ask)
Thanks guys,


Michael

---

