---
title: "How is Kubuntu Lucid RC for you?"
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cguy on 2010-04-26
Mine is incredibly UNSTABLE.
If KDE 4.4(.1) on Karmic crashed only a couple of times / week, with 4.4.2 on Lucid something crashes every half an hour or so. Mostly Dolphin.
Krunner will also behave strangely. etc.

How's yours?

---

### Post by Gavin77 on 2010-04-26
I'm running it and it's working perfectly for me, no problems at all.

---

### Post by aceracer24 on 2010-04-26
I would consistantly get a lock up when I was trying to run the updater. Usually locked up during the installs, not the downloads :( . If I did manage to get it updated, the software center would stop working. I could open it and I could search but when I would click apply, nothing would happen. So I would open a terminal and run apt-get to install. 

I don't know if the problems i had with the kwallet are bugs or standard affair but I wanted to toss the computer out of my window because that stupid wallet would come back up asking for a password every single damn time I logged in because the wireless wanted to connect. This despite the fact that I selected always allow. So I disabled the wallet which sort of solved the problem with the wireless but then Amarok would no longer save my user/password for last.fm even though it said it would on some text file. I still had to log in every time despite that but now with no wallet, last.fm stopped working. 

Plus the fact that for some reason the ATI driver wouldn't work right with compiz when you activated it. It also messed up the resolution on start up and shut down. 

I tried hard to get over/past some of these issues because I really liked the KDE styling but nothing seemed to function very well compaired to Ubuntu so I gave up finally.

---

### Post by mbz99 on 2010-04-26
> **Gavin77 said:**
> I'm running it and it's working perfectly for me, no problems at all.
+1

I installed Kubuntu RC on 2 laptops and work fine. Only one small problem , cannot open dolphin directory from firefox Download window.

---

### Post by AICollector on 2010-04-26
I'm having a ***** of a time, it runs on my netbook fine, and on my friend's laptop...but not on my laptop!

Asus X50 GL, KDE's splash screen gets to the 'K' and then freezes. My fans go mad!

Anyone know how to fix this? Or even what the hell is happening?

---

### Post by forcecore on 2010-04-27
Kubuntu is slow and hangs a lot when you want to use it from live mode to temporary chat or use email, it is not Kubuntu fault but KDE-s most horrible part called Akonadi. Kubuntu developers should nuke out Akonadi. Some day maybe someone makes KDE light that is so stable and so fast, light, no akonadi, bases only on .cfg files.

There was a hope but it is abandoned now:
[http://www.antico.netsons.org/](http://www.antico.netsons.org/)

---

### Post by Reiger on 2010-04-27
Akonadi is OK; it's a database system. Should not attempt to run that off a live CD for obvious reasons; much the same why you shouldn't run a LAMP stack off the live CD either: that kind of software assumes that it will run from an actual disk where it can write/cache results.

Anyway, the RC, for me is unexpectedly unstable. (Before I moved the disk from the old laptop to the new one and  installed the RC, it contained one Lynx that ran much more stable.) However, I have a bunch of updates in the queue as I am not yet done setting up the system the way I like. (I'll remove the software I don't want first before updating; saves me bandwidth. And I add software that I do want before updating, too: makes things easier.)

---

### Post by jerrylamos on 2010-04-27
Unstable on i845 video graphics see launchpad Bug #541492 "GPU hung".  Big problem is intel video driver code vs. Lucid kernel.  Karmic runs fine with it's kernel and default video drivers so from a user standpoint it's a Lucid bug.

The pain about Unstable is when X crashes Lucid is dead, either stopped altogether but in any case can't recover gdm.  That's true with either gnome or lxde.

Lucid O.K. on i830 video graphics an older Thinkpad when I use "vesa".  I'm trying new default video driver to see if it is stable or not.

Currently stable on ati Mobility 7500 and ati Xpress 200.

I do reboot to Karmic on occasion and Jaunty rarely.  I prefer running Lucid with some usage of Debian LXDE and Slitaz.

Jerry

---

### Post by descendent87 on 2010-04-27
Had 1 or 2 crashes on dolphin but apart from that it's brilliant, best release yet

---

### Post by Joe on 2010-04-27
Worked surprisingly well for me for a couple days but now every time I log in I get a prompt for my password because something needs admin priveleges.  I have a feeling it has something to do with me messing around in the Removable Drives section of System Settings but I haven't had a chance to investigate it further yet.

---

### Post by tquetano on 2010-04-27
So far so good, had zero crashes, better functionality with KDE SC 4.4, overall very happy. 3 points I have noticed:

1) Still have no boot splash, just a cursor flashing at the top left corner until I reach the login screen. I have the Plymouth screen on shutdown, just not on boot. A buddy with 10.04 RC has the same issue.

2) Not sure if this is a new thing, but KBluetooth is awful. I say not sure because I've never tried using the feature before, but I've tried to connect multiple devices (all of which pair with Windows on the same machine) and it gives me the same "input is not allowed with this device" error every time. Weak sauce.

3) I too get the prompt for kdesudo on login. After some digging, I learned this is probably because I have my Windows partition and external HD set to automount on login. Karmic didn't give me this prompt, so I'm curious why Lucid is.

Other than that, phenomenal work. Keep on churning out quality systems, I'll keep converting Windows users (12 so far, in 4 months).

---

### Post by Kokopelli on 2010-04-27
Kubuntu Lucid has done surprisingly well for me so far.  Somewhere in the betas I had a problem where certain hotkeys would stop working after a few dozen uses but that appears to be solved.  Stability of the overall system has been high for me. As someone who openly and vocally despised KDE 4.0, 4.1, and (to a lesser extent) 4.2 I think 4.4 is a pleasant desktop experience

Suspend is working brilliantly on both my X200 tablet and my HP DV7T Quad, though the Thinkpad is slow to wake up.

The desktop is solid in my experience so far.  I will qualify that with the fact that I use very few widgets, and those I do use are only in a panel.  I also am not big on using krunner since anything I use with regularity I bind to a hotkey. 4.4 is the first time I have left the indexer, nepomuk,  running and it seems to have come along nicely since 4.3.

Dolphin and Konqueror as file managers have been stable for me so far.  This is the first release where I feel Dolphin might be worth using over Konq; jury is still out on that.  Konqueror is pants for web browsing though. I don't know that it has gotten worse but it definitely does not appear to have gotten better.

K3B is a problem child but only indirectly.  There seems to be a permissions issue with the dvd-writer where udev (at a guess) keeps resetting the permissions back after I change them.

Amarok... works, I have gotten used to the KDE4 version now though I miss the 3 version a bit.

I don't use the software store or KDE's update system (apt-get and occasionally synaptic for me) so can't speak to those.

---

### Post by zenarcher on 2010-04-27
I have it installed on five machines here (4-64 bit and 1-32 bit...4 with Nvidia proprietary driver and 1 with ATI).  Lucid has been working very well for me...well enough that I'm using it for my primary system.  

I've tried both the test versions of OpenSUSE and Fedora and if you want problems, give them a try.  With the current test release of OpenSUSE, neither the Live CD nor the DVD install disk will work.  They have a major glitch in their installer of some sort.  As for Fedora, I've yet to manage to get a good install of the Nvidia proprietary driver.

Lucid is doing everything I expect it to do.

Cheers,
zenarcher

---

### Post by xebian on 2010-04-27
The cd images IMO are set for the final.

Which means meerkat is here in a few days!!! :guitar:

---

### Post by utkjamie on 2010-04-28
A few issues:


[LIST]
[*]Dolphin crashes often. I don't see a pattern in anything I'm doing other than trying to use it.
[*]Even though desktop search is turned off and disabled from services, I find nepomukserver and 8 nepomukservices processes running whenever I reboot the computer.
[*]Touchpad tapping was effectively disabled in Karmic. Lucid, for some reason, re-enabled it. I can disable it from Keyboard & Mouse settings -> Touchpad -> Tapping by unchecking "Enable Tapping." However, the tapping is back after rebooting even though the "Enable Tapping" checkbox is still unchecked. Only after I check and re-uncheck the box does Lucid realize that it's not supposed to allow touchpad tapping.
[/LIST]

---

### Post by oobuntoo on 2010-04-28
I have two issues with 64-bit Kubuntu Lucid RC:

1. Flash/npwrapper occasionally crashed.
2. Openoffice.org apps won't start.

Everything else is rock solid.

---

