---
title: "Black screen when trying to install 8.10"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by Uoque6Aih2 on 2008-10-31
Hi,

Yesterday I tried to upgrade 8.04 to 8.10. Everything went well until I had to restart my computer. Instead of showing the login screen, it showed nothing (no signal to monitor). I do hear the login sound when I login. 
I've had this problem before, and I don't exactly know how I fixed it back then. I tried things like dpkg-reconfigure xserver-xorg etc, but that didn't seemed to work. But one day, it just worked (?). 

Now I guess the problem is with my graphicscard, which is from ATI (HD3870). So I tried removing the ATI driver and EnvyNG, which I used to install the driver in the first place. This is probably the point were I messed up things, since I'm quite a beginner to Ubuntu/Linux.
I used the following commands as far as I remember in root command line (recovery mode):
- dpkg -l | grep fglrx
- dpkg --remove (did this with every package returned by the above command)
- dpkg --purge xorg-driver-fglrx-envy
- dpkg -l | grep envy
- dpkg --remove (did this with every package returned by the above command)

After that, I tried using xfix in Recovery Mode and using dpkg-reconfigure xserver-xorg, but without success. 

**So I decided to do a clean Ubuntu installation. But instead of showing me the installation dialogs when I select Install, it gives the black screen again, after the loading splash.**

The Check CD option says the CD is fine. Anybody knows what to do?


Computer specs:

**Processor:**  	
Intel Core 2 Quad Q6600
**Memory:**  	
Team Xtreem 2 GB DDR2-800 kit
**Hard Drive:**   	
Samsung SpinPoint T166 500GB
**Video Card:**   	
Asus EAH3870 (ATI)
**Monitor:**   	
Samsung SyncMaster 226BW
**Operating System:**   	
Ubuntu 8.10 Intrepid Ibex
**Motherboard:**   	
Gigabyte GA-P35-DS3P

---

### Post by Pumalite on 2008-10-31
Post your specs. Memory? Graphics?

---

### Post by Uoque6Aih2 on 2008-10-31
added them to my first post ;)

---

### Post by Pumalite on 2008-10-31
Try the Alternate CD

---

### Post by Uoque6Aih2 on 2008-10-31
Just tried that, and it worked flawlessly!

However, when I try to run Ubuntu (dual boot, using Grub) the old problem still appears: no signal to monitor after the loading splash screen.

Might be a bug in Intrepid?

---

### Post by Pumalite on 2008-10-31
If you can get into Recovery Mode; try 'xfix'

---

### Post by Uoque6Aih2 on 2008-11-01
Tried xfix, but the problem is still there.

---

### Post by gulch on 2008-11-01
[http://ubuntuforums.org/showthread.php?t=965478](http://ubuntuforums.org/showthread.php?t=965478)

maybe this problem

---

### Post by Uoque6Aih2 on 2008-11-01
Both problems might have something in common, but the difference is that I can't even see the login screen, and the topicstarter from that thread experiences it's problems after loging in. 
Which makes me conclude that his problem has probably more to do with his desktop environment, and mine has to do with my graphics card. But that's just the way I see it ;)

---

### Post by tsr on 2008-11-01
Hi,

I have a similar problem (that is, the symptoms are the same but it may originate from something else). Unfortunately I don't know how to look up specs, etc so if you tell me that first we can then see if it's the 'same' issue.

/tsr

---

### Post by Uoque6Aih2 on 2008-11-01
> **tsr said:**
> Hi,

I have a similar problem (that is, the symptoms are the same but it may originate from something else). Unfortunately I don't know how to look up specs, etc so if you tell me that first we can then see if it's the 'same' issue.

/tsr

I looked up my specs using Windows (dual boot). But do you by any chance know what type of graphics card you have? Or can you look it up on the "cash-register note thing" (don't know the right word for it :P)?

---

### Post by jorgitow on 2008-11-03
Hey renspoesse, I am in a similar situation as you. I too can get up through the splash screen, but then after that there is no signal to the monitor. I have an ATI HD3850.

Instead of doing an upgrade, I decided to just do a clean install of Ibex over my existing Hardy installation. I can get up through the splash screen, but once the installation GUI is supposed to appear, my monitor (also a SyncMaster, a 205BW) starts cycling between analog and digital trying to find a signal. It never finds one.

Fortunately, since I can't even get past the initial configuration steps for Ibex, my Hardy installation has remained in tact. Installation for Hardy was flawless with the FLOSS drivers being the default configuration. Then, enabling the restricted fglrx drivers (via System>Administration>Hardware Drivers) worked fine, but were a little old. So, I tried the newer fglrx drivers with the EnvyNG configuration which worked as well. So, no black screens in Hardy.

I was hoping that updated drivers would fix the Compiz/OpenGL conflict that results in flickering video playback. They did not, but now that Ibex won't display ANYTHING I have a much bigger problem to sort out.

It's interesting that we both have ATI 3xxx series video cards and Samsung SyncMasters. I don't suppose you've hooked your computer up to a different monitor to rule that out first? That hadn't even occurred to me until I read your post. I just assumed it's a video card problem.

Either way, everything was fine in Hardy (except for the Compiz/OpenGL issue), but now with Ibex I can only make it up through the splash screen before losing the signal to my monitor.

---

### Post by jorgitow on 2008-11-03
I should also add that I get the same result doing the LiveCD. Splash screen and then it loses its signal.

---

### Post by the lush on 2008-11-03
I also have an ATI MR3650, and I get a white screen (laptop, so power is still being supplied to the panel, but with no control).

For some reason 8.04.1 does not seem to work as well as 8.04 - I cannot use my wirless card with a clean install of 8.04.1, but did not have this problem with a clean install of 8.04. I think my only option now is to either find an old 8.04 installation disc, or give up and wait for 9.04 as 8.10 is completely unusable.

---

### Post by jorgitow on 2008-11-03
Okay, well I'm going to try to do an upgrade on my existing (and working) copy of Hardy. I'm assuming I will get a black screen after the splash logo when I reboot for the first time into Ibex (if I even make it that far!) I will then boot up in recovery mode and try to see what I can do from there. I got to figure out whether Ibex is failing to properly detect the SyncMaster monitor....or if it's a problem with our ATI 3xxx series video cards.

---

### Post by Ice Dragon on 2008-11-03
Just adding to the thread, that I also have this same problem.

Not an acceptable problem to have for an official release imho.

---

### Post by Uoque6Aih2 on 2008-11-03
After reading some other threads related to the - apparently known as - Black Screen of Death, I think it's quite safe to say it has something to do with the default enabled drivers in an Ubuntu installation.

In version 8.04, I believe some **open-source driver was set as the default, not the ATI proprietary driver**, which afaik causes the black screens and is set to default in 8.10 according to my way of thinking.

If this is indeed the case, **couldn't this be an option to set when installing/upgrading?**

---

### Post by jorgitow on 2008-11-03
Yes, I agree it's an ATI driver situation. Last night I did a fresh install (with the alternate cd) after a problematic upgrade and got the black screen. I then booted to recovery mode and edited my empty xorg.conf file to properly configure my SyncMaster with no success.

However, right before my initial upgrade attempt from Hardy to Ibex, I played around with my video drivers and screwed something up so that every time I rebooted into Hardy it would do low-graphics mode. I believe the driver used in low graphics mode is VESA. I thought upgrading to Ibex would fix this, but it did not. However, since it kept booting into low-graphics mode, I was actually able to get into Ibex where I did a reconfigure for X server and installed the restricted ATI proprietary drivers. When I rebooted, I got the black screen of death.

So not only does Ibex seem to have a problem with the default open-source ATI drivers, it also seems to not like the propriety fglrx drivers either.

---

### Post by the lush on 2008-11-03
This is probably a stupid question, but, does anyone know if the developers are working on a fix for this issue, and if so, will this fix be put into a new install CD? As I cannot get internet access (Intel 5100) at home, I cannot download extra patches etc when I am there and therefore need to download and burn the complete installation in my office first. I suppose I mean, will there be a service pack release?

---

### Post by zanzibarabiznaz on 2008-11-03
Same problem here, Radeon 3850 card on an LG monitor. Checked a few other threads, haven't found a solution that works yet.

---

### Post by jorgitow on 2008-11-04
Alright, well I appear to be up and running now in Ibex with my ATI 3850 using the proprietary drivers (fglrx) and Compiz is working too.

First, I had to use the alternative text-based installation CD since no GUI interface would work for me initially. Without seeing any GUI, I couldn't even start the installation using the regular CD. If you did an upgrade from Hardy I guess you can disregard this.

Once I got Ibex installed, I was at 'square one' with the monitor signal problem where the screen goes black after the ubuntu splash. When I got to the black screen, I did ctrl+alt+F1 to get to the command prompt. I edited xorg.conf (which was blank by default) with Vi and forced it to use the "vesa" video driver. I also added configuration for my monitor for good measure. Doing this allowed me to get into the Ibex GUI.

Once in Ibex, I ran updates and then activated the restricted ATI drivers. Then I checked my xorg.conf file and found that enabling the restricted drivers appropriately adjusted my configuration, making several changes including replacing "vesa" with "fglrx." After I rebooted I was good to go. 

Hopefully this will help someone else. I can provide more detail as to how I got from the black screen into the GUI using the "vesa" drivers if people are confused. I can post my xorg.conf configurations if that will help.

---

### Post by m4ss on 2008-11-04
Same problem for me, first screen after the loading install orange bar the screen goes totally blank and i can only reset my pc.

I've a Synchmaster samsung 22" LCD connected digitally and a ati 4870 1gb vers.


Anyone know how to solve this ? very imbarassing for canonical this issue in an official release for me...

---

### Post by Pumalite on 2008-11-04
> **m4ss said:**
> Same problem for me, first screen after the loading install orange bar the screen goes totally blank and i can only reset my pc.

I've a Synchmaster samsung 22" LCD connected digitally and a ati 4870 1gb vers.


Anyone know how to solve this ? very imbarassing for canonical this issue in an official release for me...
What else do you have? Post your specs

---

### Post by m4ss on 2008-11-04
> **Pumalite said:**
> What else do you have? Post your specs

I've posted only monitor/video card because reading around forum etc... I've underdand that the problem was a video card issue (ati models) with the generic video install driver..

My fully specs. of my pc is:

Asus P5N32-E SLI PLUS
INTEL CORE2 6750
4 GB RAM Corsair XMS2 800mhz
HD Samsung SATA2 750gb, Maxtor SATA2 500gb, Samsung SATA1 320gb, Maxtor SATA1 120gb.
Ati Shappire 4870 1gb ram
Samsung T220 22" LCD

Usually I'd like to play with it (vista x64), but i love ubuntu and I've format an hd to install the 8.10 with a fresh install.... and the screen goes blank immediatly with this configuration as i sayd..

---

### Post by Pumalite on 2008-11-04
Goes blank on trying to boot a Live CD or at reboot after a finished installation?

---

### Post by m4ss on 2008-11-04
Booting from cd (ubuntu 8.10 x64 vers.), select language --> install ubuntu --> loading screen with orange bar and at the next screen --> BLANK

---

### Post by Pumalite on 2008-11-04
Have you tried the Alternate amd64 CD?

---

### Post by m4ss on 2008-11-04
Not yet... later (4-5 hours) I'll try the alternate..

One question out of topic, the alternate version wich difference have with the normal vers. ?
I'm reading that is compile for pc with less than 256 mb ram, so, it's a lighter version of ubuntu with less programs than the original one ? and what's are the others differences ?

I'll try so later if the alternate vers. works...

---

### Post by Pumalite on 2008-11-04
It's a text based installer to avoid hardware and/or graphics problems.

---

### Post by m4ss on 2008-11-04
ah ok. I'll try later and I'll post this new trying :guitar:

---

### Post by Uoque6Aih2 on 2008-11-04
> **jorgitow said:**
> Alright, well I appear to be up and running now in Ibex with my ATI 3850 using the proprietary drivers (fglrx) and Compiz is working too.

First, I had to use the alternative text-based installation CD since no GUI interface would work for me initially. Without seeing any GUI, I couldn't even start the installation using the regular CD. If you did an upgrade from Hardy I guess you can disregard this.

Once I got Ibex installed, I was at 'square one' with the monitor signal problem where the screen goes black after the ubuntu splash. When I got to the black screen, I did ctrl+alt+F1 to get to the command prompt. I edited xorg.conf (which was blank by default) with Vi and forced it to use the "vesa" video driver. I also added configuration for my monitor for good measure. Doing this allowed me to get into the Ibex GUI.

Once in Ibex, I ran updates and then activated the restricted ATI drivers. Then I checked my xorg.conf file and found that enabling the restricted drivers appropriately adjusted my configuration, making several changes including replacing "vesa" with "fglrx." After I rebooted I was good to go. 

Hopefully this will help someone else. I can provide more detail as to how I got from the black screen into the GUI using the "vesa" drivers if people are confused. I can post my xorg.conf configurations if that will help.

**So basically the problem can be solved by changing xorg.conf to use vesa driver? If so, shouldn't this be changed REALLY soon on the Ubuntu installation CD?**

---

### Post by zanzibarabiznaz on 2008-11-04
> **jorgitow said:**
> I can post my xorg.conf configurations if that will help.

That would be much appreciated!

---

### Post by milaz on 2008-11-04
Pumalite, won't it be cruel to advise a person to use an alternate installation CD so that eventually m4ss will complete the installation to boot Ubuntu with the same Black Screen of Death that was on Live CD?

renspoesse, it is not the full solution to the problem. For example, 1280x1024 on my widescreen 1440x900 monitor looks blurred and untollerably stretched. Also in my idiotic monitor there is no controls to adjust the width and height of the picture.

**In fact, you can use Live CD.** Just press F4 and select "Safe graphics mode".
And after installation you still can boot from Live CD and comfortably copy live version of "/etc/X11/xorg.conf" to your hard drive.

But this is not a solution. The solution will be when I'll be able to use "ati" driver with the last kernel.

---

### Post by 10-10-20 on 2008-11-04
Hi guys - first time poster... long time lurker...

I'm having the same issue with the Black Screen of Death.
I did an upgrade from 8.04 and all was going swimmingly till the reboot.

The only way I was able to get into X was by setting the driver to VESA in xorg.conf. Basically, I reverted to the xorg.conf.failsafe and added in 'driver "vesa"' in the relevant section. 
Once I was inside X, I then enabled the community supported driver for my ATI Radeon 2400 HD, rebooted, and I was back at square one.

Prior to the upgrade I did have the latest ATI released driver set installed as I was using this for TV-out control.

I have tried forcing settings (sync, refresh, area...) for the monitor into xorg.conf, tried recovery mode and X-repair, xfix...
I've also tried "sudo dpkg-reconfigure -phigh xserver-xorg"

My config is as follows:

Dell Inspiron Desktop 530s.
ATI Radeon 2400 HD.
Dell P791 CRT (yes, a tube!)

Any fixes would be appreciated!

---

### Post by milaz on 2008-11-04
10-10-20, if you did an upgrade, at initial grub countdown you can press Esc and choose some previous kernel. Try booting with it.

In case it don't work, try this after removing your xorg.conf
For me it is the one way that worked.

---

### Post by 10-10-20 on 2008-11-04
Hi Milaz,

I just tried that - I get three options - "Ubuntu 7.10, kernel 2.6.22-14-generic" and the same as this again but with the recovery mode and lastly the "Ubuntu 7.10, memtest86+".

No older kernel.

---

### Post by jorgitow on 2008-11-04
I'm sure there are other ways to get into safe-graphics mode that I am not aware of since I am in no way an Linux expert. Milaz is correct in saying that simply changing the drivers to VESA is not the full solution. My video was also stretched and blurry to 1280x1024 on my 20" 1680x1050 monitor. I knew this would happen though.

By editing my xorg.conf to use the failsafe 'vesa' drivers, I'm basically forcing a safe graphics mode so I could at least get into the GUI and try to fix it. Then I was able to get it working by running updates, followed by enabling the restricted ATI "fglrx" driver. When I rebooted everything was fine. My resolution is now 1680x1050.

The /etc/X11/xorg.conf that I used to force the VESA is below. My BusID will most likely be different than yours. At the command prompt you can type "lspci" to find your video card entry and the matching BusID.

Note, I'm not sure if the monitor settings are necessary since I never tried it without them. You may want to leave the monitor stuff out and do just the video card configuration at first to see if it works. These are the settings for MY specific monitor and you need to search for your own. All I did was google "ubuntu+205BW+xorg.conf" and added what I found to the video entry.

Okay, so after Ibex is installed and I reboot I find myself at the black screen of death. 

1. I typed ctrl+alt+F1 to get the command prompt and login.
2. I then typed "lspci" to find the BusID for my ATI3850.
3. I then did "sudo vi /etc/X11/xorg.conf" (I hope you know how to use Vi text editor) which was blank by default, and I changed it to this:


Section "Monitor"
    Option        "DPMS"   
    Identifier    "Samsung205BW"
    VendorName    "Samsung"
    ModelName    "SyncMaster 205BW"
    HorizSync    31.4 - 80.0
    VertRefresh    56.000 - 75.000
    Modeline    "1680x1050" 146.25 1680 1784 1960 2240 1050 1053 1059 1089
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"   
    Monitor        "Samsung205BW"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1680x1050"
    EndSubSection
    Option "AddARGBGLXVisuals" "True"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
    BusID        "PCI:5:0:0"
EndSection

You may only need that last section for "Device"....I'm not sure. This allowed me to boot into the Ibex GUI. Once inside, I ran updates and then enabled the restricted fglrx drivers through System>Administration>Hardware Drivers. I checked my xorg.conf to see if it was altered correctly by the fglrx installation:

Section "Monitor"
    Option        "DPMS"
    Identifier    "Samsung205BW"
    VendorName    "Samsung"
    ModelName    "SyncMaster 205BW"
    HorizSync    31.4 - 80.0
    VertRefresh    56.000 - 75.000
    Modeline    "1680x1050" 146.25 1680 1784 1960 2240 1050 1053 1059 1089
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor        "Samsung205BW"
    Option "AddARGBGLXVisuals" "True"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1680x1050"
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    BusID        "PCI:5:0:0"
    Driver    "fglrx"
EndSection


As you can see it changed 'vesa' to 'fglrx' and added a section for loading 'glx.' I then rebooted and now everything is working at 1680x1050. Compiz works too, although they still haven't fixed the whole Compiz/OpenGL flickering problem yet.

---

### Post by milaz on 2008-11-04
It looks strange because after upgrade you must have a newer 2.6.27-7 kernel in the list. Try using files from [https://launchpad.net/~tormodvolden/+archive](https://launchpad.net/~tormodvolden/+archive)
like 
[https://launchpad.net/%7Etormodvolden/+archive/+files/xserver-xorg-video-radeon_6.9.0+git20081029.937b7ac2-0ubuntu0tormod2_i386.deb](https://launchpad.net/%7Etormodvolden/+archive/+files/xserver-xorg-video-radeon_6.9.0+git20081029.937b7ac2-0ubuntu0tormod2_i386.deb)
and
[https://launchpad.net/%7Etormodvolden/+archive/+files/xserver-xorg-video-ati_6.9.0+git20081029.937b7ac2-0ubuntu0tormod2_i386.deb](https://launchpad.net/%7Etormodvolden/+archive/+files/xserver-xorg-video-ati_6.9.0+git20081029.937b7ac2-0ubuntu0tormod2_i386.deb)

Maybe this helps?

---

### Post by jorgitow on 2008-11-04
I'm curious 10-10-20, what does your xorg.conf look like after you installed the restricted drivers?

---

### Post by 10-10-20 on 2008-11-04
> **jorgitow said:**
> I'm curious 10-10-20, what does your xorg.conf look like after you installed the restricted drivers?

Here's xorg with vesa loaded...

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"vesa"
EndSection
```

And if I load the restricted drivers, it changes to this...

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
```

Now when I reboot, I won't have X till I change vesa back again.

---

### Post by 10-10-20 on 2008-11-04
Cross referencing a similar thread...
[http://ubuntuforums.org/showthread.php?p=6106078#post6106078](http://ubuntuforums.org/showthread.php?p=6106078#post6106078)

---

### Post by jorgitow on 2008-11-04
Yeah, I'm not sure how important the BusID or the monitor configurations to my success. I should probably try variations of my xorg.conf to see how the entries effect it. 

Also did you make sure you have the very latest drivers for fglrx and its not somehow still using the old ones from hardy? 

I ask because it is my understanding that Ibex uses the new X Server 1.5 that was released with X.Org 7.4 this past September. Supposedly we're all essentially beta testers because the new restricted ATI drivers being used in Ibex haven't even been released to the general public yet. I guess they wanted to do a trial run with us first. I believe that is why, if you go to the ATI website and try to download the latest drivers, it says "Automated installer and Display Drivers for X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3"...leaving out 7.4.

My driver version is 8.54.3 and it is working for me. I would check just to make sure just in case for some odd reason the upgrade kept your old drivers that worked with the previous version of x.org and x server, but will not work with the versions in Ibex. This is my understanding of the situation, I could be wrong though.

---

### Post by 10-10-20 on 2008-11-04
You know what - I'll try an install of the ATI drivers instead of the Restricted drivers and see what that does to my system.
Stand by...

---

### Post by 10-10-20 on 2008-11-04
Bugga.
Well, that was quick...

I did a sudo ./ati-driver-installer-8-7-x86.x86_64.run and I got this...

```
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.22-14-generic; make sure that the version is being
correctly set by --iscurrentdistro
```

Which is the same as this issue...
[http://ubuntuforums.org/showthread.php?t=970059&highlight=default_policy.sh](http://ubuntuforums.org/showthread.php?t=970059&highlight=default_policy.sh)

---

### Post by ubiwan on 2008-11-04
I have this same problem, no signal to monitor or output not supported after the moving bar splash screen.

---

### Post by zaine_ridling on 2008-11-04
Same result as 10-10-20's last one. Still got a black screen. Oy. Guess I'll have to wait for ATI to bring their drivers up to x.org 7.4.

From now on, I'll check this spec. (Didn't know to do so as a n00b.)

---

### Post by jorgitow on 2008-11-04
Well the fglrx driver included in Ibex is supposed to be the new one that DOES support X.org 7.4, but has not yet been released to the general public. So it should work. It does for me anyway, but it's basically a beta so who knows what sort of bugs there will be. 

When I was troubleshooting before I also tried the ATI drivers from their website and got the invalid version message. I guess that confirms that they are older than the fglrx drivers included in Ibex.

So were you able to confirm that the restricted fglrx version was 8.54.3 ? I believe anything earlier will not support 7.4 and will not work.

---

### Post by 10-10-20 on 2008-11-04
> **jorgitow said:**
> <cut>
So were you able to confirm that the restricted fglrx version was 8.54.3 ? I believe anything earlier will not support 7.4 and will not work.

No, I wasn't sure how to check the revision. How do I do that?
It seems to pull the driver from the web though...

---

### Post by jorgitow on 2008-11-04
Well if you can get in under the 'vesa' drivers you can run the catalyst control center with 'amdcccle' and check the info. Although, I'm not positive it will display the right info if you are running under 'vesa' and not fglrx because it may be checking for fglrx versions that are actually loaded. But, the package should still be installed, so if you go to the synaptic package manager and put 'fglrx' in the quick search you can find 'xorg-driver-fglrx' and you will see the 'installed version' next to that. Mine says 2:8.543 for driver version 8.54.3.

Once again, probably not your problem. Just seems like you should make sure that Ibex properly updated the restricted driver to the new beta instead of reactivating the old one from Hardy that doesn't support X.org 7.4.

---

### Post by zanzibarabiznaz on 2008-11-04
Adding

Driver "Vesa"

to xorg.conf allowed me to boot into Intrepid normally.

Thanks jorgitow!

---

### Post by jorgitow on 2008-11-04
That's great. Once you got in, were you able to activate the restricted ATI (fglrx) drivers and have them work? That is what worked for me. After I got into Ibex, I ran all updates and then enabled the restricted drivers. Then I made sure the appropriate changes were made to the xorg.conf ('vesa' > 'fglrx') file during the installation. I then rebooted and everything started up fine with 1680x1050 resolution and 3D rendering.

---

### Post by m4ss on 2008-11-05
Solved in a best way !!!

During the first screen installer (8.10 x64) I've selected "safe mode graphics", pressing F4(don't remember exactly if it's f4), the installer goes ok, reboot, ubu install immediately the ati newest driver, reboot and all ok, 3D enable and i can set all my compiz settings :D

---

### Post by jorgitow on 2008-11-05
Nice job. Yeah the key is just simply getting into the GUI anyway you can in order to install those new pre-release ATI drivers for X.org 7.4. Then you should be good to go. I myself forced the VESA driver manually in xorg.conf, but next time I need to do it I'll try out your way m4ss if it's easier. Thanks for the info.

---

### Post by 10-10-20 on 2008-11-05
> **m4ss said:**
> Solved in a best way !!!

During the first screen installer (8.10 x64) I've selected "safe mode graphics", pressing F4(don't remember exactly if it's f4), the installer goes ok, reboot, ubu install immediately the ati newest driver, reboot and all ok, 3D enable and i can set all my compiz settings :D

I don't have the option of doing this as I performed an upgrade from 8.04.

Is there a way that we can raise this as a bug/defect with the Ubuntu staff?

---

### Post by mcb CH on 2008-11-05
10-10-20, I also up-graded online from 8.04.
Modifying the xorg.conf file by replacing the "i810" device driver with "vesa". That has brought up my display at least. I now need to re-install the proper driver, but at least I can see what I'm doing.

---

### Post by Uoque6Aih2 on 2008-11-05
> **milaz said:**
> ...
renspoesse, it is not the full solution to the problem. For example, 1280x1024 on my widescreen 1440x900 monitor looks blurred and untollerably stretched. Also in my idiotic monitor there is no controls to adjust the width and height of the picture.
...
But this is not a solution. The solution will be when I'll be able to use "ati" driver with the last kernel.

Yes I understand that, but isn't that up to ATI? In my opinion, Ubuntu should use vesa as the default video driver for ATI cards, or at least offer an option to select while installing. So I think that's something for the Ubuntu developers to fix.

---

### Post by 10-10-20 on 2008-11-05
renspoesse - I can't say I agree.
The defect should have been picked up in Ubuntu's testing of the configuration. This is a show-stopper as the native driver (vesa) nor the restricted driver rectify the issue.

The workaround is the run the vesa driver, but this limits the resolution and therefore the functionality of the system...

Do you not agree?

Also, this thread wouldn't have 1,415 views if there wasn't a significant issue!

---

### Post by Uoque6Aih2 on 2008-11-05
I certainly agree on the fact that using the vesa driver does not solve everything.

Also, it is safe to say the issue is caused by the graphics driver, or am I mistaking?

The vesa driver offers *working* basic functionalities. The fglrx does not do this in a lot of cases. Since it's a restricted driver, only ATI has the power to fix this bug in their driver. Ubuntu has not. So I think Ubuntu should use the vesa driver by default, at least until ATI fixes their drivers.

---

### Post by jorgitow on 2008-11-05
So I take it the two of you, renspoesse & 10-10-20, were unsuccessful in getting the fglrx driver working once you got inside the GUI using vesa. You guys still get the black screen even after your xorg.conf files get modified with entries for fglrx? If I remember correctly, both of you did upgrades. I hope the upgrades properly updated the fglrx drivers to version 8.54.3.

---

### Post by 10-10-20 on 2008-11-05
Correct jorgitow.
I loaded the restricted driver from the Hardware Drivers interface and on reboot, it breaks X again.
The only item I am unsure of is the version of the driver... I can't check it using the ATI-CCC application as it only works when the driver is loaded.

---

### Post by jorgitow on 2008-11-05
Did you open synaptic package manager and check the version that way? I described that method as well in a previous post.

---

### Post by 10-10-20 on 2008-11-05
I just did it now...
It report the installed version as "2:8.543-0ubuntu4"

---

### Post by 10-10-20 on 2008-11-05
I just did it now...
It report the installed version as "2:8.543-0ubuntu4"

---

### Post by jorgitow on 2008-11-05
Yeah that looks right. That's frustrating. Unless anyone else has any ideas, I guess I would recommend booting up under vesa and backing up all your files. Then do a clean install. I first attempted an upgrade and butchered my driver situation so badly that my computer refused to boot up in anything other than low graphics mode. Even with fglrx installed and the xorg.conf configured correctly. I guess trying several different drivers (ati, radeonhd, fglrx, envy) can really mess up the installation. After I did the clean Ibex install, I was able to get the fglrx drivers working properly. 

However, I'm not going to assume what worked for me, will work for you. I'm just throwing out ideas because I spent several days trying to get mine to work and I know how frustrating it is.

---

### Post by jerrylamos on 2008-11-05
Many people getting "black screen" have Intel graphics hardware.  The difficulty is compiz doing something no other screen software does and it doesn't work hanging the system.  See Launchpad bug #259385.

To test to see if this affects you,
boot in rescue mode
at the selection menu 
choose root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume normal boot

If that's not the problem compiz can be re-installed with synaptic.  If you try to install as above, then enable internet connection first
sudo dhclient

Good luck  Jerry

---

### Post by jorgitow on 2008-11-05
When I was trying to get my problem sorted out one of the things I tried was removing compiz, but it was not successful for me. Once I was able to get the fglrx drivers installed and working properly, I was able to enable Compiz and everything is working fine. So in my case, compiz has not been a problem in getting the fglrx to work. However, maybe it would work for other people with ATI cards. There are other problems with ATI and compiz when using OpenGL, so maybe there is another bug that's surfacing. Worth a try, good suggestion.

---

### Post by sr71pav on 2008-11-06
I get a black screen, but maddeningly, it's not every time.  I have the fglrx drivers, and sometimes when I reboot, it works fine, other times, I get a black screen.  There is no pattern that I've been able to detect, as yet.  At thie point, I'm just using the ati driver instead.  It's slower, but I can use the system just fine.  I'd really like to get the fglrx driver working again, though.  I am considering a clean install as my next path to go down.

---

### Post by arkster00 on 2008-11-06
I just wanted to point out that I have the exact same problem where the black screen happens after booting ibex. I upgraded from 8.04 that was flawless.
I tried a new installation and the same problem happens. I even used the livecd and that same problem still happens. I used the alternate text based installer, and that didn't work either.

I have to point out that I am using an nvidia 8800gt card. I have exactly the same configuration as the OP of this thread except for the video card and monitor.

Processor:
Intel Core 2 Quad Q6600
Memory:
4gb OCZ
Hard Drive:
Samsung SpinPoint 1TB
Video Card:
8800GT Nvidia
Monitor:
Dell 3007wfp-HC.
Operating System:
Ubuntu 8.10 Intrepid Ibex
Motherboard:
Gigabyte GA-P35-DS3P

---

### Post by PendragonUK on 2008-11-06
Given that ATI and nVidia owners are having similar issues. I believe it's a monitor detection issue, not driver. 

They have removed the ability to manual set your monitor. xorg.conf is no longer read in the same way as before. So editing this may not fix your problem. displayconfig-gtk is no longer available to put in the correct monitor spec.

These are just my opinions as we all know opinions are like bellybuttons, we have them but most don't hold much water...

I have been a member of this forum for a few years now. It has changed over time. There are plenty of people here. Lots of posts, but fewer answers. 

These discussions about "Black Screen of Death" have be circulating the forum since 8.10 came out. Still no answer or comment, the lack of comment I find strange. It would be nice to hear from the Dev's to know that they are at least aware of the situation. A few years ago they would have been all over this like a rash. We would have had at least an acknowledgement if not answers.

Has this forum become too diluted to be useful?

---

### Post by PendragonUK on 2008-11-06
I spoke too soon about the lack of input from the Devs...

[http://ubuntuforums.org/showthread.php?t=966995](http://ubuntuforums.org/showthread.php?t=966995)

---

### Post by 10-10-20 on 2008-11-06
I tried forcing the monitor to run at 800x600 (using xorg.conf) and this had no effect.

---

### Post by jorgitow on 2008-11-07
Interesting that PendragonUK thinks it's a monitor issue, because I'm one of the people who successfully got the fglrx driver to work after dealing with the black screen problem.....and I configured xorg.conf for my monitor. I configured it at the same time that I configured my video driver information, so I guess technically I don't know for sure which fixed my problem: Getting into Ibex to enable fglrx OR configuring my monitor in xorg.conf.

---

### Post by nsquare on 2008-11-07
Hello,

I am facing the same problem. First time user of Ubuntu and not sure how to fix it. The screen goes blank with a just a cursor blinking, after the splash screen on clicking Install using Live CD.

Looking at the threads it looks like its a monitor issue - prob unable to fix the resolution or something. 

I have the same monitor as renspoesse - 

Samsung SyncMaster 226BW
But Card is **Nvidia **GeForce 7900 GS
Proc - AMD Athlon 64 3000+
1GB DDR400

Anyone found the solution, I do not want to try the alternate CD, looks like once the installation is done, we run into the same problem. 

Any guidance will be helpful.

Thanks

---

### Post by sr71pav on 2008-11-07
At a guess, it's the monitor setup.  I've been able to get into X and setup fglrx, and that's sporadic for me.  I can't figure out why it works sometimes and not others.  I'm using the ati driver atm.

What did you have to setup for your monitor, specifically?  I'm on a laptop, so my issue may be different, but I thought I'd give it a shot.

---

### Post by baronvf on 2008-11-07
Just checking in here.

I upgraded from 8.04 to 8.10 using the procedure outlined here:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

I then got the Black Screen of Death (hearing startup noises but seeing nothing)

My setup:

HD1 Sata Ubuntu Linux x64
HD2 Sata Windows XP pro

Video Card: Ati Radeon x1950 pro

I was able to edit xorg.conf, but I really have no clue what I am doing.  Not sure where I should be putting the vesa driver.

At the very least I was wondering what keystrokes I could use one I get into the linux gui (by putting in my user name and password and listening for startup music)

and shutdown properly so that Linux would mount the linux drive so windows could see it.  All I need to do is tell it to restart and it should allow windows to see it using the windows xinfs2 drivers or whatever.

I have files stored on my linux HD that I need access to and windows just wants to format the drive unless linux is shutdown properly.  

Also, any advice on how to edit the xorg.conf would be great!

Thanks yall.

---

### Post by 10-10-20 on 2008-11-07
Hi,

I got around my problem by removing the ATI card and using another one!
To edit the xorg.conf file: 

(I'm typing this from memory now...)

At the black screen, press CTRL-ALT-F1 to enter terminal 1.
You will see a logon prompt to which you logon as normal.
Then, type "sudo pico /etc/X11/xorg.conf" <enter> to bring up the text editor Pico.
Find the line which should read 'Driver    "fglrx"' and change that to 'Driver    "vesa"'.
Press CTRL-X and Pico will ask you to confirm whether you want to save the file, to which you type Y, then press enter again to save it.

Now, type "sudo restart" (or is it "sudo reboot"...)... and the system will reboot.
You should then get a low resolution desktop (800x600) to work in.

:)

---

### Post by baronvf on 2008-11-07
> **10-10-20 said:**
> Hi,

I got around my problem by removing the ATI card and using another one!
To edit the xorg.conf file: 

(I'm typing this from memory now...)

At the black screen, press CTRL-ALT-F1 to enter terminal 1.
You will see a logon prompt to which you logon as normal.
Then, type "sudo pico /etc/X11/xorg.conf" <enter> to bring up the text editor Pico.
Find the line which should read 'Driver    "fglrx"' and change that to 'Driver    "vesa"'.
Press CTRL-X and Pico will ask you to confirm whether you want to save the file, to which you type Y, then press enter again to save it.

Now, type "sudo restart" (or is it "sudo reboot"...)... and the system will reboot.
You should then get a low resolution desktop (800x600) to work in.

:)

Sweet, got me into Ibex with the GUI.

Now I need to know where to get these proprietary drivers / restricted drivers to see if I can get it working.  The drivers from the ATI website certainly dont work (wrong distribution it says)

---

### Post by jorgitow on 2008-11-07
nsquare, i think the monitor configuration in xorg.conf for you would be whats below:

Section "Monitor"
    Identifier     "SyncMaster"
    DisplaySize     432    324
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection


I believe the previous entry relies on your video device being named "Generic Video Card". An example is below. You would need to make sure the video driver is correct for your situation (nvidia or nv).


Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "UseDisplayDevice" "DFP"
EndSection

---

### Post by Wolfhere on 2008-11-07
Try running the install again, but this time do the mode switch on the beginning screen and select the safe video mode? If your card is NVidia, you can use the newest drivers provided after the install...or at least install from the restricted drivers ([COLOR="Red"]177.x[/COLOR] vs 173.x envyNG). I ran into this with both the full install and the wubi install. This way around was not as evident as with the 8.04 install.

Updates after the install are pretty slow yet...having just been released.:confused:

---

### Post by ryseshan on 2008-11-08
I also face the same problem on upgrade from 8.4 to 8.10 in my system. My system using 845 Intel Desktop Motherboard no external display card.  The same I faced in 8.4 version but it used to show me the desktop but the mouse area i used to get patches.  It is fixed through displayconfig and defining my monitor type solved the problem.  Now in 8.10 monitor is showing no signal. Even in root mode I am not able to fix it. Please do help me how to fix this problem.

---

### Post by nsquare on 2008-11-08
> **jorgitow said:**
> nsquare, i think the monitor configuration in xorg.conf for you would be whats below:

Section "Monitor"
    Identifier     "SyncMaster"
    DisplaySize     432    324
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection


I believe the previous entry relies on your video device being named "Generic Video Card". An example is below. You would need to make sure the video driver is correct for your situation (nvidia or nv).


Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "UseDisplayDevice" "DFP"
EndSection


Thanks, but how do I even get to the conf file? I mean when the installation itself is not complete? The problem occurs when I click on Install. The splash screen occurs and then the screen goes blank, with the cursor blinking on the left hand corner. 

I have tried using the Safe Video mode, with the same result. Do I first need to install using the Alternate CD and then fiddle around, I am a bit skeptical to do that, since I have XP running on a different drive on the same disk and do not want to corrupt the Boot.

Anyone?

---

### Post by 10-10-20 on 2008-11-08
Have a look at my last post for details...

---

### Post by jorgitow on 2008-11-08
It sounds like we do have one small difference nsquare. I did not have the cursor blinking. After the splash screen, mine was just solid black with nothing. Not sure if that indicates a different problem or not. Anyway, I used the alternate installation cd on the ubuntu website that is text based. That gets around having the GUI problems. Then once I booted up for the first time, I edited the xorg.conf file for my video and monitor.

1) At the black screen when attempting to boot Ibex for the first time after installation, I did "ctrl+alt+F1" to get to the command prompt.

2) Logged in.

3) Used Vi text editor to alter the config file: "sudo vi /etc/X11/xorg.conf". That would be where you would enter the configuration I posted earlier for you (assuming it's correct). You're going to want to read up on the commands for using Vi if you're going to do it this way.

Not sure if this will work for you, but it works perfectly for me with a Samsung SyncMaster and an ATI 3850.

---

### Post by jorgitow on 2008-11-08
Yeah actually use Pico like 10 10 20 said, it's more intuitive if you're not familiar with Vi. I just use Vi because it's what I learned on 10 years ago. Old habits die hard.

---

### Post by nsquare on 2008-11-09
> **jorgitow said:**
> It sounds like we do have one small difference nsquare. I did not have the cursor blinking. After the splash screen, mine was just solid black with nothing. Not sure if that indicates a different problem or not.

You are right! When I checked the integrity of the CD it erred out on one file. Downloaded the Alternate CD this time, taking no chances.

Installation went smooth and I was soon greeted by the regular 800X600 poor resolution screen. Installed the restricted drivers v177 and then on reboot, the evident happened, Black screen of death.

Followed your advice and opened the xorg.conf file. Added the configurations supplied but to no avail. Browsed a bit, found the exact Display Size for the Samsung 226BW, edited that. Changed the refresh rate to 60 constant. For some reason giving a range never helped.

That did not solve the problem either. Opened the Xorg.0.log file and figured something was wrong, have a look at this - 

```
(--) NVIDIA(0): Connected display device(s) on GeForce 7900 GS at PCI:1:0:0:
[B](--) NVIDIA(0):     CRT-0
(--) NVIDIA(0):     Samsung SyncMaster (CRT-1)[/B]
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (CRT-1): 400.0 MHz maximum pixel clock
(WW) NVIDIA(0): Option "UseDisplayDevice" requested "DFP", but no unused DFPs
(WW) NVIDIA(0):     are available.
(II) NVIDIA(0): Option "UseDisplayDevice" "DFP" converted to "".
(WW) NVIDIA(0): Unable to find any of the requested display device "" in the
(WW) NVIDIA(0):     list of available display devices "CRT-0, CRT-1".
(II) NVIDIA(0): Assigned Display Device: CRT-0
```

The card has a dual display out, and evidently my monitor was configured as CRT-1. Obviously using the UseDisplayOption with DFP was not right, since there was no display like DFP. The system was then assigning CRT-0 as the assigned display device, which did not exist.
```
 (II) NVIDIA(0): Assigned Display Device: CRT-0
```

I edited my xorg.conf and changed the option line of UseDisplayDevice as this
```
    Option         "UseDisplayDevice" "CRT-1"
```

That cracked it and now I am having the most beautiful screen and now can open Nvidia X Server Settings to play with.

Thanks a ton for your help. :D

Below is the snippet of the final file if it helps anyone - 

```

Section "Module"
    Load           "glx"
EndSection

Section "Monitor"
    Identifier     "SyncMaster"
    DisplaySize     474    296
    HorizSync       30.0 - 81.0
    VertRefresh     60.0
    ModeLine       "1680x1050" 119.0 1680 1728 1760 1840 1050 1053 1059 1080
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "SyncMaster"
    DefaultDepth    24
    Option         "UseDisplayDevice" "CRT-1"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection
```

This might be a common problem if the users have a dual display and they would probably have to configure it the right output.

:guitar:

---

### Post by arkster00 on 2008-11-09
I got my black screen problem fixed as well. It was a nightmare however. This is a pretty fundamental problem that needs to get addressed. When I installed 8.10 either using the alternate install, cd install etc, I'd get a stripped down version of the xorg.conf.


Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Being a noob that has never configured an xorg.conf successfully, I decided to give it a shot. First, I checked to see what video driver was installed and decided to reinstall it again. For some reason for me, the 177 nvidia module does not get loaded even after reinstalling. Running an lsmod does not show it. I reverted back to the older 173 driver and lsmod found that. My xorg.conf was updated by the driver.
Being that I'm using a newer monitor (Dell 3007wfp), I did not know what the settings and sync frequencies needed to be set. Googling for '3007wfp xorg.conf' showed a sample file that some kind person had put up. I got the resolution info from there but used the vertical and horizontal settings from the spec sheet on the Dell website.
Everytime I would update the xorg.conf, there would be some problem booting up. Kept checking the Xorg.0.log file in the /var/logs folder for the problems and sorted them one by one. Some things were happening due to some identifiers not recognized as valid options. I commented those out and finally got my monitor working in 2560x1600. I was pretty happy finally.

I have to say that this release (8.10) was not really tested properly before releasing. The release should have been in beta for longer. How can people move to Ubuntu if basic stuff doesn't work. Kind of a sad situation too since the rest of Ubuntu is awesome and works exactly you want it to for the most part. I bet countless people got dejected by this installation crap and gave up Ubuntu as being a shitty OS.

Following is my xorg.conf.

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

#Section "Files"
 #   RgbPath         "/usr/X11R6/lib/X11/rgb"
#EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    ModelName 	"DELL 3007WFP"
    Gamma		1.21
    ModeLine	"2560x1600@60" 348.2 2560 2752 3032 3504 1600 1601 1604 1656 -hsync +vsync
    VendorName     "DELL Corporation"
   # 98.71 kHz Horizontal, 59.97 Hz Vertical
    HorizSync       98.71
    VertRefresh     59.97
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
	Option	"RenderAccel" "true"
	Option	"AllowGLXWithComposite" "true"
	Option 	"AddARGBGLXVisuals" "true"
	DefaultDepth	24
	SubSection "Display"
		Virtual	2560 1600
		Depth	24
		Modes	"2560x1600@60" "1920x1200@60" "1680x1050@60" "1600x1024@60"
	EndSubSection
EndSection

---

### Post by lpevey on 2008-11-09
I have been struggling with this problem and lurking on this thread for a while, and I want to thank everyone who has shared their tips.  For me the problem has been somewhat solved, so I want to share what finally worked for me.

First, based on joritow's success, I knew I had to use low-graphics mode to get past the initial install.  After that, I installed the restricted nvidia drivers.  But then, just as for a lot of other people, the black screen returned.  I took a look at my xserver log, and it seemed like the xserver was having trouble deciding which was my primary video device and instead of just choosing one, it would give up.  I have two 8800 GTS cards because I sometimes connect a second monitor.  (I had tried connecting my single monitor to both cards to make sure it wasn't selecting the second one, causing the black screen.  No luck there.)  I decided to try removing one of the cards, and voila, problem solved.  The xserver started up just fine with the 177 driver.

This probably won't solve the problem for everyone, but if you have two video cards in your system and can live without one of them, it's worth a try to take one out.

It seems like there are lots of different bugs with the new X system that could potentially cause the black screen of death problem.

---

### Post by 10-10-20 on 2008-11-09
So, that interesting. Three NVIDIA users now with working configurations.
Have any ATI users been able to work around this problem using a similar method?
I'll try mine when I get a chance.

---

### Post by mik9dt on 2008-11-10
I had the black screen issue with my daughters pc.

It had 2 nvidia PX6600 GT TDH video cards installed although only one was in use with 8.04.

On update to 8.10 I got the same result as you... "no screens found" and a command prompt.

startx did not work.

I physically removed the unused video card and now all is well.

The updated video software could not decide which video card to use and so said that it could not find any, although it was telling me this using the attached screen!

---

### Post by jorgitow on 2008-11-10
Good detective work nsquare. Alright so it sounds like in the end the critical step for both of us was configuring our SyncMasters correctly? I hope renspoesse, the guy who started the whole thread, has tried configuring his video card AND monitor. I hope he didn't get frustrated and give up on Ubuntu. 

Arkster00 is right. This is a pretty widespread and fundamental problem that needs to be addressed. It seems like the devs aren't ready to be moving away from xorg.conf as fast as they are. I wonder how many people gave up on Ubuntu because of this problem.

10-10-20, I have a working config and I'm an ATI 3850. I can't remember, did you try configuring your monitor in xorg.conf? I'm not sure, but for your type of monitor I think you would need something like this:

Section "Monitor"
        Identifier      "DELL P791"
        Option          "DPMS"
        HorizSync       30-96
        VertRefresh     50-160
EndSection

Section "Screen"
	Identifier	"Dell"
        Device          "Configured Video Device"
	Monitor		"DELL P791"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

I'm not sure if this will do the trick, but it's worth a shot if you really want to get that ATI card working. After this I think I'm all out of ideas.

---

### Post by 10-10-20 on 2008-11-10
Hi jorgitow.
I tried configuring the monitor again last night, to no avail.
I'll compare your xorg to mine later today and see what differences I have.

I didn't get much time to work on it, life interjected... 
:)

---

### Post by 10-10-20 on 2008-11-10
Actually, that's funny - we both have the same monitor!

---

### Post by arkster00 on 2008-11-10
> **10-10-20 said:**
> Hi jorgitow.
I tried configuring the monitor again last night, to no avail.
I'll compare your xorg to mine later today and see what differences I have.

I didn't get much time to work on it, life interjected... 
:)

Check the Xorg.0.log file to see whats going on.

---

### Post by jorgitow on 2008-11-11
Oh no no 10-10-20, I have a Samsung Syncmaster LCD like nsquare and renspoesse. I looked at your previous posts where you listed your equipment and tried to compile what would most likely work for that model of monitor. I made sure to use "Configured Video Device" in the "Screen" section because a previous post you made with your xorg.conf used that label for your video device section. If that has changed, you'll need to edit it accordingly. Hope it works!

---

### Post by bvtd092 on 2008-11-11
- After strugling a while with that problem I found the following procedure solving that problem.

- After installing ubuntu 8.10 the system came up with a blank screen.

- CNTRL-ALT-F1

- when you enter the command "ls -l /etc/X11/xorg.conf", bytecount of the file is 0 bytes (empty file).

- check if you have an ATI card with the command: "lspci | grep ATI".
Output from my system:
07:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3870
07:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device

Install available updates
- sudo apt-get update
- sudo apt-get upgrade

Install the following packages:
- sudo apt-get install build-essential
- sudo apt-get install xorg-driver-fglrx

Check if fglrx driver is properly installed with command:
fglrxinfo
Output from my system:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3870
OpenGL version string: 2.1.8087 Release

Create a new xorg.conf file with the following command:
sudo aticonfig --initial
Output of the created file:

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:7:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


After rebooting the system, the gnome desktop was starting up, with the correct resolution 1680x1050 on my Samsung Syncmaster 206BW!

---

### Post by idiotbox9 on 2008-11-12
Hey everyone.

I have had the same issue with the blank screen. I've got a Radeon HD 2400. After reading the thread and taking suggestions others posted, here is what I had to do to get this problem fixed on my machine:

1. Boot Live CD
2. Press F4 and choose "Safe Graphic Mode"
3. Install Ubuntu normally
4. Reboot after install but leave Live CD in drive and boot to it again
5. Press F4 and again choose "Safe Graphics Mode"
6. Choose Boot from first hard drive
7. Boots Ubuntu normally in "Safe Graphics Mode" (Hopefully...)
8. Login and install all available software updates
9. Reboot (Still with Live CD in drive)
10. Repeat steps 5-7
11. Login and install ATI Restricted drivers
12. Remove Live CD and Reboot
13. Success booting Ubuntu???

This is what worked for me so I hope it works for others with the same issue...

---

### Post by 10-10-20 on 2008-11-13
Hi guys, I'm back again.
I still have had no luck with my configuration despite trying a lot of things.
Here's xorg with the monitor specifics loaded as per jorgitow's assistance...

> 
ection "Monitor"
        Identifier      "DELL P791"
        Option          "DPMS"
        HorizSync       30-96
        VertRefresh     50-160
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Device0"
	Monitor		"DELL P791"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024@60" "1024x768@60" "800x600@60" 
"640x480@60"
	EndSubSection
EndSection

# Section "Module"
#	Load	"glx"
# EndSection

Section "Device"
	Identifier	"Device0"
#	Driver	"vesa"
	Driver 	"fglrx"
EndSection

With the fglrx driver loaded, I get the black screen.
I also tried reinstalling the fglrx driver as per bvtd092, but again, the same.
Am I cursed?
Is there actually any bug open in the bug tracker on this issue or am I on my own?

---

### Post by 10-10-20 on 2008-11-13
Oh, I forgot to add that I looked at my Xorg.0.log and this is what I have at the end...

> (--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
(II) fglrx(0): detected X.org 7.4.2.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x10000000
(II) fglrx(0): FBMM initialized for area (0,0)-(2048,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(2048,768) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 2048 x 7423

So, I'm going to try this fix...
[http://www.phoronix.com/forums/showthread.php?t=6062](http://www.phoronix.com/forums/showthread.php?t=6062)

---

### Post by wc4f on 2008-11-28
This isn't a complete fix, but for the people hitting the black screen of video death on bootup, it'll get you past that.

1. Do a "recovery mode" boot, and drop into a root shell.
2. cd over to /usr/lib/xorg/drivers.
3. rename the radeon_drv.so to something else...like unfinished.radeon_drv.so...because that's what it is at least for some Radeon chipsets.

Reboot. Upon reboot X will gracefully degrade to generic vesa since it can't find the (bad) Radeon driver. I've used this on Xubuntu 8.10 with a Radeon 2400 HD, but it probably applies to other ATI stuff, too.

It's not a total fix, but it's a start.

Better solution: buy an Nvidia card. Nvidia hasn't exactly been a posterchild of Open Source support, but I've used their proprietary driver with multiple video cards, on desktops and laptops, running multiple Linux distros and it has -always- worked flawlessly. They at least get their proprietary stuff right. Can't say as much for ATI.

---

### Post by MrMojoRisin on 2008-11-28
Thank you for this thread, it has enabled me to get Ubuntu working on my Dell Dimension 9150 with ATI Radeon 3850 video card.

I installed ubuntu using the Alternate Installer and followed the directions mentioned in this thread to get gnome to load properly. It now works fine. Of course, there is obviously still an issue with the 8.10 live CD in that it does show the nice Ubuntu logo when starting, but fails to start Gnome properly after that. As a side note, to all you ubuntu lovers out there, the live CD of the brand-new Fedora 10 also has the very same issues on my setup.... so at least it is not Canonical's fault I guess but more a Gnome related issue.

Regards,

Michiel

---

### Post by ryseshan on 2008-12-10
For Long time waited for the rectification. 2days back 8th december I re-installed upgrade it went smooth with the display problem.

---

### Post by Rithmarin on 2009-01-05
Here are my experiences with 8.10:

I have a Samsung X22 which uses ATI 2450

Upgraded from 8.04 which totally broke the GUI - spent 4 days trying various removing, reinstalling and reconfiguring fglrx/vesa modes xorg.conf etc. no joy.

Live CD 8.10 does not boot in either normal or safe graphics mode (fine with 8.04)

So I then tried clean reinstall using alternate install CD. On first run after installation no GUI, but I could access terminal.

After running "sudo apt-get update && sudo apt-get -y upgrade" to get the latest updates and a reboot, the GUI appeared. Yay.

Then I installed the restricted ATI drivers. Reboot. GUI. Yay. Works fine with the fancy effects too.

HTH

---

