---
title: "volume notification: just a black box"
date: 2009-02-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hanzomon4 on 2009-02-24
I only get a translucent black box when I adjust my volume...

---

### Post by glasen on 2009-02-24
You must use the Human-Icon-Theme. It's stupid, but in the moment it is the only way.

---

### Post by syko21 on 2009-02-24
Do you know which particular icons from that theme govern the notification? It would be a simple matter of a symlink from there I would think.

---

### Post by tawmas on 2009-02-24
You need these:

```
cp /usr/share/icons/Human/scalable/status/notification-* ~/.icons/(THEME NAME HERE)/scalable/status/
cp /usr/share/icons/notify_osd/icons/notification-volume.svg ~/.icons/(THEME NAME HERE)/scalable/status/
```

---

### Post by pferraro on 2009-02-24
You can also append Human to your theme's inheritance in index.theme:
e.g.
Inherits=gnome,Human

That way you won't have to keep re-copying the icons every time the art team updates the human-icon-theme package.

---

### Post by sarcaman on 2009-02-24
Thanks pferraro, that fixed it for me.

 For those of you using Mac4Lin, just go to ~/.icons/Mac4Lin_Icons_v0.4/index.theme and append ,Human to the end of the Inherits line at the top of the file

---

### Post by tawmas on 2009-02-24
> **pferraro said:**
> You can also append Human to your theme's inheritance in index.theme:
e.g.
Inherits=gnome,Human

That way you won't have to keep re-copying the icons every time the art team updates the human-icon-theme package.

Cool, thanks!

---

### Post by constanthatz on 2009-02-25
I had this problem as well (I use the Tangerine icon set) so I modified index.theme as suggested above, and had some bizarre results.

After modifying index.theme, I restarted my computer. Everything worked fine, up to and including logging in (entering my username and password).  Then one of two things would happen.  

1) My background image and mouse would become visible, but nothing else.  The hard drive activity light indicates that something is happening.  The only input that my computer will respond to is CTRL+ALT+DEL, giving me the option of restart of shutdown.  I could restart, shutdown, or cancel, but clicking help would do nothing.  I could tab through the options and hit enter to activate them as well.

2) The exact same as above, but the panel would become visible.  For a moment I am able to activate one of the drop down menus or launch Gnome-Do, but then I can't do anything.  Meanwhile the window list on the panel is filling up with endless copies of "Starting File Manger"

I suspect the two results are the same and it's simply a matter of timing whether or not ubuntu manages to start the panel before the file manager tries to open itself 1000 times and stops anything else from happening.

Restarting in terminal mode and restoring index.theme returned everything to normal.  I was able to repeat the above several times, using ",Human", ", Human", and ",human".

Weird.

I figured I would mention this in case someone else had the same problem.

Simply copying the icons over worked fine though.

---

### Post by Starks on 2009-02-25
> **tawmas said:**
> You need these:

```
cp /usr/share/icons/Human/scalable/status/notification-* ~/.icons/(THEME NAME HERE)/scalable/status/
cp /usr/share/icons/notify_osd/icons/notification-volume.svg ~/.icons/(THEME NAME HERE)/scalable/status/
```

The second command doesn't work since the notify_osd directory doesn't exist.

---

### Post by Starks on 2009-02-25
Will theme makers need to incorporate the new notification stuff or will there be modifications that allow all themes to work without doing inherit overrides?

---

### Post by constanthatz on 2009-02-25
> **Starks said:**
> The second command doesn't work since the notify_osd directory doesn't exist.

I thought I had that problem, but it's just that "notify_osd" is a subdirectory of "/usr/share/" not "/usr/share/icons/".  For me anyway.

Try this.

```
cp /usr/share/notify_osd/icons/notification-volume.svg ~/.icons/(THEME NAME HERE)/scalable/status/

```

---

### Post by RAOF on 2009-02-25
> **Starks said:**
> Will theme makers need to incorporate the new notification stuff or will there be modifications that allow all themes to work without doing inherit overrides?

We *should* be installing those icons into the "hicolor" theme.  All themes inherit from that.

---

### Post by MadsRH on 2009-02-25
Is anyone else experiencing notifications displayed on top of the panel? (see the attach screenshot)

[ATTACH]104649[/ATTACH]

Sorry for the noise in this thread :oops:

---

### Post by BwackNinja on 2009-02-25
@MadsRH

Yes, everyone. If you do a "killall notify-osd", then all the notifications will appear below the panel.

---

### Post by go7Ul1ai on 2009-02-25
Mine appears underneath the panel, even after reboots, must have been a fix released or something because I didn't use the killall command.

---

### Post by MacSlow on 2009-02-25
> **tawmas said:**
> You need these:

```
cp /usr/share/icons/Human/scalable/status/notification-* ~/.icons/(THEME NAME HERE)/scalable/status/
cp /usr/share/icons/notify_osd/icons/notification-volume.svg ~/.icons/(THEME NAME HERE)/scalable/status/
```

What package provides you with /usr/share/icons/notify_osd/icons/notification-volume.svg ?

---

### Post by Yashiro on 2009-02-25
[https://wiki.ubuntu.com/NotificationDevelopmentGuidelines#Layout%20cases%20(with%20examples%20in%20C,%20Python%20and%20C#](https://wiki.ubuntu.com/NotificationDevelopmentGuidelines#Layout%20cases%20(with%20examples%20in%20C,%20Python%20and%20C#))

> How do I get these slick icons

The user has to be using the Human icon-theme. Have a look at the icon-matrix. Or if a different icon-theme is selected, default icons satisfying the new icon-names are used. These will look different of course. The available icon-names are...

    * notification-audio-next
    * notification-audio-play
    * notification-audio-previous
    * notification-audio-volume-high
    * notification-audio-volume-low
    * notification-audio-volume-medium
    * notification-audio-volume-muted
    * notification-audio-volume-off
    * notification-battery-low
    * notification-device-eject
    * notification-device-firewire
    * notification-display-brightness-full
    * notification-display-brightness-high
    * notification-display-brightness-low
    * notification-display-brightness-medium
    * notification-display-brightness-off
    * notification-GSM-3G-full
    * notification-GSM-3G-high
    * notification-GSM-3G-low
    * notification-GSM-3G-medium
    * notification-GSM-3G-none
    * notification-GSM-disconnected
    * notification-GSM-EDGE-full
    * notification-GSM-EDGE-high
    * notification-GSM-EDGE-low
    * notification-GSM-EDGE-medium
    * notification-GSM-EDGE-none
    * notification-GSM-full
    * notification-GSM-H-full
    * notification-GSM-H-high
    * notification-GSM-high
    * notification-GSM-H-low
    * notification-GSM-H-medium
    * notification-GSM-H-none
    * notification-GSM-low
    * notification-GSM-medium
    * notification-GSM-none
    * notification-keyboard-brightness-full
    * notification-keyboard-brightness-high
    * notification-keyboard-brightness-low
    * notification-keyboard-brightness-medium
    * notification-keyboard-brightness-off
    * notification-message-email
    * notification-message-IM
    * notification-network-ethernet-connected
    * notification-network-ethernet-disconnected
    * notification-network-wireless-disconnected
    * notification-network-wireless-full
    * notification-network-wireless-high
    * notification-network-wireless-low
    * notification-network-wireless-medium
    * notification-network-wireless-none
    * notification-power-disconnected 

... and are located under /usr/share/icons/Human/scalable/status. Until symlinks or updated icons for other icon-themes are installed (provided by updated packages) using these without the icon-theme being set to Human will fail to display the intended icon. The result is an empty notification-bubble. You can still of course use full file paths to .svg/.png/.jpg icons. 

---

### Post by SoniXuS on 2009-02-26
If you are alright with modifying the theme, which we will end up anyway, then you could execute this list of commands. Modify USERNAME and ICONTHEME.

```
cd /home/USERNAME/.icons/ICONTHEME/scalable/status
ln -s /usr/share/icons/Human/scalable/status/notification-audio-next.svg notification-audio-next.svg
ln -s /usr/share/icons/Human/scalable/status/notification-audio-play.svg notification-audio-play.svg
ln -s /usr/share/icons/Human/scalable/status/notification-audio-previous.svg notification-audio-previous.svg
ln -s /usr/share/icons/Human/scalable/status/notification-audio-volume-high.svg notification-audio-volume-high.svg
ln -s /usr/share/icons/Human/scalable/status/notification-audio-volume-low.svg notification-audio-volume-low.svg
ln -s /usr/share/icons/Human/scalable/status/notification-audio-volume-medium.svg notification-audio-volume-medium.svg
ln -s /usr/share/icons/Human/scalable/status/notification-audio-volume-muted.svg notification-audio-volume-muted.svg
ln -s /usr/share/icons/Human/scalable/status/notification-audio-volume-off.svg notification-audio-volume-off.svg
ln -s /usr/share/icons/Human/scalable/status/notification-battery-low.svg notification-battery-low.svg
ln -s /usr/share/icons/Human/scalable/status/notification-device-eject.svg notification-device-eject.svg
ln -s /usr/share/icons/Human/scalable/status/notification-device-firewire.svg notification-device-firewire.svg
ln -s /usr/share/icons/Human/scalable/status/notification-display-brightness-full.svg notification-display-brightness-full.svg
ln -s /usr/share/icons/Human/scalable/status/notification-display-brightness-high.svg notification-display-brightness-high.svg
ln -s /usr/share/icons/Human/scalable/status/notification-display-brightness-low.svg notification-display-brightness-low.svg
ln -s /usr/share/icons/Human/scalable/status/notification-display-brightness-medium.svg notification-display-brightness-medium.svg
ln -s /usr/share/icons/Human/scalable/status/notification-display-brightness-off.svg notification-display-brightness-off.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-3G-full.svg notification-GSM-3G-full.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-3G-high.svg notification-GSM-3G-high.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-3G-low.svg notification-GSM-3G-low.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-3G-medium.svg notification-GSM-3G-medium.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-3G-none.svg notification-GSM-3G-none.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-disconnected.svg notification-GSM-disconnected.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-EDGE-full.svg notification-GSM-EDGE-full.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-EDGE-high.svg notification-GSM-EDGE-high.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-EDGE-low.svg notification-GSM-EDGE-low.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-EDGE-medium.svg notification-GSM-EDGE-medium.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-EDGE-none.svg notification-GSM-EDGE-none.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-full.svg notification-GSM-full.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-H-full.svg notification-GSM-H-full.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-H-high.svg notification-GSM-H-high.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-high.svg notification-GSM-high.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-H-low.svg notification-GSM-H-low.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-H-medium.svg notification-GSM-H-medium.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-H-none.svg notification-GSM-H-none.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-low.svg notification-GSM-low.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-medium.svg notification-GSM-medium.svg
ln -s /usr/share/icons/Human/scalable/status/notification-GSM-none.svg notification-GSM-none.svg
ln -s /usr/share/icons/Human/scalable/status/notification-keyboard-brightness-full.svg notification-keyboard-brightness-full.svg
ln -s /usr/share/icons/Human/scalable/status/notification-keyboard-brightness-high.svg notification-keyboard-brightness-high.svg
ln -s /usr/share/icons/Human/scalable/status/notification-keyboard-brightness-low.svg notification-keyboard-brightness-low.svg
ln -s /usr/share/icons/Human/scalable/status/notification-keyboard-brightness-medium.svg notification-keyboard-brightness-medium.svg
ln -s /usr/share/icons/Human/scalable/status/notification-keyboard-brightness-off.svg notification-keyboard-brightness-off.svg
ln -s /usr/share/icons/Human/scalable/status/notification-message-email.svg notification-message-email.svg
ln -s /usr/share/icons/Human/scalable/status/notification-message-IM.svg notification-message-IM.svg
ln -s /usr/share/icons/Human/scalable/status/notification-network-ethernet-connected.svg notification-network-ethernet-connected.svg
ln -s /usr/share/icons/Human/scalable/status/notification-network-ethernet-disconnected.svg notification-network-ethernet-disconnected.svg
ln -s /usr/share/icons/Human/scalable/status/notification-network-wireless-disconnected.svg notification-network-wireless-disconnected.svg
ln -s /usr/share/icons/Human/scalable/status/notification-network-wireless-full.svg notification-network-wireless-full.svg
ln -s /usr/share/icons/Human/scalable/status/notification-network-wireless-high.svg notification-network-wireless-high.svg
ln -s /usr/share/icons/Human/scalable/status/notification-network-wireless-low.svg notification-network-wireless-low.svg
ln -s /usr/share/icons/Human/scalable/status/notification-network-wireless-medium.svg notification-network-wireless-medium.svg
ln -s /usr/share/icons/Human/scalable/status/notification-network-wireless-none.svg notification-network-wireless-none.svg
ln -s /usr/share/icons/Human/scalable/status/notification-power-disconnected.svg notification-power-disconnected.svg
```

---

### Post by taavikko on 2009-02-26
If someone is using hydroxygen icon set, it works by just
adding Human to inherit line in index.theme

```
Inherits=gnome,hicolor,Human
```

Change icon theme, switch back, it's working.

---

### Post by Starks on 2009-02-26
> * notification-GSM-3G-full
* notification-GSM-3G-high
* notification-GSM-3G-low
* notification-GSM-3G-medium
* notification-GSM-3G-none
* notification-GSM-disconnected
* notification-GSM-EDGE-full
* notification-GSM-EDGE-high
* notification-GSM-EDGE-low
* notification-GSM-EDGE-medium
* notification-GSM-EDGE-none
* notification-GSM-full
* notification-GSM-H-full
* notification-GSM-H-high
* notification-GSM-high
* notification-GSM-H-low
* notification-GSM-H-medium
* notification-GSM-H-none
* notification-GSM-low
* notification-GSM-medium
* notification-GSM-none

And CDMA receives absolutely zero love because developers are GSM elitists. </half-sarcasm>

---

### Post by adult swim on 2009-02-28
> **taavikko said:**
> If someone is using hydroxygen icon set, it works by just
adding Human to inherit line in index.theme

```
Inherits=gnome,hicolor,Human
```

Change icon theme, switch back, it's working.

thanks for the tip, i couldnt get it to work but switching to something and back to hyrdoxygen fixed it

---

### Post by Hobbsee on 2009-02-28
> **constanthatz said:**
> I had this problem as well (I use the Tangerine icon set) so I modified index.theme as suggested above, and had some bizarre results.

Got exactly the same thing here, with various bits of gnome continuously crashing (nautilus, metacity, compiz), and the revised fix worked.  There were a lot of things spinning at 100% cpu too, which weren't in the process list?

---

### Post by Elfy on 2009-02-28
I've not seen any other threads like this so I'll throw this in here as it seems fairly relevant :)

My volume notification is fine and now I know the Inherits=gnome,hicolor,Human I don't need to use human icon all the time.

But, regardless, of what I use the other notifications appear to have gone - rhythmbox track changes are not notified for instance.

Not sure if the current load of updates would cure it - I still have a partial here so I've not done them.

---

### Post by taavikko on 2009-02-28
> **forestpixie said:**
> 
But, regardless, of what I use the other notifications appear to have gone - rhythmbox track changes are not notified for instance.


Rhythmbox notifications doesn't show if "Show notifications" box is unticked.

Notifications doesn't show if rhythmbox window is open.

Notifications should appear if it is minimized to tray.

---

### Post by Elfy on 2009-02-28
All updated now.

Rhythmbox - notifications box is ticked
Rhythmbox - not minimised but on a different desktop.
Minimising does show notifications - thanks for that.

Ok - I can see why I thought something had changed - I started using compiz. 

Without compiz I get notified of track changes regardless of Rhythmbox's minimised or maximised state.

If that in itself is a bug I shall report it as such

---

