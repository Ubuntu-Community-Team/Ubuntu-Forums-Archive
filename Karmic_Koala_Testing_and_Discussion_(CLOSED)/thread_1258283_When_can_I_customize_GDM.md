---
title: "When can I customize GDM?"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2009-09-04
When will it be easy to customize the GDM again?

---

### Post by autocrosser on 2009-09-05
Most likely close to the 10.4 release....There is a rough setting right now, but it will take time for someone to want to "hack" a nice mod panel for it...I do know that there are plans for 2 panel addons (as I hear it--one in Appearance & the other in Users & Groups?) for mods, but nothing is "cast in stone" right now.

---

### Post by tjeremiah on 2009-09-06
I had an idea that they should make it "transparent." Meaning, it can display your current wallpaper while loading with the ubuntu logo in the bg.

---

### Post by ranch hand on 2009-09-06
> **tjeremiah said:**
> I had an idea that they should make it "transparent." Meaning, it can display your current wallpaper while loading with the ubuntu logo in the bg.
You can do that now buy going to your /usr/share/backgrounds file and renaming any .png image you want to;
```

warty-final-ubuntu.png

```
If you image is not a .png you can open it in Gimp and just save it as a .png or open it in gthumb and use the "Convert Format" tool under "Tools"

---

### Post by wipeout140 on 2009-09-07
This post will show you how to change the following:

gdm background picture
gdm gtk theme 
gdm icon theme
gdm user icon

[http://ubuntuforums.org/showpost.php?p=7576112&postcount=365](http://ubuntuforums.org/showpost.php?p=7576112&postcount=365)

---

### Post by P4man on 2009-09-07
> **autocrosser said:**
> Most likely close to the 10.4 release....There is a rough setting right now, but it will take time for someone to want to "hack" a nice mod panel for it...I do know that there are plans for 2 panel addons (as I hear it--one in Appearance & the other in Users & Groups?) for mods, **but nothing is "cast in stone" right now.**

How can that be? Are they planning on using the old GDM as default again for karmic final, or are they still thinking on how to implement something that is yet to be conceived, programmed,  tested, documented and released in ... 7 weeks?

---

### Post by autocrosser on 2009-09-07
We tried to get something to customize GDM when the new version was released--at least we have *some* options--but we can't modify the new one anywhere as much as the old one until someone takes a interest in writing the mods--

This was NOT my wish--the devs sync'd with current Gnome--we were using the old 2.20 well past the "pull" date. I have talked to everyone I can & the answer I get is if the community is vocal enough something will get done--I have been reminded that Fedora & a couple of other distros already have the current GDM. (for a "interesting" read--look at Fedoras bug reports about it)

So in short--we *have too* live with the current lack for at least 6 months & maybe more--unless someone creates a mod panel (hint-hint).

So we as a group need to get "vocal" in Launchpad & other places---*hopefully* someone will step forward & fill in the blanks.

---

### Post by tjeremiah on 2009-09-21
one of the developers on this forums hinted something is coming this week to easily customize GDM.

---

### Post by P4man on 2009-09-22
I hope it allows to change the splash as well."De gustibus et coloribus non est disputandum", but My God, do i find that  brown (literally sh*t) ugly.

---

### Post by ranch hand on 2009-09-22
> **P4man said:**
> I hope it allows to change the splash as well."De gustibus et coloribus non est disputandum", but My God, do i find that  brown (literally sh*t) ugly.
Well, I have to admit to being a person that generally likes the Ubuntu brown but this splash is, to be kind, is ugly.

This doesn't bother me too much as it is only up for a few seconds.  This is a good thing.

---

### Post by oboedad55 on 2009-09-22
> **ranch hand said:**
> Well, I have to admit to being a person that generally likes the Ubuntu brown but this splash is, to be kind, is ugly.

This doesn't bother me too much as it is only up for a few seconds.  This is a good thing.

I feel the same way about the splash business. The boot times aren't an issue nor is the splash as they're both quickly dispensed with.

---

### Post by tjeremiah on 2009-10-01
does anyone believe it will allow us today to finally do something with the GDM, meaning the final version to customize?

---

### Post by zekopeko on 2009-10-01
> **tjeremiah said:**
> does anyone believe it will allow us today to finally do something with the GDM, meaning the final version to customize?

If you are thinking about the old GDM customization options the answer is NO.

---

### Post by Eversmann on 2009-10-01
I don't mind the old customization, but we need something, so we can tweak the current one (i loved the original mockup)

---

### Post by Mr. Picklesworth on 2009-10-01
Haven't tried this yet, but you could *probably* run the various configuration panels (eg: appearance-preferences) as gdm, since it uses the same infrastructure as a normal GNOME desktop... not sure how to get it writing to your display, though.

---

### Post by tjeremiah on 2009-10-02
Bump!

---

### Post by Amaranth on 2009-10-02
The only way to tweak the appearance of gdm is sudo -u gdm dbus-launch gnome-appearance-properties (to set GTK+ theme and wallpaper) and sudo -u gdm dbus-launch gconf-editor (to toggle user list on/off).

Basically you can't do much more than change the colors used.

---

### Post by ranch hand on 2009-10-02
I just gave that a whack on a clean install and got;
```

sam@sam-desktop:~$ sudo -u gdm dbus-launch gnome-appearance-properties

(gnome-appearance-properties:2701): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
I/O error : No such file or directory
I/O error : No such file or directory

```
I think that maybe the bugger isn't quite ready.

---

### Post by Amaranth on 2009-10-02
Dang, guess I should have tested that one. Looks like you'll be stuck with gconf-editor for everything instead.

---

### Post by ranch hand on 2009-10-02
Just for giggles I changed to another 9.10 variant, a Stoner Edition 1.1 (9.04 variation) upgraded to 9.10 and tried this again.  The result boil down to the sameresult but the out put is MUCH more impressive.
```

stoney@stoney-desktop:~$ sudo -u gdm dbus-launch gnome-appearance-properties

(gnome-appearance-properties:32008): capplet-common-WARNING **: Could not open file "/usr/share/themes/Glow Cinder Dark/gtk-2.0/gtkrc"

(gnome-appearance-properties:32008): capplet-common-WARNING **: Could not open file "/usr/share/themes/Glow Flower Dark/gtk-2.0/gtkrc"

(gnome-appearance-properties:32008): capplet-common-WARNING **: Could not open file "/usr/share/themes/Glow Lava Dark/gtk-2.0/gtkrc"

(gnome-appearance-properties:32008): capplet-common-WARNING **: Could not open file "/usr/share/themes/CarbonGold/gtk-2.0/gtkrc"

(gnome-appearance-properties:32008): capplet-common-WARNING **: Could not open file "/usr/share/themes/Glow Cinder/gtk-2.0/gtkrc"

(gnome-appearance-properties:32008): capplet-common-WARNING **: Could not open file "/usr/share/themes/Glow Water Dark/gtk-2.0/gtkrc"

(gnome-appearance-properties:32008): capplet-common-WARNING **: Could not open file "/usr/share/themes/Glow Grass Dark/gtk-2.0/gtkrc"

(gnome-appearance-properties:32008): capplet-common-WARNING **: Could not open file "/usr/share/themes/Glow Ice Dark/gtk-2.0/gtkrc"

(gnome-appearance-properties:32008): capplet-common-WARNING **: Could not open file "/usr/share/themes/Glow Ice/gtk-2.0/gtkrc"

(gnome-appearance-properties:32008): capplet-common-WARNING **: Could not open file "/usr/share/themes/Glow Fire/gtk-2.0/gtkrc"

(gnome-appearance-properties:32008): capplet-common-WARNING **: Could not open file "/usr/share/themes/Glow Lava/gtk-2.0/gtkrc"

(gnome-appearance-properties:32008): capplet-common-WARNING **: Could not open file "/usr/share/themes/Glow Water/gtk-2.0/gtkrc"

(gnome-appearance-properties:32008): capplet-common-WARNING **: Could not open file "/usr/share/themes/Glow Flower/gtk-2.0/gtkrc"

(gnome-appearance-properties:32008): capplet-common-WARNING **: Could not open file "/usr/share/themes/Glow Fire Dark/gtk-2.0/gtkrc"

(gnome-appearance-properties:32008): capplet-common-WARNING **: Could not open file "/usr/share/themes/Glow Sand Dark/gtk-2.0/gtkrc"

(gnome-appearance-properties:32008): capplet-common-WARNING **: Could not open file "/usr/share/themes/Glow Grass/gtk-2.0/gtkrc"

(gnome-appearance-properties:32008): capplet-common-WARNING **: Could not open file "/usr/share/themes/Glow Sand/gtk-2.0/gtkrc"

(gnome-appearance-properties:32008): capplet-common-WARNING **: Could not open file "/usr/share/themes/Aero/gtk-2.0/gtkrc"

(gnome-appearance-properties:32008): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
/usr/share/themes/Cylon Eye '72/gtk-2.0/gtkrc:79: Unable to locate image file in pixmap_path: "Others/focus.png"
/usr/share/themes/Cylon Eye '72/gtk-2.0/gtkrc:82: Background image options specified without filename

(gnome-appearance-properties:32013): Gtk-WARNING **: Theme directory scalable/apps/24 of theme OSX_Iconset has no size field


(gnome-appearance-properties:32013): Gtk-WARNING **: Theme directory  scalable/stock/128 of theme OSX_Iconset has no size field


(gnome-appearance-properties:32013): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
/usr/share/themes/DarkWood/gtk-2.0/gtkrc:51: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/usr/share/themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/usr/share/themes/Descent/gtk-2.0/gtkrc:919: Unable to locate image file in pixmap_path: "Scrollbars/stepper-up-insens.png"
/usr/share/themes/Descent/gtk-2.0/gtkrc:923: Background image options specified without filename
/usr/share/themes/Descent/gtk-2.0/gtkrc:962: Unable to locate image file in pixmap_path: "Scrollbars/stepper-down-insens.png"
/usr/share/themes/Descent/gtk-2.0/gtkrc:966: Background image options specified without filename
/usr/share/themes/Descent/gtk-2.0/gtkrc:1005: Unable to locate image file in pixmap_path: "Scrollbars/stepper-right-insens.png"
/usr/share/themes/Descent/gtk-2.0/gtkrc:1009: Background image options specified without filename
/usr/share/themes/Descent/gtk-2.0/gtkrc:1048: Unable to locate image file in pixmap_path: "Scrollbars/stepper-left-insens.png"
/usr/share/themes/Descent/gtk-2.0/gtkrc:1052: Background image options specified without filename
/usr/share/themes/Descent/gtk-2.0/gtkrc:1659: Unable to locate image file in pixmap_path: "ListHeaders/list_header-pressed.png"
/usr/share/themes/Descent/gtk-2.0/gtkrc:1662: Background image options specified without filename

** (gnome-appearance-properties:32013): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Descent/gtk-2.0/Check-Radio/check2.png: Failed to open file '/usr/share/themes/Descent/gtk-2.0/Check-Radio/check2.png': Permission denied


(gnome-appearance-properties:32013): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gnome-appearance-properties:32013): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

** (gnome-appearance-properties:32013): WARNING **: Pixbuf theme: Cannot load pixmap file /usr/share/themes/Descent/gtk-2.0/Check-Radio/option2.png: Failed to open file '/usr/share/themes/Descent/gtk-2.0/Check-Radio/option2.png': Permission denied


(gnome-appearance-properties:32013): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gnome-appearance-properties:32013): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed
I/O error : No such file or directory
I/O error : No such file or directory

```
Just thought I would share that.  Kind of a jaw dropper.

---

### Post by ranch hand on 2009-10-02
> **Amaranth said:**
> Dang, guess I should have tested that one. Looks like you'll be stuck with gconf-editor for everything instead.
Yup it looks that way but I don't seem to get any results there either.

I think that we can probably put up with the way it is (ugly) for the few seconds it is up.  It works and I am more interested in function than eye candy.

---

### Post by tjeremiah on 2009-10-02
> **Amaranth said:**
> The only way to tweak the appearance of gdm is sudo -u gdm dbus-launch gnome-appearance-properties (to set GTK+ theme and wallpaper) and sudo -u gdm dbus-launch gconf-editor (to toggle user list on/off).

Basically you can't do much more than change the colors used.

ok, that works, but the accessibly icon wont remove itself from my panel. (the blue icon next to the temp/time)

---

### Post by stevetxt on 2009-10-02
I removed the accessibility icon from my panel.  It was really hard to find a solution posted in a past forum but I finally did.  If I remember right, I went to system > preferences > keyboard > accessibility.

There i unchecked the box "Accessibility features can be toggled with keyboard shortcuts."

A little strange.  Please confirms if this works, in case I am remembering wrong.

---

### Post by Longinus00 on 2009-10-02
> **stevetxt said:**
> I removed the accessibility icon from my panel.  It was really hard to find a solution posted in a past forum but I finally did.  If I remember right, I went to system > preferences > keyboard > accessibility.

There i unchecked the box "Accessibility features can be toggled with keyboard shortcuts."

A little strange.  Please confirms if this works, in case I am remembering wrong.

system > preference > assistive technologies preferences lets you get access to all the accessibility options.

---

### Post by tjeremiah on 2009-10-02
> **stevetxt said:**
> I removed the accessibility icon from my panel.  It was really hard to find a solution posted in a past forum but I finally did.  If I remember right, I went to system > preferences > keyboard > accessibility.

There i unchecked the box "Accessibility features can be toggled with keyboard shortcuts."

A little strange.  Please confirms if this works, in case I am remembering wrong.

thanks, that works :)

---

### Post by hansheng on 2009-10-03
I suggest that let us customize(add and change) the GDM background first.  :-({|=

---

### Post by scradock on 2009-10-03
> **hansheng said:**
> i suggest that let us customize(add and change) the gdm background first.  :-({|=
+1

---

### Post by ranch hand on 2009-10-03
> **hansheng said:**
> I suggest that let us customize(add and change) the GDM background first.  :-({|=
+1
And xsplash.

---

### Post by Longinus00 on 2009-10-03
The current gdm background is```
/usr/share/images/xsplash/bg_2560x1600.jpg
```

The future xsplash background is likely to default to that as well. It's probably going to be overwritten atleast once while on the way to release but you can just keep changing it.

---

### Post by ranch hand on 2009-10-03
I will try that but with my resolution it has been using bg_1440x900.  I kenw they had to have changed it because I had replaced that file.

---

### Post by Longinus00 on 2009-10-03
> **ranch hand said:**
> I will try that but with my resolution it has been using bg_1440x900.  I kenw they had to have changed it because I had replaced that file.

In the future xsplash will probably only default to the file I posted instead of picking between several different files.
[https://code.launchpad.net/~bratsche/xsplash/trim-some-image-fat/+merge/12557](https://code.launchpad.net/~bratsche/xsplash/trim-some-image-fat/+merge/12557)

---

### Post by ranch hand on 2009-10-03
Sounds good to me.

Have changed that file.  Have not tried it yet in middle of a slow update.

Also converted the same image to .png and renamed it warty-final-ubuntu in the /user/share/backgrounds but I don't think that is where the GDM is now getting its image.

I will see when I reboot this bugger.

---

### Post by ranch hand on 2009-10-03
Nope no good.  Same old ugly.  I kind of like the new login box.

I have one more 64bit version of Kinky Kitten (9.10) to update.  As slow as things are going, I think I will replace all the bg_whatever.jpg files.

GDM is not using the /user/share/backgrounds/warty-final-ubuntu file any more.  It has to be coming from somewhere.

---

### Post by Longinus00 on 2009-10-03
> **ranch hand said:**
> Nope no good.  Same old ugly.  I kind of like the new login box.

I have one more 64bit version of Kinky Kitten (9.10) to update.  As slow as things are going, I think I will replace all the bg_whatever.jpg files.

GDM is not using the /user/share/backgrounds/warty-final-ubuntu file any more.  It has to be coming from somewhere.

I already said where it was on the last page.

---

### Post by ranch hand on 2009-10-03
> **Longinus00 said:**
> I already said where it was on the last page.
Yes you did.  However I have replaced ALL the bg_whatever.jpg files on this version of 9.10 (upgraded Stoner Edition1.1 - a 9.04 variant) and the GDM background is the same although the xsplash background is now the same as my wallpaper.

One thing that has changed since i last had this all working is that instead of xsplash, GDM, xsplash, wallpaper, we have xsplash, GDM, xsplash, GDM, wallpaper.  The GDM background just flashs on and off before the wallpaper comes up.

---

### Post by tawmas on 2009-10-03
> **Amaranth said:**
> Dang, guess I should have tested that one. Looks like you'll be stuck with gconf-editor for everything instead.

Probably it got fixed with an update.

```
sudo -u gdm dbus-launch gnome-appearance-properties
```

is working for me.

---

### Post by ranch hand on 2009-10-03
[Longinus00]("http://ubuntuforums.org/member.php?u=409388")
I AM SORRY.

I am also simple.  I had changed all of the bg images EXCEPT bg_2560x1600.  As bugs Bunny would say "what a moroon".

I went and double checked, and found I had screwed up and fixed it.  Every thing is working great now.

Thank You Very Much.

---

