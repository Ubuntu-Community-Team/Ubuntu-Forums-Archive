---
title: "Solution!!! Nvidia GeForce4 420 Go driver dump, missing gcc-3.3 gcc-3.4 &amp; more..."
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by brigadoon on 2008-04-28
I've received tons of help from these forums in the past. I felt obliged to post my solutions to upgrade issues that I came across with Ubuntu 8.04. Everyone should keep in mind that Ubuntu is FREE!!! :) Most systems work well with it. Unfortunately there are some pieces of hardware that have a conflict with it. Even with the conflicts, I'll take Ubuntu over Windows any day!!!

I have a Toshiba Satellite 1415-S173 laptop with a NVIDIA GeForce4 420 Go with 16 Meg of RAM. I'm a big fan of Neverwinter Nights so 3D graphics is a must.

I upgraded to Ubuntu 8.04 through the System/Administration/Update Manager utility. Everything went well with the exception of the graphics was set to low resolution on reboot and the gcc-3.3 and gcc-3.4 info files were dropped. The missing gcc files were critical since they prevented me from installing or un-installing programs.

I found the gcc fix in a Ubuntu bug report. The solution was provided by Tiger!P. The problem is that the files are not where some scripts think they should be. The trick is to recreate them from other gcc files. In short I opened a terminal window and typed the following...

sudo cp /usr/share/info/gcc-4.1.info.gz /usr/share/info/gcc-3.3.info.gz
sudo cp /usr/share/info/gccint-4.1.info.gz /usr/share/info/gccint-
sudo cp /usr/share/info/gcc-4.1.info.gz /usr/share/info/gcc-3.4.info.gz
sudo cp /usr/share/info/gccint-4.1.info.gz /usr/share/info/gccint-3.4.info.gz
sudo dpkg --configure -a

It may not be the best solution but it worked for me. No problems yet. [-o<

Next on the list was to fix the NVIDIA driver. NVIDIA has several drivers that worked with previous versions of Ubuntu. Each one would load and have a black bar on the right side of the flat panel display. NVIDIA didn't configure the driver to work with every display on the planet. Lucky me!!! I have one of those problem displays!!! ](*,) The black bar was a tough one and required some hexidecimal edits to an edid.bin display file to fix it.

I found that the following NVIDIA drivers do not work with Ubuntu 8.04 on my laptop (even when patched)...
NVIDIA-Linux-x86-1.0-8776-pkg1
NVIDIA-Linux-x86-1.0-9631-pkg1
NVIDIA-Linux-x86-1.0-9755-pkg1

The new legacy driver (NVIDIA-Linux-x86-96.43.05-pkg1) worked when first loaded after I fixed the edid.bin file. However, the driver was dumped on a reboot. The only way to recover was to reinstall the driver every time I turned the laptop on. The graphics were choppy and scrolling came with a poor refresh rate. My solution from the forums was as follows...

1) Load ENVY through the System/Administration/Synaptic Package Manager. Thanks to Alberto Milone (aka tseliot) for writing this sweet utility.

2) Start Envy from Applications/System Tools/EnvyNG. From the main window select NVIDIA and Uninstall the NVIDIA driver. I needed to remove any traces of NVIDIA from the system to make this work. Select Apply and reboot the system when asked.

3) Re-start Envy. From the main window select NVIDIA and Install the NVIDIA driver (Manual Selection of the Driver). The driver version I selected was the 96.43.05 option. Select Apply and reboot the system when asked.

4) After the reboot open the NVIDIA utility from System/Administration/NVIDIA X Server Settings. Go to the DFP-0 - (NVIDIA Default Flat Panel) tab and in the right side window select Aquire EDID. What happens here is the Flat Panel configuration gets exported in a binary format. This is where the hex editor comes in. You can load one through the Synaptic Package Manager. The problem is that the driver's display resolution does not match the resolution of the actual Flat Panel display. Thanks to orlo11 for the hint on fixing the display. The instructions are as follows...

Save the EDID by nvidia-settings to a file and edited this. I called mine edid_04_28_2008.bin. The horizontal resolution is saved in the bytes with the offset 56(Hex:38 ) and 58 (the upper four bits) (Hex:3A )
In the original EDIT these bytes were C9 and 31 (0x3C9 = 969)
Change them to 00 and 41 (0x400 = 1024).
Then add the Option "CustomEDID" "/path/to/patched/EDID.file" to the XORG.CONF located in /etc/X11 folder. [COLOR="Red"] ( edit made June 1, 2008 ) I needed to add a "DFP-0:" switch to the option pathway. This forces the option to be used with my flat panel display. See below for some excerpts from my xorg.conf file.[/COLOR]

Further information about the structure of the EDID you will find at
[http://en.wikipedia.org/wiki/EDID#EDID_1.1_data_format](http://en.wikipedia.org/wiki/EDID#EDID_1.1_data_format)

My XORG.CONF file looked like this in the display section (Critical lines I added are in bold type) ...
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
***	Option		"UseDisplayDevice"	"DFP"***
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"	"true"
	Driver		"nvidia"
[B][I]        Option          "CustomEDID"   "DFP-0:/etc/X11/edid_04_28_2008.bin"
[/I][/B]EndSection

Edits to the XORG.CONF file need to be made with the GDM stopped. To do this do the following...

***CTRL+ALT+F1*** "Jumps to the 1st console"
***sudo /etc/init.d/gdm stop*** "Stops GDM"
***sudo nano /etc/X11/xorg.conf*** "Starts editor. Make your edits and save"
***sudo /etc/init.d/gdm restart*** "Starts GDM. You should automatically switch back to the log in of the desktop"

Now, if only I could only get my Linksys Wireless G (WPC54GX4) card to work life would be perfect. :lolflag:

[COLOR="Red"]UPDATE TUESDAY MAY 6TH 2008!!!
I have the WPC54GX4 working on Ubuntu 8.04 now!!! See the reply below!!!
[/COLOR]
By the way...
To get Neverwinter Nights to work I had to modify the shell script. The nwn script file in the game directory looks like this...

#!/bin/sh

# This script runs Neverwinter Nights from the current directory

cd /home/david/nwn
export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
export LD_PRELOAD=./nwmovies.so
./nwmain $@

I had to change the ***export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH*** line to ***export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH*** to play the game in Ubuntu 8.04. Deleting the ***./lib*** text did the trick.

---

### Post by brigadoon on 2008-05-06
Getting the Linksys WPC54GX4 wireless adapter running on Ubuntu 8.04 was very easy!!!

Download the WPC54GX4-v1.00.09-2.0.1.19.zip driver from the Linksys web site.

Extract it to a directory.

I was using a Netgear wireless to download. I un-plugged it. ***Do not*** insert the WPC54GX4 into the PCMCIA slot.

Select System/Administration/Windows Wireless Drivers.

On the menu that pops select Install New Driver

Goto the directory the driver was extracted to and select the tmimo3P.inf data file. Press install.

After a minute my laptop froze. I killed the power. Before turning it back on I inserted the WPC54GX4 into the PCMCIA slot.

After login select System/Administration/Windows Wireless Drivers again. On the menu that pops up select Configure Network. The wireless connection appears and is locked in roaming mode.

Left click the network icon next to the time and date display in the upper right corner of the desktop. A drop down menu appears with my home wireless network on it. I select it and log in to the home network.

I could never get the card to work until I remembered that in the Windows installation instructions you are directed not to install the card until the driver is installed. The same methodology must apply to Ubuntu as well.

Nice and simple.

---

### Post by Regulluz on 2008-05-12
Hi!

Thanks for this guide. I am having exactly the same problem with the same card, although I'm using a Sony VAIO PCG-FR130. However, I am very new to Linux and Ubuntu, and really have no idea of how to perform all these steps you mentioned, or where to get the files. You, or anybody, knows an easier of newbie proof way of fixing this?

Million thanks!

-Reg

---

### Post by brigadoon on 2008-05-13
Which files do you need specifically? Some can be installed through the Synaptic Package Manager others you'll have to down load from hardware vendor sites. Let me know which files for what you can't locate and I'll try to help you out.

---

### Post by Regulluz on 2008-05-21
Hello again!

THANK YOU, THANK YOU, THANK YOU... and so on....

So, I went on... sat down and read carefully through your post, and managed to install the driver though the EnvyNG. So, I got till the part of the AquireEDID. However, my computer display resolution is correct, and everything is working like a charm. I don't know if I should edit the EDID file anyways, should I? If that is the case, then I would like to know how to open the HEX editor tough the Package Manager.

Man, I am so grateful! THANKS! I'm kind of liking the Linux support thing! :D :)

---

### Post by brigadoon on 2008-05-21
If your happy with the resolution settings available then you don't need to use a custom EDID file. There's an old programmers saying... ***Better is the enemy of good.*** If it's good I'd leave it alone. Trying to make it better sometimes makes it worse. I needed to use a custom EDID file since my driver didn't recognize the display resolutions on my laptop. It sounds like your drive works well with your monitor and you're good to go. Glad I could help.

---

### Post by brigadoon on 2008-05-31
An interesting thing happened to me this week when I updated gdm through a standard update. My NVIDIA driver was obliterated. No amount of reloading my Nvidia driver would work. I couldn't get above 800x600 resolution. Even if I tried a custom EDID file solution listed above I had no success.

I finally scorched earth my xorg.conf file in a fit of desperation. I ended up installing a fresh xorg.conf file from xorg by running the following command...

sudo dpkg-reconfigure -phigh xserver-xorg

This was a method of last resort and needs to be done with gdm stopped and the Nvidia driver components uninstalled. A very basic version of a xorg.conf file is loaded into the /etc/X11 folder. I restarted gdm and reloaded my Nvidia driver through Envy. The driver installation modified the xorg.conf file as needed for my system. I then generated a custom EDID file to get a 1024x768 resolution. Everything was back to normal.

My xorg.conf file is much simpler now. My guess is that there was just too much junk in the file that was either no longer supported or conflicted with the new updates. Either way something in the old xorg.conf file was creating a problem. The new file is much more streamlined.

---

### Post by momo07 on 2008-06-16
Help I cant edit my edid_04_28_2008.bin file

---

### Post by momo07 on 2008-06-16
Thanks so much, I had no more hair to pull out..LOL.. I appreciate your help. Thanks again. I am now enjoying what windows will never provide for free.. Thanks

---

### Post by suseno on 2008-08-11
Thanks brigadoon! Your "UseDisplayDevice" "DFP" is awesome!

I'm using Ubuntu 8.04 for my Toshiba 2450 laptop and nVidia GeForce4 420 Go. I'm almost frustated because My NVIDIA-Linux-x86-96.43.05-pkg1 driver didn't work at all. It shows blurry white screen over the display. But it's work after I try adding Option "UseDisplayDevice" "DFP" in my /etc/X11/xorg.conf Now I can activate that fancy Visual Effects and running 3D Application like Google Earth.

---

### Post by davethewave83 on 2008-09-01
Thank you so much for this!!!!!! I have the exact same laptop model and this did the trick :guitar: I never would have guessed I had to hex edit the edid file, and I saved that thing like 3 times out of curiosity

---

### Post by brigadoon on 2008-10-16
The major update from October 15th 2008 finally did in my version of Ubuntu 8.04 yesterday. I upgraded from the previous version of Ubuntu to version 8.04 when it first came out. As you can see by this thread I did a few things to keep it going as the updates came out.

After the update was finished a reboot was required. It was a very large update with lots of fixes. Upon restart I would get to the login screen. The system becomes unresponsive. Switching to terminal mode via ctrl+alt+F1 didn't help. In place of the terminal login I received nothing but errors. Starting in recovery mode didn't help either.

Fortunately I back up most of what I do so the loss was minimal. I was able to boot from a new 8.04 CD and recover most data not backed up. I could view the hard drive. When copying to an external drive a permissions message came up. I skipped all. It copied them anyway. Shouldn't have been able to do that but I'm glad it did.

Fully backed up I reinstalled from scratch to a fresh copy of 8.04. I did have to play with the NVIDIA settings as stated earlier in this thread. The custom EDID fix was still required. To be quite honest the system runs far better now than it did before.

Ubuntu 8.1 is due out soon. I may start up with a fresh install and avoid the nasty issues I've experienced with the last upgrade between versions. Still, I can't complain. Ubuntu remains the best operating system I've played with so far.

---

### Post by Barry0611 on 2008-12-22
I am a newbie and have a similar problem. Upgrade went well, no problems.  As stated above, I tried to get higher resolution goodies activated, followed the process, now the machine boots up, but I see a blank screen (I hear bongos), I can log in but can't see anything.  Not sure how to proceed.  Would like high res, would be happy just to go back to the way things were.  Thank you.
:KS

---

### Post by davethewave83 on 2008-12-22
> **Barry0611 said:**
> I am a newbie and have a similar problem. Upgrade went well, no problems.  As stated above, I tried to get higher resolution goodies activated, followed the process, now the machine boots up, but I see a blank screen (I hear bongos), I can log in but can't see anything.  Not sure how to proceed.  Would like high res, would be happy just to go back to the way things were.  Thank you.
:KS

Sounds like your display isn't initializing correctly, It's been a while since I used ubuntu (I got a new laptop and it doesn't work on it) =( but! I would guess that you add a string to your xorg.conf file, I forget it exactly but I think it goes something like 
Option UseDisplayDevice "DFP:0" or perhaps just "DFP" 
someone correct me if this is wrong :) I forget exactly where you add this, under display devices I think?

I really wish I could get ubuntu to work on my new laptop! it installs and runs but the screen is all flickery and insane, looks like a scary movie

---

### Post by brigadoon on 2008-12-23
The line in question should read...

***Option "UseDisplayDevice" "DFP"***

This assumes that you use a default flat panel for your display. You may need to specify something else if you have say a plasma display. If you list you system specs I may be able to be able to spot something. Wich version of Ubuntu and what are you running it on.

If I don't respond immediately don't be discouraged. Its the holidays and I'm usually busy in the real world.

---

### Post by Hakaroi on 2009-05-23
> **brigadoon said:**
> 

Next on the list was to fix the NVIDIA driver. NVIDIA has several drivers that worked with previous versions of Ubuntu. Each one would load and have a black bar on the right side of the flat panel display. NVIDIA didn't configure the driver to work with every display on the planet. Lucky me!!! I have one of those problem displays!!! ](*,) The black bar was a tough one and required some hexidecimal edits to an edid.bin display file to fix it.

I found that the following NVIDIA drivers do not work with Ubuntu 8.04 on my laptop (even when patched)...
NVIDIA-Linux-x86-1.0-8776-pkg1
NVIDIA-Linux-x86-1.0-9631-pkg1
NVIDIA-Linux-x86-1.0-9755-pkg1

The new legacy driver (NVIDIA-Linux-x86-96.43.05-pkg1) worked when first loaded after I fixed the edid.bin file. However, the driver was dumped on a reboot. The only way to recover was to reinstall the driver every time I turned the laptop on. The graphics were choppy and scrolling came with a poor refresh rate. My solution from the forums was as follows...

1) Load ENVY through the System/Administration/Synaptic Package Manager. Thanks to Alberto Milone (aka tseliot) for writing this sweet utility.

2) Start Envy from Applications/System Tools/EnvyNG. From the main window select NVIDIA and Uninstall the NVIDIA driver. I needed to remove any traces of NVIDIA from the system to make this work. Select Apply and reboot the system when asked.

3) Re-start Envy. From the main window select NVIDIA and Install the NVIDIA driver (Manual Selection of the Driver). The driver version I selected was the 96.43.05 option. Select Apply and reboot the system when asked.

4) After the reboot open the NVIDIA utility from System/Administration/NVIDIA X Server Settings. Go to the DFP-0 - (NVIDIA Default Flat Panel) tab and in the right side window select Aquire EDID. What happens here is the Flat Panel configuration gets exported in a binary format. This is where the hex editor comes in. You can load one through the Synaptic Package Manager. The problem is that the driver's display resolution does not match the resolution of the actual Flat Panel display. Thanks to orlo11 for the hint on fixing the display. The instructions are as follows...

Save the EDID by nvidia-settings to a file and edited this. I called mine edid_04_28_2008.bin. The horizontal resolution is saved in the bytes with the offset 56(Hex:38 ) and 58 (the upper four bits) (Hex:3A )
In the original EDIT these bytes were C9 and 31 (0x3C9 = 969)
Change them to 00 and 41 (0x400 = 1024).
Then add the Option "CustomEDID" "/path/to/patched/EDID.file" to the XORG.CONF located in /etc/X11 folder. [COLOR="Red"] ( edit made June 1, 2008 ) I needed to add a "DFP-0:" switch to the option pathway. This forces the option to be used with my flat panel display. See below for some excerpts from my xorg.conf file.[/COLOR]

Further information about the structure of the EDID you will find at
[http://en.wikipedia.org/wiki/EDID#EDID_1.1_data_format](http://en.wikipedia.org/wiki/EDID#EDID_1.1_data_format)

My XORG.CONF file looked like this in the display section (Critical lines I added are in bold type) ...
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
***	Option		"UseDisplayDevice"	"DFP"***
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"	"true"
	Driver		"nvidia"
[B][I]        Option          "CustomEDID"   "DFP-0:/etc/X11/edid_04_28_2008.bin"
[/I][/B]EndSection

Edits to the XORG.CONF file need to be made with the GDM stopped. To do this do the following...

***CTRL+ALT+F1*** "Jumps to the 1st console"
***sudo /etc/init.d/gdm stop*** "Stops GDM"
***sudo nano /etc/X11/xorg.conf*** "Starts editor. Make your edits and save"
***sudo /etc/init.d/gdm restart*** "Starts GDM. You should automatically switch back to the log in of the desktop"

Now, if only I could only get my Linksys Wireless G (WPC54GX4) card to work life would be perfect. :lolflag:

[COLOR="Red"]UPDATE TUESDAY MAY 6TH 2008!!!
I have the WPC54GX4 working on Ubuntu 8.04 now!!! See the reply below!!!
[/COLOR]
By the way...
To get Neverwinter Nights to work I had to modify the shell script. The nwn script file in the game directory looks like this...

#!/bin/sh

# This script runs Neverwinter Nights from the current directory

cd /home/david/nwn
export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
export LD_PRELOAD=./nwmovies.so
./nwmain $@

I had to change the ***export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH*** line to ***export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH*** to play the game in Ubuntu 8.04. Deleting the ***./lib*** text did the trick.


I have the exact same laptop as you (Toshiba Satellite 1415-S173) running 9.04.  I used Envy to activate the driver (when i tried with the "Hardware Drivers" menu under Administration, it would restart, then the x server wouldnt work, but it does through envy) and now i can see. i changed the xorg.conf to use the custom EDID and edited the EDID like you said, but i still get the black bar on the side of the screen. how can i fix this?

---

### Post by brigadoon on 2009-05-27
My guess is that you did not edit the edid.bin file correctly. In a HEX editor you must change the block containing C9 to 00 and the block containing 31 to 41. This changes the horizontal display from 969 to 1024. The black bar is there because the flat panel display is too wide for a 969 resolution.

Check your file permissions. Check the modified edid.bin file you created and make sure the changed blocks have actually been changed. You may need to change the file permissions in order to accept the changes.

Also, make sure the syntax in the xorg.config is correct. Good luck.

---

### Post by cbbnewbie on 2010-05-05
hi, is there a solution like this for Nvidia GeForece2 Go, i think my problem with enabling visual effects is caused by this. anyone?

---

### Post by brigadoon on 2010-05-06
I'm not sure that this is related to visual effects on Ubuntu 10.04 and this post are related. This post was for a resolution fix. I think not being able to activate visual effects may be something else. 

The latest version of Ubuntu (10.04) does not need to use the xorg.conf file in order to run the graphics card. Try renaming xorg.conf as xorg.old and restart GDM. If the Gnome interface starts then you can try and activate the graphics effects. If the graphics effects do not start then it may be that the card doesn't have the memory for it. Do you have the go, go 100 or go 200? The graphics effects take a lot of memory.

The old Toshiba is in storage so I don't know if it can run the graphics effects with 10.04 running. I had the graphics effects turned off on the Toshiba. The graphics were too choppy or would lock the system up. It was a good laptop but only had 16 meg of dedicated video memory. I had 1 Gig of working RAM that I could use for sharing. I think the graphic effects need more dedicated video memory due to the buss speed of the main board of the laptop. It would do memory sharing to boost the 16 meg to what ever it needed to be. The buss speed of the laptop kind of made unworkable.

Let me know what you are using for a system. More spec information (manufacturer, model, cpu, RAM, etc...) may help someone in the forum propose a solution for you.

---

### Post by cbbnewbie on 2010-05-07
the laptop i use only have 256 ram 800mhz pentium3 nvidia geforce2 go wth 16mb memory,, now i think my problem too is about the resolution  because as long as it stays in 800x600 even though i turn off the laptop compiz still works when i turn it on, but if i change it to 1024x768 and restart or shutdown upon loging in compiz doesnt work and i cant enable visual effects.. for now im being satisfied to 800x600 its the only way compiz would work the next time I start the laptop. Im just a week old in using ubuntu so i still dont know a lot of things thanks for helping. ^_^

---

### Post by brigadoon on 2010-05-07
Just to be clear, with visual effects turned off, can you change the resolution from 800x600 to 1024x768?

---

### Post by cbbnewbie on 2010-05-07
on my appearance preferences, visual effects tab none is selected I mean nothing is selected no check on "none", "normal' and "extra" so I dare not to to touch those setting for im afraid I'm gonna reinstall the driver again if things goes wrong.. my problem always start after i change the resolution to 1024x768 and save on the x configuration.

---

### Post by brigadoon on 2010-05-08
I had a similar problem when I originally tried to use Compriz. When I allowed Ubuntu to automatically load in the driver it turned into a disaster. I've done some searching and have noticed that the 1.0-96xx driver supports the Nvidia GeForece2 Go chip for linux. The link is located at...

[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

It also seems like Envy may not have caught up to the latest version of Ubuntu. I do know that I had to manually load in the driver myself or use Envy to do it. 

If you can download and install the Linux driver for the Nvidia GeForece2 Go card on your laptop then I don't see why it wouldn't work for you. I don't know if it's compatible with the latest version of Ubuntu so there may be some trial and error experimentation to get it to work.

When you download the driver extract it. There should be an instruction file supplied within the archive on how to make the install script. You need to do this so that the driver can install properly on you laptop model and Ubuntu version. To load in the linux driver manually you'll need to exit Gnome and log in under a shell...

CTRL+ALT+F1 "Jumps to the 1st console"
login
sudo /etc/init.d/gdm stop "Stops GDM"

Change directory to where you extracted the driver files. If you are not familiar with the old fashioned key commands then type man cd for instructions on how to use the command. Type <ctrl><Z> to exit the manual page. Follow the NVIDIA driver instructions to load in the driver. You'll need to type in sudo prior to the command since sudo allows the install script the required permissions to modify the system. Linux and Unix in general have an all powerful user called the Super-user. In Ubuntu the Super-user is invoked by the sudo command.

Prior to doing any of this make sure you backup any critical information from your laptop. Also, if the driver install script states that the driver is not compatible at any time in the install process then abort. This means that the version of Ubuntu you are trying to use is not compatible with the Nvidia GeForece2 Go card on your laptop. This can happen with any operating system. Old drivers are phased out to make sure that the operating system is more compliant with newer hardware architecture.

If this is the case you can always load in an older version of Ubuntu that is compatible with the Nvidia GeForece2 Go card on your laptop. I know its not the best option but it may allow you to use the graphic effects. I currently have older versions of Ubuntu loaded onto several desktop units at work. These are legacy systems that cannot run newer versions of Ubuntu. Two even have the first version Xubuntu loaded.

Let me know how it turns out. Feel free to ask more questions.

Good Luck.

---

### Post by cbbnewbie on 2010-05-09
downloaded the driver but how do i extract it its in ".run"

---

### Post by cbbnewbie on 2010-05-09
figured out the ".run" problem sorry. I installed it but on the first screen an error showed about scripts(distribution provided pre-install script failed), then i continue after installation i reboot i did not reenable gdm forgot about it or is it ok that way. Anyway before the login screen appears the screen blinked 3 times then a window appeared saying an error. It says ubuntu is now running in low-graphics mode.....failed to load nvidia ... module, screens found but none have usable configuration. I clicked ok then i created a new configuration from the menus and log in,, i think the driver didn't install well i tried doing it again but failed because it says im running an x server and says to hmm close it i tried the sudo /etc/init.d/gdm stop but didnt work so now im stuck here without visual effects although usable i still want my ubuntu to be running with no problems, thanks for helping out im now getting used to things. What should i do now? should i revert it or use the hardware drivers instead.

---

### Post by brigadoon on 2010-05-09
It sounds as if the driver architecture is too old to run with the version of Ubuntu you are running. If you are not using Ubuntu for anything requiring 3-D graphics then I would run with the default video driver originally loaded in when you installed Ubuntu. If you need the 3-D effects for a game or studio application then You may want to try an earlier version of Ubuntu. The revision history can be found at...

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

Most can be downloaded at...

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

The Nvidia driver and your chip may work with one of these Ubuntu versions.

---

### Post by StuartIanNaylor on 2010-05-13
There is a fix for this and it has nothing to do with Lucid not supporting GeForce4 420 Go.

The GeForce4 420 Go is a pain and like the Toshiba Satellite Pro I have been battling with it would seem if you have a GeForce4 420 Go then you are going to have problems.

Basically the answer to your question is here ----> [http://blog.freshnewpage.com/2008/04/26/nvidia-geforce4-420-go-on-ubuntu-804-hardy-heron/](http://blog.freshnewpage.com/2008/04/26/nvidia-geforce4-420-go-on-ubuntu-804-hardy-heron/)

Make sure you put the digital panel option in you screen section as some tips seem to put this in the device section. This works with Jaunty but not with Lucid.

Strangely on a reboot I still got stripey lines on the screen but persevering I did a cold start and I got to the funny resolution stage of 	"969x768"

Follow the steps in the above url.

PS I usually do a sudo nautilus to move files with root permissions.

I am going to paste the url content here just to keep it.
    	 		**[freshnewpage blog]("http://blog.freshnewpage.com/")**

 		 	
 
   	  	 		 			« [Hello!]("http://blog.freshnewpage.com/2008/04/22/hello/")
 			 		
  		 			**[NVIDIA GeForce4 420 Go on Ubuntu 8.04 (Hardy Heron)]("http://blog.freshnewpage.com/2008/04/26/nvidia-geforce4-420-go-on-ubuntu-804-hardy-heron/")**

  			 				**Preamble**
 This is a guide to installing [NVIDIA]("http://nvidia.com/") drivers  for a GeForce4 420 Go  graphics card on [Ubuntu]("http://www.ubuntu.com/"). This guide was tested on a [Toshiba Satellite Pro 2100]("http://uk.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/SUPPORTSECTION/discontinuedProductPage.do?PRODUCT_ID=45659&DISC_MODEL=1&service=UK") running [Ubuntu 8.04]("http://www.ubuntu.com/")  but should work for other laptops with GeForce4 420 Go graphics cards  and other versions of Ubuntu.
 **Introduction**
 On a laptop with a GeForce4 420 Go, Ubuntu will recognise there is an  NVIDIA card and offer to install the restricted driver. Installing this  driver will cause two problems.
 
[LIST=1]
[*]On rebooting the screen will be blankThis is because the driver is causing the graphics card to output on  the VGA port rather than to the laptop screen.
[*]The correct resolution is not available once driver is working.This is because the [EDID]("http://en.wikipedia.org/wiki/EDID") data being supplied to the driver  is not correct.
[/LIST]
 **Requirements**
 
[LIST]
[*]laptop with a GeForce4 420 Go graphics card.
[*]Ubuntu (assumed to be a clean install)
[*]the correct maximum resolution of your display (e.g. 1024×768)
[/LIST]
 **Installation**
 The first stage is to check the correct repositories are enabled.
 
[LIST]
[*]Go to: “System -> Administration -> Software Sources”
[*]Under the “Ubuntu Software” tab ensure the first three boxes are  ticked (main, universe and restricted).
[/LIST]
 Next the restricted NVIDIA driver must be enabled.
 
[LIST]
[*]Go to: “System -> Administration -> Hardware Drivers”
[*]Tick the box next to “NVIDIA accelerated graphics driver”.
[*]Close the window and confirm the changes.
[/LIST]
 You should be informed that a restart of the computer is required  before the changes will take effect. Do this now. Do not be alarmed if  the computer has a blank screen after the restart; this is expected.
 Now we will change the “xorg.conf” file to tell the driver to output  to the laptop screen rather than the VGA port.
 
[LIST]
[*]Press “Ctrl + Alt + F1&#8243; to open a terminal.
[*]Login
[*]As root, open “/etc/X11/xorg.conf” for editing.
sudo vim /etc/X11/xorg.conf
(you can use the editor you are most comfortable with in place of “vim”  e.g. nano)
[*]Find the “Device” section (look for the line Section "Device")  and insert as the last line of that section (before the EndSection)
Option "UseDisplayDevice" "DFP-0"
[*]Now save and close the file.
[*]Restart the X server by typing$ sudo /etc/init.d/gdm restart
[/LIST]
 You should now see the login window but it will likely be at the  wrong resolution. First check that the desired resolution really is not  available. For example on the Toshiba Laptop the screen resolution  should be 1024×768.
 
[LIST]
[*]Go to: “System -> Preferences -> Screen Resolution” and see if  the correct resolution is available.
[/LIST]
 If the correct resolution is available then select it and everything  should now be working. If the correct resolution is not available then  you have encountered the EDID problem. This requires some additional  packages to fix. First we must install “nvidia-settings, ghex and  read-edid”
 
[LIST]
[*] Open a terminal “Applications -> Accessories -> Terminal”
[*] Run:$ sudo apt-get install nvidia-settings ghex read-edid
[/LIST]
 We now need to obtain the EDID data.
 
[LIST]
[*]Go to: “System -> Administration -> NVIDIA X Server Setting”
[*]From the left hand list choose: “DFP-0 - (Nvidia Default Flat  Panel)”
[*]Click the “Aquire EDID” button.
[*]Save “edid.bin” to the desktop. (click “Desktop” then click “OK”)
[*]Close “NVIDIA X Server Settings” window.
[/LIST]
 Now we need to check the EDID data.
 
[LIST]
[*]In the terminal change directory to the Desktop (or where the EDID  data was saved to).$ cd ~/Desktop
[*]Check the resolution mode in the EDID data.$ parse-edid edid.bin | grep "Mode "

[/LIST]
 The output should look something like this:
parse-edid: parse-edid version 1.4.1
parse-edid: EDID checksum passed.
Mode 	"969x768"	# vfreq 60.004Hz, hfreq 48.363kHz

 Here you can see that the EDID data has an incorrect resolution of  “969×768&#8243;. The resolution is stored in the EDID file as a [hexadecimal]("http://en.wikipedia.org/wiki/hexadecimal")  value. We need to correct the value. To do this we have to edit  “ebid.bin” with a hexadecimal editor. We will keep the terminal window  open while we do this.
 
[LIST]
[*]Go to: “Applications  -> Programming -> Hex Editor”
[*]Click: “File -> Open -> Desktop -> edid.bin -> Open”
[/LIST]
 You should now be looking at the “ebid.bin” in hexadecimal format.  The data is represented as pairs of hexadecimal characters. Each pair  correspodes to one [byte.]("http://en.wikipedia.org/wiki/byte") Notice that there are 17 bytes in a row. The  bytes are indexed from zero so the last byte on the first line is the  sixteenth byte.
 We need to change the horizontal resolution. This is slightly  confusingly split across two bytes. When converted to a hexadecimal  value,  the first digit of the value is stored in the first charater of  the 58th byte and the last two digits of the value are stored in the  56th byte. In our example the resolution in the EDID file is 969. We can  use the calculator to convert this to hexadecimal.
 
[LIST]
[*]Go to:  “Applications -> Accessories -> Calculator -> View  -> Scientific”
[*]Click “Dec” to put the calculator into decimal mode.
[*]Then enter the number “969&#8243;
[*]Click “Hex” to convert the number to hexadecimal.
[/LIST]
 You should get the answer 3C9 (hex). The 56th and 58th bytes are show  on the forth line of the hex editor. This is the forth line from my  file with the releveant characters in bold:
 “01 01 01 64 19 **C9** 77 **3**1 00  26 30 4F 88 36 00 42 FF ”
 Notice how the value is written with the last two digits then the  first digit.
 In my example the desired resolution is 1024. Converted to  hexadecimal this is 400 (hex). Hence the 56th byte of my EDID file  should be “00&#8243; and the first character of the 58th byte should be “4&#8243;.  The new line in the file is:
 “01 01 01 64 19 **00** 77 **4**1 00  26 30 4F 88 36 00 42 FF ”
 Save the file and re-run parse-edid. (You can go to the terminal and  press the up arrow and enter). The output should now look like this:
parse-edid: parse-edid version 1.4.1
parse-edid: EDID checksum failed - data is corrupt. Continuing anyway.
Mode 	"1024x768"	# vfreq 57.645Hz, hfreq 46.462kHz

Don’t worry about the fact the checksum failed. This is not important.  We now need to copy the “edid.bin” in to the X configuration directory  and set it to override the real EDID data.
 
[LIST]
[*] Copy the “edid.bin” to /etc/X11/$ sudo cp edid.bin /etc/X11/
[*]Edit “xorg.conf” to override EDID.$ vim /etc/X11/xorg.conf
[*]In the “Screen” section, insert the line:     Option      "CustomEDID" "DFP-0:/etc/X11/edid.bin"
[*]Save the file and restart the computer.
[/LIST]
oooof I love ubuntu

Stuart

---

### Post by brigadoon on 2010-05-16
The preceding post by StuartIanNaylor is more or less the edid.bin fix that has been posted in several locations on the web. Everything posted by StuartIanNaylor is relevant to the difficulties of having the 420 Go driver run with various versions of Ubuntu and providing a solution. 

However, this posting has been dormant for quite some time. I was surprised to find that anyone was using any of the old video chips anymore. The last question posted was from cbbnewbie. In this last question cbbnewbie is asking whether or not this post or those similar to it would work for the ***GeForece2 Go*** driver when trying to activate the 3D graphics for Ubuntu screen effects. If anyone has had any success getting the GeForece2 Go driver working with any version of Ubuntu please respond to cbbnewbie's question.

To cbbnewbie: Please let us know if you were able to solve your particular problem with 3D effects. Someone else may have a similar issue with the same driver. They may benefit from you solution.

To everyone else: If you know of a verifiable solution to getting the GeForece2 Go driver working with 3D graphics please post a reply for cbbnewbie's benefit. Thanks to all.

---

### Post by cbbnewbie on 2010-05-16
Hello to all, at the momment im using xubuntu 10.04 and my problem with 3D graphics seems to be fixed for now as long as i do the following.

@**cant enable visual effects:** what i did is not to touch those settings on Appearance Settings>Visual Effects tab. I just installed my graphics card driver through Hardware Drivers on System Tools. Then let compiz do the visual effects the problem is that my resolution stays at 800x600.

@**changing to resolution higher than 800x600**: its hard to navigate when the resolution is 800x600 especially on firefox but everytime i change the resolution through X server settings bad things happen, so i searched for a solution and came accross this command 

*sudo nvidia-xconfig --ad-argb-glx-visuals -d 24*

**i dont really know what it does** im a noob (smart people please explain) but it worked now i was able to change my resolution to 1024x768 without the visual effects disappearing

@**vlc can't play movies it just disappears**: in connection with graphics card problems I also came across this problem, I cant play any movies at any movie player, my solution for this is to turn off compiz and replace it with the default window manager when i will watch a movie zzz.

*metacity --replace* (replace metacity with openbox or whatever you are using)

That is all i did thanks to this forum and the wonderfull people in it. Hope this does help to some, sorry if this is not that comprehensive.

---

### Post by travlemon on 2010-05-23
> **StuartIanNaylor said:**
> There is a fix for this and it has nothing to do with Lucid not supporting GeForce4 420 Go.

The GeForce4 420 Go is a pain and like the Toshiba Satellite Pro I have been battling with it would seem if you have a GeForce4 420 Go then you are going to have problems.

Basically the answer to your question is here ----> [http://blog.freshnewpage.com/2008/04/26/nvidia-geforce4-420-go-on-ubuntu-804-hardy-heron/](http://blog.freshnewpage.com/2008/04/26/nvidia-geforce4-420-go-on-ubuntu-804-hardy-heron/)

Make sure you put the digital panel option in you screen section as some tips seem to put this in the device section. This works with Jaunty but not with Lucid.

Strangely on a reboot I still got stripey lines on the screen but persevering I did a cold start and I got to the funny resolution stage of     "969x768"

Follow the steps in the above url.

PS I usually do a sudo nautilus to move files with root permissions.

I am going to paste the url content here just to keep it.
                 **[freshnewpage blog]("http://blog.freshnewpage.com/")**

              
 
                                   « [Hello!]("http://blog.freshnewpage.com/2008/04/22/hello/")
                      
                       **[NVIDIA GeForce4 420 Go on Ubuntu 8.04 (Hardy Heron)]("http://blog.freshnewpage.com/2008/04/26/nvidia-geforce4-420-go-on-ubuntu-804-hardy-heron/")**

                               **Preamble**
 This is a guide to installing [NVIDIA]("http://nvidia.com/") drivers  for a GeForce4 420 Go  graphics card on [Ubuntu]("http://www.ubuntu.com/"). This guide was tested on a [Toshiba Satellite Pro 2100]("http://uk.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/SUPPORTSECTION/discontinuedProductPage.do?PRODUCT_ID=45659&DISC_MODEL=1&service=UK") running [Ubuntu 8.04]("http://www.ubuntu.com/")  but should work for other laptops with GeForce4 420 Go graphics cards  and other versions of Ubuntu.
 **Introduction**
 On a laptop with a GeForce4 420 Go, Ubuntu will recognise there is an  NVIDIA card and offer to install the restricted driver. Installing this  driver will cause two problems.
 
[LIST=1]
[*]On rebooting the screen will be blankThis is because the driver is causing the graphics card to output on  the VGA port rather than to the laptop screen.
[*]The correct resolution is not available once driver is working.This is because the [EDID]("http://en.wikipedia.org/wiki/EDID") data being supplied to the driver  is not correct.
[/LIST]
 **Requirements**
 
[LIST]
[*]laptop with a GeForce4 420 Go graphics card.
[*]Ubuntu (assumed to be a clean install)
[*]the correct maximum resolution of your display (e.g. 1024×768)
[/LIST]
 **Installation**
 The first stage is to check the correct repositories are enabled.
 
[LIST]
[*]Go to: “System -> Administration -> Software Sources”
[*]Under the “Ubuntu Software” tab ensure the first three boxes are  ticked (main, universe and restricted).
[/LIST]
 Next the restricted NVIDIA driver must be enabled.
 
[LIST]
[*]Go to: “System -> Administration -> Hardware Drivers”
[*]Tick the box next to “NVIDIA accelerated graphics driver”.
[*]Close the window and confirm the changes.
[/LIST]
 You should be informed that a restart of the computer is required  before the changes will take effect. Do this now. Do not be alarmed if  the computer has a blank screen after the restart; this is expected.
 Now we will change the “xorg.conf” file to tell the driver to output  to the laptop screen rather than the VGA port.
 
[LIST]
[*]Press “Ctrl + Alt + F1&#8243; to open a terminal.
[*]Login
[*]As root, open “/etc/X11/xorg.conf” for editing.
sudo vim /etc/X11/xorg.conf
(you can use the editor you are most comfortable with in place of “vim”  e.g. nano)
[*]Find the “Device” section (look for the line Section "Device")  and insert as the last line of that section (before the EndSection)
Option "UseDisplayDevice" "DFP-0"
[*]Now save and close the file.
[*]Restart the X server by typing$ sudo /etc/init.d/gdm restart
[/LIST]
 You should now see the login window but it will likely be at the  wrong resolution. First check that the desired resolution really is not  available. For example on the Toshiba Laptop the screen resolution  should be 1024×768.
 
[LIST]
[*]Go to: “System -> Preferences -> Screen Resolution” and see if  the correct resolution is available.
[/LIST]
 If the correct resolution is available then select it and everything  should now be working. If the correct resolution is not available then  you have encountered the EDID problem. This requires some additional  packages to fix. First we must install “nvidia-settings, ghex and  read-edid”
 
[LIST]
[*] Open a terminal “Applications -> Accessories -> Terminal”
[*] Run:$ sudo apt-get install nvidia-settings ghex read-edid
[/LIST]
 We now need to obtain the EDID data.
 
[LIST]
[*]Go to: “System -> Administration -> NVIDIA X Server Setting”
[*]From the left hand list choose: “DFP-0 - (Nvidia Default Flat  Panel)”
[*]Click the “Aquire EDID” button.
[*]Save “edid.bin” to the desktop. (click “Desktop” then click “OK”)
[*]Close “NVIDIA X Server Settings” window.
[/LIST]
 Now we need to check the EDID data.
 
[LIST]
[*]In the terminal change directory to the Desktop (or where the EDID  data was saved to).$ cd ~/Desktop
[*]Check the resolution mode in the EDID data.$ parse-edid edid.bin | grep "Mode "
[/LIST]
 The output should look something like this:
parse-edid: parse-edid version 1.4.1
parse-edid: EDID checksum passed.
Mode     "969x768"    # vfreq 60.004Hz, hfreq 48.363kHz

 Here you can see that the EDID data has an incorrect resolution of  “969×768&#8243;. The resolution is stored in the EDID file as a [hexadecimal]("http://en.wikipedia.org/wiki/hexadecimal")  value. We need to correct the value. To do this we have to edit  “ebid.bin” with a hexadecimal editor. We will keep the terminal window  open while we do this.
 
[LIST]
[*]Go to: “Applications  -> Programming -> Hex Editor”
[*]Click: “File -> Open -> Desktop -> edid.bin -> Open”
[/LIST]
 You should now be looking at the “ebid.bin” in hexadecimal format.  The data is represented as pairs of hexadecimal characters. Each pair  correspodes to one [byte.]("http://en.wikipedia.org/wiki/byte") Notice that there are 17 bytes in a row. The  bytes are indexed from zero so the last byte on the first line is the  sixteenth byte.
 We need to change the horizontal resolution. This is slightly  confusingly split across two bytes. When converted to a hexadecimal  value,  the first digit of the value is stored in the first charater of  the 58th byte and the last two digits of the value are stored in the  56th byte. In our example the resolution in the EDID file is 969. We can  use the calculator to convert this to hexadecimal.
 
[LIST]
[*]Go to:  “Applications -> Accessories -> Calculator -> View  -> Scientific”
[*]Click “Dec” to put the calculator into decimal mode.
[*]Then enter the number “969&#8243;
[*]Click “Hex” to convert the number to hexadecimal.
[/LIST]
 You should get the answer 3C9 (hex). The 56th and 58th bytes are show  on the forth line of the hex editor. This is the forth line from my  file with the releveant characters in bold:
 “01 01 01 64 19 **C9** 77 **3**1 00  26 30 4F 88 36 00 42 FF ”
 Notice how the value is written with the last two digits then the  first digit.
 In my example the desired resolution is 1024. Converted to  hexadecimal this is 400 (hex). Hence the 56th byte of my EDID file  should be “00&#8243; and the first character of the 58th byte should be “4&#8243;.  The new line in the file is:
 “01 01 01 64 19 **00** 77 **4**1 00  26 30 4F 88 36 00 42 FF ”
 Save the file and re-run parse-edid. (You can go to the terminal and  press the up arrow and enter). The output should now look like this:
parse-edid: parse-edid version 1.4.1
parse-edid: EDID checksum failed - data is corrupt. Continuing anyway.
Mode     "1024x768"    # vfreq 57.645Hz, hfreq 46.462kHz

Don’t worry about the fact the checksum failed. This is not important.  We now need to copy the “edid.bin” in to the X configuration directory  and set it to override the real EDID data.
 
[LIST]
[*] Copy the “edid.bin” to /etc/X11/$ sudo cp edid.bin /etc/X11/
[*]Edit “xorg.conf” to override EDID.$ vim /etc/X11/xorg.conf
[*]In the “Screen” section, insert the line:     Option      "CustomEDID" "DFP-0:/etc/X11/edid.bin"
[*]Save the file and restart the computer.
[/LIST]
oooof I love ubuntu

Stuart

Hey! Thanks for this fix! I had MEPIS installed on a junky kitchen laptop just meant for simple browsing.  The fix didn't work on MEPIS.  I simply wiped out the machine and did a clean install of Ubuntu 10.04 and followed this step for step. Worked great! Thanks again for the fix! I thought that horrible video issue would never have a solution.

For reference for anyone else who sees this, the machine I did this on was a Toshiba Satellite 6100 Pro with an Nvidia Geforce4 420 Go onboard graphics card.  Piece of junk! Thanks again!

---

### Post by cziss on 2010-10-16
Hello, could you help me please? Does anyone know how to make working this graphic card in new Xubuntu 10.10? EnvyNG seems not to be for this version:(.

---

