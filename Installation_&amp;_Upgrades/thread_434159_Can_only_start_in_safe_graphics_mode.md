---
title: "Can only start in safe graphics mode"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by Kivamaki on 2007-05-05
I'm using the Feisty live CD. SO it's not installed yet. So when I click "Start ubuntu or install it" it will load, and after the loading I'll get a black page with my monitor saying "Out of Range". I can hear the audio in the background, but can't see anything. If I try to use CNTRL ALT F1 to use the shell, it just comes up with a bunch of messed up lines everywhere.

If I choose "Start ubuntu in safe graphic mode" I can start perfectly, but none of the changes I make in the xorg.conf save when I reboot.

So how can I fix this problem?

---

### Post by Blackforge on 2007-05-05
Did you try specifying a resolution on LiveCD bootup using F4?  Thats what I have to do.

---

### Post by Kivamaki on 2007-05-05
I've tried that, but the screen comes out extremely distorted and messed up.

---

### Post by Blackforge on 2007-05-05
> **Kivamaki said:**
> I've tried that, but the screen comes out extremely distorted and messed up.

During the distorted screen can you see Ubuntu loaded/loading?  If so you can now switch to a shell using Ctrl-Alt-F1 and edit the xorg.conf.  Then from that point you can switch back to X Windows (Ctrl-Alt-F7) and use Ctrl-Alt-Backspace to restart X.  It should load your X changes.  If you get any gnome/nautilus errors when it attempts to restart switch back to a shell and run this:



```

sudo pgrep gnome | xargs kill -9

```

Then go back and restart X (Ctrl-Alt-Backspace)

---

### Post by Kivamaki on 2007-05-05
When I try to edit the xorg.conf with (Control Alt F1) and I type this in:

```
gedit /etc/X11/xorg.conf
```

I get this message:

```
Cannot open display
```

---

### Post by Blackforge on 2007-05-05
> **Kivamaki said:**
> When I try to edit the xorg.conf with (Control Alt F1) and I type this in:

```
gedit /etc/X11/xorg.conf
```

I get this message:

```
Cannot open display
```

You can't use gedit (Gnome Edit) from the shell you need to use vi or nano.

Try this instead:

```
sudo nano /etc/X11/xorg.conf
```

Ctrl-O to save your changes and Ctrl-X to exit.

---

### Post by Kivamaki on 2007-05-05
I changed all the resolutions to this "1280x1024_60"  Then I save it, and exit. Then I type "sudo reboot" to reboot ubuntu. When it reboots, it will go to a loading screen and eject my CD and say "Remove the CD from the tray (if any) and push back in the tray and press ENTER". 

I do that, and then it just does nothing, it freezes or something. So I have to manually power off my computer and the changes reset.

---

### Post by Blackforge on 2007-05-06
> **Kivamaki said:**
> I changed all the resolutions to this "1280x1024_60"  Then I save it, and exit. Then I type "sudo reboot" to reboot ubuntu. When it reboots, it will go to a loading screen and eject my CD and say "Remove the CD from the tray (if any) and push back in the tray and press ENTER". 

I do that, and then it just does nothing, it freezes or something. So I have to manually power off my computer and the changes reset.

This is a LiveCD.  Everything gets loaded in RAM and nothing is permanently saved to disk until you do an Install and run it from the HD.

Once you made your xorg.conf changes and saved them switch back to X-Windows and force a restart of it.

Switch back using Ctrl-Alt-F7 and then press Ctrl-Alt-Backspace.  This will restart X with your xorg.conf.

---

### Post by Kivamaki on 2007-05-06
Ok, that kind of worked. After I went back to the main screen with ctrl alt f7 I hit "Cntrl Alt Backspace" and it reloaded. Now the screen was a bit messed up but I could deffinitly see. It didn't change the resolution to "1280x1024", it changed it to "1280x800", and so it cut off the screen when going up and down, but on that part it repeated my desktop. So on the top of my screen, was being repeated on the bottom of the screen. Plus I couldn't see my mouse.

So I went back and checked my xorg.conf, and it's still "1280x1024_60" yet my screen res is 1280x800. Then I tried to restart, so I click System>Quit and quit, then it started to shut down, ejected my CD and said "Take out CD and press ENTER", and of course it froze up/did nothing.

Thanks for all your help so far.

---

### Post by Kivamaki on 2007-05-06
Bump, was 4 pages behind.

---

### Post by Blackforge on 2007-05-06
> **Kivamaki said:**
> Ok, that kind of worked. After I went back to the main screen with ctrl alt f7 I hit "Cntrl Alt Backspace" and it reloaded. Now the screen was a bit messed up but I could deffinitly see. It didn't change the resolution to "1280x1024", it changed it to "1280x800", and so it cut off the screen when going up and down, but on that part it repeated my desktop. So on the top of my screen, was being repeated on the bottom of the screen. Plus I couldn't see my mouse.

So I went back and checked my xorg.conf, and it's still "1280x1024_60" yet my screen res is 1280x800. Then I tried to restart, so I click System>Quit and quit, then it started to shut down, ejected my CD and said "Take out CD and press ENTER", and of course it froze up/did nothing.

Thanks for all your help so far.

What kind of graphics card do you have?

Make sure whatever resolution you want to use by default at your current Color Depth setting is listed first in your lists of resolutions.

Notice in my xorg.conf you see the DefaultDepth is set to 24.  So if we find the Depth 24 subsection in my xorg.conf under the Screen Section, we find 2560x1600 is listed first, so thats what Ubuntu will use by default.

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8800 GTS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "2560x1600" "1920x1200" "1600x1200" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "2560x1600" "1920x1200" "1600x1200" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "2560x1600" "1920x1200" "1600x1200" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "2560x1600" "1920x1200" "1600x1200" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "2560x1600" "1920x1200" "1600x1200" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "2560x1600" "1920x1200" "1600x1200" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
```


When I did my LiveCD install, I had to change my Driver to vesa in order for everything to display properly.  This may be something you may want to try temporarily.  Just find your graphics card in the xorg.conf and change it.  Its something to try anyways.  Then just restart the X server as you have been doing.

```
Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8800 GTS]"
    Driver         "vesa"
EndSection
```

---

### Post by Kivamaki on 2007-05-06
Okay I've gotten further now. I changed "nv" to "vesa" and changed all the resolutions to "1280x1024_60". And rebooted X.

When it came back on, it was fullscreen and working, but the resolution wasn't 1280x1024. It was 1024x768 and in the Screen Res options, 1280x1024 wasn't one of them.

---

### Post by Blackforge on 2007-05-06
> **Kivamaki said:**
> Okay I've gotten further now. I changed "nv" to "vesa" and changed all the resolutions to "1280x1024_60". And rebooted X.

When it came back on, it was fullscreen and working, but the resolution wasn't 1280x1024. It was 1024x768 and in the Screen Res options, 1280x1024 wasn't one of them.

Try leaving off the _60 off the resolutions and adjusting the Monitor sync rates instead.

This is currently what my Dell 3007WFP LCD is using:
```

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

```

Just to see if you can get 1280x1024 working.  Otherwise since you have a "workable" desktop, you can just play around with it from there.  Otherwise, I'd suggest installing it to the Hard drive.  After bootup you can then install Envy to have it install the "real" nvidia drivers for you.  It should carry over the vesa settings for X during the install.  If you have an 8800 series Nvidia card you'll have to take some extra steps though.

I haven't tried Envy or installing the nvidia drivers while being booted on a LiveCD, though I guess theoretically it could work as long as you don't reboot.  Though you'd have to kill any nv modules (rmmod nv) that were loaded during boot time.  You could then use the Nvidia settings panel under Applications -> System Tools to adjust/add resolutions.  This is something you'll want to do when you have it installed anyways.

---

### Post by Kivamaki on 2007-05-06
Okay I'll try that. For installing it, I'm not sure how to make a partition.

When I run the ubuntu partition maker, it gives those three options, on the first option is have a bar for me to move which shows my memory. Is it the higher I move it, the less storage ubuntu gets? Because the lowest I can go is 60GB when I move it left. I'm just kind of confused on that.

For example, If I move the bar left, the GB gets lower (but it's higher than my actual free space). If I move it to the right, the GB gets higher and it will say something like 94%. Is that what I want to do?

Sounds confusing without a screenshot.

---

### Post by Blackforge on 2007-05-06
> **Kivamaki said:**
> Okay I'll try that. For installing it, I'm not sure how to make a partition.

When I run the ubuntu partition maker, it gives those three options, on the first option is have a bar for me to move which shows my memory. Is it the higher I move it, the less storage ubuntu gets? Because the lowest I can go is 60GB when I move it left. I'm just kind of confused on that.

For example, If I move the bar left, the GB gets lower (but it's higher than my actual free space). If I move it to the right, the GB gets higher and it will say something like 94%. Is that what I want to do?

Sounds confusing without a screenshot.

I do all my partitioning manually and am not a resizer, so I may not be the best help for that part.  But what I believe you're referencing is the slider that allows you to resize an existing partition.  How many drives do you have?  Were you planning on resizing a current Windows partition?

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

From that link it appears when you move the slider left, you're resizing the Windows partition to freeing up disk space to allow Ubuntu to be installed, thats why the GB grow.  When you're moving the slider to the right, you're allowing more space for Windows and less space for Ubuntu, which is why the GB shrink.

---

### Post by Kivamaki on 2007-05-06
I only have one Drive for my files, which is C:, and I was planning on just resizing my Windows partion, giving about 15 or 20GB for ubuntu.


So for example, let's say I want 30GB for ubunutu, and the rest is to keep for my windows, this is what I would want?

[https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=6.png](https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=6.png)




Edit: I forgot this in my last post, my Graphics Card is  nVidia GeForce 6600.

---

### Post by Blackforge on 2007-05-06
> **Kivamaki said:**
> I only have one Drive for my files, which is C:, and I was planning on just resizing my Windows partion, giving about 15 or 20GB for ubuntu.


So for example, let's say I want 30GB for ubunutu, and the rest is to keep for my windows, this is what I would want?

[https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=6.png](https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=6.png)




Edit: I forgot this in my last post, my Graphics Card is  nVidia GeForce 6600.

Yes, you would "shrink" your Windows partition until you had 15-20GB free for Ubuntu.

---

### Post by Kivamaki on 2007-05-06
Ok ubuntu is installing now (I'm on another computer), I looked for the:

```
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
```

But it was already exactly like that, so I tried just "1280x1024" without the _60. It's the same thing, I get the 1024x768 resolution. Maybe should I try adding "1280x1024" to the list instead of just having 1280x1024.

Offtopic: Since I need to install Envy to get the nVidia drivers, I need to get my internet working. Since I'm on a wireless router, is there any guide to get it setup, haven't found anything on the forum *yet*.

Again, thanks for helping me on this, I appreciate it.

---

### Post by Blackforge on 2007-05-06
> **Kivamaki said:**
> Ok ubuntu is installing now (I'm on another computer), I looked for the:

```
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
```

But it was already exactly like that, so I tried just "1280x1024" without the _60. It's the same thing, I get the 1024x768 resolution. Maybe should I try adding "1280x1024" to the list instead of just having 1280x1024.

Offtopic: Since I need to install Envy to get the nVidia drivers, I need to get my internet working. Since I'm on a wireless router, is there any guide to get it setup, haven't found anything on the forum *yet*.

Again, thanks for helping me on this, I appreciate it.

Wifi setup:  Try this [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by Kivamaki on 2007-05-06
Didn't work. Plus half the stuff it says to do or go to, isn't there. Plus I don't have a wireless card. I have a adapter that plugs into my USB port.

---

### Post by Blackforge on 2007-05-07
> **Kivamaki said:**
> Didn't work. Plus half the stuff it says to do or go to, isn't there. Plus I don't have a wireless card. I have a adapter that plugs into my USB port.

Well either way it should still detect as a wireless adapter if there's a built-in driver for it.  This may be where you're "on your own" of sorts.  You may have to search around on Google or here for your specific adapter.  If there are not any native drivers you may have to use a Windows driver wrapper to attempt to even get them working.  I had to do this a couple of years ago with my laptop card, but no longer have to.

NDISWRAPPER is one such program:  [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

Of course there may be a native driver floating around out there.

---

