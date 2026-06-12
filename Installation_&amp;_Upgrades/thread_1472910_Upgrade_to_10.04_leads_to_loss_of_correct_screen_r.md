---
title: "Upgrade to 10.04 leads to loss of correct screen resolution,wireless networking,sound"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by mpavey on 2010-05-04
Excited at seeing the new features in 10.04, I clicked the Upgrade button tonight. I am now really regretting it! Problems:

1. My screen resolution should be 1280x1024 but the System>Preferences>Monitors control panel only shows 1024x768.

I think I have onboard Realtek graphics. Do I need to install proprietary drivers? Everything worked fine out of the box with 9.10!

2. The sound isn't working. Again I think I have onboard Realtek sound, and again it used to work fine without any intervention from me...

3. Although on first startup wireless networking was working fine, I restarted to see if that would solve the display issue, and wireless networking stopped working too!

I have an RaLink wireless card.

When I used Grub to choose 2.6.31.20, I got some error messages at startup (e.g. mount couldn't mount /dev), but then it did eventually start up and the sound and wireless networking are working again. But the resolution is still not fixed. It is now offering 1152x864, which it didn't previously, but no 1280x1024 (my screen's native resolution).

Any help most gratefully received. If there are no straightforward solutions, I'd be quite happy to just revert to 9.10 -- is there a simple way of doing that?

Thanks.

Michael

---

### Post by quixote on 2010-05-06
That's quite an unfortunate mess of problems!  There's no simple way to downgrade as far as I know, although it's something lots of us have been saying they need to implement.  (I do remember seeing a non-simple way once.  I'll try to dig it up.)

Have you tried the automatic system for installing proprietary drivers? (System > Administration > Hardware Drivers)  Does installing any of those deal with any of the problems?

---

### Post by mpavey on 2010-05-06
Thanks quixote, really appreciate your response. 

I since gave up and have reverted to 9.10 by formatting the partition and reinstalling from CD. 

In both 9.10 and 10.04, the (System > Administration > Hardware Drivers) window just comes up blank.

FWIW I was slightly wrong about the resolution, it turns out 9.10 only manages 1152x864 too (though still better than 1024x768). So I will see if I can find a way of solving that problem in 9.10. Looking in Windows 7 (which I also have installed), it appears my graphics may in fact be Radeon. I guess I will have to open up the computer to check.... :cry:

---

### Post by dino99 on 2010-05-06
most of your issues have already been solved on this forum

---

### Post by mpavey on 2010-05-06
> **dino99 said:**
> most of your issues have already been solved on this forum

That's great news, thanks dino99. Would you mind pointing me in the right direction? I have already spent considerable time browsing this forum, as well as the Ubuntu Wiki, and not found any answers. 

For example, I tried following the [Nvidia wiki article]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"), but the terminal command you have to try yielded no result. I also tried running the Hardware Drivers dialog as suggested by quixote, but that did nothing. I also tried following some instructions to install a new package called "linux-restricted" or similar before then trying the Hardware Drivers dialog again, but still nothing. I also tried following some instructions somewhere that told me to issue various commands in the terminal aimed at forcing the OS to change resolution even though it had not detected 1280x1024 as an available resolution, but the most I was able to accomplish by doing that was to make windows disappear off the edge of the screen.

Michael

---

### Post by mpavey on 2010-05-06
I've now also tried something else but to no avail. I followed the instructions linked to from the [Radeon driver page]("https://help.ubuntu.com/community/RadeonDriver#Customized configuration for X.org, the new way") to [enable KMS]("https://wiki.ubuntu.com/X/KernelModeSetting")("KMS with a Radeon card"), since this sounded like it might allow the system to then configure itself automatically. However, I have now restarted the system and not noticed any difference.

---

### Post by mpavey on 2010-05-06
I've now also tried (on 9.10) installing [startup-manager]("https://help.ubuntu.com/community/StartUpManager"). One of the options this has is resolution, so I set it to 1280x1024. For good measure I also set the bootloader resolution to 1280x1024.

When I then restarted, the bootloader loaded up at a much higher resolution than normal, i.e. what looked like 1280x1024.

However, when the GUI loaded, I was back to 1152x864. I did see a message flash up very briefly whilst it was loading, along the lines of "VGA 775 deprecated". Could this be a clue?

---

### Post by kansasnoob on 2010-05-06
Regarding the resolution I prefer this solution:

[http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)

But that does not change the login screen, so if you want to do that also, this works:

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

In fact the latter of those two links will change both the login screen res and the main screen res but it doesn't work with auto-login.

I have done both in combo and it's fine.

**[COLOR="Red"]Just be sure to use your own "cvt" output![/COLOR]**

---

### Post by quixote on 2010-05-06
kansasnoob: that's a useful link you gave there!  ("noob"?  With 5000+ beans?  Some noob :biggrin: )

By the way, mpavey, you don't need to open the machine for that.  Use```
lspci | grep 'VGA'     *(Case sensitive!)*
``` Or, to see every last bit of hardware: sudo lshw.

---

### Post by quixote on 2010-05-06
(dup)

---

### Post by quixote on 2010-05-06
(dup) (mods: please delete these if you see them!)

---

### Post by quixote on 2010-05-06
(another duplicate)

---

### Post by mpavey on 2010-05-08
Brilliant, thanks kansasnoob. I followed the instructions in your first link, and it worked! Am very pleased, thanks so much for your help. 

This is also frustrating -- this is one of the things I tried before (following similar instructions elsewhere). I guess I must have got it slightly wrong before, possibly not substituting the VGA1 in the example for the VGA-0 that appeared on my system.

In case anyone is interested I have documented below what happened.

Finally, I think I will now leave it a few months before attempting the upgrade to 10.04 again. Hopefully by that time someone will have sorted the other issues (audio and wireless networking) and I'll be able to upgrade more smoothly :)

Michael


Command: ```
xrandr
```
Output:
```
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1360 x 1360
VGA-0 connected 1152x864+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0 +   75.0     60.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     59.9  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
  1152x864 (0x50)   81.6MHz
        h: width  1152 start 1216 end 1336 total 1520 skew    0 clock   53.7KHz
        v: height  864 start  865 end  868 total  895           clock   60.0Hz

```

Next I ran the following command:
```
cvt 1280 1024
```
And got this output:
```
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

```

Then I ran:
```
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

```
(No output.)

I tested it with the following command:
```
xrandr
```
and got this output:
```
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1360 x 1360
VGA-0 connected 1152x864+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0 +   75.0     60.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     59.9  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
  1152x864 (0x50)   81.6MHz
        h: width  1152 start 1216 end 1336 total 1520 skew    0 clock   53.7KHz
        v: height  864 start  865 end  868 total  895           clock   60.0Hz
  1280x1024_60.00 (0x9f)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz

```

I then issued this command:
```
xrandr --addmode VGA-0 1280x1024_60.00
```

and went into System > Preferences > Display. It had already selected 1280x1024 in its dropdown (oddly, since that was not the current resolution!) so I just clicked Apply and...it worked!! :D

FWIW I then tried selecting 75 Hz instead of 60 Hz but noticed that colours looked a lot more dull, and possibly blurred. So I reverted to 60 Hz.

---

