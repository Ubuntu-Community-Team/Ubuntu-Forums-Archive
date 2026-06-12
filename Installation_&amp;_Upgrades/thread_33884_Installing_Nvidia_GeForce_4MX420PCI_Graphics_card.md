---
title: "Installing Nvidia GeForce 4MX420PCI Graphics card"
date: 2005-05-12
forum: Installation &amp; Upgrades
---

### Post by Frankly on 2005-05-12
After installing Hoary and doing updates and installing multimedia features I tried to install my PNY  GF4MX420PCI graphics card. PC seems to boot but instead of getting GUI I get a black/empty screen. Removing the card and booting with the onboard Intel graphics is ok again.

I have read all the forums and how too's but still dont get it right.I tried to install the Nvidia drivers while I was running with onboard graphics and then put the Nvidia card in but still nothing. I think many newbies hit this wall.

/home/frank/Desktop/Screenshot.png

Please help
Thanx

---

### Post by Laemel on 2005-05-12
Have you tried disabling your onboard video in your BIOS? Sometimes there will be a section in your BIOS setup called "integrated peripherals" or something, and you can go in there and disable your video card, thus avoiding daul-video-card conflicts.

When you booted up with the Geforce and got a black screen, did you try plugging your monitor into both the onboard video and the Geforce?

If you hit Ctrl+Alt+F1 can you access the command prompt?

Also, I guess posting your /etc/X11/xorg.conf would be a good idea...

---

### Post by Frankly on 2005-05-12
I have option for primary graphics in bios, between Onboard and PCI. It is set on PCI.  I have plugged monitors in both and swopping out.

Just after it says gnome is loading  the black screen comes up. CRL + ALT+ F1 has no effect.

I have no idea what /etc/X11/xorg.conf  is or where and how to get it.LOL Guess its back to WindowsXP

---

### Post by Laemel on 2005-05-13
[QUOTE=Frankly]I have option for primary graphics in bios, between Onboard and PCI. It is set on PCI.  I have plugged monitors in both and swopping out.

Just after it says gnome is loading  the black screen comes up. CRL + ALT+ F1 has no effect.

I have no idea what /etc/X11/xorg.conf  is or where and how to get it.LOL Guess its back to WindowsXP[/QUOTE]
 You might try reinstalling with the Geforce in...  Hoary might have an easier time detecting it then, since it creates your graphics configuration at that time.

---

### Post by Frankly on 2005-05-13
Doing install number 13 on Friday the 13th. Maybe I will get it to work this time. At least I have learned how to make TV, DVD play and some music files play. Some crash course is needed before attemting Linux. I am starting to appreciate my Windows XP. But its FREE so hey lets try some more.
LOL

---

### Post by crane on 2005-05-13
Try installing drivers, installing card. then boot to live cd and look at you config file.
If the live cd works then you could look at it's config and maybe copy it to the one on your system.

---

### Post by Laemel on 2005-05-13
[QUOTE=Frankly]Doing install number 13 on Friday the 13th. Maybe I will get it to work this time. At least I have learned how to make TV, DVD play and some music files play. Some crash course is needed before attemting Linux. I am starting to appreciate my Windows XP. But its FREE so hey lets try some more.
LOL[/QUOTE]

Trust me, keep trying.  I only converted to Linux about a month ago, and for the first week or two I was thinking exactly the same thing: "Man... this really makes me appreciate how easy Windows was."  But once you get over that threshold and get comfortable with Linux, it's beautiful.

If you're looking for some beginner guides to Linux, there are lots of good ones around. You might start by with [this one](http://www.ubuntulinux.org/wiki/UbuntuHowCome) that's written by the Ubuntu people.  There are also a wide range of guides at [the Linux Documentation Project](http://www.tldp.org/guides.html).  A few you might want to start with are:

[An Introduction to Linux](http://www.tldp.org/LDP/intro-linux/html/intro-linux.html), and
[A Guide to the Linux Filesystem Hierarchy](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html), which explains what all those directories on your computer are for (like /etc, and /bin).

---

### Post by Frankly on 2005-05-13
Thanx for all the advice and support. Sure need it when Hoary gets hairy.

I have installed Kubuntu now. I installed with card IN and still no luck. I plugged a 2nd monitor into onboard and that does works. From the onboard monitor I can see in KinfoCenter under PCI that the card details are displayed correctly there. Now I haven't attempted anything else before I get further advise and courage.lol.I am downloading the live Kubuntu cd to try Crane's advice.

I am sure anybody with a little knowledge it wont be a problem, but I have zero knowledge and I guess reading books before installing hardware is part of the Linux free fun.

I have a bunch of old pc's which I am trying to re-erect with Kubuntu for disadvantaged kids and really hope I can make this work.

---

### Post by Laemel on 2005-05-13
Does the Nvidia card work at all? For instance, can you see your bios with it? When Linux starts, do you see all the text scolling by before the graphical part comes up?  Or do you get nothing, ever?

---

### Post by Frankly on 2005-05-14
Yes the card works fine, run Windows XP and also when booting Ubuntu or Kubuntu shows everyting during bootup till GUI is suppose to come up and then give me the black screen. Same black screen with live cd.
Same thing during many installs.. back to RTFM

Thanx

---

### Post by Frankly on 2005-05-14
OK I have found the  /etc/X11/xorg.conf 

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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
 FontPath "unix/:7100"   # local font server
 # if the local font server has problems, we can fall back on these
 FontPath "/usr/lib/X11/fonts/misc"
 FontPath "/usr/lib/X11/fonts/cyrillic"
 FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
 FontPath "/usr/lib/X11/fonts/Type1"
 FontPath "/usr/lib/X11/fonts/CID"
 FontPath "/usr/lib/X11/fonts/100dpi"
 FontPath "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
 Load "bitmap"
 Load "dbe"
 Load "ddc"
 Load "dri"
 Load "extmod"
 Load "freetype"
 Load "glx"
 Load "int10"
 Load "record"
 Load "type1"
 Load "vbe"
EndSection

Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver  "keyboard"
 Option  "CoreKeyboard"
 Option  "XkbRules" "xorg"
 Option  "XkbModel" "pc104"
 Option  "XkbLayout" "us"
EndSection

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver  "mouse"
 Option  "CorePointer"
 Option  "Device"  "/dev/input/mice"
 Option  "Protocol"  "ImPS/2"
 Option  "Emulate3Buttons" "true"
 Option  "ZAxisMapping"  "4 5"
EndSection

Section "Device"
 Identifier "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
 Driver  "i810"
 BusID  "PCI:0:1:0"
EndSection

Section "Monitor"
 Identifier "Generic Monitor"
 Option  "DPMS"
 HorizSync 28-49
 VertRefresh 43-72
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device  "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
 Monitor  "Generic Monitor"
 DefaultDepth 24
 SubSection "Display"
  Depth  1
  Modes  "1024x768" "800x600" "720x400" "640x480" "640x350"
 EndSubSection
 SubSection "Display"
  Depth  4
  Modes  "1024x768" "800x600" "720x400" "640x480" "640x350"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1024x768" "800x600" "720x400" "640x480" "640x350"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1024x768" "800x600" "720x400" "640x480" "640x350"
 EndSubSection
 SubSection "Display"
  Depth  16
  Modes  "1024x768" "800x600" "720x400" "640x480" "640x350"
 EndSubSection
 SubSection "Display"
  Depth  24
  Modes  "1024x768" "800x600" "720x400" "640x480" "640x350"
 EndSubSection
EndSection

Section "ServerLayout"
 Identifier "Default Layout"
 Screen  "Default Screen"
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
EndSection

Section "DRI"
 Mode 0666
EndSection


I think I have to install Gnome again as there seems to be more RTFM available. KDE might be better for kids though.

---

### Post by Laemel on 2005-05-14
[QUOTE=Frankly]Yes the card works fine, run Windows XP and also when booting Ubuntu or Kubuntu shows everyting during bootup till GUI is suppose to come up and then give me the black screen. Same black screen with live cd.
Same thing during many installs.. back to RTFM

Thanx[/QUOTE]

Ok.. That means that the problem is just with your X config.  See how in xorg.conf, your Intel video card is listed, but nothing is mentioned about nVidia?  Try following [these instructions](http://ubuntuguide.org/#installnvidiadriver) for installing the nVidia video drivers and recreating xorg.conf.

Gnome has nothing to do with this... it's definetly an X problem.  Also, I disagree that KDE would be better.  Gnome is much simpler and easier to use IMO.  KDE has tons and tons of options and included programs that make it a bit confusing to people who aren't great at computers... just my opinion (For all I know, the kids are better than me at computers :P)...

Anyway, try those instructions, and if that doesn't work I'll try and help you set up your xorg.conf manually.

---

### Post by Frankly on 2005-05-14
I have installed Ubuntu again.

During Nvidia driver install, in step 4., where is this "new file" that need to be edited? I do step 2 and then look for a file named nvidia? sorry not clear to me
been here before and then after ctrl=alt=backspace i see nothing...not on onboard or nvidia.
thanx

---

### Post by Laemel on 2005-05-15
[QUOTE=Frankly]I have installed Ubuntu again.

During Nvidia driver install, in step 4., where is this "new file" that need to be edited? I do step 2 and then look for a file named nvidia? sorry not clear to me
been here before and then after ctrl=alt=backspace i see nothing...not on onboard or nvidia.
thanx[/QUOTE]
 So, if I understand you, you're having a problem with step 3?  The parts in black (such as step 3) are commands that you're supposed to type in at a prompt.  so after finishing stip 2, you just go to a command prompt and type in "sudo apt-get install nvidia-glx", and then hit enter and type in your password.  Then type in the next thing, etc...

---

### Post by Frankly on 2005-05-15
Step 3 is running the commands, I have done that

Then step 4.
Insert the following lines into the **new file ** [Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

Where is this new file?

---

### Post by Frankly on 2005-05-15
After yet another install I ran the Nvidia installation script and then there appeared an empty file which I edited and saved as instructed. On restart I get the following message on ablue screen  

I cannot start thr X server (your graphical interface). It is likely that it is not set up correctly. Would you like yo view the X server output to diagnose the problem?
   <yes>    <no>

Then says  I will disable this X server for now. Restart GDM when it is configured correctly. <ok>

---

### Post by crane on 2005-05-15
[QUOTE=Frankly]Thanx for all the advice and support. Sure need it when Hoary gets hairy.

I have installed Kubuntu now. I installed with card IN and still no luck. I plugged a 2nd monitor into onboard and that does works. From the onboard monitor I can see in KinfoCenter under PCI that the card details are displayed correctly there. Now I haven't attempted anything else before I get further advise and courage.lol.I am downloading the live Kubuntu cd to try Crane's advice.

I am sure anybody with a little knowledge it wont be a problem, but I have zero knowledge and I guess reading books before installing hardware is part of the Linux free fun.

I have a bunch of old pc's which I am trying to re-erect with Kubuntu for disadvantaged kids and really hope I can make this work.[/QUOTE]

You said you can plug the monitor into your onboard video and it works? Have you checked your bios and cut the on board video off., Could be causing conflicts. Also I had to change my bios setting for plug and play to no. (somewhere in your bios it should ask if it's a plug and play OS, set it to no) Seems it too can sometimes cause conflicts.

Just a couple things I thought of, if they have already been mentioned please ignore this post.

---

### Post by crane on 2005-05-15
[QUOTE=Frankly]After yet another install I ran the Nvidia installation script and then there appeared an empty file which I edited and saved as instructed. On restart I get the following message on ablue screen  

I cannot start thr X server (your graphical interface). It is likely that it is not set up correctly. Would you like yo view the X server output to diagnose the problem?
   <yes>    <no>

Then says  I will disable this X server for now. Restart GDM when it is configured correctly. <ok>[/QUOTE]

Once it kills Xserver look at xorg.conf dile and make sure you have your driver set to nvidia not nv.

---

### Post by Laemel on 2005-05-15
[QUOTE=Frankly]After yet another install I ran the Nvidia installation script and then there appeared an empty file which I edited and saved as instructed. On restart I get the following message on ablue screen  

I cannot start thr X server (your graphical interface). It is likely that it is not set up correctly. Would you like yo view the X server output to diagnose the problem?
   <yes>    <no>

Then says  I will disable this X server for now. Restart GDM when it is configured correctly. <ok>[/QUOTE]

 Ya... on the last command in step 3, where you say "sudo gedit .....", that starts the text editor with a new blank file and then you type in that stuff in step 4 and save it. (Note: if you're stuck at a prompt with no graphics, you can say "sudo nano -w /path/filename" to use a text-mode editor)


I think that the automatic X configuration is just detecting the onboard video and then quiting at that point, so it never gets to your nVidia card.  If you're up for it, you can try to configure it yourself.  So, start up Ubuntu in failsafe mode, and when you get to the prompt, type:```
lspci
```That will list all the devices in your comuter, and somewhere in that list, you should see your nVidia GeForce.  Now, the important thing to find here is the "bus ID".  That's the number on the left.  For my compuer the output of lspci reads
```
0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4400] (rev a2)
0000:02:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:02:07.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
0000:02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```You can see there that my Geforces bus id is 0000:01:00.0.  Now, only the last three numbers are important (for mine, they are 1, 0, and 0) So make a note of those numbers, and then type:```
nano -w /etc/X11/xorg.conf
```That will bring up your X configuration in a text editor. Scroll down until you find a section called "Device".  Then, where it says BusID, change the value to your new bus id, starting with PCI and seperated by ":".  For me, that line reads:```
BusID    "PCI:1:0:0"
``` so make your like that but with whatever three numbers you got from lspci.  Also, change the Driver option to "nvidia".  Then hit Ctrl+x, and say yes you want to save, and hit enter.  Now you'll be back at the command prompt. Restart and see what happens.

P.S.  If that doesn't work, you could try putting "nv" for the driver.

---

### Post by Frankly on 2005-05-16
I thought we had it but when I saved I got message  [ Could not open file for writing : Permission denied ]

---

### Post by Laemel on 2005-05-16
Sorry... I forgot to put "sudo" in front of it.  If you ever need root access to do something in Ubuntu, you just slap "sudo" before the command.  So for editing the file, you'd do "sudo nano -w /etc/X11/xorg.conf"

---

### Post by Frankly on 2005-05-16
It's up and running!  :grin: Thank you for helping and sticking it out with me. Much appreciated. This seems to be a newbie illiminator, common problem that is way beyond most newbies abillities. I saw at least two other post with same problem, I will refer em here.

I wonder if it will be possible to run both nvidia and the Intel onboard with two monitors? Just wondering. 

Once again Thanx a LOT \\:D/

---

### Post by Laemel on 2005-05-17
[QUOTE=Frankly]It's up and running!  :grin: Thank you for helping and sticking it out with me. Much appreciated. This seems to be a newbie illiminator, common problem that is way beyond most newbies abillities. I saw at least two other post with same problem, I will refer em here.

I wonder if it will be possible to run both nvidia and the Intel onboard with two monitors? Just wondering. 

Once again Thanx a LOT \\:D/[/QUOTE]

Glad I could help.. did you get it working by using lspci and editing xorg.conf?

You should be able to get dual monitor working with your video cards, but it's going to take some more playing with xorg.con  What you have to do is have two seperate "Device" sections, one for each video card. Then you need two "Monitor" sections, one for each.  And then you create two "Screen" sections, each one using one of the Device/Monitor pairs.  Then in your "ServerLayout" section you add both screens.  I attached my xorg.conf so you can look at how it's set up.  The only thing that will be different from mine is that you will have two seperate video cards with different BusIDs, whereas I have a single videocard with two outputs.  Also note the "ServerFlags" section at the top that disables Xinerama.

---

### Post by vinoloco on 2005-05-17
Frankly,

Does your card work with *any* live CD distro out there?  

I was having much difficulty with an old Riva TNT2 card.  Just to see it if it worked at all I booted from a Damn Small Linux live CD and it worked fine.  I was then able to copy some settings to the xorg.conf on the Ubuntu system and now it is working fine.  The DSL live CD seems to do a really good job of detecting and autoconfiguring hardware so I use it as my failsafe "testing" config.   Good luck!   And now that I have read further in the thread, it seems like you did get it to work... I agree, this forum (and Linuxquestions) is great for new users.

  -- vino

---

### Post by penguinzrool on 2005-05-18
i've got the same problem, only in a standard desktop with just one Nvida GeForce 2 MX card. Using the nv driver Xorg runs fine, albeit sluggishly in 1024x768 in 16bit. If I follow the instructions to install the Nvidia driver, Ubuntu gets to the point where it starts X and the screen goes blank. The monitor doesn't change resolution (the menu stil shows 720x400) and ctl-alt-backspace does nothing, nor does ctl-alt-f1. Only after ctl-alt-del when the system reboots back to the BIOS screen do I get a display again.

I've checked my xorg.conf file and the BusID is correct, and the driver is listed as nvidia. Changing to nv means the display works, so the rest of the file is OK.

Only other things I've noticed are a warning at startup that the nvidia module taints the kernel, though it still seems to get loaded, some pnp output straight after, and the fact that there's something at the bottom of xorg.conf saying the DRI mode is 666.

Any ideas?

Cheers,
Chris.

---

### Post by penguinzrool on 2005-05-19
Some more info:

the pnp output says that it's initialised 2 new devices, at 01:01.00 and 01:01.02. I thought at first this could be the Twinview setup on the card but then realised that I think it's the sbawe driver loading straight after setting up the gameport etc. Damn...

I tried using the nvidia driver with the 686 kernel as well, which didn't work but at least my PC's faster! I've also tried disabling the glx, dri and GLcore modules but this doesn't solve the problem.

It's funny that this card worked beautifully with no user intervention on Mandrake 8.1 - obviously modern drivers are just getting too complicated! In the meantime I've dropped in a Rage 128 card to make Firefox bearable, but there must be some way to get these nvidia drivers working?!

---

### Post by biggy_paul on 2005-06-24
Thanks for the help.
I installed a Nvidia MX400 but automatic X configuration would only detect the i810. I followed the lspci and manual edit solution and I now have a working NVIDIA setup.

Thanks again.

---

