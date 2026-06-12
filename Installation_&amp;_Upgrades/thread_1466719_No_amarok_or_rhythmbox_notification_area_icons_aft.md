---
title: "No amarok or rhythmbox notification area icons after upgrade to Lucid"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by bolucpap on 2010-04-30
Hi, completed the first of my five pending Lucid upgrades a few hours ago, the upgrade progress went real smooth. 
So, I have been checking various apps to make sure they are working ok after the upgrade, and noticed that Amarok will not show its notification (tray) icon in the usual place after the upgrade. This is a pain because normally one would launch Amarok, select a playlist/album whatever, than close the window and skip tracks whatever using the tray icon. Did a bit of googling and found a bug in launchpad it's because Amarok draws a custom icon instead of passing a bitmap, or something, but cannot locate the bug again now. I then tested Rhythmbox and found the same issue. Are there any workarounds? Did anybody else notice it's not limited to Amarok?

---

### Post by Rigrig on 2010-05-01
Rhythmbox no longer puts an icon in the Notification Area, instead it adds itself to the Indicator Applet.
You might need to add the Indicator Applet to your panel:
right-click on an empty space in the panel, select 'Add to panel...', and drag the Indicator Applet to your panel.

---

### Post by JustinRez on 2010-05-05
Wow, I see that you're correct.  This is extremely disappointing.  I understand the direction they're moving in with this Indicator app but it's nowhere near being as useful as it needs to be... I also miss being able to bring up RythmBox with a single click. I mean... at least make "Show Rythmbox" the first item at the top...

In general, the indicator app is a waste of space. The icons are spaced too far apart and the "messages" menu is useless for me... and I use Gwibber and Pidgin, so you would think it would be useful, but it essentially does what the MeMenu does/should do (and all the other things the MeMenu should be doing is an issue for another post...)

---

### Post by HotDrive on 2010-05-07
Isn't there a way to make the icons appear in the Notification Area again? I've managed to put the volume icon there, setting the "gnome-volume-control-applet" as a start application, but all the rest failed... 
Quite annoying these changes...

---

### Post by stats on 2010-06-03
I removed the indicator-applet, added the notification area applet, and pidgin, amarok and gnome-volume-control-applet use that fine. Functionality has gone back to how it was in jaunty (meaning it's actually functional with left-click show/hide, instead of the newer system which is 'consistently' useless)

---

### Post by Eladon on 2010-06-10
I noticed this, and also that whenever I was listening to Internet radio in Rhythmbox it used to pop up a box near to the notification area, telling me what the next song was.  I loved that, now it's gone.  Is this also because they are using the indicator applet?  :(

[Never mind, I think my install was messed up from upgrading to Lucid, cuz I removed & reinstalled Rhythmbox, and this was OK again]

---

### Post by tamashumi on 2010-07-02
Yea I removed indicator applet by purpose.
It sucks a lot but I want to still use Rhythmbox.

I found an applet called music-applet.
It's not the same as simple "tray" icon like in notification-applet but for now I'll stay with it.
Maybe you;ll find it useful too.
```
sudo-apt get install music-applet
```
Then add to panel and set preferences.

---

### Post by nk8215 on 2010-07-06
> **tamashumi said:**
> Yea I removed indicator applet by purpose.
It sucks a lot but I want to still use Rhythmbox.

I found an applet called music-applet.
It's not the same as simple &quot;tray&quot; icon like in notification-applet but for now I'll stay with it.
Maybe you;ll find it useful too.
```
sudo-apt get install music-applet
```Then add to panel and set preferences.

Oops, an error occurred ;) The correct form would be ```
sudo apt-get install music-applet
``` :)

---

### Post by tamashumi on 2010-08-20
Sorry my mistake ;)

---

### Post by DarkBattM14 on 2010-09-08
hmmm... nice... and there are more options for several players... THNX!! ):P

---

### Post by marmux on 2011-01-07
Take a look here. It explains how to restore the old behavior

[http://www.uluga.ubuntuforums.org/showpost.php?p=9788973&postcount=6]("http://www.uluga.ubuntuforums.org/showpost.php?p=9788973&postcount=6")

---

