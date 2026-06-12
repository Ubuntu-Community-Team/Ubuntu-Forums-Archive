---
title: "Ubuntu 9.10 64 bit install problems on Dell Studio 1558"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by mikevin01 on 2010-02-08
Dell Studio 1558 64bit
Core i5-520M 2.40GHz (2.93Ghz Turbo Mode, 3M cache)
320GB 7200 RPM SATA Hard Disk Drive
4GB Shared Dual Channel DDR3 at 1066MHz
15.6 inch High Definition (720p) LED Display
	1366 x 768
Intel Graphics Media Accelerator HD
Sound Creative Sound Blaster X-Fi MB
Wireless Dell 1520 Wireless-N Card

Dual Boot with Windows 7 using EasyBCD 2.0 that accommodates GRUB2.

Installed Ubuntu 9.10 64 bit  in Safe Graphics mode due to issues with blank screen
/dev/sda5 – boot 120m
/dev/sda6 – swap 7000m
/dev/sda7 – root 14000m



 Sound – fixed with exception of function keys to control volume
	 /etc/modprobe.d/alsa-base.conf
          appended to end:
		 options snd-hda-intel model=dell-m6

	NOTE: Function keys to adjust volume results in screen notification box to blink rapidly. Cursor becomes unresponsive, reboot necessary.

 Wireless - fixed
	 updated proprietary drivers with System/Administration/Hardware Drivers.  Note: this was after updating the system after install.


Brightness – Still an issue, need help
	 /etc/default/grub
         modified line to show:
		GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic" 
	controlled by function keys F4 and F5,  nothing happens.

     NOTE: noapic causes screen to lockup after login and cursor moved	
		

Screen Resolution – fixed, but Boot Splash screen has poor resolution – need help
	/etc/X11/xorg.conf 
		changed Driver “vesa” to Driver "intel"
	
 
Suspend Mode – not working, black screen when wakes up, need help.
Hybernate – seems to work, blank screen on wake up resolved by hitting Enter key.


Current summary of issues;
   Function keys to control brightness keys not working
   Function keys to control speaker volume “goes crazy”
   Suspend mode awakes to blank screen.
   Boot splash screen resolution degenerated.


Any help or insight is much appreciated!

---

### Post by mörgæs on 2010-02-09
You have a lot of questions, and it is not easy to answer them all in one, especially with such little background information.

I would recommend that you focus on the problems one by one. Best is if you could try another Ubuntu, for example 9.04 or 10.04 (alpha) 32 bit, and post the results for comparison (if there isn't any advice already on Ubuntuforum).

[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by mikevin01 on 2010-02-09
I agree!  In process now of downloading 32 bit 8.1 and 9.04 just to see how it goes.
If one of them 'works out', I may be able to extract parameters to incorporate into 64 bit 9.1. 
Otherwise, I'm stuck with Windows 7 until a new version of Ubuntu comes out that works with this box.

Thanks again
Mikevin01

---

### Post by mörgæs on 2010-02-09
> **mikevin01 said:**
> 
Otherwise, I'm stuck with Windows 7 until a new version of Ubuntu comes out that works with this box.



Perhaps 10.04 is that version :-) It is actually pretty stable, at least on my machine, though it is an alpha. Well, try a few of them and let us hear the result.

---

### Post by mikevin01 on 2010-02-09
Will do! Glad to hear 10.04 has been stable. Just bought a pile of new disks for installing 10.04 64 and 32 bit. Hopefully won't have to go too far to get the new Dell up to speed.  :)

---

### Post by mikevin01 on 2010-02-13
Update:
Installed 10.04
Resolution fixed
Sound fixed
Short evaluation using live cd.
During this evaluation, Proprietary drivers recognized for wireless.

Did an install as mentioned above partition layout.
Connected to Internet - hard wire - 
Tried to install proprietary drives for wireless - nothing to select from.
As though what you see on the live cd, is different from what you get on install. Another example is the live cd has gparted partition manager, but that's gone on install too.

After install, blank screen again, fixed using nolapic as mentioned above.
Updates, first one totally 'jacked up' the system.
Resolution was to select safe mode - repair broken packages, reboot again into safe mode to fix the nolapic line in /etc/default/grub.

Another update, now the update proprietary hardware shows something, installed, now able to connect wireless.

Still unable to adjust brightness using the F4 / F5 keys.
Sound adjustment using F7 8 and 9 keys still causes the box thingy to blink crazy and lock the ability for the cursor to select anything, except to select reboot / shutdown after ctl alt del.

So... now back at same point I was in on 9.10. The new version seems to have fixed the resolution and sound issue. Hopefully, the function key problems will be resolved in the near future.

Regards

Mikevin01

---

### Post by putxi on 2010-02-15
> **mikevin01 said:**
> Update:
Installed 10.04
Resolution fixed
Sound fixed


Great!

I've the same box and almost ready to change win7 for ubuntu (first i need an stable version on my desktop, which recently crashed - working on that!).

Which 10.04 version: 32b or 64b?

Regards,
jordi

---

### Post by putxi on 2010-02-16
> **putxi said:**
> Great!

I've the same box and almost ready to change win7 for ubuntu (first i need an stable version on my desktop, which recently crashed - working on that!).

Which 10.04 version: 32b or 64b?

Regards,
jordi

SOLVED!

I've seen that in 10.04 there is no 64bit yet.

And it seem that for laptop there's an additional packet to adapt desktop to laptop (energy mng, ...): [this one]("http://packages.ubuntu.com/lucid/laptop-mode-tools").

---

### Post by mikevin01 on 2010-02-17
On this dell 1558, I installed ubuntu 10.04 64 bit from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/).

I'm able to "get by" with the bright screen and being careful not to hit the speaker function keys, or try to go into suspend mode. Until a more stable version is available, I'll have keep the dual boot setup with Windoz 7.

---

### Post by mörgæs on 2010-02-17
> **mikevin01 said:**
> On this dell 1558, I installed ubuntu 10.04 64 bit from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/).

I'm able to "get by" with the bright screen and being careful not to hit the speaker function keys, or try to go into suspend mode. Until a more stable version is available, I'll have keep the dual boot setup with Windoz 7.

Good to hear that it worked - more or less.
If (when) bugs appear, you are welcome to report them at

[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

The developers are very responsive to 10.04 bugs reports.

---

### Post by putxi on 2010-02-17
> **mikevin01 said:**
> On this dell 1558, I installed ubuntu 10.04 64 bit from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/).

I'm able to "get by" with the bright screen and being careful not to hit the speaker function keys, or try to go into suspend mode. Until a more stable version is available, I'll have keep the dual boot setup with Windoz 7.

Thanks!

I had tried with the 32b version of alpha2 release site, but i guess it might be better use the daily current.

Now i'm downloading de current 64b.

Using the 32bit i have got stucked with the frozen login screen problem.
The process i've done is the one you suggested:
- update using synaptic.
- hardware drivers: activate both b43 (free) and sta (propietary) - i've done one behind the other, but haven't succeed with wireless setup!
- while rebooting, i've got the black screen.
- recovery mode and update grub line adding nolapic (also tried noapic).
- reboot and now reaches the login screen. i can enter pwd, but after "enter", FROZEN!
- reboot, login screen, and after "enter" on user, FROZEN! 

Although being 32b and not 64, it is quite similar to the results you obtained, **mikevin01**.

Can you give me some more details on how you solved the black screen and wireless, so that i can use them with 64b installation?

Thanks again!

Regards,
jordi

Btw, i use grub 'cos have windows 7 in an other partition ...
i didn't want to change the hd setup done by DELL (it seems there is a partition for their use ... maintaninance?).

---

### Post by putxi on 2010-02-17
Btw,

After installing version Lucid 32b Alpha, just at the end, i got this error message window:

[COLOR="Blue"]2ubi-migrationassistant failed with exit code 141. Further information may be found in /var/log/syslog.
[/COLOR]
I've not look at this file, yet ...

Then i could restart and everything went ok (as said on just previous post), until i installed wireless drivers and restarted ...

But anyone has more information about the meanig and consquences of this FATAL message ???

---

### Post by mörgæs on 2010-02-17
Here is some more information on the 141-error:

[http://ubuntuforums.org/showthread.php?t=1402704](http://ubuntuforums.org/showthread.php?t=1402704)

In general, if you guys are digging deeper in 10.04, the forum 'Lucid Lynx Testing and Discussion' is worth studying.
[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

---

### Post by mikevin01 on 2010-02-17
putxi

for the black screen thingy, on the boot screen I selected the safe mode log in option, then vi /etc/default/grub to show GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic" and then made sure /etc/X11/xorg.conf was changed from Driver "vesa" to Driver "intel".
Then, connected to internet w/ cat 5, and selected Hardware Drivers that show the proprietary drivers available - selected both to install, wireless then worked. 
Also, if you have a brand new 1558, the BIOs will have to be upgraded. Fan doesn't work after startup, unit overheats, shuts down crashing everything, works ok after that. The guys at Dell supprt fixed it for me - warranty - via remote, did a good job!
Good Luck !

---

### Post by mörgæs on 2010-02-18
It seems that a lot of experience about the Dell 1558 is forming here. Do you feel like writing a short review on [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/) ?

---

### Post by putxi on 2010-02-18
> **mikevin01 said:**
> 
Also, if you have a brand new 1558, the BIOs will have to be upgraded. Fan doesn't work after startup, unit overheats, shuts down crashing everything, works ok after that. The guys at Dell supprt fixed it for me - warranty - via remote, did a good job!
Good Luck !

Yes, i received de 1558 just 10 days ago.
It haven't crashed, yet, but the box doesn't get "hot".
How did you realised about that: temperature warning? box hot? didn't hear the fan? ...

If it's on the bios that fan problem, then it happens with ubuntu and windows? Or only ubuntu ?
Using windows, it keeps showing-up dell update news ..., perhaps some of them are from bios?

Before calling them i'd like to know a bit more about this?

Thanks!
jordi

---

### Post by putxi on 2010-02-18
> **mikevin01 said:**
> putxi

for the black screen thingy, on the boot screen I selected the safe mode log in option, then vi /etc/default/grub to show GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic" and then made sure /etc/X11/xorg.conf was changed from Driver "vesa" to Driver "intel".
Then, connected to internet w/ cat 5, and selected Hardware Drivers that show the proprietary drivers available - selected both to install, wireless then worked. 


Thanks!
Yestarday, after seeing you had used 64bit, i changed the 32b to 64b too, so that we could compare accordingly.

The black screen problem doesn't apper, by now.
What i was most afraid of was the **frozen login screen** or even the desktop ... ](*,)

The only thing i did after installing, was updating packets from synaptic. And then, i started copying my backup data to the system, in order to use it, even on limitated conditions.
I rebooted 2/3 times, and no problem.

But today, at the first boot early in the morning, again [COLOR="Purple"]**FROZEN**[/COLOR] (when i press some key, soon or late, ... or with the "enter")!
I've modified the grub file (following your indications), with these combinations:
- adding nolapic
- adding noapic
- adding nolapic and noapic

Eachtime, i updated the grub.cfg using the update-grub command.

But no way! I don't know how to fix it ...
And what is worse, i've to work using windows ](*,)

Any idea?

Thanks in advance. O:)
jordi

---

### Post by putxi on 2010-02-18
mörgæs, thanks for the info on 141-error ;)


> **mörgæs said:**
> It seems that a lot of experience about the Dell 1558 is forming here. Do you feel like writing a short review on [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/) ?

It seems a good idea! I'd wait until more info is collected, ...
until now, i still haven't been able to use Lucid over Dell (frozen, ...) ...
But hopefully soon i will.

Most of these low-level linux is new for me, but collaborating with mikevin01 we could wrap up all this on a report.

Until then, this post could be the reference for 1558.

Regards,
jordi

---

### Post by Mechaphoenix25 on 2010-02-24
Hi, I'm a fellow 1558 owner, and on a clean install of Karmic I've fixed or worked around most of these issues myself.  

I got the ATI Mobility Radeon 4570 card instead of the built in Intel GMA, and my brightness keys work fine out of the box, but before I tried them (after reading issues of this laptop before buying) I used the gnome-panel brightness app.  Works like a charm for me.

Also, I use the lock-keys-applet to show cap-lock on the screen, since there's no indication of it on the computer.  Get it by doing the following in a terminal:
```
sudo apt-get install lock-keys-applet
```

As far as suspend goes, I've found linux suspend on dell laptops in general to be VERY hit-or-miss, with it breaking or fixing itself sometimes on a monthly basis.  With the ATI proprietary drivers, suspend and hibernate both work flawlessly, but for those of you on the Intel chipset, you may want to try a tactic I used for a while.  Press alt+ctrl+f1 to switch to a VT, log in as yourself, then run
```
sudo pm-suspend
```That way your video drivers won't have to resume X, just a VT.  When you pull the computer back up, just press alt+ctrl+f7 to return to your normal desktop.  It may or may not work, but it's worth a shot.

Boot splash resolution can be improved slightly, install the following and it will allow you to edit your grub configuration without having to manually edit raw system files.  
```
sudo apt-get install startupmanager
```[COLOR="Red"]IMPORTANT: DO NOT SELECT A RESOLUTION FOR THE BOOTLOADER THAT IS BIGGER IN **ANY** DIMENSION THAN YOUR PRIMARY REAL DISPLAY[/COLOR]
I cannot stress this enough, it will render your Linux partition unbootable, and rescuing it is a royal pain.  The splash will still be distorted (as I've yet to find a way to get GRUB to go widescreen) but it'll probably look less grainy.

The only really big problem I've had thus far is the volume keys making the display flash and requiring a reboot.  It seems to me like the keyboard is detecting the key being pressed down, but not the key being released.  I think this is making the key repeat forever, and the display keep flashing, preventing system use.

Any ideas on how to turn off key-repeat for a specific set of keys?

---

### Post by aharown07 on 2010-02-26
**WiFi connects w/zero signal strength**

Just got my 1558 today. The plan was to go w/32 bit 9.10 (actually Mint 8 ) & pae for access to the additional ram.

So maybe this belongs in a different thread (not using 64b--yet), but... I'm not clear on how you got the wifi to work. My adaptor is the one they call "Dell Wireless 1520 802.11n Half Mini Card"  ... Broadcom, but I'm not sure what model.

I enabled the proprietary driver that showed up in the list, and the wifi claims to have connected (I had to put the connection in manually, though. It didn't "see" the network), but the signal strength doesn't show at all and there's no web access.

Elsewhere I've read about installing backports. Is that a good idea?

---

### Post by burhangondal on 2010-02-28
Hello, 

I didnt read through the whole thread but i did read the first few posts. I have the exact model as OP (Dell Studio 1558 ) with exactly same specs but with ATI RADEON HD 4570 512MB video card. I had no blank screen issue as drivers were available in the restricted hardware section for video card and wireless card. However, i did have problem with sound and i couldn't make it work after trying to many things.Then, i finally uninstalled it because no point without sound but i just read OP's post and i m thinking of reinstalling it and adding that sound line. Also, i have a problem with my volume control buttons as i use them my keyboard disables i mean stops working exactly as OP.....so pretty much everything else was working but sound....i had no problem with video at all neither with internet....but only with SOUND but i think i m gonna fix that too as i follow what OP did.....thanks :D

Here is my setup just in case developers can look at it :D

SYSTEM INFORMATION
Computer Manufacturer:	Dell Inc.
Computer Model:	Studio 1558
Operating System (O/S):	Microsoft Windows Vista Home Premium Edition Service Pack 2 & Windows 7 ( dual booted )
Operating System Build (O/S):32-bit - 64 bit
Operating System (version):	------
System RAM:	4.0 GB
CD or DVD Device:	HL-DT-ST DVD -RW GA31N

System Hard Drive Overview
System Total Storage size:	500 GB AHCI

GRAPHICS INFORMATION
Graphics Product:	ATI Mobility Radeon HD 4570
Video Memory:	1.7 GB

[B]SOUND INFORMATION
IDT High Definition Codecs 92HD7C31 <------ ONLY THIS DOESN'T WORK[/B]

MOTHERBOARD INFORMATION
Manufacturer:	Dell
Model:	Intel HM55
AA Number:	not detected
BIOS Vendor:	Dell Inc.
BIOS Version:	A03
BIOS Release Date:	01/08/10
System Memory:	4.0 GB
Sound Card:	ATI High Definition Audio Device

PROCESSOR INFORMATION
Manufacturer:	GenuineIntel
Model:	Intel(R) Core(TM) i5 CPU M 520 @ 2.40GHz
Intel® Processor analysis tools	Additional tools
CPU Speed:	2.39 GHz
Link to Processor Spec Finder:	Intel(R) Core(TM) i5 CPU M 520 @ 2.40GHz

WIRED NETWORKING INFORMATION
Wired Networking Product:	Realtek


WIRELESS NETWORKING INFORMATION
Wireless Networking Product:	Dell Wireless-N Mini 1520

---

### Post by aharown07 on 2010-02-28
burhangondal,
I've been unsuccessful getting my wifi to work in 32bit (adapter appears and sees networks--sometimes--even reports a connect, but no actual moving of data and signal strength shows zero)

Did you test your wifi much? Were you using 32bit Ubuntu or 64bit? 

Attempted 64 bit install yesterday and all went well until I downloaded updates, then enabled drivers.. on reboot: black screen. So broke it somehow.

---

### Post by burhangondal on 2010-02-28
well i tested in 32B and 65B...no difference...mine works like krazy...did u install it through restricted hardware drivers? it should work....if not then download wcip...more graphical interface

---

### Post by aharown07 on 2010-03-01
OK, redid the 32b and this time wireless is fine. The only thing I did differently, as far as I can tell, is install the Broadcom driver *before* the ATI rather than at the same time or after.
So I'm not sure what's up with that. But working slick now. 
Next... get sound working!

---

### Post by Mechaphoenix25 on 2010-03-02
I did an experiment to see if I could get the volume keys working, with limited success.  If you turn off key repeat in your keyboard preferences, the volume indicator no longer gets stuck flashing and the system no longer needs a reboot to stay functioning.  However, this still doesn't make the volume keys work (more than once anyway) and is a general pain for those of us who need key repeat.  Any ideas on how to automatically generate a "key released" code for the volume keys?

---

### Post by mörgæs on 2010-03-02
> **Mechaphoenix25 said:**
> I did an experiment to see if I could get the volume keys working, with limited success.  If you turn off key repeat in your keyboard preferences, the volume indicator no longer gets stuck flashing and the system no longer needs a reboot to stay functioning.  However, this still doesn't make the volume keys work (more than once anyway) and is a general pain for those of us who need key repeat.  Any ideas on how to automatically generate a "key released" code for the volume keys?

There are a number of bugs describing more or less this problem in Launchpad, for example:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/293642](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/293642)

If you can confirm this in Launchpad for 10.04 and Dell Studio 1558, it would be great.

---

### Post by mörgæs on 2010-03-02
> **aharown07 said:**
> Next... get sound working!

Are you on 10.04?

---

### Post by aharown07 on 2010-03-02
> **mörgæs said:**
> Are you on 10.04?
Yes. Actually Mint8, which is mostly Ubuntu 10.04.
Have sound working now. The solution in the OP does work for playback. Haven't tested recording yet (for Skype, etc.)

> /etc/modprobe.d/alsa-base.conf
appended to end:
options snd-hda-intel model=dell-m6
No ideas yet on how to make the vol. control hotkeys work right.

FYI, for anyone looking considering buying a 1558. Summary of what works in Ubuntu 10.04 & Mint 8 if you have the ATI graphics card.
[list]
[*] Screen brightness control buttons (with or without the ATI propriety driver)
[*] Fan operation (seems to run constantly at top speed unless the ATI propriety driver is installed. Then it works like a charm)
[*] Suspend/Wake (No problems. Haven't tested "hybernate"...never use that.)
[*] Touchpad (No issues. Default settings pretty much fine for me, though did tweak motion speed a little)
[*] WiFi (Works fine if you have the 1520 card and install Braodcom proprietary driver. I had trouble until I did a fresh install then enabled the Broadcom driver and rebooted before enabling the ATI driver)
[*] Sound (playback works fine after adding line to alsa-base.conf)
[*] Eject key (no issues)
[*] Sound mute toggle key (no issues)
[*] Wifi enable/disable key (**turns wifi off, but turning back on seems to be iffy... maybe just slow**[/list]

All in all, I'm happy with this unit, though the super-high resolution LCD is taking some getting used to (may need new glasses!)

---

### Post by Mechaphoenix25 on 2010-03-02
I've found the solution to the volume key problem!  it's here, drvista did a revised version of the fix for Jaunty, it now works in Karmic.  
[http://ubuntuforums.org/showthread.php?t=974723&page=6](http://ubuntuforums.org/showthread.php?t=974723&page=6)

[COLOR="Red"]YOU MAY WANT SAVE/BACK UP BEFORE TRYING IT[/COLOR]
when I did it, my screen/keyboard/mouse/everything froze, had to do a hard reboot.  Works like a champ now though :)

---

### Post by mörgæs on 2010-03-02
> **aharown07 said:**
> 
FYI, for anyone looking considering buying a 1558. Summary of what works in Ubuntu 10.04 & Mint 8 if you have the ATI graphics card ... 

Congratulations. Do you feel like writing a summary on [http://www.ubuntuhcl.org](http://www.ubuntuhcl.org) ?

---

### Post by janderpola on 2010-03-03
Hi all, i have the same Dell 1558 but with an Intel Wireless 6200, that doesn´t work on Karmic but works on Lucid (also sound works on Lucid for me). 

The problem is... as aharown07 says, Fan operation without the propietary ATI driver is constantly at top speed, but how to enable it in Lucid???

Lucid have Xorg 1.7.5 and there are no Catalyst driver for that... so how to enable it?

Rest of the things worked fine for me (except volume keys).

---

### Post by mörgæs on 2010-03-04
> **janderpola said:**
> Fan operation without the propietary ATI driver is constantly at top speed, but how to enable it in Lucid???

Lucid have Xorg 1.7.5 and there are no Catalyst driver for that... so how to enable it?


I guess you will get the best answers if you post in 
[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

---

### Post by aharown07 on 2010-03-04
> **mörgæs said:**
> Congratulations. Do you feel like writing a summary on [http://www.ubuntuhcl.org](http://www.ubuntuhcl.org) ?

Yeah, I'll go over there.

I am having trouble implementing the volume control key fix linked to a couple of posts ago. When I get to step 2...
> sudo apt-get source xserver-xorg-input-evdev
The result is...
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list

Don't know what to add to my sources.list

---

### Post by janderpola on 2010-03-04
> **mörgæs said:**
> I guess you will get the best answers if you post in 
[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

Ok, i´ll go there. :$

Thanks! (Again)

---

### Post by mörgæs on 2010-03-04
> **aharown07 said:**
> 
Don't know what to add to my sources.list

Most users only care about installing pre-compiled (binary) packages, when they search for new applications. This is faster and easier than downloading the source code and compile. However, you need the source code for this fix.

If you go to System > Administration > Software sources (or something like that - I use a Danish Ubuntu, so I don't know the wording for sure), can you then enable source code in the repositories?

If the system does not do it by itself, you need to reload the package list after this.

---

### Post by aharown07 on 2010-03-04
I think I've got it now. Wasn't working because I'm in Mint and it doesn't have the Ubuntu "source code" box. Just a Mint one... which doesn't seem to have evdev.

Anyway, this seems to be working:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

---

### Post by mörgæs on 2010-03-05
I noticed that you are downloading from the Hardy Heron repository. I am just curious... is this on purpose?

Thanks for contributing to [www.ubuntuhcl.org]("http://www.ubuntuhcl.org")

---

### Post by aharown07 on 2010-03-05
> **mörgæs said:**
> I noticed that you are downloading from the Hardy Heron repository. I am just curious... is this on purpose?

Thanks for contributing to [www.ubuntuhcl.org]("http://www.ubuntuhcl.org")

Got a bit sloppy on the cut and paste there. Actually, what I'm using replaces "hardy" with "karmic"... so it's really
> deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

---

### Post by aharown07 on 2010-03-08
I'm having problems implementing the evdev stuck keys fix.
But did discover that it is possible to reassign vol up and vol down using the keyboard shortcuts tool (I picked mod4+up and mod4+down). Works on my system.

---

