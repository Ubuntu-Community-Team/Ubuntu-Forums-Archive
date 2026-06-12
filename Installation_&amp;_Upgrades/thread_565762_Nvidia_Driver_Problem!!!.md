---
title: "Nvidia Driver Problem!!!"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by xoron on 2007-10-02
hi
i am pretty new to ubuntu (or linux for that matter).

i cnt get nvidia to work properly

i mean it works kinda (that is how i am sending this message)

the problem is that every time i start the computer i get the blue screen telling me there is something wrong with the XServer.

to fix this i have to install the nvidia driver again (for everyboot) if i don't then i am faced with the text mode (ctrl + alt + F1-F6)

i have got it to work b4 so i know it is the rightdriver wehat is the problem now?

please help

if more information is needed please ask i will be happy to supply the information.

---

### Post by dabl on 2007-10-02
This should help: [http://kubuntuforums.net/forums/index.php?topic=3086232.0](http://kubuntuforums.net/forums/index.php?topic=3086232.0)

:)

---

### Post by xoron on 2007-10-02
thanks but i would like to keep it as gnome

i have got it to work b4 this is the second install...i think that i may be installing it wrong

i have a BFG 8800 GTS if it helps

---

### Post by Cygnus on 2007-10-02
I have the exact same problem, every time I reboot my computer I have to reinstall the nvidia drivers. After reinstall they work perfectly, but as soon as I reboot they fail again.

I get the following output when it fails (for startx or kdm):

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Kunniasta 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct  2 23:13:24 2007
(==) Using config file: "/etc/X11/xorg.conf"

Error: API mismatch: the NVIDIA kernel module has the version 1.0-7184, but
this X module has the version 1.0-9755.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly.
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.


```

---

### Post by xoron on 2007-10-02
yeh that is the same error i get

i think somthing is reset to previouse settings ...what could be reverting it back to previose settings? sothing happens in the install of the driver that is undone at reboot.

---

### Post by Cygnus on 2007-10-02
I tried envy, but the same problem. Just with a slightly different error message:

```

Error: API mismatch: this NVIDIA driver component has version
100.14.19, but the NVIDIA kernel module's version does not match.
Please make sure that the kernel module and all NVIDIA driver
components have the same version.

```

If I change the driver to "nv" instead of "nvidia" in xorg.conf, then it works but resolutions are strange. Resintalling the true nvidia driver makes everything works much better.

---

### Post by LBattis on 2007-10-03
I'm a Fawn who's getting his legs underneath him.  I just built myself an ASUS M2NPV-VM with nVidia GeForce 6500 GPU onboard as my new wksta.  I wanted to load the latest nVidia  drivers so after getting no joy with the nVidia suggested method I found/followed the following post regarding 'Envy' from dabl:
-----------------------------------------------------------------------------------------------------------
 Re: Nvidia Driver Problem!!!
This should help: [http://kubuntuforums.net/forums/inde...opic=3086232.0](http://kubuntuforums.net/forums/inde...opic=3086232.0)
-----------------------------------------------------------------------------------------------------------
[COLOR="DarkRed"]This method appears to have loaded the drivers without a hitch.  System reboots smoothly.  Graphics are fine.  I wasn't having any particular problem with the system or graphics before I started so I went to /var/log to have a look at the Envy Install Log.  It was empty.  Is, 'no news good news,' or am I missing a point?  How do I confirm that I am running the latest nVidia drivers?
[/COLOR]
Additional Info:  I've ascertained that I have not loaded the nVidia drivers to my (Gnome) system.  I still cannot set resolution above 600x800 . . .  Help!

So I went ahead and tried installing the nVidia package I downloaded from the nVidia site ([COLOR="Lime"]NVIDIA-Linux-x86_64-100.14.19-pkg2.run[/COLOR]) again.  I got further this time; it recompiled the kernel and made adjustments to the "/etc/x11/xorg.conf," file and now I've truly broken my freshly loaded and fully updated AMD64-bit Fiesty Fawn system.  I'm receiving the following error message on boot:
-----------------------------------------------------------------------------------------------------------
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux asus-unhu 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007 x86-64
Build Date: 04 April 2007
                          Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
                          to make sure you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default settings,
                (++) from command line, (!!) notice, (II) informational,
                (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log File: "/var/log/Xorg.0.log", Time: Wed Oct   3  15:35:47 2007
(==) Using config file: "/etc/X11/xorg.conf
Error: API mismatch: this NVIDIA driver component has version
100.14.19, but the NVIDIA kernel module's version does not match.
Please make sure that the kernel module and all NVIDIA driver
components have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIIA kernel module! Please ensure
(EE) NVIDIA(0):      that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):      that the NVIDIA device files have been created properly.
(EE) NVIDIA(0):      Please consult the NVIDIA README for details.
(EE) NVIDIA(0):   *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

                                          <Ok>
-----------------------------------------------------------------------------------------------------------

I'm bummed.  Anybody have any ideas before I crank up fdisk and start this over again?

---

### Post by PmDematagoda on 2007-10-03
To the people with the "no screens found" error, try this:-

```
sudo dpkg-reconfigure xserver-xorg
``` in Recovery Mode.

To Cygnus, I got the same problem with Envy which I solved by doing the stuff in this thread:-

[http://ubuntuforums.org/showthread.php?t=545987&page=3](http://ubuntuforums.org/showthread.php?t=545987&page=3)

If it doesn't help you, just tell me.

---

### Post by LBattis on 2007-10-08
I've been attempting to get a clean load of the nVidia drivers onto the following system for a couple of weeks now with less than complete success:

MoBo:     ASUS M2NPV-VM AM2 NVIDIA GeForce 6150 Micro ATX AMD Motherboard
CPU:       AMD Athlon 64 X2 5200+ Windsor 2.6GHz Socket AM2
RAM:      2GB (2x1GB) 240-Pin DDR2 SDRAM DDR2 800(PC2 6400) Dual Channel
nVidia:    NVIDIA-Linux-x86_64-100.14.19-pkg2.run   (driver pkg downloaded from the nVidia 
website)

I have succeeded in getting an install where I can control resolution above the 600x800 default from the Feisty load.  When I reboot the system X fails with the message included below.  I have been getting assistance from a good guy who goes by the name of 
Techxplorer.  I've included the threads pertaining from his website (wiki?)

I have tried PmDematagoda's suggestion of 'sudo dpkg-reconfigure xserver-xorg' and still receive the error message of  “API mismatch,” included in its entirety below.
______________________________________________________________
[B]Installing NVIDIA drivers under Ubuntu – Feisty Fawn
May 9th, 2007 — techxplorer [/B]
I’ve been a long time fan of Ubuntu Linux but this past week has tested my patience.
The issue I was having was that I couldn’t get the correct screen resolution on my new Toshiba Laptop. It has an NVIDIA based video card. I installed the latest version of Ubuntu, Feisty Fawn, and the new Restricted Drivers Manager I thought it would be easy.
Unfortunately this was not the case. The driver that is currently available via the Ubuntu repositories wasn’t working with my hardware. I could change to the right resolution using the nvidia-settings application but the changes wouldn’t last a reboot. I also couldn’t use the nvidia-settings application to save a new xorg.conf file. I kept getting this error:
ERROR: Unable to determine valid vertical refresh ranges
    for display device'LPL' (GPU: GeForce Go 7300)!
ERROR: Failed to add display device 'LPL' to screen 0!
ERROR: Failed to add X screen 0 to X config.
ERROR: Failed to add X screens to X config.
ERROR: Failed to generate an X config file!
I discovered that this is a known issue in that driver and that I needed to upgrade to the new one. Sadly the new one isn’t in the repositories yet. So I thought I’d just need to install the build-essential package and install the latest driver from the NVIDIA website.
Sadly this didn’t work either. It appeared as though the kernel module installed by the Ubuntu package wasn’t being removed when I removed the package. The installation of the NVIDIA driver would go fine, but it wouldn’t work because it would see the old kernel module and fail.
Last night I had a breakthrough. I installed Ubuntu Feisty Fawn overwriting the old installation. I then installed the build-essential package and finally installed the NVIDIA driver using their installer. This was a success. I know am able to use the laptop at the native resolution.
The downside to this is that if there is an update to the Kernel I’m going to need to build a new NVIDIA driver kernel module to match before it will work again. But that’s not too hard. It’s also possible that by then the Ubuntu package will have the version that I need.
In the end, I’m still happy with Ubuntu and have learned more about Linux in general. I’ve also gained a renewed dislike for binary only drivers.

[B]1.Larry Battis Says: 
October 8th, 2007 at 4:17 am [/B]
I’m new to Ubuntu and only somewhat conversant with Linux in general. I want to make it my only OS. I’m discovering I truly share your dislike of binary-only drivers.
I think I could use some clarification on what you mean by the following from the above procedure:
“Last night I had a breakthrough. I installed Ubuntu Feisty Fawn overwriting the old installation. I then installed the build-essential package and finally installed the NVIDIA driver using their installer.”
Are you using NVIDIA’s installer at this point or is there an installer in the build-essential package?
I’m trying to get control of the embedded nVidia GeForce 6 GPU on an ASUS M2NPV-VM motherboard and have resorted to fdisk 6 times now . . .
I confess; I’m not getting it.

[B]2. techxplorer Says: 
October 8th, 2007 at 8:40 am [/B]
@Larry,
I use the NVIDIA installer. The build-essential package has things in it like the C++ compiler and other tools / software that are necessary to build, a.k.a compile, programs. These are used by the NVIDIA installer to build the Kernel module it needs. 
The bare bones steps are (some commands are truncated):
- Start with a fresh install
- Install the build-essential package
- Download the latest NVIDIA driver
- Switch to a new terminal: CTL+Alt+F1
- Stop the X server: sudo /etc/init.d/gdm stop
- Change the permissions on the NVIDIA installer: chmod +x NVIDIA-Linux….
- Start the installer: sudo ./NVIDIA-Linux….
- Start the X server again: sudo /etc/init.d gdm start
Hope this helps, and apologies for not being clearer in my original post. Perhaps an avenue to take will be to try the Ubuntu 7.10 release when it comes hope. I’m personally hoping this will resolve the issues I had that brought me to this. 
Let me know how you go.

[B]3.Larry Battis Says: 
October 8th, 2007 at 10:48 am [/B]
techxplorer,
Thanks for all the good information. I followed your instructions with success (able to control resolution up to 1280×1024) until I rebooted the system. On reboot I received the following error message:
————————————————————————-
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux asus-unhu 2.6.20-16-generic #2 SMP Sunun Sep 23 18:31:23 UTC 2007 x86-64
Build Date: 04 April 200707
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure you have the latest version.n.
Module Loader present
Markers: (–) probed, (**) from config file, (==) default settings,g,
(++) from command line, (!!) notice, (II) informational,l,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log File: “/var/log/Xorg.0.log”, Time: Sun Oct 7 17:57:55 200707
(==) Using config file: “/etc/X11/xorg.conf
Error: API mismatch: this NVIDIA driver component has version
100.14.19, but the NVIDIA kernel module’s version does not match.
Please make sure that the kernel module and all NVIDIA driver
components have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIIA kernel module! Please ensure
(EE) NVIDIA(0): that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0): that the NVIDIA device files have been created properly.
(EE) NVIDIA(0): Please consult the NVIDIA README for details.
(EE) NVIDIA(0): *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.
Fatal server error:
no screens found
————————————————————————-
I moved over to the F1 terminal and tried:
sudo /etc/init.d/gdm restart
The song remained the same.
Is there something I can do from this terminal to repair X?

[B]4. techxplorer Says: 
October 8th, 2007 at 12:32 pm[/B] 
@Larry,
The issue here isn’t that X is necessarily broken. The issue is that there is probably two versions of the NVIDIA kernel module on your system. 
As I understand it the chain of components is something like:
X -> NVIDIA Driver -> NVIDIA Kernel module -> Linux Kernel
I also had this issue, and as far as I could tell it was because I’d tried to use the drivers from the Ubuntu repositories. When I tried to remove them, no matter what I tried, the kernel module(s) from the Ubuntu versions would be left behind. 
The only way I got around it was to:
- Install Ubuntu from scratch again
- Install the build-essential package
- Install the NVIDIA driver from the NVIDIA package
- Install the outstanding updates
Sorry I can’t be of any more help.

[B]5.Larry Battis Says: 
October 8th, 2007 at 1:19 pm [/B]
Is it that I updated my install before I installed the NVIDIA drivers from the NVIDIA package? I’ll throw fdisk at it and then try loading NVIDIA’a drivers before I update.
______________________________________________________________

Unfortunately upon reboot I found this did not clear up the problem.  The Error Message is the same as above.  Does anyone have any ideas that would help me?

---

### Post by chris_ak on 2007-10-08
after installing the driver, sudo modprobe nvidia

---

### Post by Throwback on 2007-10-08
Try using this package (Envy) to install your drivers:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Of course there is a benefit to working this out the manual way, in that you learn more, but after much banging of heads on the problem I solved all my Nvidia driver issues by just using this package.

FYI I am using Ubunty 7.04 AMD64 build, on a BFG nvidia 8800 gts.

---

### Post by SpirosDell on 2007-10-08
HI guys I m new to Ubuntu and Linux.
I have nVidia GeFo 6600 nad I really have a BIG problem i've tried everything
What ever i do always the x server has a problem(the same) and always cp the old xorg.conf
plz help ask me for ferther information.

---

### Post by PmDematagoda on 2007-10-08
What is the error you get?

---

### Post by LBattis on 2007-10-08
re: sudo modprobe nvidia

[LIST=1]
[*]Tried this on the F1 terminal screen of the crashed X system first w/ no improvement on reboot.
[*]Rebooted to Recovery Mode and tried this with no improvement on reboot
[*]Fdisk'd system, re;loaded from scratch using Techxplorer's method of gaining some control over the nVidia system, shifted to F1 terminal, shutdown GDM and tried modprobe w/ no improvement on reboot
[/LIST]

I'm still getting the same, "API mismatch/NVIDIA kernel module mismatch," error message.

Will a verbose, dry run of 'sudo modprobe nvidia' shed any light on what's happening here?

What's my next move on this one?

---

### Post by LBattis on 2007-10-08
re:  Try using this package (Envy) to install your drivers:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Sorry,  I'm still getting used to how this site works, (how new am I to this!) didn't notice there was a pp2.  I'll Fdisk and try Envy with the 'build-essentials' package loaded as my next tack.

---

### Post by LBattis on 2007-10-08
I am pleased and insanely relieved to report that I now have a stable Feisty system with the nVidia drivers loaded and everything rebootable.  The details of my system (incl. embedded GeForce 6150) and what it took to get from there to here are included in the previous posts (above).  The short form of what I did that worked is listed below:
[LIST=1]
[*]Started with a fresh load of 'Ubuntu 7.04 Desktop AMD64/Intel64 Feisty Fawn Client.
[*]Updated the Install.
[*]Installed the Build-Essentials Package & Dependencies via Synaptic.  (this is important, I'd tried Envy without this and it didn't work)
[*]Installed Envy from Alberto Milone's (link included above) Homepage
[*]Ran the Envy Install
[*]Ran Envy to Install the nVidia Drivers.
[*]""Rinsed!"" and Rebooted (don't take the 'rinsed' too seriously)
[/LIST]
To everyone who lent a hand along the way, my sincere thanks.
Alberto Milone has a donation coming.
I'll be going back to Techxplorer's page to let him know about the resolution.
This Rocks!  Once again, Thank-you!

---

### Post by Beve Stallmer on 2007-10-09
Getting an install to work properly shouldn't be like following a recipe. This is what keeps Linux  in Geekland. Note: I was having a very similar problem to these fellas.

---

### Post by LBattis on 2007-10-09
Agreed: however I'm too new to this to look a gift horse in the mouth.  I need this video operational in order to keep learning about the OS.  I'll let everyone know when I'm ready to start writing drivers in Linux.  I really have written drivers for Netware.  In the interim; this old man is on to the next set of experiments.  . . . And; I don't mind assisting the terminally brilliant when I come across them.

---

### Post by Cygnus on 2007-10-22
I never totally sorted out the prolems I had, but I can add that when I now tried an upgrade to kubuntu 7.10 (from 7.04) it all started to work without me doing anything really :)

There is one small problem however, when logging in it sets the resolution to 1600x1024, but my lcd wants 1680x1050 so I have to manually change that every time I log in. Chosing "save to x configuration file" in nvidia-settings do not help. Would be nice to fix, but I can live with it as I am usually logged in 24h/d.

---

