---
title: "&quot;Cannot Display this Video Mode&quot;"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by Pai on 2007-03-07
Today I was planning to begin on a clean install of Edgy. I am currently running Dapper without any problems.

I popped in my CD (The proper i386) and booted from it.  I was of then of course given the basic options, of which I chose the first: Start or Install Ubuntu. After waiting about a minute, in which the little orange progress bar moved back and forth across my screen, I received a completely blank screen with the centered text: 
"1: Analogue Input 
Cannot Display this video mode"

I next tried to install in Safe Graphics mode, yet this too resulted in the above error.  I believe the CD is fine, as the hash sums matched, the integrity of the disc was fine, and it is the correct version for my specific system.

I assumed this was due to a conflict with my monitor, so I went to the documentation (specifically troubleshooting) which can be found through this link:  [**Dell&#8482; 1704FPT Flat Panel Monitor**]("http://support.dell.com/support/edocs/monitors/1704fpt/EN/index.htm")

[quote=Dell]
One of the following warning messages may appear on the screen indicating that the monitor is out of sync.

1. Analog Input

Cannot Display This Video Mode

This means that the monitor cannot synchronize with the signal that it is receiving from the computer. Either the signal is too high or too low for the monitor to use. See Monitor Specifications for the Horizontal and Vertical frequency ranges addressable by this monitor. Recommended mode is 1280 X 1024 @ 60Hz. [/quote]

This is exactly the error that I got, so next I went to monitor specifications and found the following information:

**Resolution**
Horizontal scan range: 	*30 kHz to 81 kHz (automatic)*
Vertical scan range: 	*56 Hz to 76 Hz (automatic)*
Optimal preset resolution: 	*1280 x 1024 at 60 Hz*
Highest preset resolution: 	*1280 x 1024 at 75 Hz*

**Preset Display Modes**
*Display Mode ||	Horizontal Frequency (kHz) || Vertical Frequency (Hz) || Pixel Clock (MHz) || Sync Polarity (Horizontal/Vertical)*
VESA || 720 x 400 || 31.5 || 70.0 || 28.3 || 	-/+
VESA || 640 x 480 || 31.5 || 60.0  ||	25.2 || 	-/-
VESA || 640 x 480 || 37.5 || 75.0  ||	31.5 || 	-/-
VESA || 800 x 600 || 37.9 || 60.3  ||	49.5 || 	+/+
VESA || 800 x 600 || 46.9 || 75.0  ||	49.5 || 	+/+
VESA || 1024 x 768 || 48.4 || 60.0  ||	65.0 || 	-/-
VESA || 1024 x 768 || 60.0 || 75.0  ||	78.8 || 	+/+
VESA || 1152 x 864 || 67.5 || 75.0  ||	108 || 	+/+
VESA || 1280 x 1024 || 64.0 ||60.0  ||	135.0 || 	+/+
VESA || 1280 x 1024 || 80.0 || 75.0  ||	135.0 || 	+/+

All of the above info came from:
[http://support.dell.com/support/edocs/monitors/1704fpt/EN/solve.htm#Troubleshooting%20Your%20Monitor](http://support.dell.com/support/edocs/monitors/1704fpt/EN/solve.htm#Troubleshooting%20Your%20Monitor)
[http://support.dell.com/support/edocs/monitors/1704fpt/EN/about.htm#Specifications](http://support.dell.com/support/edocs/monitors/1704fpt/EN/about.htm#Specifications)

However, all of that information is essentially meaningless to myself. What do I do with it? What settings need to be changed, and how do I do so? Am I going to have problems running Edgy on this system? 

Thanks in advance.
Please let me know if any other information is needed.

---

### Post by PatrickE on 2007-03-07
Hi,

I think this could help you to set the right/appropriate values for your monitor:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

And this link will help you to get the right modeline for the configuration of your choice:
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

Hope that helps
Patrick

---

### Post by Pai on 2007-03-07
I just went through both of those links, which were helpful, but they didn't solve my problem.

Today I took a photo of the screen I am "stuck" at.

When I installed Dapper I left all of the settings at default, however, when doing the same with Edgy I got the aforementioned error:
"1. Analog Input
Cannot Display This Video Mode"

I tried changing the default from VGA to 1280x1024x32 (as seen in the following photo), which is my monitors optimal resolution according to the specifications.  Instead of ending up with the error message, I saw a garbled mess of the desktop. It was in about 8 tiles, with multiple black lines going through it rendering it useless.  I could vaguely make out the power button in the upper right corner (there were 8 of them, one for each tile), and shut it down from there because it was completely unusable.  Hard to explain, sorry. I have no clue what would be causing this... Suggestions? 

[img]http://img90.imageshack.us/img90/4787/untitledde9.png[/img]

---

### Post by PatrickE on 2007-03-08
Ooops, I should have read your posting more carefully, sorry ;-)

Alright, I think I know what you mean. I had a similar problem with Knoppix on my laptop once (messed up, tiled x display). I think I solved this by adding

```
vga=771
```

as a boot option (the boot command line should be accessible with F6, I think).

You can find several such vga boot options under [http://www.bobpeers.com/linux/mount](http://www.bobpeers.com/linux/mount) , maybe an even lower options helps too...

Good luck
P.

---

### Post by Hervard on 2007-03-30
I'm suffering the same problem, too.

I've got a Dell 24" LCD screen.

Booting from the CD for the first time, I select from the menu to install Ubuntu (I'm using version 6.10).

The screen then changes to a loading bar with a bit bouncing back and forth a few times.

Eventually the loading bar starts filling up from the left side.

Soon after, the screen goes blank, except for a single blinking underscore character.

After a few blinks, my monitor then reports that the frequency it's receiving is out of range.

My monitor would like it to be 1920 x 1200 @ 60 Hz.

What we need is a boot command that changes whatever this unknown resolution and refresh rate is to something we can choose.

I tried vga=711 but that didn't help.

I've tried selecting a resolution from the initial VGA menu (see above photo).

I, among others, appear to be having this problem.

[B]Thank you for the suggestions for editing our config files, but how can we edit config files when we can't even boot up in the first place? All the files are located on the CD.

So please, an extra boot option to change the resolution and refresh rate by pressing F6 and typing in a command would be great.[/B]

Thanks in advance :)

---

### Post by genecaldwell on 2007-04-05
**This is a re-fresh rate problem, not a resolution problem**

I too am having the same exact problem. This problem started for me some 12 months back and has not been resolved since. I do not understand what the linux experts do not understand about this problem, how can you change anything if you do not have any display output ? and if you are trying to install from a CD then how can you edit any files ? 

We need an option to set the refresh rate AS WELL AS the resolution! I however have tested many othe Ubuntu based distros and all seem to have the same problem, leading me to think that its not Ubuntu, or Xubuntu, or even LinuxMint or FluxuBuntu with the problem, it seems to be the kernal, or X or something like that.

I just don't have the time to become a Linux expert just to get it to install, I'd like to get it installed and then try to learn Linux. Can we please get an option that lets us set the refresh rate to what we are being told to use ? I know for a fact that my brand new Dell flat panel uses 1600x1200 @60hz. native. why can't I just chose that ? I get the very same message on my monitor as posted above from both Live CD when booting as well as the "alternate CD" when the GUI starts up after install. It is clear that something other than some safe value is being used. I remember that on earlier versions during the display config screen it actually let me chose my refresh rate and I had no problems then, now that that option has been removed to verify the display output, all kinds of people are having display problems. Just give us the option to confirm what you are going to use for display output.

---

### Post by qneill on 2007-04-05
Ubuntu gurus: Is there a console (text) version of the install?

If not then I think your best bet is to get an old monitor and complete your install, and then configure the X Server after the install is done.

Once your install has completed, see if you can get to a console login with
   Ctl-Alt-F1
and login as root.  Then the "FixVideoResolution" link steps can be followed.

The problem is the **kernel boot parameters are completely separate from the X Server configuration** so I don't think there is a way to change the XServer config during the installation short of cooking your own installation CDs.

Quentin

---

### Post by westsurf on 2007-04-08
Has  there been any updates with this issue?

I was upgrading a Celeron 1000 Mhz from Efty 6.10 to Feisty 7.04. The Feidty upgrade failed, went to clean install 7.04, failed again, went to reinstall 6.10 and "Cannot display this frequency issue".

Funny thing is that this now effects all install versions of Ubuntu :(

for reference,

Celeron 800 Mhz @ 1000
512 Mb RAM
Geforce 5200X.
Tried Dell 2405FPW and LG 17" LCD.

I find this situation incredible. Why has a resolution not been found?
:confused:

HELP!

---

### Post by westsurf on 2007-04-09
Found my own answer.

In order to get GUI so you can proceed with the installation, you will need to edit /etc/X11/xorg.conf

When you get an all black screen, do the following:

Press CTRL+ALT+F1, to get you text mode:

sudo nano /etc/X11/xorg.conf

Locate the [Device] section and add this line to the bottom of it:

Option "MonitorLayout" "LVDS,Auto"

You're done editing. Press CTRL+O to save changes (with nano) or ESC and :wq if you're using vi

Press CTRL+ALT+F7 to get back to the GUI mode followed by CTRL+ALT+BackSpace to restart the X server

From [https://answers.launchpad.net/ubuntu/+ticket/4699](https://answers.launchpad.net/ubuntu/+ticket/4699).

I hope this helps others in the future.

:popcorn:

Any comments to [email]westsurf@gmail.com[/email].

Linux nood movin up :)

---

### Post by Hugmup on 2007-05-27
This is how a problem with Linux always ends. You have to do something while you are not doing it, then wait for the Sunday funnies, find out what cuss words Sarge said to Beetle Bailey, and type them into some sort of shell--if you can find it--making sure to spell @$(# correctly--then framulate the cramistans while flargling. The instructions almost always end with, "And that's all there is to it! Enjoy!" as if you're making brownies. 

("And that's all there is to it"? Imagine if it were complicated!)

And the geeks wonder why Linux hasn't taken over the world. 

Well, this is why.

---

### Post by gineraso on 2007-10-24
Westsurf, your instructions worked perfectly, Thank you.

---

### Post by SouthMan on 2007-10-27
I'm having a very similar problem during an install of 7.10.  It goes through the logo with the moving bar parts then I get the "Cannot Display This Video Mode" error.  I tried the ctl-alt-F1, with no luck.  And yes, I waited until the HDD light went out with still no luck.  Luckily I had a 6.4 cd, so I tried that and it worked fine.

This was an older computer with a couple of hdds that I'm just going to use for a file server, so I may never upgrade to 7.10 on this box.

---

### Post by anchor1te on 2007-11-02
Re: "Cannot Display this Video Mode"
I'm having a very similar problem during an install of 7.10. It goes through the logo with the moving bar parts then I get the "Cannot Display This Video Mode" error. I tried the ctl-alt-F1, with no luck. And yes, I waited until the HDD light went out with still no luck. Luckily I had a 6.4 cd, so I tried that and it worked fine.

This was an older computer with a couple of hdds that I'm just going to use for a file server, so I may never upgrade to 7.10 on this box.


I'm also getting this for xubuntu 7.10 and fluxbuntu 7.10.  Tried the same steps as you with no luck.  Hopefully there is something that can be done.

---

### Post by ghostofcain on 2008-02-24
I have a similar issue, just done a clean install of 7.04 amd64 and although it boots just fine instead of the splash screen i get the black screen with "cannot display this video mode", although as it boots alright this is a niggle for me.

As this occurs during boot, i am assuming it's before X initiates? also i notice from the above post we all appear to be using Dell monitors (mines a 15" e513fp)

---

