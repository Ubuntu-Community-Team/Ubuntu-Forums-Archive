---
title: "How do I set display resolution on old monitor?"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lightstream on 2010-04-21
I have a new PC which I upgraded to Lucid Lynx a week or so ago. Since then though the display resolution appears to be set too high, or something so that all I see are flickering bands going up and down the screen.

Am I right in thinking that in this new release a lot of the display stuff is now incorporated into the kernel, so the old option of adding settings to xorg.conf no longer helps?

The PC has an Intel IGP, the monitor is an old Cornerstone CRT.

Has anyone got any suggestions for me to try and get the graphics working correctly?

At the moment all I can do is use the TTYs on Ctrl-Alt-F1 etc.

Thanks in advance

edited to add: when I connect up a more recent flat screen, the display works fine, and I can set all the supported resolutions of the monitor. The Cornerstone, being older, doesn't supply full data via plug-and-play (I think) and hence a too high resolution or frequency is being used.

---

### Post by dino99 on 2010-04-22
try  sudo dpkg-reconfigure -phigh xserver-xorg

or follow links in my signature

maybe you have to add into xorg.conf the horizontal & vertical refresh rates of your display

---

### Post by robert shearer on 2010-04-22
You can create an xorg.conf file using..

```
sudo Xorg -configure
```

see this thread for details..
[http://ubuntuforums.org/showthread.php?t=1456399&highlight=Xorg-configure](http://ubuntuforums.org/showthread.php?t=1456399&highlight=Xorg-configure)

---

### Post by lightstream on 2010-04-22
thanks for that. still haven't cracked it though. 

It turned out I did have an xorg.conf, but with fairly empty looking entries.

I deleted it, and rebooted to no effect. 

Then I ran **sudo Xorg -configure** which actually created a file called xorg.conf.new in my home directory. I copied that to /etc/X11 as xorg.conf and rebooted, and finally I tried **sudo dpkg-reconfigure -phigh xserver-xorg** but still the same thing.

---

### Post by robert shearer on 2010-04-22
Have you **edited** your new xorg.conf file ?.

You will need to find the **vertical and horizontal refresh rates **for your monitor and add those to the monitor section.

Then when you reboot the xorg.conf file will be used to set the rates you have input and your monitor should work.

So, step one find those rates..Manufacturers website, book that came with the monitor, google ??

Once you have those if you need help from there then post back and we can step you through.

It is simple and will work, provided you have the **correct** rates. (the wrong rates can damage the monitor.)


note that sudo dpkg-reconfigure -phigh xserver-xorg no longer applies to recent releases.

---

### Post by robert shearer on 2010-04-22
See this thread for editing xorg.conf.
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Scroll down to > How to edit or add HorizSync and VertRefresh lines
for an example of what you will be adding.(just an example, you will need to use the data for **your** monitor.)

---

### Post by lightstream on 2010-04-22
well I seem to have got somewhere but it really seems like it isn't looking at the xorg.conf file at all.

I managed to dig up an old xorg.conf that had settings for this monitor and copied them over, but the display was exactly the same mess of flickering lines.

I found [this article]("http://insidesocal.com/click/2010/02/turning-off-kernel-mode-settin.html") online which said to add **i915.modeset=0** to the Grub boot parameters, and then the system booted and the video was working at last (wahey! thanks for all the suggestions guys :).

At first I thought it was now picking up the xorg.conf settings until I checked the display options and found a completely different set of resolutions to those I'd supplied, and also only 60Hz was present as the refresh frequency for all of them.

So to test this I deleted xorg.conf (well renamed it) and rebooted, and sure enough the system still works ok.

I don't really get what this kernel modesetting is all about (note this machine had Jaunty Jackelope on until I put the new mobo in, at which time I then upgraded to Karmic and then Lucid.

I still don't really get why the system started up OK in Karmic, as it was then apparently that kernel modesetting (whatever that is) was introduced for Intel (and ATi). In Lucid it is also extended to nvidia. So it seems odd that it was with Lucid that I started getting the video issue.

I now need to find if there's some where I can change the frequencies available as xorg.conf is obviously being ignored!

---

### Post by robert shearer on 2010-04-22
has an xorg.conf been generated after you renamed the old one ??

If so what happens if you edit that ?

---

### Post by lightstream on 2010-04-25
when i renamed the existing xorg.conf and rebooted without one, a new one was not generated automatically.

I had to run **sudo Xorg -configure** and then copy the file it created to /etc/X11.

But it just seems that whether or not there's an xorg.conf in the right place, and regardless of what it contains, my system is booting up with some other settings that it's getting from somewhere else as the display only works when that line is added to the GRUB boot parameters and the display resolutions available to X are always the same regardless of what appears in the monitor section in xorg.conf.

So my question now is where are the settings for my hardware coming from if xorg.conf is being ignored?? 

Is there something wrong with my setup if xorg.conf is being ignored, or is it to do with this new 'kernel modesetting' for video?

---

### Post by grandtoubab on 2010-04-25
xrandr will give you the information. The best choice is marked by an *
Example:
```
@ubuntu-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 4096 x 4096
VGA-0 connected 1440x900+0+0 (normal left inverted right x axis y axis) 410mm x 256mm
   1440x900       59.9*+   75.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
S-video disconnected (normal left inverted right x axis y axis)

```

---

### Post by Zimmer on 2010-04-25
> **lightstream said:**
> ....

So my question now is where are the settings for my hardware coming from if xorg.conf is being ignored?? 

Is there something wrong with my setup if xorg.conf is being ignored, or is it to do with this new 'kernel modesetting' for video?

Have you read the xorg log to see if the settings are being ignored..?
A perusal of the first few lines of the log will show you what to look for.. whether the settings are coming from defaults or from the xorg.conf (and which xorg.conf)  :)

---

### Post by Tadhg B on 2010-04-25
Heya I have a similar issue with an older computer and Im really stuck.
In addition to this I am so new to this and have no idea what Im doing. 
I have tried suggestions from loads of forums but none have worked.
I am using a rubbish laptop with (i think) an integrated Intel graphics card, when I installed Ubuntu 9.10 the maximum resolution is only 800x600 which just looks horrible. You would be my absolute hero if you could help me out.

---

### Post by grandtoubab on 2010-04-25
use modeline in xorg
[http://www.x.org/wiki/FAQVideoModes](http://www.x.org/wiki/FAQVideoModes)

---

