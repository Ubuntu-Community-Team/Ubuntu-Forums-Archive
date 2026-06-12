---
title: "Minimal Install with 7.10 mini.iso &amp; fluxbox; help?"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by fINTiP on 2008-05-17
NOTE! SUMMARY AT BOTTOM FOR THOSE WHO DO NOT LIKE READING!

--

After getting fed up with running my dismal 6gig laptop harddrive at 85%, I decided ubuntu running with fluxbox as per normal desktop install was just way too bloated.

I had tons of software I didn't ever use.

So after a bit of chatting on the IRC channel, I took the plunge and burned a minimal CD, of 7.10.

I proceeded to install as per [Psychocats' instruction]("http://psychocats.net/ubuntu/minimal#barebones"), with a few small exceptions:

Where she said to type in this:
```
sudo apt-get install xorg xterm gdm icewm menu firefox gksu synaptic
```

I traded icewm for fluxbox, and dropped synaptic & gdm altogether. I also added pidgin, dillo, & xchat to the list.

The biggest deal here is that I dropped gdm. I don't want a graphical login, I want to boot and just go to terminal, log in there, and manually start my window manager.

But I can't find info on doing this anywhere. On the #ubuntu, I am told to look into more documentation in fluxbox, which I'm doing (but I am having trouble finding the info there also).

Anyways, I tried following her instructions, which go as follows:

```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

But obviously I wasn't going to start gdm, which is when I realized the above problem. I tried "startx", which, as I typed on #fluxbox, 

>  started a fluxbox session, but my right click *[menu]* did not work, my resolution was not good (which is probably not fluxbox's fault), and what's more, now my tty's aren't accesible. I just get black screens.

:confused:

WHY are my tty's not accesible???

Note: my resolution is poor using fluxbox (my LCD is capable of better), and my mouse has two shadows. Right clicking the toolbar does bring up the toolbar menu, to clarify- right clicking the desktop is where the loss is. No menu comes up.

This means no terminal. Which means I'm at a total loss as to what to do. Where did I go wrong?

----

To summarize:

1. I'm trying to do an ABSOLUTE MINIMAL install- fluxbox, ubuntu kernel, and programs of choice ONLY.
2. I don't want a graphical login, but seem unable to start a window manager session without one. :\ How to overcome this?
3. Why are my tty's unaccesible?
4. Of lesser importance, my resolution sucks.

Also, if you have any tips on how I could better do this install, I'm open to suggestion and starting from scratch if need be.

I am running a 500Mhz old HP laptop with 384ish Ram, 6gig HD. Model is N3290 Pavilion.

Was working fine with ubuntu 6.10 previously, capable of gnome but preferred fluxbox.

If you need any more info, let me know... I'm kajo on #ubuntu if you prefer to help me in real time.

---

### Post by kerry_s on 2008-05-17
> o summarize:

1. I'm trying to do an ABSOLUTE MINIMAL install- fluxbox, ubuntu kernel, and programs of choice ONLY.
2. I don't want a graphical login, but seem unable to start a window manager session without one. :\ How to overcome this?
3. Why are my tty's unaccesible?
4. Of lesser importance, my resolution sucks.

Also, if you have any tips on how I could better do this install, I'm open to suggestion and starting from scratch if need be.

I am running a 500Mhz old HP laptop with 384ish Ram, 6gig HD. Model is N3290 Pavilion.

Was working fine with ubuntu 6.10 previously, capable of gnome but preferred fluxbox.

If you need any more info, let me know... I'm kajo on #ubuntu if you prefer to help me in real time. 

1. that looks right, after you install you programs you need to run->
**sudo update-menus**
to setup the menu

2. the command is just> startx

3. not a clue sounds like you have a boned install from the start

4. you proably need to adjust your xorg.conf to your driver.


ubuntu is not the best choice on the old stuff, you should give debian a go.
net installer:
[http://cdimage.debian.org/cdimage/lenny_di_beta1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_beta1/i386/iso-cd/debian-testing-i386-businesscard.iso)

i'm a summing your res is 1024x768:

start the install with> install vga=791 or installgui vga=791
installgui is the fancy installer.

at the package selection, uncheck everything
that will give you a base install

after it ejects and reboots:

log in as root:
apt-get install xorg fluxbox menu
update-menus

type> exit <to get out of root

log in as user:
startx

that's all that's need to get you into gui. in the gui, open xterm, su to root, and install the rest of your goodies.
run> update-menus
so the new stuff is added to the menu(use the fluxbox restart to load the new menu)

---

### Post by fINTiP on 2008-05-17
sudo update menus. xD

It was that simple yeah?

That solved that, I can now right click.

> ubuntu is not the best choice on the old stuff, you should give debian a go.
net installer:
[http://cdimage.debian.org/cdimage/le...sinesscard.iso](http://cdimage.debian.org/cdimage/le...sinesscard.iso)

What exactly is the difference between Debian & this minimal install I am doing? I understand ubuntu is just a very specific flavor of Debian, but I don't exactly which parts are debian & which parts are ubuntu.

Or to ask it another way- my understanding is that Ubuntu just means 
 Debian's terminal/kernal (with slight mods for optimization)
+Gnome (or other Dektop Manager on equivalent 'buntus)
+GDM
+[usually] lots of packaged software.

I've taken away the last three, so... exactly what makes what I have ubuntu instead of debian?

> i'm a summing your res is 1024x768:

start the install with> install vga=791 or installgui vga=791
installgui is the fancy installer.

at the package selection, uncheck everything
that will give you a base install

after it ejects and reboots:

log in as root:
apt-get install xorg fluxbox menu
update-menus

type> exit <to get out of root

log in as user:
startx

that's all that's need to get you into gui. in the gui, open xterm, su to root, and install the rest of your goodies.
run> update-menus
so the new stuff is added to the menu(use the fluxbox restart to load the new menu)

What do you mean "start the install with"? I have already done the install (just prior to this post); do you mean installing something else, or how I would redo it in theory starting with the reinstall, or what?

Is it right to assume my resolution is 1024x768? Aren't most laptops like this easily capable of 1600x1200?

And lastly, should I still run that file that you told me?

Also, my resolution actuall is not that bad, it was just that the default fluxbox theme seemed huge to me because of the one I had previously used; I hadn't been able to open a window to really see what it was.

Thanks for the help. :D

.L

---

### Post by fINTiP on 2008-05-18
Also, this is pretty serious... my TTY's still don't work, and only bring up black screens.

O.O

???

What in the world would cause that?

And I can't figure out despite my best attempts why my mouse has two glitchy shadows. :/

.L

---

### Post by kerry_s on 2008-05-18
there are big differences between the 2. no need to go into it if your happy with what you got. maybe on your next install you try it for yourself.

you don't need to do anything else but learn your way around.

according to your specs the max res is 1024x768x16, same as mine, so if your running at 24 and it's all laggy, you might want to change that to 16.

vga=791 puts the screen at 1024x768x16 so the tty/console looks right.

```

Product Details and Features
Product MPN
MPN 	F1918A#ABA
Key Features
Processor  What is "Processor"?
	Pentium III 500 MHz
Installed Memory  What is "Installed Memory"?
	64 MB (SDRAM)
Hard Drive  What is "Hard Drive"?
	6 GB IDE
Display 	14.1 in. TFT Active Matrix
Processor
Processor Manufacturer 	Intel
Processor Type  What is "Processor Type"?
	Pentium III
Processor Speed  What is "Processor Speed"?
	500 MHz
Motherboard
Bus Speed 	100 MHz
Memory
Installed RAM 	64 MB
RAM Technology 	SDRAM
Max Supported RAM 	256 MB
Hard Drive
Storage Controller Type 	IDE
CD / DVD
CD / DVD Type  What is "CD / DVD Type"?
	DVD-ROM
Optical Drive Read Speed 	6x (DVD)
Other Drives
Floppy Drive 	3.5" 1.44 MB floppy
Display
Display Tech 	TFT Active Matrix
Display Size  What is "Display Size"?
	14.1 in.
Display Color Support 	16-bit (64K colors)
Display Max. Resolution 	1024 x 768
Video
Installed Video Memory 	4 MB
External Video Resolution 	1024 x 768
Audio
Audio Output Type 	Sound card
Operating System
Platform 	PC
Technical Features
Input Method 	Keyboard • Touchpad
Modem
Modem Type 	Fax / Modem
Analog Modulation Protocol 	Bell 103 • Bell 212A • ITU V.17 • ITU V.27ter • ITU V.29 • ITU V.32 • ITU V.32bis • ITU V.34 • ITU V.34bis • ITU V.90 • K56Flex
Battery
Battery Run Time 	3 Hours
Battery Technology 	Lithium ion
Dimensions
Width 	12.25 in.
Depth 	9.81 in.
Height 	1.58 in.
Weight 	6.84 lb.
Warranty
Warranty 	1 Year
Miscellaneous
Exterior Color 	Black
Product ID 	20123791
```

your specs are just a little better than mine, so it should be pretty fast if you use good light programs.

---

### Post by RedSquirrel on 2008-05-19
> **fINTiP said:**
> Also, this is pretty serious... my TTY's still don't work, and only bring up black screens.

I recall that Ubuntu 7.10 had some problems with consoles. You might be able to find the fix with a bit of searching or you could try Ubuntu 8.04 or Debian instead.

---

### Post by fINTiP on 2008-05-20
8.04 seems a bit unstable to me at this point- I'd rather wait three months while everyone else irons it out.

Do you have any knowledge of why that happened in 7.10 to cause that problem?

Debian still sounds iffy to me; as far as drivers and hardware recognition go, I'm not quite ready to invest that much time in trying to get it to work (I just had a friend try Debian who is just a few steps further into linux than I am, and he said it took him about a week to get everything working).

.L

---

### Post by kerry_s on 2008-05-20
> **fINTiP said:**
> 8.04 seems a bit unstable to me at this point- I'd rather wait three months while everyone else irons it out.

Do you have any knowledge of why that happened in 7.10 to cause that problem?

Debian still sounds iffy to me; as far as drivers and hardware recognition go, I'm not quite ready to invest that much time in trying to get it to work (I just had a friend try Debian who is just a few steps further into linux than I am, and he said it took him about a week to get everything working).

.L


i don't know what your friends specs are, but yours should work right from install, looking over your specs, everything is supported, you don't have to configure anything.
most of the problems that happen in ubuntu is because of there custom kernel. for older systems the 2.6.2* kernel gives problems, i use the etch 2.6.18 kernel on mine it works the best on my system. ubuntu does not give you that kind of choice so your screwed.

you can try debian live if you don't want to mess up what you got already->
[http://debian-live.alioth.debian.org/](http://debian-live.alioth.debian.org/)

---

### Post by RedSquirrel on 2008-05-20
> **fINTiP said:**
> 8.04 seems a bit unstable to me at this point- I'd rather wait three months while everyone else irons it out.

I installed Hardy Heron a couple of weeks before it was released officially and then removed it not long after it came out. It didn't seem too bad to me, but then I didn't really push it very hard. I run Gentoo these days.



> **fINTiP said:**
> Do you have any knowledge of why that happened in 7.10 to cause that problem?

For me, it was the lack of framebuffer support. I managed to fix it, but you'll want to research the "blank console in Gutsy" issue on your own to see if you can find an acceptable solution that matches your situation. That sounds like a hassle to me. Hence, if I were you, I would probably just move on to 8.04 or another distribution, but you must do what you feel is right, of course. ;)

I haven't used Gutsy in a long time. My approach to Gutsy was identical to Hardy: installed it a couple of weeks before it was released and then removed it. 



> **fINTiP said:**
> Debian still sounds iffy to me; as far as drivers and hardware recognition go, I'm not quite ready to invest that much time in trying to get it to work (I just had a friend try Debian who is just a few steps further into linux than I am, and he said it took him about a week to get everything working).

.L

As kerry_s wrote, as long as your hardware is well-supported, Debian is very straightforward. I can't imagine you would you have to invest much time to simply get it to work. My Debian installations were a breeze. Most of my time post-install was spent on "tinkering". :)

---

### Post by fINTiP on 2008-05-30
So I had problems because I tried to 'temporarily' install banshee, and it ended up screwing my system up because I didn't have gnome (which banshee kindly decided to attempt to remedy. :\).

So I decided to go ahead and try the same thing as above, only with 8.04.

However, I'm having problems with resolution, for real this time.

When I do ```
dpkg-reconfigure xserver-xorg
```

I run through the options for a while, and then it dies after I click "enter" when it is giving me the option to enter keyboard arguments (a field which I leave blank).

I see this in my terminal:

```
user@computer:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for user:
xserver-xorg postinst warning: overwriting possible-customized configuration file; backup in /etc/X11/xorg.conf.20080530191957
FATAL: Error inserting battery (/lib/modules/2.6.24.17-generic/kernel/drivers/acpi/battery.ko): No such device
user@computer:~$
```

My desktop occupies about 75% of my screen.

And I still have two glitchy mouse shadows. 

The TTY's function before I run startx, but once I'm in fluxbox, pressing alt+F3 gets me the third desktop within fluxbox, not TTY3. -_-

alt+F5, F6, F7, F8, F9...F12 gets me the fourth desktop within fluxbox.

Any help?

.L

---

### Post by RedSquirrel on 2008-05-30
> **fINTiP said:**
> When I do ```
dpkg-reconfigure xserver-xorg
```I run through the options for a while, and then it dies after I click "enter" when it is giving me the option to enter keyboard arguments (a field which I leave blank).

I see this in my terminal:

```
user@computer:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for user:
xserver-xorg postinst warning: overwriting possible-customized configuration file; backup in /etc/X11/xorg.conf.20080530191957
FATAL: Error inserting battery (/lib/modules/2.6.24.17-generic/kernel/drivers/acpi/battery.ko): No such device
user@computer:~$
```My desktop occupies about 75% of my screen.

And I still have two glitchy mouse shadows. 

The TTY's function before I run startx, but once I'm in fluxbox, pressing alt+F3 gets me the third desktop within fluxbox, not TTY3. -_-

alt+F5, F6, F7, F8, F9...F12 gets me the fourth desktop within fluxbox.

Any help?

.L

Press **Ctrl**-Alt-F1, **Ctrl**-Alt-F2, etc.

I have no idea about the mouse shadows nor the fatal battery module insertion.

Is there any sort of "Auto Image Adjust" feature for your screen?

There is (or used to be) a separate laptop discussion section on these forums. You might be able to find some info about your resolution issue there. Or maybe kerry_s will have an idea...

---

### Post by fINTiP on 2008-06-08
I found out that there is a bug report for this exact problem. dpkg-reconfigure xserver-xorg or whatever only lets you configure the keyboard, and lots of people are really mad/distressed about it.

So I've taken up learning how to write an xorg.conf. In lieu of any manual to do so (I couldn't find one), I started hacking away. It was very simple the first time I tried it, but I have since installed 8.04 *again*, because I had rhythmbox do exactly the same thing banshee did, only it was a near perfect (with some weird messups) gnome desktop environment.

Anyways, It was simple to rewrite last time, I just changed a handful of variables, and all was dandy. Now, however, those variables aren't there- there are no such subsections. So I found someone else's xorg.conf somewhere on these forums, and heavily edited what I could (they were using an nvidia, so I left out large chunks), and copy pasted pieces.

I made progress- my screen is now 1024x768, however, my display is still 800x600; i.e., I have to move the mouse to the edge to scroll to the rest of my desktop.

Here is my current xorg.conf-

```



Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"


        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"


Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Plug 'n' Play"
Modelname "Plug 'n' Play"
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync

EndSection


Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
Defaultdepth 16
SubSection "Display"
Depth 16
Virtual 1024 768


Depth 16
Virtual 1024 768
Modes "1024x768@60" "800x600@60" "640x480@60"
EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection
```

Out of curiousity, what do "vsync" and "hsync" mean, and what does the "+ -" do? I presume that indicates on/off for them, but I really have no idea.

.L

---

### Post by kerry_s on 2008-06-08
try this:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"MaxTapTime"	"0"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by Ptero-4 on 2008-06-12
Hi. I'm trying to do a minimal install with the mini iso in a VirtualBox VM (to make it into a "base, cli-only" liveCD from which to make custom ubuntu liveCD's later). But it won't install, it says that it can't find the repositories (And I know that VirtualBox networking works). How do I get it to see the repos?

---

### Post by stream303 on 2008-06-12
Be sure to see this really helpful Ubuntu wiki for doing exactly what is discussed.  And it won't install a graphical login manager unless you want it to:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Even though it is intended for low-memory systems, it still applies to those who want to "roll their own" custom ubuntu.  It even works on Apple PPC boxes with low memory.

You can choose to start with a server-install, or a cli-install only.

---

### Post by Harii on 2008-06-12
If all you need is minimal distro --
Try fluxbuntu and cut it down--alot faster
ubuntulite?
AntiX has a minimal install/live-cd.
puppy linux and DSL would work without all the work to configure.

You have a system in hours and not days.

I did a debian minimal install and it toke a week and AntiX minimal was 5 min. install for the same thing!

Plus they boot faster and lite on the hard drive.

---

### Post by snowpine on 2008-06-12
Hi fINTiP,
I tried doing exactly what you want to do--I even have the same size (6G) hard drive! But I am too much of a n00b to get Fluxbox working the way I wanted to do. So what I did was install Fluxbuntu. Basically it is a great example of what is possible with Fluxbox. I am studying it and figuring out how they did the things that they did. Perhaps some day when I am a Fluxbox wizard I will get rid of Fluxbuntu and do my own minimal install like you are contemplating. For now, it is a great learning experience for me. My 2 cents! :)

---

### Post by Harii on 2008-06-14
Well said:
I think thats how most of us did it.
It's slow but its the best way to learn.

Just remember to have fun.

---

### Post by fINTiP on 2008-06-15
Well, I got my xorg.conf ironed out after spending 5 hours (no exaggeration) on IRC troubleshooting with 2 or 3 other people (Richard left for several hours, came back, and I was still there).

So that's dandy. But I still have a few other problems.

To be clear- I have a super lite install of ubuntu *8.04* (did the mini.iso cli).

Problems:

-My other tty's don't work. "Ctr+alt+[F1-F6]" bring me to totally black screens, no prompt.

-If I kill "x", (ctr+alt+backspace) I also get a completely black screen, and am forced to shutdown with the power button. (typing blind "ctr+c sudo shutdown -P now" doesn't seem to do anything).

-something I can't remember...

-sudo shutdown now -P doesn't sound like it actually stops the harddrive, just like it brings me to a black screen. (The power does not cut, either, clearly.)

-I have two glitchy mouse shadows that trail behind my 'real' mouse indicator. They sometimes do negative, and aren't correctly rendered- but are consistent in their incorrect rendering.

-When I have multiple windows open on one desktop (none fullscreen), and I click a window behind the window I am using, it selects the window, but does not bring it on top of the window I was at previously. Using alt+tab is the workaround, as it does not suffer the same problem.

That is probably really confusing... Let's try that again, in case you didn't catch that.

Let's say I have firefox open & xchat open, each in their own window, firefox on top, with xchat partially visible 'behind' firefox. I then use the mouse to click on the xchat window. 

When I do that, the xchat window will go from gray-edged to blue-edged, indicating that it is now my 'active' window. But it won't be on top of Firefox, now- firefox, though it is not my 'active' window, is still on top of xchat.

The only way around this is using "alt+tab". If I change windows by alt+tab, the window will 'rise to the surface'. 

Needless to say, this is fairly annoying, and I can't imagine where to begin trying to fix that.

Help is greatly appreciated!

.L

---

### Post by AAlt1 on 2008-08-03
I'm really glad that I caught this thread, it's not *totally* old yet.

I have exactly the same problems as you do, on exactly the same computer model. 

I am wondering what it is that you did to fix the screen issues.

As for the mouse problem, with the funny shadows, in order to fix it you just need to drop this in you xorg.conf under the "Device" section

Option "SWCursor" "true"

That will fix it. The hardware cursor rendering is le suck.

Thanks.

---

### Post by fINTiP on 2008-08-18
For the sake of sharing the love, here is my current working xorg.conf (I haven't loaded it with the "SWCursor" option yet, btw- I just added it a few seconds ago. Thanks for that.)

```


Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "siliconmotion"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Option    "DPMS"
        HorizSync 31.5-49
        VertRefresh 50-70
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
        Defaultdepth  16
  SubSection "Display"
    Depth 16
    Modes   "1024x768"
  EndSubSection
EndSection

Option "SWCursor" "true"

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

Section "ServerFlags"
        Option "DontZap" "false"
EndSection


```

Enjoy.

---

