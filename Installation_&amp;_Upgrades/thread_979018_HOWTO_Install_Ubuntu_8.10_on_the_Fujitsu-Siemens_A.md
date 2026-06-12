---
title: "HOWTO: Install Ubuntu 8.10 on the Fujitsu-Siemens Amilo Li1705"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by Maverickprowls on 2008-11-11
How to install Ubuntu Intrepid Ibex on Amilo Li1705

Grateful thanks to the following forum members, without whose guidance this would not have been possible.
[killwin]("http://ubuntuforums.org/member.php?u=700549") and [yar4ek]("http://ubuntuforums.org/member.php?u=560568")

What you will need:
Willingness to work at the command line - this is not a complicated process, however.
Ability to use nano, or any command line text-editor you're comfortable with
Ubuntu 8.10 Alternate Install CD, available [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") (The nature of the problem with the graphics card in the Li1705 means you will not be able to start X until you have fixed your installation)

1) Insert the alternate install CD into your drive and boot the system.
2) When you are presented with the options menu, press F6 to open the "Further Options" bar.
3) Add the line ```
vga=0x3b8
``` to the list of boot options (This will fix the display for the duration of your text-mode install)
4) Follow the instructions given to you by the installation program.  When the program asks you to eject your CD and allow the system to reboot, do so.  When you see the Boot loader line saying "Press ESC for menu", press ESC to gain access to the Grub boot options window.
5) You will be presented with a series of options, choose the one ending in "Failsafe" and press return to boot your system.
6) After a short while you will see a grey menu screen with a number of options, choose the one allowing you to exit to a "Root console"
7) BE CAREFUL!  You are now at the root prompt, and messing around in the innards of your system using rootly powers is a good way to break your install.  However, nothing I am going to advise you to do here is dangerous to your system.
8) Change to the directory for your X config file by typing ```
cd /etc/X11
```
9) Backup your xorg.conf (this is just paranoia, but a very good habit to get into when changing configuration files) by typing ```
cp ./xorg.conf ./xorg.conf.backup
```
10) Start a text editor, nano is probably the simplest to use ```
nano xorg.conf
```
11) Change the file so it is identical to the one attached to this post, the details are listed below.  Take care with your typing, mistakes in this file will stop your system from working just as much as the original.
		
Changes to make to the file:
>   
[INDENT]Section "Device"
[INDENT]Identifier   "Configured Video Device"
Driver       "openchrome"
Option       "XaaNoImageWriteRect"
Option       "HWCursor" "False"
Option       "SWCursor" "True"[/INDENT]
EndSection
[/INDENT]
  
[INDENT]Section "Monitor"
[INDENT]Identifier   "Configured Monitor"[/INDENT]
EndSection[/INDENT]

[INDENT]Section "Screen"
[INDENT]Identifier   "Default Screen"
Monitor      "Configured Monitor"
Device       "Configured Video Device"
[INDENT]SubSection "Display"
[INDENT]Virtual   1280  800[/INDENT]
EndSubSection[/INDENT][/INDENT]
EndSection[/INDENT]

12) Use Ctrl+X to exit nano, and answer "Yes" when asked if you want to save the changes.
13) When you are returned to the command prompt, type "exit" to exit from the prompt and go back to the grey menu.
14) Choose the option to reboot your system.
15) That's it, your system should reboot and present you with the Ubuntu graphical login screen, you may find that your desktop displays at a lower than expected resolution, but this can be easily fixed in System > Preferences > Screen Resolution

This howto was compiled based on my own experimentation detailed [here]("http://ubuntuforums.org/showthread.php?t=976397"), and from the information provided to me by the aforementioned forum members, and from the following [thread]("http://ubuntuforums.org/showthread.php?t=967198").  All due credit must be paid to the individuals writing in those threads.  
This howto is offered as a collection of the available information in order to help anyone installing Ubuntu on similar machines.

---

### Post by patrichian on 2008-11-20
Sweet! Now I don't have to wait for half an hour before vista starts up anymore!

---

### Post by tzotzolyno on 2008-12-08
Great! I have the same Amilo Li 1705.
Please, tell me how the wireless and the sound works!
I know that there are problems with the sound when need to listen with headphones. Ubuntu doesn't recognises it. 
Anyway, great job and I'll be extremely happy if you'll review how Ubuntu 8.10 rules in our Amilos.

Thank you in advance and sorry for my english.

---

### Post by Maverickprowls on 2008-12-09
> **tzotzolyno said:**
> Great! I have the same Amilo Li 1705.
Please, tell me how the wireless and the sound works!
I know that there are problems with the sound when need to listen with headphones. Ubuntu doesn't recognises it. 
Anyway, great job and I'll be extremely happy if you'll review how Ubuntu 8.10 rules in our Amilos.

Thank you in advance and sorry for my english.

My wireless worked straight away under 8.10 (impressed!), so I haven't actually had to do anything to "fix" it.  I know about the problem with the sound card not outputting to the headphones and I'm trying to get a solution together as we speak.  My searches around this forum and others have lead me to believe that I need to compile a more bleeding-edge alsa driver, but so far I've had no success. I will keep this forum posted if I can discover a fix.

Could I ask you a question, does your screen flicker (under windows or linux), or is it simply bad build quality on my laptop?

---

### Post by tzotzolyno on 2008-12-09
> **Maverickprowls said:**
> 
Could I ask you a question, does your screen flicker (under windows or linux), or is it simply bad build quality on my laptop?

Under XP it doesn't flicker. I've tried Vista too: there are not problems with the screen (in Vista it flickers just after logon, but I've seen that it's normal with others kind of laptops too...e.g. HP).
Under linux I've tried Mandriva 2009 (rc, gnome) and Fedora 10 (KDE). This distributions boots with Live CD-s, have the same problems with the sound but there are not problems with the screen (correct resolution, no flicker).
Anyway, I prefer Ubuntu.


By the way, does the hot butons (Fn+Fx) work in Ubuntu 8.10?

P.S. please, when you'll find the solution of the sound bug, please post here a detailed solution. I've never get a solutions with the indications from the Launchpad.

---

### Post by Maverickprowls on 2008-12-09
I'm glad to report that the function buttons do work (Or at least, Brightness, Mute and Volume Controls do, these are all I've tested). 

I'll be trying to solve the audio problem tomorrow, and will post my progress.

---

### Post by tzotzolyno on 2008-12-10
> **Maverickprowls said:**
> I'm glad to report that the function buttons do work (Or at least, Brightness, Mute and Volume Controls do, these are all I've tested). 

I'll be trying to solve the audio problem tomorrow, and will post my progress.

Perfect! The function buttons doesn't work in Fedora or Mandriva on this Amilo. One more motive to use Ubuntu :)

---

### Post by tzotzolyno on 2008-12-14
I found some interesting indications of resolving this sound bug problem with our Amilo Li 1705 [_**here**_]("http://forums.opensuse.org/applications/multimedia/394709-codecs-again.html").
It's on OpenSuse forum and there are problems with openSUSE 11.0 too. 
The moderator tryied to help the user, and after a cup of work the user says that the sound works. :-({|= Maybe it could be usefull. 
I can't try myself 'cause I'm a complete beginner. ](*,) Sorry.
:popcorn:

---

### Post by beeman on 2009-03-25
Thanks Maverickprowls, the options in xorg.conf was what i was looking for!

You made me a happy man :)

---

### Post by ya_abdoo on 2009-06-20
yesss :D it finally worked 

thank u sooooooooooooooooo much u r wonderful

---

