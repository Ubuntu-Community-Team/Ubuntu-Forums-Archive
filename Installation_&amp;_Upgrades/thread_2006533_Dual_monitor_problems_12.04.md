---
title: "Dual monitor problems 12.04"
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by kalkems on 2012-06-19
Hi,

I have installed 12.04 on a Acer aspire 5750 (i3) which I use at work. My problem is that I am unable to get a second monitor to function properly. The second monitor is a 19" Dell screen. The problem is stated as being a unrecognized screen resolution. I'm not interested in using it as dualmonitor system. I will only be using the Dell monitor when connected (unless of course I'm using a projector.)

I've tried xrandr but the computer doesn't accept the resolution (1280x800). The thing that is weird is that if I use the cloning function my computer screen is split horizontally and I still get the message that the screen resolution cannot be accepted onm the Dell monitor. This means that using a projector will also be a problem.

I'm in a bind.

---

### Post by dino99 on 2012-06-19
which is the graphic card/chipset ?
is it with a xorg.conf or not ?

---

### Post by kalkems on 2012-06-19
No xorg. conf.  I believe it's an Intel HD 3000.

---

### Post by martinr on 2012-06-19
No worries mate, we'll help you.
Could you do a reboot with the external monitor connected?
After that log in and copy your /var/log/Xorg.0.log file and paste/attach it here?
If present please paste the /etc/X11/xorg.conf file here also.

Furthermore start in single user mode/runlevel 1 (booting in rescue mode to the command prompt will do also) without X and run (as root): Xorg -configure. This will create a skeleton xorg.conf.new file. Please copy that here as well.
That will give us some diagnostical information.

Good luck.

---

### Post by kalkems on 2012-06-20
Hi again. My computer was at work.

I have attached 2 Xorg logs (just remove the .doc part - only way I could get it uploaded - I most probably did something wrong.) The first one is the log after starting the laptop with the external monitor attached (Dell 1908F), the second is attaching the monitor after login (now it's functioning as a second screen and works perfectly as such as long as I detach the monitor before starting next time.) I need to have a system were the Dell monitor is the only screen available and that it can be adjusted with the resolution modes that this monitor can deliver and if the Dell monitor is detached the laptop will display as normal.

I will now restart and do the second part of your request.

---

### Post by kalkems on 2012-06-20
I received error messages using Xorg -config - comments like missing requests connected to this command and also problems with unlocking lock file in /tmp and errors concerning Xorg log file. No file was created.

---

### Post by martinr on 2012-06-20
> **kalkems said:**
> I received error messages using Xorg -config - comments like missing requests connected to this command and also problems with unlocking lock file in /tmp and errors concerning Xorg log file. No file was created.

It should be Xorg -configure (typo, sorry)

I understand it's a laptop. Do you have a function key that switches between monitor modes, eg external, internal and both active?
(Probably <Fn>+F5 or something similar).

Did you try playing with them in order to get your internal TFT to switch off and only use the external monitor?

You can then cycle X resolutions by pressing <ctrl>+<alt>+<numkeypad +> and <ctrl>+<alt>+<numkeypad -> whilst in X, or use the monitor tool in the preferences menu.

---

### Post by martinr on 2012-06-20
I only see the following monitor appear in you log files:
EDID vendor "AUO", prod id 9964
DDC gathered resolution: "1366x768"

Could this be you internal TFT display?

What kind of monitor is it (Dell 1908FP ?) and what is the resolution that you want on the external monitor?

---

### Post by martinr on 2012-06-20
> **kalkems said:**
> The thing that is weird is that if I use the cloning function my computer screen is split horizontally and I still get the message that the screen resolution cannot be accepted onm the Dell monitor. This means that using a projector will also be a problem.


Did any of the logs contain the logging for this situation?

Your projector will be recognised as a different device, so the results you got for your Dell monitor will not automatically be the same for you projector as well. Just try it and see what happens.

---

### Post by kalkems on 2012-06-20
> **martinr said:**
> It should be Xorg -configure (typo, sorry)

I understand it's a laptop. Do you have a function key that switches between monitor modes, eg external, internal and both active?
(Probably <Fn>+F5 or something similar).

Did you try playing with them in order to get your internal TFT to switch off and only use the external monitor?

You can then cycle X resolutions by pressing <ctrl>+<alt>+<numkeypad +> and <ctrl>+<alt>+<numkeypad -> whilst in X, or use the monitor tool in the preferences menu.

I tested -configure but that gave the same errors. 

I actually didn't test if the Fn key will do that :oops:

I saw this site [http://askubuntu.com/questions/73804/wrong-login-screen-resolution](http://askubuntu.com/questions/73804/wrong-login-screen-resolution) and tried their solution which works to a degree but not perfectly as the login screen is only seen in the top left hand corner.

---

### Post by kalkems on 2012-06-20
I tested the Fn keys. The only thing that worked was switching off the laptop.

You quoted the log file and that resolution coincides with the laptop resolution.

I uploaded the .sh file that I wrote after reading at askubuntu. Those are the resolutions that each monitor functions best with. 

I find it really wierd that the laptop won't handle 1280x1024 or 768 for that matter. Xrandr -q gives the following result for the laptop

[HTML]Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)[/HTML]

and with the exteral monitor:

[HTML]Screen 0: minimum 320 x 200, current 2646 x 1103, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1280x1024+1366+79 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)[/HTML]

---

### Post by martinr on 2012-06-20
> **kalkems said:**
> 
I actually didn't test if the Fn key will do that :oops:

I saw this site [http://askubuntu.com/questions/73804/wrong-login-screen-resolution](http://askubuntu.com/questions/73804/wrong-login-screen-resolution) and tried their solution which works to a degree but not perfectly as the login screen is only seen in the top left hand corner.

That's probably because the virtual size of your desktop is set to the size of your internal TFT (or output LVDS1) and the external monitor has a bigger size. What happens if you make only the external monitor active with the <Fn> keys and cycle resolutions orlog out and log in?

To which port do you have the external monitor connected? VGA, HDMI???

---

### Post by kalkems on 2012-06-20
> **martinr said:**
> Did any of the logs contain the logging for this situation?

Your projector will be recognised as a different device, so the results you got for your Dell monitor will not automatically be the same for you projector as well. Just try it and see what happens.

The attached logfile was after the laptop became a split screen.

F5 and F& are the keys that should deal with screen swapping. Pressing F5 gives no reaction and F6 just switches between the screens. Using ctrl+alt and the plus minus keys has no effect.

---

### Post by martinr on 2012-06-20
If your displays are cloned and the primary one is your internal TFT, than the other one won't fit. Try a non cloned setup or with only the External monitor active, log out and in again.

---

### Post by kalkems on 2012-06-20
> **martinr said:**
> That's probably because the virtual size of your desktop is set to the size of your internal TFT (or output LVDS1) and the external monitor has a bigger size. What happens if you make only the external monitor active with the <Fn> keys and cycle resolutions orlog out and log in?

To which port do you have the external monitor connected? VGA, HDMI???

I've tried setting the external screen to 1280x1024 and the internal to 1366x768 but after a restart the result is a black screen on both monitors. I think I mentioned that if I attach the external monitor once the laptop is started then it works but only as an extended screen. Choosing mirrored results in 1024x768.

---

### Post by martinr on 2012-06-20
> **kalkems said:**
> 
F5 and F& are the keys that should deal with screen swapping. Pressing F5 gives no reaction and F6 just switches between the screens. Using ctrl+alt and the plus minus keys has no effect.

The screenswapping function keys are the ones <Fn>+<F5>, pressed together at the same time.

The cycling keys need to be the + and - keys on the numeric keypad only!
But you'll only cycle through what xrandr -q has shown you.

---

### Post by martinr on 2012-06-20
> **kalkems said:**
> I've tried setting the external screen to 1280x1024 and the internal to 1366x768 but after a restart the result is a black screen on both monitors. I think I mentioned that if I attach the external monitor once the laptop is started then it works but only as an extended screen. Choosing mirrored results in 1024x768.
Try to make only the external monitor active and set the resolution via the settings menu Monitor Preferences.

---

### Post by kalkems on 2012-06-20
> **martinr said:**
> Try to make only the external monitor active and set the resolution via the settings menu Monitor Preferences.

I tried this and everything was okey until I logged in then external screen was black with message that the resolution 1280x1024 was unsupported which tells me that it is only recognising the laptop screen resolution at that stage. Non of the function key presses resulted in a change and trying to cxycle through the resolutions gave no result - which most probably means that the Fn key setup is incorrect.

---

### Post by martinr on 2012-06-20
> **kalkems said:**
> I tried this and everything was okey until I logged in then external screen was black with message that the resolution 1280x1024 was unsupported which tells me that it is only recognising the laptop screen resolution at that stage. Non of the function key presses resulted in a change and trying to cxycle through the resolutions gave no result - which most probably means that the Fn key setup is incorrect.

That's normal, before you logout, revert back to the resolution of your internal laptop display.
So you're able to work on the external monitor in the correct resolution, with your internal TFT switched off?

(resolution cycling is not done with the <Fn> keys, but with the key combination from my previous message.)

(By <Fn> key I mean a <Shift> like key to invoke manufacterer specific functions like: volume control, display switching, hybernation, brightness control, etc.)

---

### Post by kalkems on 2012-06-20
> **martinr said:**
> That's normal, before you logout, revert back to the resolution of your internal laptop display.
So you're able to work on the external monitor in the correct resolution, with your internal TFT switched off?

(resolution cycling is not done with the <Fn> keys, but with the key combination from my previous message.)

(By <Fn> key I mean a <Shift> like key to invoke manufacterer specific functions like: volume control, display switching, hybernation, brightness control, etc.)

I tried the ctrl+alt+(+/-) keys on the numeric pad but that gave no result.

> Try to make only the external monitor active and set the resolution via the settings menu Monitor Preferences.

The result I got was when I followed this - making only the external monitor active. If I, on the other hand, remove the external monitor and start the laptop, log in and then plug in the external the laptop shuts off and the my external screen is the only one displaying my desktop. I've tried to have both monitors active and choosing their optimal resolution. I see that this is saved but restarting with the external monitor connected results in black screen.

---

### Post by martinr on 2012-06-20
> **kalkems said:**
> 
  
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   
VGA1 connected 1280x1024+1366+79 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   

1024x768@60Hz is the highest resolution that both internal and external monitors support. So if you're running in cloned mode that's the first resolution that works for both monitors.

You can do tricks with the virtual size, but then one of the screens would be scrolling I presume. The simplest is to make one screen active at a time (like you intended) and set the right resolution for it via the preferences menu.

---

### Post by martinr on 2012-06-20
> **kalkems said:**
> I tried the ctrl+alt+(+/-) keys on the numeric pad but that gave no result.



The result I got was when I followed this - making only the external monitor active. If I, on the other hand, remove the external monitor and start the laptop, log in and then plug in the external the laptop shuts off and the my external screen is the only one displaying my desktop. I've tried to have both monitors active and choosing their optimal resolution. I see that this is saved but restarting with the external monitor connected results in black screen.

That's normal in cloned mode, see my other [reply]("http://ubuntuforums.org/showthread.php?p=12041646#post12041646") for an explanation.

You said you only wanted to have one monitor active at a time. Didn't this solve your problem then?

---

### Post by kalkems on 2012-06-20
> **martinr said:**
> That's normal in cloned mode, see my other [reply]("http://ubuntuforums.org/showthread.php?p=12041646#post12041646") for an explanation.

You said you only wanted to have one monitor active at a time. Didn't this solve your problem then?

Not quite. For me there is no problem in pulling out the vga contact before starting and logging in via the laptop to then connect to the external monitor but I am trying to fix this for other employies at the school that am administer at and they will not be able or willing to deal with this. At moment I have u11.10 installed and there it works but I am trying to move the whole school, servers and all, to u12.04 so that I can leave it there for the next 5 yrs. By not solving this I will have to do this move when and if the problem is solved and that's not quite what I had hoped for.

---

### Post by kalkems on 2012-06-20
You commented about 1024x768 being the common denominater so I set this as the resolution on both screens and that seems to work. I can then switch off the laptop and restart with the external monitor connected. This solution will definitely work for 2 of the employees who use their laptops as stationary desktops but it feels wrong to have to use these workarounds when I know there is no trouble in MSWin.

IF I open the screen of the laptop I have a horizontally split screen and it does not correct it self so this not a solution just a workaround.

Here is the result of the command lspci:

[HTML]00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10)
02:00.2 System peripheral: Broadcom Corporation Device 16be (rev 10)
02:00.3 System peripheral: Broadcom Corporation Device 16bf (rev 10)
03:00.0 Network controller: Broadcom Corporation BCM43227 802.11b/g/n[/HTML]

According to specs I have this card: Intel HD 3000 Graphics. Is there anyway of checking that the drivers are correct for this card?

---

### Post by kalkems on 2012-06-20
I need to clarify how I got it working in 1024x768 mode. I used the method of using a .sh file added to lighdm.conf forcing both screens to use this mode.

---

### Post by kalkems on 2012-06-20
> **kalkems said:**
> I need to clarify how I got it working in 1024x768 mode. I used the method of using a .sh file added to lighdm.conf forcing both screens to use this mode.

Tested without this change in lightdm.conf and I am met with a black screen and the message that the resolution 1280x1024 is a nono.

I restored the lightdm.conf file with my change and I can start on the external screen once again.

---

### Post by martinr on 2012-06-20
If you want to get into the nitty gritty Xorg configuration stuff, I'm sure you'll get it to work. It is extreme highly customizable.

Because the on chip intel 3000 HD stuff is pretty new, I'd first recommend you to upgrade to 12.04 LTS (and make your efforts worth your while). See if that solves it first.

If not, get out of the cloned view. Get rid of the xrandr script (you shouldn't need that anyway) and create a proper xorg.conf file.
Configure all video hardware and monitors explicitly.
Set the virtual size to the largest view and you should be in business.

---

### Post by kalkems on 2012-06-20
> **martinr said:**
> If you want to get into the nitty gritty Xorg configuration stuff, I'm sure you'll get it to work. It is extreme highly customizable.

Because the on chip intel 3000 HD stuff is pretty new, I'd first recommend you to upgrade to 12.04 LTS (and make your efforts worth your while). See if that solves it first.

If not, get out of the cloned view. Get rid of the xrandr script (you shouldn't need that anyway) and create a proper xorg.conf file.
Configure all video hardware and monitors explicitly.
Set the virtual size to the largest view and you should be in business.

I am using 12.04 LTS. I didn't have these problems with 11.10. I'll find some solution that works. Thanks.

---

### Post by martinr on 2012-06-21
> **kalkems said:**
> I am using 12.04 LTS. I didn't have these problems with 11.10. I'll find some solution that works. Thanks.

Hmmm, that's strange a digression from 11.10?
What did 11.10 do when you hooked up the monitor?
and what were the 11.10 settings (cloned, xorg.conf file present)?

---

### Post by kalkems on 2012-06-21
> **martinr said:**
> Hmmm, that's strange a digression from 11.10?
What did 11.10 do when you hooked up the monitor?
and what were the 11.10 settings (cloned, xorg.conf file present)?

Not cloned. 2 separate screens with their own resolutions. There was no Xorg.conf on those installs either. If I remember correctly I think I had problems in the beginning then as well but it sorted itself out. It's as if there has been a change in the driver from 11.10 to 12.04.

We are planning for my father's ninetieth birthday this midsummer weekend and have relatives here from South Africa so I will let this vegetate until next week.

---

### Post by martinr on 2012-06-25
Up until now I did not see a proper detection of the external Dell monitor in any of the xorg log files that you provided.

I did see the supported modes for the Dell in the xrandr output however?? 

You also didn't create a generated xorg.conf file yet, with both monitors attached.

Start in single user mode/runlevel 1 (booting in rescue mode to the command prompt will do also) without X and run (as root): Xorg -configure. This will create a skeleton xorg.conf.new file. Please copy that here as well. That will hopefully contain the Dell monitor detections as well and give us some diagnostical information.

It might be that the External Dell monitor isn't recognized correctly. Providing a proper monitor section in the xorg.conf file might do the trick in that case.

---

### Post by kalkems on 2012-06-26
> **martinr said:**
> Up until now I did not see a proper detection of the external Dell monitor in any of the xorg log files that you provided.

I did see the supported modes for the Dell in the xrandr output however?? 

You also didn't create a generated xorg.conf file yet, with both monitors attached.

Start in single user mode/runlevel 1 (booting in rescue mode to the command prompt will do also) without X and run (as root): Xorg -configure. This will create a skeleton xorg.conf.new file. Please copy that here as well. That will hopefully contain the Dell monitor detections as well and give us some diagnostical information.

It might be that the External Dell monitor isn't recognized correctly. Providing a proper monitor section in the xorg.conf file might do the trick in that case.

Added the files with .doc (no external monitor) and .txt (with external monitor) ending. Entering rescue mode gave me an error when I tried to run Xorg -configure. It was unable to create a lock file in /tmp.

---

### Post by kalkems on 2012-06-26
What I have noticed is that if I keep the laptop screen cover open and plug in the external monitor the laptop shows a blank screen and the external monitor works fine but if I try to close the laptop the external screen shows a message that the optimal screen resolution of 1280x1024 cannot be shown and everything goes blank but with the laptop open and connecting the external screen after login produces an external screen resolution of 1280x1024 without problems.

---

### Post by martinr on 2012-06-26
If X is running you won't be able to do the monitor detection. That's why you need to be in runlevel 1, without X.

Your monitor sections look rather empty.

I would expect something like this:
```
Section "Monitor"
	DisplaySize	  510   290	# mm
	Identifier   "Monitor0"
	VendorName   "SAM"
	ModelName    "SMXL2340HD"
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection
```

In your file I see this: 
```

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection


```
If the conf file was generated with the lock in place, there probably won't have been any detection.

When you close the lid, won't your laptop go into suspend mode?
Can you try to switch the display to your external monitor only, before closing the lid?

---

### Post by martinr on 2012-07-03
Are your problems solved?

---

### Post by kalkems on 2012-07-04
No I am still having these problems. At the moment I am not working  - on holiday. Next week I will be back to trying to solve this situation.

The best thing would have been to get the graphics card to recognize 1280x800 then all would be solved.

---

### Post by martinr on 2012-07-07
If you're absolutely sure your monitor detection is off. 
Be sure that not both monitors are active at the same time in cloned mode, then you'll get the least common denominator (and that's what we've seen).

Here's what I think you can do otherwise.

1. try to let your monitor be auto detected and generate a config file and use that.
2. Find out your monitor specs and hand craft an xorg.conf file.
 Create a mode line for 1280x800.

---

### Post by kalkems on 2012-07-07
Thanks.  I'm going to work again on monday so I'll try this out and come back with the results.

---

### Post by kalkems on 2012-07-09
I let the computer detect both screens and there it gives the optimum size for both.  I save this choose to clse the laptop and only keep the external monitor but after restarting it's as if the computer forgot the size of the external monitorand tries to start with a widescreen resolution and of course fails.

---

### Post by kalkems on 2012-07-09
I thought I'd test something else.  I set both screens to a resolution both have,  1024x768,  worked perfectly until I restarted.  At restart I get the same message - not able to set 1280x1024 - but when I remove the external montor and restarting the computer has not reverted back to any other resolution than 1024x768.  There seems to be a process checking the computers standard resolution against the external monitors standard and refusing to start once it sees that the computer cannot handle 1280x1024 although I have set both to work with 1024x768 - this is even saved in the file. config/monitors. xml.

---

### Post by martinr on 2012-07-11
I once encountered a similar problem.
Then it sufficed to provide decent monitor sections (see below) and some mode lines. 

Be sure not to use both monitors at the same time in cloned mode, then you will get the leas common denominator.

I would only switch to the external monitor (with the output selector function keys) and might have done some mode cycling in X, but you could also do that with prefs-> monitor config I guess.

```
Section "Monitor"
	DisplaySize	  510   290	# mm
	Identifier   "Monitor0"
	VendorName   "SAM"
	ModelName    "SMXL2340HD"
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection
```

---

### Post by kalkems on 2012-07-12
Thanks. I have decided to let this be a long term project and will return with comments as I try your suggestion and maybe some of my own.

I found that using a widescreen monitor solved the problem although the external widescreen does not cater for the same resolutions. For work this will suffice but I personally need to solve the other problem as it almost feels as if this is a bug - maybe.

Thanks again you've been a star!

---

### Post by martinr on 2012-07-13
It sure sounds like something's off in the monitor detection in X in Ubuntu 12.04 especially because it used to work for you under Ubuntu 11. You'd surely be able to get it to work, but might have to generate and tweak your own xorg.conf file.

If you've got an old Ubuntu 11 live CD lying around, maybe you can use that to boot and generate an xorg.conf file and copy the monitor sections out of that file to use in your hand crafted xorg.conf file on 12.04 for the time being.

In the early days you'd always have to handcraft your xorg.conf file. :)

---

