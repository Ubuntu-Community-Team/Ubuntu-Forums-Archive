---
title: "Some bugs in Kubuntu Karmic"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by librano on 2009-09-03
Hi all,

Just wanted to point out some probable bugs that I have come across in the Alpha  4 of Kubuntu Karmic. I have since been keeping it up to date. Most probably most bugs have already been reported in Launchpad as they are glaringly obvious. So here goes.

1. Network Manager: The network manager plasmoid did not work out of the box with my WPA encrypted wireless network. I installed the Hardy driver for my Broadcom card (from my HD) as later drivers didnt work. The NM would just try to conect and then fail. I noticed the Gnome NM came preinstalled and I tried using that but couldnt connect either. I could see my network. Just couldnt connect. However the plasmoid NM did manage to connect after a reboot. I dont know if it was something I did. The Karmic Broadcom driver must be fixed as it still works with all recommended updates.

2. Arora crashes occasionally with flash content. Must be a flash problem.

3. KDM: During installation I selected for the system to automatically log in. But if I logged out I wouldn't get the log in screen. It would drop to the F8 virtual terminal.

4. Tapping on the top right of my touchpad was equivalent to middle clicking. I use this a lot in the browser to open in a new tab. But this mysteriously stopped working. And I can't find a way to reenable it in the KDE settings.

5. The method for installing new plasmoids is very intuitive. However, many plasmoids do not appear in the 'Add Widget' dialod after installation... and many other do not work as advertised. I understand the team cannot cover for all the plasmoids but it is annoying. Maybe there should be some officially supported plasmoids. Kind of like how the packages are separated into main, universe, multiverse. (If anyone knows how to get the Remember the milk plasmoid to log in, I would be grateful.)

6. Running programs in Wine causes many rendering issues and many things like the panel disappear.

Can't think of anything else right now. I'll write more as I find them. I would scour Launchpad but I just don't have the time right now.

Cheers.

---

### Post by Hellmark on 2009-09-04
For remember the milk, go to the settings, there should be a button to authorize the plasmoid. It'll load up a webpage asking if you want to authorize that client. Say yes, then go back to the settings, and give it your ID and password.

---

### Post by hikaricore on 2009-09-04
> **librano said:**
> 
6. Running programs in Wine causes many rendering issues and many things like the panel disappear.

I've had no problems here and I've been running it since it was bleeding edge.  Turn off desktop effects.

---

### Post by librano on 2009-10-01
Just want to give an update...

1. I did reinstall Kubuntu Karmic (alpha 5 i think) later and the NM plasmoid connected without problems... of course after installing the Hardy drivers for my Broadcom wireless card. Updating the driver to the Karmic drivers, the wireless did not break... unlike with other versions after Hardy. Well done to the team!

2. Arora is a really good browser. But I find myself using Chromium as my default more and more. <Insert Kanye West meme here :lolflag: >

3. The KDM problem persisted. I couldnt get back to the login screen after logging out.

4. Ever since xorg.conf was depreciated I've been pretty ignorant of configuring xorg. The Gnome/XFCE tools did what I wanted. However, KDE4 is lacking in these tools and that's a shame. On the brighter side, I learnt how to configure the synaptics touchpad in HAL which is where the settings are now by enabling SHMConfig.

5. Plasmoids are very cool but right now they are still a hit or miss affair. There should be a better way of installing these that accounts especially for system requirements... i.e. stuff that is required by the plasmoid.

6. The rendering problems with WINE was caused by the windows application itself. It is a Java app and to fix this issue I had to configure WINE to run in Vista mode. This is easily done with winetricks. I did not have effects turned on... I wish my integrated SiS card could handle effects... :(

I have since uninstalled Kubuntu Karmic and installed the Chakra Project... which is Arch + KDEmod. It hasnt been a day yet but it looks like a very promising project (still in alpha). This is my first venture into Arch and I really like the Arch way! However, you should be willing to dig into the system to get things the way you want. e.g. acpi wasn't installed by default! On a side note, the KDM issue exists in Arch as well and Arora has a few glitches with the Qt widgets.

Conclusion? KDE4 makes me want to get a new computer, coz 768MB RAM and a measly 5GB testing partition just isn't cutting it. Well done KDE folks! After 4 years it looks like I'm coming back!

---

### Post by flowerdealer on 2009-10-01
My bugs in Kubuntu right now are:

a)No usplash at boot, only text messages, booting takes quite a long time compared to jaunty.
b) My brother printer isnt detected, it used to work in jaunty.
c) Minor bug but annoying, password field in the login screen doesnt have focus, have to click on it any time.
d) Wrong resolution (actually more like wrong aspect) in login screen in my 1920x1080 monitor (with glitches on the sides).
e)Ati related bug: Everything works, but apparently smooth resizing needs a "no backfill" patch which isnt in the repos. 

Other than that, Im all good. Im quite happy with how this release is coming, but Im worried as it still has a lot of very glaring bugs which are still there at the beginning of beta. I have reported some of this bugs but fore some reason I havent been able to report bugs in launchpad for the past week.

---

### Post by buzzmandt on 2009-10-01
> **flowerdealer said:**
> My bugs in Kubuntu right now are:

c) Minor bug but annoying, password field in the login screen doesnt have focus, have to click on it any time.


go to system settings/advanced/login manager
click convenience tab and make sure "focus password" is checked.  should take care of it.


the kdm logout option is bugged for me too.  can't get a login screen.  it doesn't drop me to tty but it stays black screen with mouse cursor that still works.  have to restartx to get a login screen

---

### Post by flowerdealer on 2009-10-01
Yep, it is checked, it worked before, must have changed after some update.

---

### Post by Eclipse. on 2009-10-01
Please file bug reports for all of those bugs, its the only way they can get fixed. :)

See here for info: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by nanog on 2009-10-01
Developers do not read these forums, much. And even less so as release get closer. So please, please file bugs.

---

### Post by flowerdealer on 2009-10-01
When I go to launchpad an press the report bug page, it keeps sending me here:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

This is how I used to report bugs. The problem is that some of the bugs I have, I do not know what package they are from, or the software does not include a report bug option. How can I get to launchpad and report bugs from there again?

---

### Post by NormanFLinux on 2009-10-01
Confirmed bug in Karmic:

all instances of Open Office just die.

---

### Post by librano on 2009-10-05
I don't mean to insult or belittle the work the devs do here at ubuntu... but most of the time I report bugs, the conclusion is 'it is an upstream bug, we will wait for them to fix it' or 'the bug will not be fixed'. I understand that my problems are probably not the most pressing and unless they are critical, I haven't been reporting them. 

Usually, eventually they do get fixed... e.g. the drivers post Hardy for my wireless card being broken right up to Karmic. Or a bug in FF where it doesn't use the GTK theme properly. This bug is upstream and still exists in the latest releases. I even reported it to the mozilla devs, but still... 

The only time I can remember a bug I reported getting fixed was an OO bug for which I had to pester the devs on launchpad and the IRC channel for some time... and even then it was only fixed in the .1 LTS release.

Again, I'm not blaming... just saying my experiences.

As for the problems I faced:

1. This was fixed. Again... well done to the team!
2. It is very minor and will probably get fixed upstream. (Some text entry boxes and Qt widgets are not aligned perfectly)
3. This is upstream and present in Arch as well. i.e. we'll wait for upstream to fix it.
4. This was a config issue and a matter of personal preference. KDE4 does not have synaptics config tools yet.
5. Upstream issue.
6. Configuration issue.

Maybe some of the other bugs in this thread should be reported, but mine are trivial and/or nothing a little tinkering won't fix.

---

### Post by librano on 2009-10-05
> **flowerdealer said:**
> When I go to launchpad an press the report bug page, it keeps sending me here:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

This is how I used to report bugs. The problem is that some of the bugs I have, I do not know what package they are from, or the software does not include a report bug option. How can I get to launchpad and report bugs from there again?

It doesn't matter if you don't know what package the bug is caused by. Just submit it and give as much information as you can. If your bug catches someones attention they may ask for more info and eventually the offending package and hopefully the problem will be located and fixed.

Search for similar bugs, so that we don't have duplicates... which just makes things more chaotic, and give as much info as you can.

---

### Post by Zorael on 2009-10-05
As for 3 (drops to terminal upon logout), assuming you're on Intel video hardware, that's X segfaulting when it's trying to regenerate (reuse) the X session.

The workaround is to tell X to terminate the server and start a completely new one. Edit /etc/kde4/kdm/kdmrc, find the line TerminateServer, uncomment it if commented, and set it to true.

The solution is to update the Intel driver. The bug has been fixed upstream, but the Karmic driver is old.

---

### Post by gali98 on 2009-10-05
If you just want to file a bug directly on launchpad use this:
[https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)
Kory

---

### Post by librano on 2009-10-06
> **Zorael said:**
> As for 3 (drops to terminal upon logout), assuming you're on Intel video hardware, that's X segfaulting when it's trying to regenerate (reuse) the X session.

The workaround is to tell X to terminate the server and start a completely new one. Edit /etc/kde4/kdm/kdmrc, find the line TerminateServer, uncomment it if commented, and set it to true.

The solution is to update the Intel driver. The bug has been fixed upstream, but the Karmic driver is old.

Thanks! that worked like a charm! On Arch though the file is located at /usr/share/config/kdm/kdmrc. I wonder what would happen if more than one user was logged in to the same machine...

---

### Post by HankB on 2009-10-08
> **librano said:**
> ... On the brighter side, I learnt how to configure the synaptics touchpad in HAL which is where the settings are now by enabling SHMConfig.


Can you provide the particulars for this? I have not yet figured out how to get the "tap upper right for middle mouse click" working on my Eee PC 901 with Karmic. Scrolling and left/right click work fine.

thanks,
hank

---

### Post by Zorael on 2009-10-08
> **HankB said:**
> Can you provide the particulars for this? I have not yet figured out how to get the "tap upper right for middle mouse click" working on my Eee PC 901 with Karmic. Scrolling and left/right click work fine.

thanks,
hank
See [http://ubuntuforums.org/showthread.php?p=7643273&postcount=2](http://ubuntuforums.org/showthread.php?p=7643273&postcount=2). The prop you want to modify is "Synaptic Tap Action".

```
Synaptics Tap Action (267):     2, 3, 0, 0, 1, 2, 3
```
If memory serves the first figure is top-right, then bottom-right, then top-left, then bottom-left. 1 corresponds to the left mouse button, 2 to the middle and 3 to the right.

The last three figures are multi-finger taps, I think; one finger, two fingers, three fingers (if the pad supports it).

---

### Post by HankB on 2009-10-09
Thank you for the reply. Your memory serves and my problem is fixed! :guitar:

And on the next boot it didn't!

I found that the property number had changed. :( I modified the script to use symbolic names instead:

```
xinput set-int-prop "ETPS/2 Elantech Touchpad" "Synaptics Tap Action" 8 2 3 0 0 1 3 2
```

The script runs from System -> Preferences -> Startup Applications.


best,
hank

---

