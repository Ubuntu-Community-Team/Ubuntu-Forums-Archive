---
title: "Indicator applet"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by UpSignal on 2010-04-18
well, i need some help, nobody reply me to my last post. It's about the Gnome-volume applet, and the mail notification from evolution. I believe it's all part of "indicator applet". so, i was saying, the nest times i reboot my laptop, they disapeared from my tray. i only have now the wireless applet. Other than that, i still think gnome shell it's the best manager i saw so far. it rocks :)

---

### Post by cariboo on 2010-04-18
This question had noting to do with gnome-shell, moved to it's own thread, for better visiblity.

---

### Post by x-shaney-x on 2010-04-18
May have crashed or something and when it asks if you want to remove it you did?
Try right-click on panel and add applets and add it back?

---

### Post by drewsus on 2010-04-18
Try:
```
killall gnome-panel
```
?

Also, you could try restoring your panels to default and resetting them up the way you like? 
Restore Panels t default:
```
gconftool-2 --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
killall gnome-panel
```

---

### Post by dannyboy79 on 2010-04-18
this happened to me also. what I did was rename you users .gnome2 folder within his home directory (or delete if you have nothing else in your users home directory .gnome2 folder), then just log out and log back in. should be fixed. that's what did it for me.  !NOTE --- nautilus scripts are located within .gnome2 so be careful what you delete if you have scripts you use in Nautilus's context menu (right click menu)

---

### Post by UpSignal on 2010-04-18
Aham, i'm sorry, i probably didn't explain too well. I have no problems with my applets in gnome 2. This is indeed a problem with gnome shell. because if i reboot my computer using gnome shell instead of metacity, the applet goes away, only wireless stays there. But, as soon as i reboot with metacity, everything loads normally. Weird thing is... the first boot with shell went all good :o

---

### Post by JCollierDavis on 2010-04-24
> **x-shaney-x said:**
> May have crashed or something and when it asks if you want to remove it you did?
Try right-click on panel and add applets and add it back?

Happened to me as well, all my applets dissappeared.  I managed to get them all back.

This is what happened when my applets crashed.  I got a message saying indicator-applet crashed and the different applets started to disappear.  It happened several times until now I'm just down to the date. 
Right clicking on the panel and adding the "off" button enabled me to shutdown without using the CLI.  You can't right click on the applet area to add things.  There's no empty space on it to right click on so a right click there is interpreted as related to the underlying app.  
Following suggestion at: [http://ubuntuforums.org/showthread.php?t=1422515&highlight=indicator-sound](http://ubuntuforums.org/showthread.php?t=1422515&highlight=indicator-sound)
I succeeded in getting my volume applet back by entering:

gnome-volume-control-applet &


I had originally tried the command
/usr/lib/indicator-sound/indicator-sound-service

which resulted in the below message.

jcollierdavis@JCollierDavis:~$ /usr/lib/indicator-sound/indicator-sound-service
** (process:2901): DEBUG: Root ID: 1
** (process:2901): DEBUG: update pa state with state 0, availability of 0, mute value of 0 and a volume percent is 0.000000
** (process:2901): DEBUG: Building new Slider Menu Item
** (process:2901): DEBUG: !!!!!!**in the rebuild sound menu - slider active = 0
** (process:2901): DEBUG: Emitting signal: SINK_AVAILABILITY_UPDATE, with value 0
** (process:2901): DEBUG: Emitting signal: SINK_VOLUME_UPDATE, with sink_volme 0.000000
** (process:2901): DEBUG: Emitting signal: SINK_MUTE_UPDATE, with sink mute 0
** (process:2901): DEBUG: connecting - waiting for the server to become available
** (process:2901): DEBUG: authorizing
** (process:2901): DEBUG: context setting name
** (process:2901): DEBUG: PA daemon is ready
** (process:2901): DEBUG: server info callback
** (process:2901): DEBUG: Just set the default sink index to 0

** (process:3326): WARNING **: Default Sink info callback failure
** (process:2901): DEBUG: About to add an item to our hash
** (process:2901): DEBUG: After adding an item to our hash
** (process:2901): DEBUG: About to test for to see if the available sink is null - s->name = alsa_output.pci-0000_00_1b.0.analog-stereo
** (process:2901): DEBUG: PA_Manager ->  determine_sink_availability: 1
** (process:2901): DEBUG: software volume = 35.482788
** (process:2901): DEBUG: update pa state with state 1, availability of 1, mute value of 1 and a volume percent is 35.482788
** (process:2901): DEBUG: in the refresh menu method
** (process:2901): DEBUG: Emitting signal: SINK_AVAILABILITY_UPDATE, with value 1
** (process:2901): DEBUG: Emitting signal: SINK_VOLUME_UPDATE, with sink_volme 35.482788
** (process:2901): DEBUG: Emitting signal: SINK_MUTE_UPDATE, with sink mute 1

(process:3326): libindicator-WARNING **: No watchers, service timing out.
** (process:2901): DEBUG: Service shutdown !
** (process:2901): DEBUG: freeing the pulse context
** (process:2901): DEBUG: I just closed communication with Pulse

Tried @dannyboy79's suggestion and renamed the .gnome2 folder as .gnome2_backup.  Only effect was the "Default Keyring" was reset.
Tried @drewsus's suggestion which reset the panel as desired.  Works so far.

---

### Post by Mr. Picklesworth on 2010-04-24
> **UpSignal said:**
> Aham, i'm sorry, i probably didn't explain too well. I have no problems with my applets in gnome 2. This is indeed a problem with gnome shell. because if i reboot my computer using gnome shell instead of metacity, the applet goes away, only wireless stays there. But, as soon as i reboot with metacity, everything loads normally. Weird thing is... the first boot with shell went all good :o

That is because gnome-shell doesn't provide an Indicator Applet. (Yet).

---

