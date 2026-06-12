---
title: "Is it possible to change monitor specific resolution"
date: 2019-03-04
forum: Installation &amp; Upgrades
---

### Post by MibunoOokami on 2019-03-04
Forgive the title, that's the best way I could think to word it. I picked up an old used desktop PC to do a quick project on and then give it to my son. After installing a fresh minimal Ubuntu-MATE (first time trying this) os, I have found the resolution is stuck at 600x480 (from memory) and it's hideous. The monitor has a built in menu panel and according to the settings the monitor is only 600x480. The thing is, during the installation process, the resolution looked quite good and normal, only after install finished and reboot did it become hideous.

So as per the title, is it possible to change the resolution on the described monitor using Ubuntu-MATE, and if so, how do I go about that? If not, is there a different lightweight Linux distro that would work on said monitor?

Thanks in advance

ETA: Posted this before going to bed, forgot to mention there are no additional drivers available for the display. It's a 12 year old Aspire M1610 desktop if that helps.

---

### Post by DuckHook on 2019-03-04
If the monitor itself states that 600 x 480 is its max resolution, then I don't see how this can be changed. What resolution did it appear to have during install?

You could also try the old xrandr basket of tricks:
What results do you get with:```
xrandr
```
What are results of:```
sudo get-edid | parse-edid
```…you may have to install *read-edid* first.

---

### Post by CatKiller on 2019-03-04
You haven't said what monitor you're using, which is pretty critical to knowing what resolution it should be running at. You'll also need to say how it's connected, and what GPU it's connected to.

---

### Post by MibunoOokami on 2019-03-04
> **DuckHook said:**
> If the monitor itself states that 600 x 480 is its max resolution, then I don't see how this can be changed. What resolution did it appear to have during install?

You could also try the old xrandr basket of tricks:
What results do you get with:```
xrandr
```
What are results of:```
sudo get-edid | parse-edid
```&#8230;you may have to install *read-edid* first.

I don't know the specific resolution, just that the preview of how things look in the OS looked like an appropriate size. This 600x480 resolution just makes everything giant and really hard on the eyes. If I had a wireless keyboard and mouse, I could probably go to the next room and still be able to see everything on the monitor. (slight exaggeration). See below for requested terminal outputs.

```
mate@Mate:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480       73.00* 

```

```
mate@Mate:~$ sudo get-edid | parse-edid
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
Looks like no busses have an EDID. Sorry!
Attempting to use the classical VBE interface

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0xc19bf "SiS"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful

    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination supports DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call successful

Checksum Correct

Section "Monitor"
    Identifier "AL1916W"
    ModelName "AL1916W"
    VendorName "ACR"
    # Monitor Manufactured week 16 of 2007
    # EDID version 1.3
    # Analog Display
    DisplaySize 410 260
    Gamma 2.20
    Option "DPMS" "true"
    Horizsync 31-84
    VertRefresh 56-76
    # Maximum pixel clock is 140MHz
    #Not giving standard mode: 1400x1050, 75Hz
    #Not giving standard mode: 1440x900, 75Hz
    #Not giving standard mode: 1280x1024, 60Hz
    #Not giving standard mode: 1280x960, 60Hz
    #Not giving standard mode: 1280x800, 75Hz
    #Not giving standard mode: 1280x800, 60Hz
    #Not giving standard mode: 1152x921, 76Hz
    #Not giving standard mode: 1152x864, 75Hz
    Modeline     "Mode 0" 89.00 1440 1488 1520 1600 900 903 909 926 +hsync +vsync 
EndSection
Looks like VBE was successful. Have a good day.

```

I haven't a clue what any of that means.

ETA: When first trying the machine out to make sure it works, it was running Windoze Vista and again the resolution looked appropriately sized. That OS is long since gone and I never bothered looking at the resolution settings...

---

### Post by MibunoOokami on 2019-03-04
> **CatKiller said:**
> You haven't said what monitor you're using, which is pretty critical to knowing what resolution it should be running at. You'll also need to say how it's connected, and what GPU it's connected to.

My mistake. It's an Acer AL1916W monitor, connected via VGA, I can't answer the last question as I have no idea.

Oh and under "displays" it says unknown default for the monitor.

---

### Post by DuckHook on 2019-03-04
According to EDID, you should be able to take your resolution up to 1440 x 900.

Instructions are in the following wiki page: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

EDIT,

&#8230;and, according to [your monitor specs]("https://www.cnet.com/products/acer-al1916w-lcd-monitor-19/"), the resolution is, indeed, 1440 x 900.

---

### Post by MibunoOokami on 2019-03-04
> **DuckHook said:**
> According to EDID, you should be able to take your resolution up to 1440 x 900.

Instructions are in the following wiki page: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

EDIT,

…and, according to [your monitor specs]("https://www.cnet.com/products/acer-al1916w-lcd-monitor-19/"), the resolution is, indeed, 1440 x 900.

That's strange, I wonder why it thinks the max is 600x480?

The following outputs are what I have received when trying to follow the instructions in the wiki page you linked.

```
mate@Mate:~$ xrandr --output VGA1 --mode 1024x768
xrandr: Failed to get size of gamma for output default
warning: output VGA1 not found; ignoring
```

```
mate@Mate:~$ xrandr --output LVDS --mode 1024x768
xrandr: Failed to get size of gamma for output default
warning: output LVDS not found; ignoring
```

```
mate@Mate:~$ rm ~/.config/monitors.xml
rm: cannot remove '/home/mate/.config/monitors.xml': No such file or directory
```

I also followed the method of creating ~/.xprofile but got some error message after logging out and back in again. I couldn't screenshot it and when I tried copying it, that "worked" but I couldn't paste it. It effectively told me to get rid of ~/.xprofile or display may not function as desired.

ETA: xrandr -q gave this response which is different from what wiki says I should get. ```
mate@Mate:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480       73.00*
```

---

### Post by CatKiller on 2019-03-05
> **MibunoOokami said:**
> That's strange, I wonder why it thinks the max is 600x480? 

Because the BIOS is at 640×480, and nothing else sets it higher. 

> The following outputs are what I have received when trying to follow the instructions in the wiki page you linked. 

Don't just blindly paste random commands that you found somewhere on the Internet, that you don't understand, and haven't even read. Seriously.

The GPU you're using has never been supported by its manufacturer; what support there is comes from volunteers reverse engineering it.

You're using output names that are specific to other graphics cards rather than the output name yours is using, and requesting a mode that is completely different than the one you actually want. You should try not doing those things.

---

### Post by MibunoOokami on 2019-03-05
> **CatKiller said:**
> Because the BIOS is at 640×480, and nothing else sets it higher. 

 

Don't just blindly paste random commands that you found somewhere on the Internet, that you don't understand, and haven't even read. Seriously.

The GPU you're using has never been supported by its manufacturer; what support there is comes from volunteers reverse engineering it.

You're using output names that are specific to other graphics cards rather than the output name yours is using, and requesting a mode that is completely different than the one you actually want. You should try not doing those things.

That raises more questions. BIOS would be unchangeable right? Because I was in the BIOS (menu) yesterday and didn't see any options regarding resolution. Did ```
sudo get-edid | parse-edid
``` produce a false positive regarding different resolutions? And why would the resolution have appeared fine in windoze and during the install process, only to change after install?

---

### Post by CatKiller on 2019-03-05
> **MibunoOokami said:**
> BIOS would be unchangeable right?

BIOS displays at 640×480. Some UEFIs try for 1024×768. The software is 16 MB in total; custom modesetting is not on the menu.

>  Because I was in the BIOS (menu) yesterday and didn't see any options regarding resolution. 

Of course not. The BIOS has a fixed resolution.

After the BIOS has set the resolution, the bootloader can sometimes set a different resolution for the boot process (and the text mode TTYs). Then when X is initialised it can set a resolution for the login screen. Then, when you log in, you can set your own resolution there.

At the moment, only the first step is happening.

> Did ```
sudo get-edid | parse-edid
``` produce a false positive regarding different resolutions? 

No. [EDID](https://en.wikipedia.org/wiki/Extended_Display_Identification_Data) is how your monitor advertises which resolutions it can handle. Your SIS GPU simply ignores that because it's an unsupported POS.

> And why would the resolution have appeared fine in windoze and during the install process, only to change after install?

Windows monitor "drivers" are simply a text file that contains the timing specifications of the monitor, exactly of the sort that one might put in their xorg.conf to enable the higher resolutions.

The install process runs at 1024×768 (if it doesn't know that higher is safe) because it's widely supported and 640×480 is horrible. When booting from your computer, the screen will stay at 640×480 (set by the BIOS) until something changes it. You aren't changing it.

1024×768 is not your monitor's resolution either. That is 1440×900.

---

### Post by DuckHook on 2019-03-05
Post output of:```
xrandr --listmonitors
```
You need to know what the output port of *your* GPU is called. Can't just assume that it's VGA1 or LVDS. You must use *your* port name.

CatKiller is also correct in instructing you to define a resolution of 1440 x 900. This is your monitor's native resolution. There is no point in using a non-native resolution like 1024 x 768.

The modeline for this resolution was given in your EDID output:```
Modeline     "Mode 0" 89.00 1440 1488 1520 1600 900 903 909 926 +hsync +vsync
```
You can alternately generate a modeline with:```
cvt 1440 900 60
```Either should work.

The xrandr man page is admittedly somewhat dense and obscure, but it provides an example you should read:```
…Forces to use a 1024x768 mode on an output called VGA:
              xrandr --newmode "1024x768" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
              xrandr --addmode VGA 1024x768
              xrandr --output VGA --mode 1024x768
```…note that this example is based on a 1024 x 768 resolution, which is ***not*** what you should be using. It's only an example. Use your proper resolution and modeline instead.

---

### Post by MibunoOokami on 2019-03-05
Yep, guilty of not paying closer attention to the commands I was inputting into terminal when it came to resolution...

Output below.

```
mate@Mate:~$ xrandr --listmonitors
xrandr: Failed to get size of gamma for output default
Monitors: 1
 0: +default 640/169x480/127+0+0  default
```

---

### Post by MibunoOokami on 2019-03-07
Ok I have learned this problem must relate to later versions of Linux distros.

I decided to ditch Ubuntu Mate 18.04 and install Ubuntu 7.10 because I still had a copy of that. The resolution was acceptable, however, the OS wouldn't recognize my USB wifi adapter so I was unable to install read-edid and post the output of that or anything else. Xrandr gave what appeared to be a good output without the gamma error, but no connection to the internet means no output at this time.

Next I tried Linux Lite, but after installation was complete, I had the same resolution problem.

The last OS I tried to try was LXLE 16.04, but I must have downloaded a bad copy as it was the longest attempted install of Linux ever of one and s half hours, after which point it gave an error message that said ithe install had crashed. I will try this again tomorrow. 

The point I was trying to make is Mate 18.04, and LXLE 16.04 produced the same resolution problem whereas Ubuntu 7.10 didn't. So...

---

### Post by DuckHook on 2019-03-07
You have been given the instructions needed to try setting up xrandr on current maintained OSes. Due to the age and weakness of your HW, stick to the lighter flavours: Mate, Budgie, Xubuntu, Lubuntu.

[LIST=1]
[*]CatKiller has already alluded to the fact that your GPU is primitive and unsupported&#8212;translation: you won't be able to get it to work without a lot of tweaking and experimentation&#8212;if this troubles you, then the solution is to get a better GPU, not resurrect an undead OS even for comparison.
[*]You have already been given the modeline:> **DuckHook said:**
> ```
Modeline     "Mode 0" 89.00 1440 1488 1520 1600 900 903 909 926 +hsync +vsync
```
[*]If that doesn't work, you have already been informed how to generate another:> **DuckHook said:**
> You can alternately generate a modeline with:```
cvt 1440 900 60
```
[*]You have already been given the template to follow:> **DuckHook said:**
> &#8230;an example you should read:```
&#8230;Forces to use a 1024x768 mode on an output called VGA:
              xrandr --newmode "1024x768" 63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
              xrandr --addmode VGA 1024x768
              xrandr --output VGA --mode 1024x768
```&#8230;note that this example is based on a 1024 x 768 resolution, which is ***not*** what you should be using. It's only an example. Use your proper resolution and modeline instead.
[*]You have already been given the instructions to make any transient fix permanent:> **DuckHook said:**
> Instructions are in the following wiki page: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
[*]NOTE: your output label is one I have not seen before&#8212;unsurprising given the obscurity of your GPU. It is not VGA or LSVD, but "default":> **MibunoOokami said:**
> ```
mate@Mate:~$ xrandr --listmonitors
xrandr: Failed to get size of gamma for output default
Monitors: 1
 0: +default 640/169x480/127+0+0  default
```&#8230;you may have to try this in lieu of the usual output labels through trial & error.
[*]Purely as a GUI aid, if the CLI is too overwhelming (which is understandable) try *arandr*:```
sudo apt install arandr
```
[*]Testing on 7.10 is not informative. It has long since been buried in the scrapheap of ancient history. I for one do not remember a thing about it: what drivers it used, what video subsystem, what kernel&#8212;you would not be able to reproduce any of it on a current OS anyway.
[/LIST]
Executing on all of the above does not guarantee success. The fact is that your GPU is so obscure and bronze age that you are in hobbyist territory. See the link in my sig: ***Resurrecting Old Hardware***. Linux can often be persuaded to work with even the most recalcitrant HW but it requires knowledge, patience and the willingness to invest a level of time, research and trial & error that most users are just unwilling to commit. If you are unwilling, then it is much easier to just purchase a cheap old (but supported!) video card on ebay to replace the one you have.

---

### Post by MibunoOokami on 2019-03-07
Hi Duckhook, 

I did try those steps regarding the modeline, and each time it produced the same error message regarding size of gamma. I'll give arandr a go, and have a read of the resurrecting old hardware thread in your signature.

---

### Post by DuckHook on 2019-03-07
> **MibunoOokami said:**
> …I did try those steps regarding the modeline, and each time it produced the same error message regarding size of gamma. I'll give arandr a go, and have a read of the resurrecting old hardware thread in your signature.
…hmmm…

To recap: you tried:
```
xrandr --newmode "1440x900" 89.00 1440 1488 1520 1600 900 903 909 926 +hsync +vsync
xrandr --addmode VGA 1440x900
xrandr --output VGA --mode 1440x900
```
If that doesn't work, then try:
```
xrandr --newmode "1440x900" 89.00 1440 1488 1520 1600 900 903 909 926 +hsync +vsync
xrandr --addmode default 1440x900
xrandr --output default --mode 1440x900
```Note the change from "VGA" to "default". Case is important in Linux, so be careful to type accurately.

If that doesn't work, then generate a new modeline with *cvt* and substitute that modeline for the one above.

---

### Post by CatKiller on 2019-03-07
I've not seen any reason to consider that the message about the gamma is at all significant.

An alternative to using xrandr to create the mode is to put
```

        HorizSync 31-84
        VertRefresh 56-76

```
in the Monitor section of a skeletal xorg.conf. Those are the frequency ranges that your monitor says that it can do. That information would normally be used to automatically set the resolution, but your GPU is throwing it away instead. You can help things along by specifying that information manually.

Happily, a skeletal xorg.conf has already been provided on the wiki page that DuckHook kindly linked to. It would look something like this:

```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

---

### Post by MibunoOokami on 2019-03-07
> **DuckHook said:**
> …hmmm…

To recap: you tried:
```
xrandr --newmode "1440x900" 89.00 1440 1488 1520 1600 900 903 909 926 +hsync +vsync
xrandr --addmode VGA 1440x900
xrandr --output VGA --mode 1440x900
```
If that doesn't work, then try:
```
xrandr --newmode "1440x900" 89.00 1440 1488 1520 1600 900 903 909 926 +hsync +vsync
xrandr --addmode default 1440x900
xrandr --output default --mode 1440x900
```Note the change from "VGA" to "default". Case is important in Linux, so be careful to type accurately.

If that doesn't work, then generate a new modeline with *cvt* and substitute that modeline for the one above.

Yes, I can't get past the xrandr --newmode commands as they have all produced the size of gamma error. I can generate the new modeline, but when trying to use it, again, the size of gamma error comes up. 

I have since installed arandr, that doesn't offer additional resolutions and terminal displayed an error message that included xrandr size of gamma blah blah. I apologise, I forgot to copy the exact message.

About 20 minutes ago I decided to open the machine and have a look at what type of video/graphics card is being used so I know what to look for when upgrading it, however, the graphics must be built in as there is no card. The VGA port is soldered directly to the motherboard. Since I've got it opened I'll give it a good clean. I'm also in the process of looking for a card that is compatible with the machine and hopefully with Mate so that I can get a better resolution. To be honest, I just don't know that I have the time to troubleshoot from Morgaes' thread of giving old hardware new life, and typically if one doesn't have enough time, they try rushing and/or become impatient and... That said, if I can't find a graphics card, or one that's not more expensive than the actual machine, I will definitely very slowly, but surely work through that thread when I have a bit of free time here and there.

---

### Post by MibunoOokami on 2019-03-09
A new (used) graphics card has solved this problem, took a while too. See why [here]("https://ubuntuforums.org/showthread.php?t=2414335").

Thanks for the advice and help DuckHook and CatKiller

---

