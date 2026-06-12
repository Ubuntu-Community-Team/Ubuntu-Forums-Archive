---
title: "fix for monitor resolution planned?"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by wstauffer on 2009-12-07
My monitor is not being recognized by Ubuntu 9.10, defaulting it into
a very low resolution with no other choices.
 
I have had issues with this monitor on other computers at times, but
it worked previously on this computer.  I think the monitor is
putting out the incorrect setting.
 
I am new to Linux, and simply have trouble following the code solutions that manually
configure the monitor.  I am in desparate need of step by step instructions on manually configuring my monitor, or would be even more happy if this problem 
could be fixed with an update of some sort since I am most comfortable with gui's
at this stage of my learning (I am trying!)
 
Can someone help me?  I will look up the specs on my monitor if I have to program
refresh, etc., but the end result of 1024/768 with 60hz 4/3 (apect ratio) refresh is in the ballpark I have had before with success.
 
Does anyone know if a fix for this bug will be offered in the near future?  I think it is fair to say that many others are having this problem, as well.  Us "non-programmer types" that are just learning linux are in need of some help, please!
 
Thanks in advance!

---

### Post by jaylsi on 2009-12-07
What kind of graphic card does it have? What do you see if you select "System->Administration->Hardware Drivers"? Monitor configuration normally goes with graphic card configuration. So if you have a proper driver installed, then you should be able to get the optimal configuration for monitor.

---

### Post by mikewhatever on 2009-12-07
Can you post the output of the following commands from Terminal:

xrandr -q

cvt 1024 768

---

### Post by wstauffer on 2009-12-07
Hi, and thanks for entertaining my issue below are the results:

$ xrandr -q
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  

$cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

My video card is a GeForce 4 MX, 64 MB DDR nVidia, and driver is NVidia (version 96) recommended as proprietary driver

Bill

---

### Post by wstauffer on 2009-12-07
> **jaylsi said:**
> What kind of graphic card does it have? What do you see if you select "System->Administration->Hardware Drivers"? Monitor configuration normally goes with graphic card configuration. So if you have a proper driver installed, then you should be able to get the optimal configuration for monitor.

NVidia (version 96) is the recommended proprietary driver.
Card is 64 MB DDR NVidia GeForce 4 MX (Dell Dimension 4600)

---

### Post by wstauffer on 2009-12-07
> **mikewhatever said:**
> Can you post the output of the following commands from Terminal:

xrandr -q

cvt 1024 768
Hi, and thanks for entertaining my issue below are the results:

$ xrandr -q
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  

$cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

My video card is a GeForce 4 MX, 64 MB DDR nVidia, and driver is NVidia (version 96) recommended as proprietary driver

Bill

---

### Post by mikewhatever on 2009-12-07
Try these now, and post the outputs:

xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync

xrandr -q

Given that you have the nvidia driver for your card enabled, you can also try running the GUI configuration program that comes with it.

gksudo nvidia-settings

---

### Post by wstauffer on 2009-12-07
> **mikewhatever said:**
> Try these now, and post the outputs:

xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync

xrandr -q

Given that you have the nvidia driver for your card enabled, you can also try running the GUI configuration program that comes with it.

gksudo nvidia-settings

Here is what I got...

$ xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync

$ xrandr -q
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  
  1024x768_60.00 (0xe4)   63.5MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.8KHz
        v: height  768 start  771 end  775 total  798           clock   59.9Hz

I apologize if things might look a little weird when I post...it is tough to proofread in 640x480 resolution.

---

### Post by wstauffer on 2009-12-07
> **mikewhatever said:**
> Try these now, and post the outputs:

xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync

xrandr -q

Given that you have the nvidia driver for your card enabled, you can also try running the GUI configuration program that comes with it.

gksudo nvidia-settings

I went into the Nvidia X server settings, and the only choices are the 640x480 and 320x240.  Below that it say "panning" and has 640 by 480 that can be edited....but I was not sure if I should enter 1024x768 in there or not.  As for the "Monitor Model" it states "CRT-0 (CRT-O on GPU-O).  I was also able to get more info about my video card, as it is a GeForce 4 MX440 with AGP8X, if that helps.

---

### Post by mikewhatever on 2009-12-08
I don't know what else to say. If you want bigger resolution, nvidia-settings is the GUI tool for add it. If it doesn't work, we'll go back to the other approach. Just a note, don't open nvidia-settings from the System menu, because it doesn't run with admin privileges that way, and you will need those to save the new settings to X config file. Instead, open it wit <gksudo nvidia-settings>.

---

### Post by wstauffer on 2009-12-08
> **mikewhatever said:**
> I don't know what else to say. If you want bigger resolution, nvidia-settings is the GUI tool for add it. If it doesn't work, we'll go back to the other approach. Just a note, don't open nvidia-settings from the System menu, because it doesn't run with admin privileges that way, and you will need those to save the new settings to X config file. Instead, open it wit <gksudo nvidia-settings>.
 
So in the GUI, I can manually type in my desired resolution where it says "Pan?",which is what I asked previously(?)  My question is, will the refresh change as well, since there are not settings for that.
 
How do I save the settings to the x-config file once I make the changes through GUI with administration priviledges?
 
I will report back once I attemp changes....I am at work now, but will try tonight and see what happens.
 
Thank you so much!  BIll

---

### Post by jaylsi on 2009-12-08
Are you sure you have a nvidia driver installed on your system? On the Hardware Drivers screen, do you see a green circle in front of driver name? If all circles are gray, then you don't have one activated. Try select the recommended one and click 'Activate' and reboot, see what happens.

---

### Post by wstauffer on 2009-12-08
> **jaylsi said:**
> Are you sure you have a nvidia driver installed on your system? On the Hardware Drivers screen, do you see a green circle in front of driver name? If all circles are gray, then you don't have one activated. Try select the recommended one and click 'Activate' and reboot, see what happens.
 
Yes, I have it activated.  But the resolution does not give me many choices.  Since I have had problems on other computers, my "guess" is that the monitor is putting out incorrect DHDT.  The monitor is an old Planar Modintor (dell sold them) and originally was connected to the computer using another type of cable, perhapts the hdmi, but now I am hooking uf the monitor conventionally (there were two cords...don't know where the other one is).  I think that the driver and video card are doing there job, but the DHDT is giving the wrong information to the driver.  Thus, since I am Linux illiterate at this point, I think that I need to manually override the DHDT output of the monitor and manually configure.  And, I have no clue how to do that correctly.
 
At least that is "my" thoughts, would could be wrong.  I still need to try one of the other suggestions above, and see if that works, then proceed from there.  Thanks for your help....perhaps I might need some more troubleshooting here shortly

---

### Post by jaylsi on 2009-12-08
It looks like you have a bad /etc/X11/xorg.conf file. Running 'gksudo nvidia-settings' helps you to create a new one. Once its screen is up, select 'X Server Display Configuration', your monitor brand name and resolution should show on the layout. Click 'Detect Displays' button, see what you will get. You also have a pulldown list for resolution, see if there is a higher one you can choose.

---

### Post by wstauffer on 2009-12-08
> **jaylsi said:**
> It looks like you have a bad /etc/X11/xorg.conf file. Running 'gksudo nvidia-settings' helps you to create a new one. Once its screen is up, select 'X Server Display Configuration', your monitor brand name and resolution should show on the layout. Click 'Detect Displays' button, see what you will get. You also have a pulldown list for resolution, see if there is a higher one you can choose.

Got into nvidia settings through gksudo....when I try to detect monitor, it says "CRT-0 (CRT-0 on GPU-0)"  No other monitors listed.  From what I am thinking (could be wrong) is that it is not detecting my monitor, and is assigning it the generic default resolutions of 640/480, or God forbid, 320x240.  My gut tells me it has something o do with the monitor not putting out a detectable signal for auto configuration.  

To explain further, when I first hooked up this monitor under Ubuntu 9.10, I had "another" monitor hooked up that "autodetected" at 1024x768, which Ubuntu recognized and offered a slew of resolution choices.  Since then I switched to this monitor, but did not restart...so I assume the computer remembered the old settings of that other monitor....but when I "did" restart, that's when my resolution changes, thus giving me the problem.  

In other words, I think I could probably hook up most other monitors, and be okay (I don't have others except on other computers in use).  For some reason, this particular monitor can not be recognized, and thus I am "defaulted" to these generic settings(?)  If it makes a difference, my monitor is a Planar PX171M-SI.  Sure, I could go out and purchase another monitor, but I would rather save the dough and get this one working instead.

---

### Post by mikewhatever on 2009-12-08
I really don't see what's wrong with CRT-0, it's a CRT monitor, isn't it? If you haven't rebooted since changing monitors, please do so, cause it might solve the problem. Otherwise, use nvidia-settings to add the required resolution.

---

### Post by wstauffer on 2009-12-08
Also, originally, my monitor had a dvi cable, which allowed me to hook it up with that cable, or with a svga cable (choice).  Do you think that it is possible that the monitor is acting goony because I am using a svga cable instead of the dvi cable?  Could it only be detected if the DVI cable is used?  Unfortunately, I do not have a DVI cable anymore, but perhaps I should get one to try to see if that makes a difference.

---

### Post by PRC09 on 2009-12-08
As you said you have changed monitors or cables you can try removing the current nvidia drivers and reboot.Then try re-activating the nvidia drivers again and try your settings.Just a thought....

---

### Post by wstauffer on 2009-12-08
> **mikewhatever said:**
> I really don't see what's wrong with CRT-0, it's a CRT monitor, isn't it? If you haven't rebooted since changing monitors, please do so, cause it might solve the problem. Otherwise, use nvidia-settings to add the required resolution.

No....17 inch planar LCD monitor.  I have rebooted....several times....and that is what caused the problem, since it could not detect "this" monitor....it was remembering old setting from old monitor, which worked until I rebooted and it tried to detect "this" monitor, and could not find setting and defaulted to low resolution.  Correct me if I'm wrong, but what I read in one of the other posts I looked at in the archives, that if the monitor can't be detected, it will default to this low resolution(?)  I also read that you can 'turn off" the "autodetection" feature so that one would have to manually configure the monitor based on monitor literature.  

Of course, I don't want to have to do all of this if there is an easier or better way.  I was hoping someone might be able to have an alternate solution.

Below (link) is the closest I would come to describing the "symptoms" I  am having.  The solution is obscure for me to follow (aka....afraid of screwing something up)

[https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution)

scroll down to where it talks about "Problem: Wrong resolutions, refresh rates or monitor specs."  

The symptoms are the same, but the solution is confusing to me.

---

### Post by jaylsi on 2009-12-08
Like PRC09, try deactivate driver and activate again, or active another one.

Since your problem involves changing monitors, you may want to power down computer completely, and unplug the power cord. Wait a few seconds, and restart again. The reason I say this is because I have a monitor with both DIV and VGA port and somehow DVI connect did not work, but VGA worked. This was involving changing monitors too. I was confused. After I opened the case, I noticed the card light is still on even power is off. So I unplug and replug, thinking card may need a hard reset. Everything indeed worked after that. Don't know if that really the reason though.

---

### Post by wstauffer on 2009-12-09
> **jaylsi said:**
> Like PRC09, try deactivate driver and activate again, or active another one.
 
Since your problem involves changing monitors, you may want to power down computer completely, and unplug the power cord. Wait a few seconds, and restart again. The reason I say this is because I have a monitor with both DIV and VGA port and somehow DVI connect did not work, but VGA worked. This was involving changing monitors too. I was confused. After I opened the case, I noticed the card light is still on even power is off. So I unplug and replug, thinking card may need a hard reset. Everything indeed worked after that. Don't know if that really the reason though.
 
 
I will try this tomorrow...and will keep you posted.
 
Thanks again,

---

### Post by doas777 on 2009-12-09
what version of ubuntu are you using? 
my guess is that much of the problem is that that card is no longer supported by the proprietary nvidia packages (nvidia-glx-new), so there shouldn't be an restricted driver listed, and thus no nvidia-settings.

if you go into your xorg, and find the driver line of the device section, what does it say?

---

### Post by wstauffer on 2009-12-11
using 9.10....I haven't gotten any further yet...but will keep you posted.

Thanks so much, Bill

---

### Post by juliobahar on 2009-12-20
> **mikewhatever said:**
> Try these now, and post the outputs:

xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync

xrandr -q

Given that you have the nvidia driver for your card enabled, you can also try running the GUI configuration program that comes with it.

gksudo nvidia-settings

Thanks pal this solved my intel graphic controller refresh rate issue with my samsung 2233sw LCD monitor.

Great job!

---

