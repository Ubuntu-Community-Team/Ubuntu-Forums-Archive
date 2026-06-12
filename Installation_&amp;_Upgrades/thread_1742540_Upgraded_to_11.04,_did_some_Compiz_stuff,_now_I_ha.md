---
title: "Upgraded to 11.04, did some Compiz stuff, now I have no toolbars"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Maheriano on 2011-04-28
I have a desktop with a 1024x768 monitor (primary) and a 1280x720 projector (secondary). Today I upgraded to 11.04 and this sidebar thing was there but it was on my primary monitor which I hardly use, I mostly use my projector when working. So I changed my primary display to be my projector and it worked great. Then I enabled the Desktop Cube which disabled the Desktop Wall and I enabled the Show Desktop (I think it was this) that disabled the Unity something or other. And when I exited Compiz, I couldn't click on any of the menu bars, like the white Ubuntu logo, clicking it did nothing. Clicking the mail envelope, power button, calendar, nothing in the toolbar worked. So I pushed the power button on the computer which is set to shut down, then powered it back on and when it came back up I have a desktop on both monitor/projector but no toolbars. So I can't access any applications. I literally just have the 2 desktops and all the files on them.

---

### Post by Blasphemist on 2011-04-29
At the login screen, when entering the password, look at the bottom of the screen and choose Ubuntu Classic instead of Ubuntu. Go into ccsm and change back to desktop wall and the other original settings including enabling the unity plugin and expo. Log out and log back in to Ubuntu. Unity should be back. You can now continue to use unity or go back to Ubuntu classic.

See this for unity information.

[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

---

### Post by Maheriano on 2011-04-29
When I reboot I don't have the option for classic/Unity and it doesn't ask me for a password. However I do have No Machine installed so I can remote into a graphical desktop from my laptop and it automatically logs me in with classic mode. So I changed back to Desktop Wall, enabled Unity, SSH into the box, ran > sudo shutdown -r now, waited for it to come back up and nothing changed. I still have no toolbars.

---

### Post by myoldhouse on 2011-04-29
Hmmm.... Nvidia or ATI(AMD) or Intel graphics?

I have found that making -any- changes to Compiz settings from the initial default Unity ones tends to FUBAR the desktop. (For fun try turning off Window Decorations then turn them on again. If you have Nvidia proprietary drivers you might find that your top panel has disappeared!)

If you can open a terminal 'compiz --replace' (without the quotes of course) might restore things to normal, especially after you close the terminal window.

Otherwise try the Control-Alt-Backspace keyboard combination to force a logout, then log in again to the Ubuntu Classic Desktop instead of Unity.

Seriously though, don't play around with Natty 11.04 on a production box. This thing is still closer to Alpha/Beta status than a polished release despite what the release docs say. Hey, I'm not complaining, I'm just giving my observations. I've played with 11.04 on a spare drive on my system and from Beta 1 and I only upgrade my main system once I can confirm that all the aggravating issues (for me) are resolved or worked around and all my critical software works. I've done this since release, oh, about 7.10 or so. You might want to consider doing the same. Or not? :)

Ah, I see that you do not use a normal login, so no choice for the "Classic" desktop...

---

### Post by Hedgehog1 on 2011-04-29
From the terminal, please do this to reset your Unity to a functional state (factory defaults):

```
unity --reset
```

Also, you can do all the effects you love in 'Ubuntu Classic' on Natty:  [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")


***The Hedge***

:KS

---

### Post by Maheriano on 2011-04-29
Thanks, I come from 6.06 myself. I use nVidia and my top panel is gone, hence the reason I can't access anything. Nothing.

> 
deemar@Clementine:~$ ssh deemar@192.168.0.199
deemar@192.168.0.199's password: 
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-8-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

Last login: Thu Apr 28 22:04:28 2011 from clementine.local
deemar@Chugger:~$ compiz --replace
compiz (core) - Fatal: Couldn't open display 


---

### Post by Maheriano on 2011-04-29
> **Hedgehog1 said:**
> From the terminal, please do this to reset your Unity to a functional state (factory defaults):

```
unity --reset
```

Also, you can do all the effects you love in 'Ubuntu Classic' on Natty:  [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")


***The Hedge***

:KS

```
deemar@Chugger:~$ unity --reset
WARNING: no DISPLAY variable set, setting it to :0
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done
** (<unknown>:3494): DEBUG: Unity accessibility initialization
** (<unknown>:3494): DEBUG: Shows on edge: 1

(<unknown>:3494): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:3494): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

Screen geometry changed:
  Monitor 0(primary)
   1024x0x1280x720
  Monitor 1
   0x0x1024x768

unity-panel-service: no process found
** (<unknown>:3494): DEBUG: PanelController:: Added Panel for Monitor 0
unity-panel-service: no process found
** (<unknown>:3494): DEBUG: PanelController:: Added Panel for Monitor 1
Initializing unityshell options...done
** (<unknown>:3494): DEBUG: PlaceEntry: Applications
** (<unknown>:3494): DEBUG: PlaceEntry: Commands
** (<unknown>:3494): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:3494): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:3494): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:3494): DEBUG: Setting to primary screen rect: x=1024 y=0 w=1280 h=720
Couldn't find a perfect decorator match; trying all decorators
Starting unity-window-decorator
** (<unknown>:3494): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus

** (<unknown>:3494): DEBUG: TrayChild Rejected: padevchooser padevchooser Padevchooser
** (<unknown>:3494): DEBUG: TrayChild Rejected: nm-applet nm-applet Nm-applet
Segmentation fault

```

---

### Post by markymark64 on 2011-04-29
I have this exact same problem and I didn't screw around with anything. For some reason or another I believe the installation of my video drivers are the culprit. They were showing up as active but not being used and I meant to go to the synaptics package manager to uninstall and reinstall them but logged off because I was attempting to get my old cursor back. When I logged back on I had no top or bottom menus. I'll try the tip to use ctrl alt backspace and see if I can log on. The only way I can get on to my windows partition is by hitting enter a few times when the square box telling me that the input is not recognized goes floating by. This is frustrating for me because I spent three hours reinstalling apps that got screwed up with the upgrade. I've almost got everything installed but this happened and I feel totally screwed. Just no you're not alone. I wasn't doing a thing and this happened to me. lol

---

### Post by neuralnet on 2011-04-29
Same problem here, 11.04 fubar'd my compiz. Have tried following the posts [here]("http://ubuntuforums.org/showthread.php?t=1742481") and [here]("http://ubuntuforums.org/showthread.php?p=10734118#post10734118") and still I have no toolbars. ATI gfx, using the proprietary drivers.. In desperation have tried un & re-installing compiz related packages and unity, to no good effect.

compiz --replace

brings the top toolbar back, but windows have no title-bar... WTF?

---

### Post by Maheriano on 2011-04-29
Mine's working again. I used NXClient to remote into it and change some of the Compiz settings I thought I might have changed previously. Then I rebooted the desktop and it came up perfect.

---

### Post by neuralnet on 2011-04-30
After 5 hrs messing around with compiz settings etc I decided my laptop was fubar'd & REinstalled 10.10 instead.

If I'd known unity wasn't anything special I wouldn't have bothered & saved myself a days work.

---

### Post by AlaskanPotHead on 2011-05-16
"Go into ccsm and change back to desktop wall and the other original settings including enabling the unity plugin and _***expo***_."
Thank you, thank you, thank you! Been beating my head against the wall for 2 days trying to fix this. That did it!

---

### Post by markymark64 on 2011-05-16
I personally just went back to Ubuntu 10.10.  I also downloaded Clonezilla so I can back up my pc next time and it won't be such a mess. Personally, I think 11.04 is the biggest screw up so far from Ubuntu. If I were to go with 11.04 I'd have to go out and spend at least $80 - $100 on a new video card just to deal with the video requirements for 11.04. I think this one O.S. has given more people problems than any other as of late. This is not to say that I don't love Ubuntu, because I do, but I do not like 11.04 at all. It caused too many problems so I'll wait until the next update. 

Oh, and the new laptop that I'm buying has windows 7 premium but I'm going to back it up, wipe it and install ubuntu 10.10.

---

