---
title: "Visual effects"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by ManfredKlinglmair on 2010-06-09
Hello,
my problem is this: until yesterday, I could change my desktop's (Ubuntu 10.4) visual effects (transparency, etc., the standard sort), from low to standard to high as I wished. After a reboot, I'm told visual effects cannot be changed.

What on earth happened? I want a little eye candy! Could anybody tell an inexperienced Ubuntu user what to do?

Thanks a lot,
Manfred

---

### Post by Deadite81 on 2010-06-09
I've been tinkering with effects a lot lately, so maybe I can help.

But I need to know what your running (compiz, kwin...).  Gnome or KDE or something else...

How are you trying to change the effects settings?  From the appearance Preferences "Visual Effects" tab or from CompizConfig Settings Manager?  

What exactly is it telling you?  

If your using Compiz (I assume you are), is "compiz" a running process in your System Monitor?  (Administration -> System Monitor "Processes" tab)

Perhaps I could help if you answer those questions and provide any other relevant information you can think of.

---

### Post by ManfredKlinglmair on 2010-06-09
Hi,
ok, I'll try to provide as much information as I can. I'm new to Linux (& Ubuntu), and such issues are really diminishing user friendliness and the enjoyment of a nice desktop environment.
I'm using Gnome to my knowledge (installed Ubuntu 10.4 a couple days ago).

I tried to change the visual effects using the Visual Effects tab in Preferences - it used to be on standard, this morning it had switched to low and there was no changing it back. I do assume I am using Compiz (it sounds familiar), but it is not a running process.

If I try to change the effects setting, I am simply told that they couldn't be changed and that's it.

I suppose it doesn't have anything to do with my hardware not being supported, as it used to work just fine until yesterday, and ATI drivers (I use an ATI Mobility Radeon 9700) are installed.

Hm. 

Thanks for your help, btw!
M.

---

### Post by Deadite81 on 2010-06-09
Ok, sounds like an easy fix (I hope):)
Open a terminal and type
```
sudo apt-get install compiz compizconfig-settings-manager
```
or fire up Synaptic Package Manager (Administration -> Synaptic Package Manager) and search for "compiz".  Click the box next to compiz and compizconfig-settings-manager, select "mark for installation" and then hit the "Apply" button.

Once it installs you'll need to log out and in.  The go to Preferences -> CompizConfig Settings Manager in your menu and be blown away by the insane amount of eye candy configurations!

If compiz is already installed, go to Aministration -> Hardware Drivers and make sure your driver has a green light.

---

### Post by Deadite81 on 2010-06-09
Oh, obviously write back if this does not help!  Another useful tool is the "fusion-icon" which can be started from Accessories -> System Tools (after you install it). You will then get a systray icon which can restart your window manager, etc.  This is very useful if something's not working and you don't know how to start/restart it otherwise.

Also there are other Compiz plugins available in the repositories that offer even more eye candy goodness and productivity too!  The Grid plugin is indispensable!

---

### Post by ManfredKlinglmair on 2010-06-09
Will try this later! Thanks in the meanwhile, I'll let you know if it worked.
M.

---

### Post by ManfredKlinglmair on 2010-06-09
Ok, it doesn't work... installed Compiz, but it doesn't show up as a running process. Also, the Hardware Drivers window does not show any hardware drivers whatsoever. So the effects would work if Compiz were running? I'm talking only about the 'standard' visual effects that can be chosen from the System>Preferences menu right after installing the OS - I don't need much more...

I'm a bit clueless now since I haven't installed or uninstalled anything since the effects were working fine.

Any other ideas...? Perhaps an update that screwed things up? I do get a 'looking for drivers' message if i want to change the effects under System>Preferences. Needless to say, no drivers are found. Gaaah!

---

### Post by Deadite81 on 2010-06-09
Hm.  I had my suspicions that this might not work.  I use nvidia graphics, but I've heard that ATI cards can be a pain.  If it were nvidia I could give you all kinds of step by step advice...but since I don't know the first thing about ATI I'd rather give no advice than bad advice!

However, doing a quick Google search and looking around this forum, Its clear that you are not alone in this problem, and some potential solutions have been given.  They worked for some and didn't work for others.  

Apparently and unfortunately your graphics card is not well supported.  This is not Ubuntu's fault, its the fault of your graphics card manufacturer.  They keep their driver software proprietary so it's hard for open source developers to create new drivers that can handle 3D effects.  I would go to their website or call them and complain. 

Anyway, it seems you need a package called "xorg-driver-fglrx".  But installing this package is problematic from what I've gathered from others.  If you go to Administration -> Hardware Drivers and the list is empty that spells trouble. :(

Here's some links to get you started and on your search:
[http://ubuntuforums.org/showthread.php?t=1479719](http://ubuntuforums.org/showthread.php?t=1479719)
[http://ubuntuforums.org/showthread.php?p=9430346](http://ubuntuforums.org/showthread.php?p=9430346)
[http://kubuntuforums.net/forums/index.php?topic=3104791.0](http://kubuntuforums.net/forums/index.php?topic=3104791.0)

Sorry I couldn't help more.  Someone else may come along that knows more, but just from my brief search I can see there's a lot of info out there about this issue.  Good Luck!

---

### Post by ManfredKlinglmair on 2010-06-09
I think the problem has to do with Compiz being installed, but not running as a process. I tried removing and installing it again, but no result. Graphics driver should be working fine, the lspci command shows my card is recognized.

---

### Post by ManfredKlinglmair on 2010-06-10
If you are having the same problem, check out this thread: 
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

It works now! Visual effetcs restored! So apparently it's a problem of mutually interfering drivers. Good luck!

M.

---

### Post by Deadite81 on 2010-06-10
Glad you solved it!  You should mark this thread as solved so others may benefit from your solution!

---

### Post by ManfredKlinglmair on 2010-06-10
This is embarassing - how do I mark it as solved...?

---

