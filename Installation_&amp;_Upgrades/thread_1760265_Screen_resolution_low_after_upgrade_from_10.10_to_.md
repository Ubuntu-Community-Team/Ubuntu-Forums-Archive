---
title: "Screen resolution low after upgrade from 10.10 to 11.04"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by chris.dangerfield on 2011-05-16
I have upgraded my machine from Ubuntu 10.10 to 11.04, initially it worked fine, and then I had to replace my VGA cable - now I wind up with a screen resolution that is too low.

It is possible to change the resolution with xrandr, but is there a way to set this permanently (currently it resets on startup)? Previous versions have altered the xorg.conf file and just added a new resolution setting - but I think these settings have been moved out of xorg.conf. Does anyone have any ideas how to change the screen resolution settings permanaently in 11.04?

Thanks,

Chris

---

### Post by MAFoElffen on 2011-05-16
> **chris.dangerfield said:**
> I have upgraded my machine from Ubuntu 10.10 to 11.04, initially it worked fine, and then I had to replace my VGA cable - now I wind up with a screen resolution that is too low.

It is possible to change the resolution with xrandr, but is there a way to set this permanently (currently it resets on startup)? Previous versions have altered the xorg.conf file and just added a new resolution setting - but I think these settings have been moved out of xorg.conf. Does anyone have any ideas how to change the screen resolution settings permanaently in 11.04?

Thanks,

Chris
Yes-- But >
If you change with xrandr, it only lasts for the current session.  That means when you shut down and reboot, it's gone... Unless:
You created a text file in your home directory called ~/.xprofile with those xrandr commands, such as 
```

xrandr --output LVDS --mode 1024x768 --rate 75
xrandr --output VGA1 --mode 1024x768 --rate 60

```Another way would be to create a generic xorg.conf (if it doesn't exist already).  In order to generate a generic xorg.conf you need to switch to one virtual console using the key combination <CTRL><ALT><F1>.
 Now execute the following commands:
```

sudo service gdm stop

```This command will stop the X.
 Now we need to generate the xorg.conf file:
```

sudo Xorg -configure

```This has generated the file in ~/xorg.conf.new.
 We need to make the X using it so we have to put this file inside /etc/X11/
```

sudo mv ~/xorg.conf.new /etc/X11/xorg.conf

```After moving this file to the proper location you can start the X again and see what happens:
```

sudo service gdm start

```Which would generate an xorg.conf on his PC that you could  edit without worrying about external things that were added or  different.  You could then chnage the resolutions under the Screens > Display > Modes Section:

```

Section "Monitor"     
  Identifier      "External DVI"     
  Modeline        "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync     
  Option          "PreferredMode" "1280x1024_60.00" 
EndSection 

Section "Device"     
  Identifier      "ATI Technologies, Inc. M22 [Radeon Mobility M300]"     
  Driver          "ati"     
  Option          "Monitor-DVI-0" "External DVI" 
EndSection 

Section "Screen"     
  Identifier      "Primary Screen"     
  Device          "ATI Technologies, Inc. M22 [Radeon Mobility M300]"     
  DefaultDepth    24     
SubSection "Display"         
  Depth           24         
  Modes   "1280x1024" "1024x768" "640x480"     
EndSubSection 
EndSection  

Section "ServerLayout"         
  Identifier      "Default Layout"         
  Screen          "Primary Screen" 
EndSection[FONT=Verdana]
[/FONT]
```What is easier and faster than this in 11.04 is to edit /etc/default/grub and change this line from
```

# GRUB_GFXMODE=640x480

```To uncomment that line and add your resolutions, such as this example
```

GRUB_GFXMODE=1280x1024x24;1024x768x24;640x480x24

```After you make those changes and save that file
```

sudo update-grub
sudo reboot

```Curious how just changing a cable changed this though...

Please refer to my sticky for help and reference.  Please tell me how it goes.

---

### Post by chris.dangerfield on 2011-05-18
Thanks for your ideas MAFoElffen. Here is what I found:
- Grub default: This setting seems to set the screen resolution for the Grub menu but not for the operating system as a whole
- Xorg file - I generated the xorg file with your code, it came out a bit of a mess in the screen department - there were multiple screen settings and multiple depths, but none had a "modes" section - I tried putting one in here, but it doesn't seem to be picked up on startup
- .xprofile - I changed the code already there in xprofile ("~/.xprofile") - but no change in resolution or resolution options.

I wonder if:
- I could alter the xorg file to make things work
- or, if my screen may be broken...

Thanks for your help,

Chris

---

### Post by shmk on 2011-05-20
I got the same error.
Before upgrade I got my monitor at 1920x1080 full hd.
Now I could choose only three 4:3 resolutions max @ 1024x768

---

### Post by chris.dangerfield on 2011-05-22
Not sure if this is going to help anyone else - but this problem was solved for me when I unplugged the VGA cable, switched the ends and plugged it back in - I never knew VGA cables worked one-way.

---

### Post by MAFoElffen on 2011-05-22
> **chris.dangerfield said:**
> Not sure if this is going to help anyone else - but this problem was solved for me when I unplugged the VGA cable, switched the ends and plugged it back in - I never knew VGA cables worked one-way.
They aren't supposed to be, which goes back to my first post back to you:
> **MAFoElffen said:**
> 
Curious how just changing a cable changed this though...

Which means that there is *still* a problem with this cable, but at least it works when you change it around.

Since you are the person who started this thread, if solved, please use the forum thread tools to mark this thread as "solved."

---

### Post by chris.dangerfield on 2011-05-26
Futher to this - I did find that my VGA cable was not working. I have replaced the VGA cable and it is working fine.

---

