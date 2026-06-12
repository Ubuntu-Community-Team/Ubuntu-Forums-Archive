---
title: "Unable to load LiveCD - Ubuntu 11.10"
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by laicepsydobon on 2011-11-15
HARDWARE:  

 Computer: HP Pavilion HPE h8-1114 PC 

Graphic card: NVidia GeForce GT 520 HDMI out 

 Monitor: Samsung Syncmaster S27A550H (500 series 27&quot; monitor) HDMI in  

    MEDIA:  .iso burned from ubuntu-11.10-desktop-i386.iso (md5sum OK) at 16x (lowest speed available) on Dell Inspiron 530  

    PROBLEM:  Insert disc in HP and boot.  Splash screen comes up with the &quot;loading&quot; dots working.  After an unknown amount of time the screen begins to deteriorate, then goes black with a cursor centered and flashing at about a 3 second cycle.  Any thoughts?

---

### Post by Mark Phelps on 2011-11-15
That sequence is the start of the boot ... so how long did you wait before shutting off the PC?

Asking, because boot times in the 11.x series have become long, especially from the CD.  Several minutes is not unusual.

---

### Post by laicepsydobon on 2011-11-15
I believe it was only about 3 minutes.  I'll let it run longer, and come back if I still have problems.  Thank you.

---

### Post by laicepsydobon on 2011-11-15
Results of attempt to boot Ubuntu 11.10 LiveCD 

10:46 Insert Ubuntu LiveCD and boot the system[FONT=monospace].  Ubuntu splash screen with color changing dots appears. [/FONT]
10:56 Screen flashes between cursor and vertical bars at 1 second intervals.
10:58 Screen goes blank with background glow.
11:07 Screen goes black (no background glow).
11:08 Perhaps a screensaver?  Wiggle mouse to determine.  Blank screen with background glow returns.
11:18 Shut-down, since there's been no change since the last time tick.
  
Looks like it didn't work.  :confused:

---

### Post by 2F4U on 2011-11-15
Try to add **nomodeset** to the kernel boot parameters.

---

### Post by laicepsydobon on 2011-11-15
How?  This is the LiveCD.  I wasn't aware that one could get into the boot parameters on a LiveCD.

EDIT:  Nevermind.  I found it at [http://ubuntuforums.org/showthread.php?t=1613132&highlight=livecd+kernel+boot+parameters](http://ubuntuforums.org/showthread.php?t=1613132&highlight=livecd+kernel+boot+parameters) .  Now seeing how it will go.

EDIT 2:  Fail.  Will try adding acpi_osi= to see if it's because it was originally an installed Windows 7 machine (I never ran it in Windows).

EDIT 3: Fail.  I was able to get into a terminal an vi some of the logs.  syslog ended with ten (10) segfaults and 2 dropped frames from ieee80211.

---

### Post by MAFoElffen on 2011-11-15
> **laicepsydobon said:**
> HARDWARE:  

 Computer: HP Pavilion HPE h8-1114 PC 

Graphic card: NVidia GeForce GT 520 HDMI out 

 Monitor: Samsung Syncmaster S27A550H (500 series 27&quot; monitor) HDMI in  

    MEDIA:  .iso burned from ubuntu-11.10-desktop-i386.iso (md5sum OK) at 16x (lowest speed available) on Dell Inspiron 530  

    PROBLEM:  Insert disc in HP and boot.  Splash screen comes up with the &quot;loading&quot; dots working.  After an unknown amount of time the screen begins to deteriorate, then goes black with a cursor centered and flashing at about a 3 second cycle.  Any thoughts?
With that card and the LiveCD...

Boot > First screen is black with a person/keyboard Icon at the bottom. Press escape. > That will get you to a low res. Language selection screen. Press escape or enter... > You will not be at the Advanced Installtion Menu where it gives you the menu items Try, Install, Check disk, Test memory, Boot from disk... > Press F6. A drop down menu with kernel boot otion will appear. Arrow down until "nomodeset" is highlighted. > Press the spacebar to select. > Press escape to exit that menu > Select the "Try" menu item.

If you install, install from the Live image desktop... When the installation options menu shows up, make sure you select "Download Updates while installing" and "Install Third party sofware"... This may pickup your video drivers or not.  

If not, you'll get a black screen on reboot after install. If it does that, reboot > Hold the shift key down. At the Grub Menu, select the Rescue Menu item > Select safe mode > At the Desktop, click on the username (upper right) > System settings > Additional Drivers > Nividia current > Activate.

Hope that info helps.  Tell me how it goes.

---

### Post by laicepsydobon on 2011-11-16
Tomorrow.  Unfortunately, I have an appointment tomorrow morning at 9:30 AM (UTC-7) for hearing aids (my first) and I don't know how long it will take.  Hopefully, I can do something before 12:00 PM (UTC-7) and will get back to you.

Thanks for the response (actually, thank all of you for your responses.  I do appreciate it).

---

### Post by laicepsydobon on 2011-11-16
> **MAFoElffen said:**
> With that card and the LiveCD...

Boot > First screen is black with a person/keyboard Icon at the bottom. Press escape. > That will get you to a low res. Language selection screen. Press escape or enter... > You will not be at the Advanced Installtion Menu where it gives you the menu items Try, Install, Check disk, Test memory, Boot from disk... > Press F6. A drop down menu with kernel boot otion will appear. Arrow down until "nomodeset" is highlighted. > Press the spacebar to select. > Press escape to exit that menu > Select the "Try" menu item.

If you install, install from the Live image desktop... When the installation options menu shows up, make sure you select "Download Updates while installing" and "Install Third party sofware"... This may pickup your video drivers or not.  

If not, you'll get a black screen on reboot after install. If it does that, reboot > Hold the shift key down. At the Grub Menu, select the Rescue Menu item > Select safe mode > At the Desktop, click on the username (upper right) > System settings > Additional Drivers > Nividia current > Activate.

Hope that info helps.  Tell me how it goes.

The following is what happened following your instructions (time ticks are not exact due to time necessary for me to write things down):

11:41 - Insert disk - Boot - Hit ESCAPE - Select language - F6 - Select nomodeset - Hit ESCAPE.  (NOTE - I have already done this part before and have NOT gotten the Desktop.  Results were as indicated in #4, above)

11:46 - Install from Low-Res screen menu (since I couldn't reach the desktop before, I changed the instruction with the hopes that it would go to another Low-Res screen)

11:49 - Same results as in #4 above.  

Sorry, it didn't work.

---

### Post by MAFoElffen on 2011-11-16
> **laicepsydobon said:**
> The following is what happened following your instructions (time ticks are not exact due to time necessary for me to write things down):

11:41 - Insert disk - Boot - Hit ESCAPE - Select language - F6 - Select nomodeset - Hit ESCAPE.  (NOTE - I have already done this part before and have NOT gotten the Desktop.  Results were as indicated in #4, above)

11:46 - Install from Low-Res screen menu (since I couldn't reach the desktop before, I changed the instruction with the hopes that it would go to another Low-Res screen)

11:49 - Same results as in #4 above.  

Sorry, it didn't work.
Here we go...
- At boot, hold down shift key, Grub Menu should come up...
- Press "e" key, that should put you into an edit mode.
- Arrow Down to the Line that starts with "linux", that is the kernel Boot line.
- Arrow Right to where is says "quiet splash vt.handoff=7"
- Replace that text with "--verbose single"
- Press <cntrl><x>, It will boot with those options.

That will boot into a TTY Text Console. Login.
```

sudo apt-get update
sudo nvidia-installer --uninstall
sudo apt-get remove nvidia-*
sudo apt-get install 'uname -r'
sudo apt-get install nvidia-current  
sudo nvidia-xconfig  
sudo echo RUN+="/sbin/modprobe nvidia" > /etc/udev/rules.d/90-modprobe.rules
sudo echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf[FONT=monospace]
[/FONT]sudo update-initramfs -u
sudo reboot

```

Tell me how it goes.

---

### Post by laicepsydobon on 2011-11-16
MAFoElffen,

I'm having trouble parsing your suggestion (not that I'm a programmer, but I know a bit about logic).  You start out with dropping into grub edit, which is fine.  You then close with "Press <cntrl><x>, It will **boot** with those options". (emphasis mine)  That's OK if it simply continues the boot sequence.

Let's presume, for the moment, that it does continue from there, as I see that as a valid possibility.  But then we come to the next section where I'm dropped into the terminal.

In the terminal you have me using apt-get to get a bunch of things including nvidia current.  I believe the current NVidia driver is 195.36.31-x.  The card in the computer is NVidia GeForce GT 520, which requires **at least** 275.28.x.  I've already run into that problem with Debian Wheezy.  There is no .deb for anything above 195 in the repositories.

The next problem is the nvidia-xconfig.  Now, maybe it's different with Ubuntu 11.10, but in Wheezy the system finds fault with the xorg.conf file created by NVidia and refuses to use it.

However, the worst comes at the end:  "sudo reboot".  I'm working off a LiveCD.  Wheezy is on partition 1 (in VERY Low-Res).  Removing the disc from the CD tray would defeat the whole purpose of going through this.  Leaving the disc in the tray means that I would be **rebooting** off the LiveCD, and all the changes would be eliminated.

Am I wrong?

---

### Post by MAFoElffen on 2011-11-17
> **laicepsydobon said:**
> MAFoElffen,

I'm having trouble parsing your suggestion (not that I'm a programmer, but I know a bit about logic).  You start out with dropping into grub edit, which is fine.  You then close with "Press <cntrl><x>, It will **boot** with those options". (emphasis mine)  That's OK if it simply continues the boot sequence.

Let's presume, for the moment, that it does continue from there, as I see that as a valid possibility.  But then we come to the next section where I'm dropped into the terminal.

In the terminal you have me using apt-get to get a bunch of things including nvidia current.  I believe the current NVidia driver is 195.36.31-x.  The card in the computer is NVidia GeForce GT 520, which requires **at least** 275.28.x.  I've already run into that problem with Debian Wheezy.  There is no .deb for anything above 195 in the repositories.

The next problem is the nvidia-xconfig.  Now, maybe it's different with Ubuntu 11.10, but in Wheezy the system finds fault with the xorg.conf file created by NVidia and refuses to use it.

However, the worst comes at the end:  "sudo reboot".  I'm working off a LiveCD.  Wheezy is on partition 1 (in VERY Low-Res).  Removing the disc from the CD tray would defeat the whole purpose of going through this.  Leaving the disc in the tray means that I would be **rebooting** off the LiveCD, and all the changes would be eliminated.

Am I wrong?
Yes, you are wrong... nvidia-current is presently 285.x or 270 series... running out door for day. Back laters.

---

### Post by MAFoElffen on 2011-11-17
> **MAFoElffen said:**
> Yes, you are wrong... nvidia-current is presently 285.x or 270 series... running out door for day. Back laters.

Next thing I noted was when you said you were working off the LiveCD The instructions I gave you were HowTos on fixing your system from your crippled system...

You have to be attached/mount to your installed system to able to install drivers.

If you prefer to do it from a LiveCD, it is more work but it can be done.  Follow the instructions at the bottom half of this post to mount a system from a LiveCD:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Mounting An Installed System From the LiveCD]("http://ubuntuforums.org/showpost.php?p=10740097&postcount=3")**[/SIZE][/COLOR][/SIZE][/COLOR]

Then install your drivers.  They will install to the mounted system (your install).

---

### Post by laicepsydobon on 2011-11-17
I think we're working at cross-purposes, here.  I don't have a crippled system.  Ubuntu never installed because the boot process broke (stopped without a clean halt).  There was nothing there to boot from.  This has happened every time I've tried to either run the LiveCD OR install once it's past the Low-Res menu screen.

I appreciate your help and attempts to find work-arounds for me, but at this time I have to feel that it's just not going to happen.  I think there may be some sort of conflict between the equipment I've got and the processes and decisions made in the initial boot process.

I'll have to see if I can figure out where those conflicts are then maybe I can get back to you.

Thanks again.

---

### Post by MAFoElffen on 2011-11-18
> **laicepsydobon said:**
> I think we're working at cross-purposes, here.  I don't have a crippled system.  Ubuntu never installed because the boot process broke (stopped without a clean halt).  There was nothing there to boot from.  This has happened every time I've tried to either run the LiveCD OR install once it's past the Low-Res menu screen.

I appreciate your help and attempts to find work-arounds for me, but at this time I have to feel that it's just not going to happen.  I think there may be some sort of conflict between the equipment I've got and the processes and decisions made in the initial boot process.

I'll have to see if I can figure out where those conflicts are then maybe I can get back to you.

Thanks again.
Noted.

Curious- So you don't know if you even have a working system...Like a booting kernel or the xorg server. You probably don't have Grub as it is the last to install before the install process finsihes. Is it consistent in where in stops?  If you install from the LiveCD "Try" desktop, then when it errors out, you can read the syslog and see what happened... The installer would be locked up, but the rest of the system is still working.

---

### Post by laicepsydobon on 2011-11-20
> **MAFoElffen said:**
> Noted.

Curious- So you don't know if you even have a working system...Like a booting kernel or the xorg server. You probably don't have Grub as it is the last to install before the install process finsihes. Is it consistent in where in stops?  If you install from the LiveCD "Try" desktop, then when it errors out, you can read the syslog and see what happened... The installer would be locked up, but the rest of the system is still working.

I was never able to get to a terminal on the "Try" on the LiveCD.  However, I've replicated it on Wheezy.  The break-point is the GDM.  "WARNING: GdmDisplay: display lasted 0.079983 seconds" (Time varies but is approximately the same, and repeats until the system is killed) (quoted from the Wheezy Syslog from an attempt I made at adding an xorg.conf file to the mix).  In Wheezy it occurred whenever I attempted to add an xorg.conf file (/etc/X11/exorg.conf). including the one from the NVidia 290 proprietary driver.  

As it stands right now, that computer is limited to 800 X 600 resolution.  If I could even get VESA to accept a higher resolution (such as 1280 X 1024) I could live with it until Linux catches up with the new hardware.  But so far even attempting to force the boot sequence at the grub menu hasn't worked (vesa=795).  If I could get that far, then I could use Samba to transfer files from one computer to the other.

With Wheezy installed (different installer than Ubuntu) I am at least able to reboot and choose "Recovery", and log in as root and move the file to a .bak file, and/or make changes in vi IYEEECHT!!!).  At least I still remember how to get around vi, though it's been years.  It's better than EDLIN, though only just.  :)  I don't have that option with the Ubuntu LiveCD.

BTW, NVidia 280.13 is really 275.36.1, which does not support the NVidia GeForce GT 520 graphics card.  EDIT:  NVidia 280.13.really.275.36-1 is in Debian Unstable.  NVidia 290.06-1 is in experimental.  That's why I figure about 6 months (MAYBE a year, since it would have to get out of Unstable before they would issue .iso's).

---

### Post by MAFoElffen on 2011-11-20
> **laicepsydobon said:**
> I was never able to get to a terminal on the "Try" on the LiveCD.  However, I've replicated it on Wheezy.  The break-point is the GDM.  "WARNING: GdmDisplay: display lasted 0.079983 seconds" (Time varies but is approximately the same, and repeats until the system is killed) (quoted from the Wheezy Syslog from an attempt I made at adding an xorg.conf file to the mix).  In Wheezy it occurred whenever I attempted to add an xorg.conf file (/etc/X11/exorg.conf). including the one from the NVidia 290 proprietary driver.  

As it stands right now, that computer is limited to 800 X 600 resolution.  If I could even get VESA to accept a higher resolution (such as 1280 X 1024) I could live with it until Linux catches up with the new hardware.  But so far even attempting to force the boot sequence at the grub menu hasn't worked (vesa=795).  If I could get that far, then I could use Samba to transfer files from one computer to the other.

With Wheezy installed (different installer than Ubuntu) I am at least able to reboot and choose "Recovery", and log in as root and move the file to a .bak file, and/or make changes in vi IYEEECHT!!!).  At least I still remember how to get around vi, though it's been years.  It's better than EDLIN, though only just.  :)  I don't have that option with the Ubuntu LiveCD.

BTW, NVidia 280.13 is really 275.36.1, which does not support the NVidia GeForce GT 520 graphics card.  EDIT:  NVidia 280.13.really.275.36-1 is in Debian Unstable.  NVidia 290.06-1 is in experimental.  That's why I figure about 6 months (MAYBE a year, since it would have to get out of Unstable before they would issue .iso's).
EDLIN! LOL!  I remember the DOS days... I prefer nano over vi. Although I have over 2 decades using emacs... You are right. I now find myself quite spoiled by GUI based program editors!!!

290.03 has been in the Ubuntu Edgers PPA a little over a month... We tested it for Precise 12.04.  Works with Gnome, fails with Unity... Also had problems with 64bit flash here and there.

The unique problem is that only Ubuntu does Unity... I still use mostly Gnome3 on Ubuntu, but I have to test Unity as part of the dev builds. Desktop environments...

I am currently back on NVidia binary 285.05.09  on my 2 main boxes.

---

### Post by MAFoElffen on 2011-11-20
Hey-- Been thinking all night about your last post... About what would hold you until Linux caught up with your hardware.

I have an idea, but I need a little info from you to do it.

Please install hwinfo, if not already installed:
```

sudo apt-get install hwinfo

```Then post of the results from these:
```

sudo hwinfo --framebuffer
sudo hwinfo --monitor
sudo hwinfo --gfxcard

```
Also, if you could post your /var/log/Xorg.0.log file...

What I'm thinking is if you "get in" how you have been, if I create you an xorg.conf file that uses vesa or default as the driver, adds modelines of what your card and monitor supports, then we can extend your resolutions... You know, tweak it a bit to get you by.

Just thinking that might be an idea that might work out for you...

---

### Post by laicepsydobon on 2011-11-21
> **MAFoElffen said:**
> Hey-- Been thinking all night about your last post... About what would hold you until Linux caught up with your hardware.

I have an idea, but I need a little info from you to do it.

Please install hwinfo, if not already installed:
```

sudo apt-get install hwinfo

```Then post of the results from these:
```

sudo hwinfo --framebuffer
sudo hwinfo --monitor
sudo hwinfo --gfxcard

```Also, if you could post your /var/log/Xorg.0.log file...

What I'm thinking is if you "get in" how you have been, if I create you an xorg.conf file that uses vesa or default as the driver, adds modelines of what your card and monitor supports, then we can extend your resolutions... You know, tweak it a bit to get you by.

Just thinking that might be an idea that might work out for you...


MAFoElffen,

The problem, from my side, was solved last night.  A friend came over and we installed the NVidia 290 driver, then modified the xorg.conf created by NVidia to reflect the correct horizontal and vertical.  Just out of curiosity, I ran the hwinfo just now.  The monitor did not return anything.  Framebuffer ran off the page, and the nvidia card does show up as installed and active.  This is on the installation of Debian Wheezy on the new machine (which I'm typing from).  Apparently, when I was typing the figures in I miss-read or miss-typed the numbers repeatedly.  My friend caught it, and the xorg.conf binary blob worked without any problem

The problem with the Ubuntu LiveCD appears to be that it couldn't detect the card and monitor, and used default horizontal and vertical ranges.

I've marked this thread solved (which it was, the hard way) even though it doesn't solve the Ubuntu problem, only my own.

Thanks for the help and for trying.

---

### Post by MAFoElffen on 2011-11-23
> **laicepsydobon said:**
> MAFoElffen,

The problem, from my side, was solved last night.  A friend came over and we installed the NVidia 290 driver, then modified the xorg.conf created by NVidia to reflect the correct horizontal and vertical.  Just out of curiosity, I ran the hwinfo just now.  The monitor did not return anything.  Framebuffer ran off the page, and the nvidia card does show up as installed and active.  This is on the installation of Debian Wheezy on the new machine (which I'm typing from).  Apparently, when I was typing the figures in I miss-read or miss-typed the numbers repeatedly.  My friend caught it, and the xorg.conf binary blob worked without any problem

The problem with the Ubuntu LiveCD appears to be that it couldn't detect the card and monitor, and used default horizontal and vertical ranges.

I've marked this thread solved (which it was, the hard way) even though it doesn't solve the Ubuntu problem, only my own.

Thanks for the help and for trying.
Good deal... 

Check your /var/log/Xorg.0.log. Look after the driver loads... Where it probes the display and should get the EDID data back from it...

---

