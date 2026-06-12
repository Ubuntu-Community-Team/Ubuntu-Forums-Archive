---
title: "Using Live CD and my mouse won't work"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by dustyken on 2007-02-03
I have been trying to install 6.06 for a couple of days now.  I have an official ubuntu CD and now the install works fine.  Now my only problem is that my mouse is disabled when the Live CD boots up.  I like what I see so far, but I can't do anything if my mouse runs to the top right corner and stays there.  It's a Micro Innovations mouse.  Any suggestions?

---

### Post by Rhubarb on 2007-02-03
I can't be sure because you're not specific enough about what type of Micro Innovations mouse you have.
But from just looking at their website
[http://www.microinv.com/Display.aspx?category=Input%20Devices](http://www.microinv.com/Display.aspx?category=Input%20Devices)
It seems that most of the mice there are 800dpi 3000Hz.
While I can accept many reasons for the need of a higher resolution mouse, I don't see the point in having an overkill refresh rate.

I'm currently using a Logitech G5 Laser mouse here, 2000dpi @ 100Hz --> works fine on Dapper and Edgy.

Most optical mice would be around 800dpi @ 50Hz.
My guess is that Ubuntu doesn't like 60 times the normal refresh rate a mouse normally has.
If you can, plug in a different mouse to check if all is running well.
There may be some configuration files you might be able to change to let Ubuntu recognise your insane 3kHz mouse refresh rate.  - I'll try to find it and will post back here for you.

---

### Post by Rhubarb on 2007-02-03
If you do have a 3000Hz mouse (3000Hz = 3000fps), then you could try editing your xorg.conf as follows:

Open up the terminal
```
cd /etc/X11/
sudo cp xorg.conf xorg.conf.backup
sudo nano xorg.conf
```

Use the cursor keys to scroll down to something that looks a bit like this:
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection
```

And insert the following Option:
```
    Option         "SampleRate" "3000"
```

So it all should look something like this:
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "SampleRate" "3000"
EndSection
```

Press "ctrl o" and enter to save, then press "ctrl x" to exit the nano editor.

Now to restart your graphical environment to see if your mouse works:
Press "ctrl alt backspace" all at the same time, your desktop should reload and hopefully your mouse will work.

If it doesn't work, perhaps email the manufacturer asking for some help getting your mouse to work with linux.
There's a also a chance the more recent Ubuntu 6.10 "Edgy Eft" will detect your mouse properly.  If you can download it and give it a try.

Hope this is of help.

---

